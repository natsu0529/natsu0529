# Hi, I'm Natsuhiro Suzuki 👋

Machine Learning Engineer and undergraduate researcher at the Takenawa Laboratory, Tokyo University of Marine Science and Technology. I work where search algorithms, machine learning, and production backends meet — and I care most about the unglamorous half: making a research idea survive contact with a deploy pipeline.

- **Research:** Monte Carlo Tree Search, reinforcement learning, GBDTs, search-budget optimization
- **Engineering:** Go, Python, Flutter, PostgreSQL, AWS, CMake
- **Currently:** test-time search for coding agents, and lightweight learning systems

## What I build day to day

Most of my commits land in private repositories, so here is what they are:
backend and ML-infrastructure work on a production recommendation and
generative-media product, shipped continuously with a small team.

- **Deploy orchestration.** Designed and shipped a broker-mediated deployment system for auto-scaling EC2 fleets: a DynamoDB-backed state machine, artifact verification against the registry before promotion, instance-refresh collision handling, and smoke-test gates that block promotion on failure. Delivered as a reviewed 5-part PR series with runbooks and an ADR.
- **Recommendation pipelines.** Built candidate generation from a social follow graph into a served ranking path, with versioned artifacts, explicit rollback, and freshness monitoring with alerting.
- **Reliability and security.** Made external-dependency failure paths fail-closed rather than silently degrading, hardened an authentication flow against account enumeration, and fixed partition-projection loss in the analytics layer.
- **Team practice.** Introduced CODEOWNERS, made resolution of every review thread a merge requirement, and removed date-dependent flakiness from CI.

Tools across that work: Go, Python, Flutter, Terraform/Ansible, AWS (EC2, ASG, Lambda, DynamoDB, Glue, Athena), Redis/RQ, GitHub Actions.

## Projects

| Project | What it is |
| --- | --- |
| **[agent-mcts](https://github.com/natsu0529/mcts-llm-agent)** · [PyPI](https://pypi.org/project/agent-mcts/) | A test-time MCTS search harness that turns a coding agent into a tree-searching one: UCT over isolated git worktrees, test pass-ratio as the value function, live terminal tree. MIT, CI, 12 test modules. Claude Code first, adapter-based for other CLIs. |
| **[cc-plan-tree](https://github.com/natsu0529/cc-plan-tree)** · [PyPI](https://pypi.org/project/cc-plan-tree/) | A Claude Code plugin and Python CLI that turns plan mode into a visual design tree, verifies the tree against the diff that was actually implemented, and embeds it as Mermaid in the PR body. MIT, CI, published through v0.2.0. |
| **[original_LLM](https://github.com/natsu0529/original_LLM)** | A small Japanese decoder-only Transformer trained from scratch in PyTorch — no pretrained weights, no fine-tuning, tokenizer to sampling loop written by hand. |
| **[Ramen Radar](https://github.com/natsu0529/ramen-radar)** | A Flutter app that ranks nearby ramen shops by combining Google ratings with real travel distance rather than straight-line proximity. |

## Open-source contributions

Six merged pull requests across five upstream projects. The two worth reading:

**[wang-bin/fvp#381](https://github.com/wang-bin/fvp/pull/381)** — checksum-pinned MDK SDK dependencies *(+692/−52, 10 files)*
Optional SHA-256 verification for CMake dependency downloads, making native builds reproducible. Handles cache invalidation, atomic replacement, concurrent builds, and recovery from interrupted installs, with network-free CMake tests on Ubuntu and Windows.

**[rlglab/minizero#13](https://github.com/rlglab/minizero/pull/13)** — Python bindings for MiniZero environments *(+131)*
A pybind11 interface exposing the compiled C++ environments to Python research code: reset/act, legal actions, rewards, feature tensors, action history. Returns copied NumPy arrays rather than exposing C++ internals. Validated on TicTacToe, Go, and 2048.

Also merged: [minizero#12](https://github.com/rlglab/minizero/pull/12) replacing a non-standard `std::bitset::_Find_first()` dependency with a portable `__builtin_ctzll()` fallback for Clang/libc++ *(+63/−43)*; a trained-policy documentation GIF for [Gymnasium#1654](https://github.com/Farama-Foundation/Gymnasium/pull/1654); and documentation fixes to [xgboost#12392](https://github.com/dmlc/xgboost/pull/12392) and [aeon#3801](https://github.com/aeon-toolkit/aeon/pull/3801).

## Affiliation

4th-year undergraduate, Tokyo University of Marine Science and Technology — Logistics and Information Engineering.
Undergraduate researcher, Takenawa Laboratory.

## Contact

Open to conversations about ML research, open-source collaboration, and engineering opportunities.

[suzukioff.com](https://suzukioff.com) · [LinkedIn](https://www.linkedin.com/in/natsuhiro-suzuki-1b6a90382/) · [suzuki@suzukioff.com](mailto:suzuki@suzukioff.com)
