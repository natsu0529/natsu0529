# Natsuhiro Suzuki

Undergraduate researcher at the **Takenawa Laboratory**, Tokyo University of Marine Science and Technology. I work on **search-budget allocation for Monte Carlo Tree Search in two-player zero-sum games** — and on getting search results out of the framework they were published in and into tools people actually run.

**Interests:** MCTS · AlphaZero/MuZero-style systems · reinforcement learning · test-time search for LLM agents · GBDTs

## Research

**Search-budget allocation for MCTS in two-player zero-sum games** (Takenawa Laboratory).
Strength in AlphaZero-style systems is usually bought by spending more simulations. I am interested in the allocation question instead: given a *fixed* budget, where should it go, and when do additional simulations stop changing the decision?

## Research infrastructure

Ordered by research relevance rather than size.

### [agent-mcts](https://github.com/natsu0529/mcts-llm-agent) — test-time MCTS over real software tasks · [PyPI](https://pypi.org/project/agent-mcts/) · MIT

[SWE-Search (ICLR 2025)](https://arxiv.org/abs/2410.20285) reported a ~23% relative improvement on SWE-bench by putting MCTS on top of software agents — but that result lives inside a research framework. `agent-mcts` brings it to the agents people actually run.

- Real UCT — selection, expansion, evaluation, backup — not best-of-N.
- Each node is an isolated `git worktree` plus a forked agent session, so filesystem *and* conversation state branch together and every node stays reproducible as an ordinary git branch.
- Value function is the project's own test suite: exit code plus partial credit by pass ratio, with failing output fed into the children's revision prompts.
- Every state change is journaled append-only, so an interrupted search is still a valid, inspectable tree — MCTS is anytime, and the harness respects that.
- Search hyperparameters, the UCT constant included, are first-class and configurable: it is built to double as a harness for test-time-search experiments, not just as a CLI.

Agent-agnostic by design — a thin adapter layer speaks each agent's headless mode, and the search engine never knows which one it is driving. MIT, CI, 12 test modules.

### [rlglab/minizero](https://github.com/rlglab/minizero) — merged upstream

MiniZero is RLGLab's AlphaZero/MuZero training framework (IEEE ToG). Both contributions target the friction between the compiled C++ core and the Python side research actually runs in.

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
