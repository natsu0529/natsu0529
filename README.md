# Natsuhiro Suzuki

Undergraduate researcher at the **Takenawa Laboratory**, Tokyo University of Marine Science and Technology. I work on **learned search-budget allocation for AlphaZero-style MCTS** — deciding, before search begins, how much of a game's fixed simulation budget each move should get — and on getting search results out of the framework they were published in and into tools people actually run.

**Interests:** MCTS · AlphaZero/MuZero-style systems · reinforcement learning · time management in game search · test-time search for LLM agents

## Research

**Whole-game search-budget allocation for AlphaZero-style MCTS, learned end-to-end** — 9×9 Go, Takenawa Laboratory. Manuscript in preparation (target: IEEE CoG).

DS-MCTS (Lan et al., AAAI 2021) and V-MCTS (Ye et al., NeurIPS 2022) speed up PV-MCTS by solving a *local* problem: how far to search *this* position, decided while searching. I work on a different one. Give the engine a fixed simulation budget for the **whole game** under a sudden-death rule — run out and you lose — and ask how much each move should get, decided **before** the search starts so the policy stays compatible with real time controls.

- **Setup.** MiniZero's public 9×9 Go AlphaZero network (3 residual blocks, 3.62M parameters), frozen throughout. Each move is a binary decision: search with 800 simulations, or play the raw policy for a cost of one. The decision is made by a ~4.4k-parameter MLP trained with REINFORCE on win/loss alone, over 240k self-play games, at two operating points (mean budget 50% and 10% of the full search).
- **Results.** Against opponents that do not manage budget — fixed-threshold difficulty gating, including a DS-MCTS State-UN baseline I reimplemented in the same codebase — the learned policy wins 71–93% by driving them to flag-fall. Under a hard-reservation rule where nobody *can* flag-fall, it still beats equal allocation (52–64%) and matches or beats the State-UN baseline (49–65%) at roughly a fifth of its per-move cost.
- **The finding that reshaped the paper.** My original hypothesis was that a position-difficulty signal extracted from the frozen network's intermediate features would drive allocation; a probing study showed those features do carry more budget-relevant signal than the raw board. But when I removed the signal from the allocation policy entirely, nothing changed — head-to-head, the difficulty-aware and difficulty-free policies are indistinguishable (p = 0.15–0.71). Progress information alone — moves remaining, budget remaining — is sufficient in this game. That collapses the budget decision to 0.245 ms per move: 0.03% of one 800-simulation search, and about 1/5 of the State-UN forward pass.
- **Status.** Single seed so far; replication across seeds is running, along with a check that a more direct supervision signal (value gained by searching) reproduces the null result.

## Research infrastructure

The same question — where should a fixed search budget go — runs through the tooling too. Ordered by research relevance rather than size.

### [agent-mcts](https://github.com/natsu0529/mcts-llm-agent) — test-time MCTS over real software tasks · [PyPI](https://pypi.org/project/agent-mcts/) · MIT

[SWE-Search (ICLR 2025)](https://arxiv.org/abs/2410.20285) reported a ~23% relative improvement on SWE-bench by putting MCTS on top of software agents — but that result lives inside a research framework. `agent-mcts` brings it to the agents people actually run.

- Real UCT — selection, expansion, evaluation, backup — not best-of-N.
- Each node is an isolated `git worktree` plus a forked agent session, so filesystem *and* conversation state branch together and every node stays reproducible as an ordinary git branch.
- Value function is the project's own test suite: exit code plus partial credit by pass ratio, with failing output fed into the children's revision prompts.
- Every state change is journaled append-only, so an interrupted search is still a valid, inspectable tree — MCTS is anytime, and the harness respects that.
- Search hyperparameters, the UCT constant included, are first-class and configurable: it is built to double as a harness for test-time-search experiments, not just as a CLI.

Agent-agnostic by design — a thin adapter layer speaks each agent's headless mode, and the search engine never knows which one it is driving. MIT, CI, 12 test modules.

### [rlglab/minizero](https://github.com/rlglab/minizero) — merged upstream

MiniZero is RLGLab's AlphaZero/MuZero training framework (IEEE ToG) and the engine my research runs on. Both contributions target the friction between the compiled C++ core and the Python side research actually happens in.

- **[PR #13](https://github.com/rlglab/minizero/pull/13)** *(+131)* — a pybind11 interface exposing the compiled environments to Python: reset/act, legal actions, rewards, feature tensors, action history. Returns action IDs and copied NumPy arrays rather than handing out C++ internals. Validated across TicTacToe, Go, and 2048, including configuration-dependent board sizes and environment-specific reset signatures.
- **[PR #12](https://github.com/rlglab/minizero/pull/12)** *(+63/−43)* — replaced a non-standard `std::bitset::_Find_first()` dependency with a portable `__builtin_ctzll()` fallback while preserving the libstdc++ fast path, so MiniZero builds under Clang/libc++.

### [original_LLM](https://github.com/natsu0529/original_LLM) — a Japanese decoder-only Transformer from scratch

No pretrained weights and no fine-tuning: tokenizer, training loop, and sampler written by hand in PyTorch. Kept as a controlled-experiment log — a byte-level baseline (3.29M params, `valid_loss` 1.061 at 20k steps) against a char-level run (4.32M params, 4,265 vocab), with what changed, what the number did, and what to try next recorded per run. The log notes explicitly that loss is not comparable across tokenizers and defers those judgements to generation quality.

## Engineering

Most of my commits land in private repositories: backend and ML-infrastructure work on a production recommendation and generative-media product, shipped continuously with a small team. Deploy orchestration for auto-scaling fleets — a state machine, artifact verification before promotion, smoke-test gates, rollback — plus candidate generation from a social graph into a served ranking path with versioned artifacts, and fail-closed handling of external-dependency failure. Go, Python, AWS, Terraform/Ansible, Redis/RQ, GitHub Actions.

I mention it because it is why I can build the infrastructure an experiment needs rather than wait for it. Also merged upstream: [wang-bin/fvp#381](https://github.com/wang-bin/fvp/pull/381) *(+692/−52, 10 files)*, adding checksum-pinned, restart-safe CMake dependency downloads with network-free tests on Ubuntu and Windows; plus a trained-policy documentation GIF for [Gymnasium#1654](https://github.com/Farama-Foundation/Gymnasium/pull/1654) and documentation fixes to [xgboost#12392](https://github.com/dmlc/xgboost/pull/12392) and [aeon#3801](https://github.com/aeon-toolkit/aeon/pull/3801).

Other work: [cc-plan-tree](https://github.com/natsu0529/cc-plan-tree) ([PyPI](https://pypi.org/project/cc-plan-tree/)), a Claude Code plugin that turns plan mode into a design tree and verifies it against the diff that was actually implemented; and [Ramen Radar](https://github.com/natsu0529/ramen-radar), a Flutter app ranking ramen shops by real travel distance rather than straight-line proximity.

## Affiliation

4th-year undergraduate, Tokyo University of Marine Science and Technology — Logistics and Information Engineering.
Undergraduate researcher, Takenawa Laboratory.

## Contact

Open to conversations about search, reinforcement learning, and research engineering.

[suzukioff.com](https://suzukioff.com) · [LinkedIn](https://www.linkedin.com/in/natsuhiro-suzuki-1b6a90382/) · [suzuki@suzukioff.com](mailto:suzuki@suzukioff.com)
