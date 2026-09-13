# Natsuhiro Suzuki

Undergraduate researcher at the **Takenawa Laboratory**, Tokyo University of Marine Science and Technology, working on Monte Carlo Tree Search and reinforcement learning in AlphaZero-style game engines. First-author manuscript in preparation, targeting **IEEE Conference on Games (CoG) 2027**.

**Looking for:** research internships in search, reinforcement learning, and test-time compute.

## Research

MCTS and reinforcement learning for AlphaZero-style engines, at the Takenawa Laboratory. The current project is being prepared for submission, so the write-up is not public yet.

What I can show is how I run experiments:

- **Baselines get reimplemented in my own codebase.** Published numbers come from different engines, network sizes, and evaluation conditions, so comparing across papers is not a comparison. If a method is my baseline, it runs in my environment under my conditions.
- **Conclusions wait for enough games.** Win rates are reported with significance tests and match counts large enough to separate a real effect from noise, and I re-run evaluations when a change to the training setup makes earlier numbers non-comparable.
- **Everything goes in a running log** — what changed, what the number did, what to try next — including the runs that went against what I expected. Those are the ones worth keeping.
- **Public models and libraries where possible**, so results can be reproduced outside my lab.

Day to day this means PyTorch, C++ via pybind11, CUDA, and a lot of self-play compute to schedule.

## Open-source contributions

Six merged pull requests across five upstream projects, mostly in the research-tooling layer I work in.

### [rlglab/minizero](https://github.com/rlglab/minizero) — merged

MiniZero is RLGLab's AlphaZero/MuZero training framework (IEEE ToG). Both contributions target the friction between its compiled C++ core and the Python side research actually happens in.

- **[PR #13](https://github.com/rlglab/minizero/pull/13)** *(+131)* — a pybind11 interface exposing the compiled environments to Python: reset/act, legal actions, rewards, feature tensors, action history. Returns action IDs and copied NumPy arrays rather than handing out C++ internals. Validated across TicTacToe, Go, and 2048, including configuration-dependent board sizes and environment-specific reset signatures.
- **[PR #12](https://github.com/rlglab/minizero/pull/12)** *(+63/−43)* — replaced a non-standard `std::bitset::_Find_first()` dependency with a portable `__builtin_ctzll()` fallback while preserving the libstdc++ fast path, so MiniZero builds under Clang/libc++.

### [wang-bin/fvp](https://github.com/wang-bin/fvp) — merged

- **[PR #381](https://github.com/wang-bin/fvp/pull/381)** *(+692/−52, 10 files)* — checksum-pinned MDK SDK dependencies: optional SHA-256 verification for CMake dependency downloads, with cache invalidation, atomic replacement, concurrent-build protection, and recovery from interrupted installs. Network-free CMake tests on Ubuntu and Windows.

Also merged: a trained-policy documentation GIF for [Gymnasium#1654](https://github.com/Farama-Foundation/Gymnasium/pull/1654), and documentation fixes to [xgboost#12392](https://github.com/dmlc/xgboost/pull/12392) and [aeon#3801](https://github.com/aeon-toolkit/aeon/pull/3801).

## Projects

| Project | What it is |
| --- | --- |
| **[agent-mcts](https://github.com/natsu0529/mcts-llm-agent)** · [PyPI](https://pypi.org/project/agent-mcts/) · MIT | A test-time MCTS search harness for coding agents. Real UCT — selection, expansion, evaluation, backup — with each node an isolated `git worktree` plus a forked agent session, the project's own test suite as the value function, and an append-only journal so an interrupted search is still a valid tree. Search hyperparameters are first-class, so it doubles as a harness for test-time-search experiments. CI, 12 test modules. |
| **[original_LLM](https://github.com/natsu0529/original_LLM)** | A small Japanese decoder-only Transformer trained from scratch in PyTorch — no pretrained weights, no fine-tuning, tokenizer to sampling loop written by hand. Kept as a controlled-experiment log with per-run configs, losses, and the reasoning for what to try next. |
| **[cc-plan-tree](https://github.com/natsu0529/cc-plan-tree)** · [PyPI](https://pypi.org/project/cc-plan-tree/) · MIT | A Claude Code plugin and CLI that turns plan mode into a design tree, verifies it against the diff that was actually implemented, and embeds it as Mermaid in the PR body. |
| **[Ramen Radar](https://github.com/natsu0529/ramen-radar)** | A Flutter app that ranks nearby ramen shops by real travel distance rather than straight-line proximity. |

## Engineering

Most of my commits land in private repositories: backend and ML-infrastructure work on a production recommendation and generative-media product, shipped continuously with a small team. Deploy orchestration for auto-scaling fleets — a state machine, artifact verification before promotion, smoke-test gates, rollback — plus candidate generation from a social graph into a served ranking path with versioned artifacts, and fail-closed handling of external-dependency failure. Go, Python, AWS, Terraform/Ansible, Redis/RQ, GitHub Actions.

It is why experiment infrastructure is something I build rather than wait for.

## Affiliation

4th-year undergraduate, Tokyo University of Marine Science and Technology — Logistics and Information Engineering.
Undergraduate researcher, Takenawa Laboratory.

## Contact

Open to conversations about search, reinforcement learning, and research internships.

[suzukioff.com](https://suzukioff.com) · [LinkedIn](https://www.linkedin.com/in/natsuhiro-suzuki-1b6a90382/) · [suzuki@suzukioff.com](mailto:suzuki@suzukioff.com)
