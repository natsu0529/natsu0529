# Natsuhiro Suzuki (鈴木 夏大)

I am a fourth-year undergraduate in the Takenawa Laboratory at Tokyo University of Marine Science and Technology (TUMSAT), where I study search algorithms and reinforcement learning for game AI. I will start the master's program at TUMSAT in April 2027.

Alongside my research, I work at Meltly Inc. on the recommender system of Days AI, an AI illustration app, handling most of its machine learning and infrastructure. Since November 2026 I have also been a reinforcement learning research intern at [GHELIA Inc.](https://ghelia.com/)

While I am a student, I am open to remote, part-time research positions related to search and reinforcement learning.

[Homepage](https://suzukioff.com/en/) ([日本語](https://suzukioff.com/), [中文](https://suzukioff.com/zh/)) / [LinkedIn](https://www.linkedin.com/in/natsuhiro-suzuki-1b6a90382/) / [Email](mailto:suzuki@suzukioff.com) / [Zenn](https://zenn.dev/natsu529) / [Qiita](https://qiita.com/natsu529)

## Research

I study search algorithms for game AI, and how to improve the quality of their decisions, through both theory and experiments. I am interested in methods that combine search with learning.

In my experiments I reimplement the baselines in my own codebase and compare them under identical conditions. I evaluate win rates over a sufficient number of games and with significance tests. I also send features and fixes to [MiniZero](https://github.com/rlglab/minizero), the training framework I use in my research.

I will list papers on my [homepage](https://suzukioff.com/en/) once they are public.

## Open source

These are my main contributions to external projects. The rest are in [this list of merged pull requests](https://github.com/search?q=author%3Anatsu0529+is%3Apr+is%3Amerged+is%3Apublic+-user%3Anatsu0529&type=pullrequests).

- [Restored Linux CI for the Leela Chess Zero chess engine](https://github.com/LeelaChessZero/lc0/pull/2516). Switched the Linux build to Microsoft’s NuGet package for ONNX Runtime. In a [follow-up PR](https://github.com/LeelaChessZero/lc0/pull/2518), I verified all five Syzygy endgame tablebase tests in CI and checked that the engine returned a move using the ONNX CPU backend.
- [Checksum verification for dependencies downloaded by CMake](https://github.com/wang-bin/fvp/pull/381) (wang-bin/fvp #381). Added SHA-256 verification for the native dependency downloaded at build time, which makes builds reproducible. The change also handles cache invalidation, concurrent runs, and recovery from interrupted installs.
- [Python bindings for MiniZero environments](https://github.com/rlglab/minizero/pull/13) (rlglab/minizero #13). Made the environments of MiniZero, an AlphaZero / MuZero training framework, usable directly from Python research code. Verified with TicTacToe, Go, and 2048.

## Software

- [mac-alpha-zero](https://github.com/natsu0529/mac-alpha-zero) ([PyPI](https://pypi.org/project/mac-alpha-zero/)). A Python library for training Connect Four and Othello agents through self-play on Apple Silicon. It implements batched Monte Carlo tree search and Gumbel AlphaZero using MLX. You can play against the released Othello model.
- [agent-mcts](https://github.com/natsu0529/agent-mcts) ([PyPI](https://pypi.org/project/agent-mcts/)). A harness that makes a coding agent run tree search (MCTS) at test time. Each node is expanded as an independent git worktree and agent session, and UCT searches with the test pass rate as the value.

## Experience

**Reinforcement Learning Research Intern, GHELIA Inc.** (Nov 2026 – present)

I work on reinforcement learning research at GHELIA, an AI research and development company.

**Software Engineer, ML and Infrastructure (contract), Meltly Inc.** (Jul 2025 – present)

I am on the small team behind Days AI, an AI illustration app, where I handle most of the machine learning and infrastructure for its recommender system. Most of these commits are in private repositories.

I connected candidate generation from the social graph to the ranking path that is actually served. I also built a model that predicts how likely a post is to be liked, for evaluating the recommender, so that we can estimate the effect of an algorithm change before it reaches production. On the infrastructure side, I implemented deploy orchestration for auto-scaling fleets, including artifact verification before promotion, smoke tests, and rollback, as well as fail-closed handling of outages in external services.

This work is covered in a [case study interview by Classmethod, Inc.](https://classmethod.jp/cases/meltly-craftlab/) (in Japanese), published in October 2026.
