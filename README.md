# Hi, I'm Natsuhiro Suzuki 👋

I'm a Machine Learning Engineer and undergraduate researcher at the Takenawa Laboratory, Tokyo University of Marine Science and Technology. I enjoy turning research ideas into reliable software, especially where search algorithms, machine learning, and backend systems meet.

- **Research:** Monte Carlo Tree Search (MCTS), reinforcement learning, GBDTs, and efficient search
- **Engineering:** Go, Python, CMake, PostgreSQL, Flutter, and cloud infrastructure
- **Current focus:** search-budget optimization and lightweight learning systems

## Open-source contributions

**6 merged pull requests across 5 upstream projects.**

### [Farama-Foundation/Gymnasium](https://github.com/Farama-Foundation/Gymnasium) — merged

[PR #1654: Use a trained-policy GIF for HalfCheetah](https://github.com/Farama-Foundation/Gymnasium/pull/1654)

- Replaced the random-action HalfCheetah documentation GIF with a render of a policy trained with Stable-Baselines3 SAC for 1M timesteps, so the docs show a stable forward-running gait.
- Verified the policy with deterministic evaluation over 10 episodes (11,772 ± 122 mean reward) and confirmed sustained forward motion with no falls or resets across the capture.
- Followed the docs' `gen_gifs.py` conventions (301 frames, 50 ms per frame) and adjusted only the rendered floor extent for visibility, leaving environment dynamics and the policy untouched.

### [wang-bin/fvp](https://github.com/wang-bin/fvp) — merged

[PR #381: Support checksum-pinned MDK SDK dependencies](https://github.com/wang-bin/fvp/pull/381)

- Added optional SHA-256 verification for CMake dependency downloads to make native builds reproducible.
- Implemented cache invalidation, atomic replacement, concurrency protection, and recovery from interrupted installs.
- Added network-free CMake tests for Ubuntu and Windows and improved the related CI and Android example build.

### [rlglab/minizero](https://github.com/rlglab/minizero) — merged

[PR #13: Expose MiniZero environments through Python bindings](https://github.com/rlglab/minizero/pull/13)

- Added a pybind11 interface that lets Python research code directly use MiniZero's compiled C++ game environments.
- Exposed environment control, legal actions, rewards, feature tensors, action history, and metadata with safe NumPy ownership and invalid-action handling.
- Validated the API across TicTacToe, Go, and 2048, including configuration-dependent board sizes and environment-specific reset signatures.

[PR #12: Replace non-standard bitset `_Find_first` usage](https://github.com/rlglab/minizero/pull/12)

- Replaced the non-standard `std::bitset::_Find_first()` dependency with a portable helper while preserving the existing libstdc++ fast path.
- Added a Clang/libc++ fallback that scans 64-bit chunks with `__builtin_ctzll()`, improving macOS toolchain compatibility.
- Updated call sites across the Go, Havannah, and KillallGo environments and validated the fallback and MiniZero Python module builds.

Also merged: minor documentation contributions to [dmlc/xgboost](https://github.com/dmlc/xgboost) ([PR #12392](https://github.com/dmlc/xgboost/pull/12392)) and [aeon-toolkit/aeon](https://github.com/aeon-toolkit/aeon) ([PR #3801](https://github.com/aeon-toolkit/aeon/pull/3801)).

## Selected projects

| Project | What it demonstrates |
| --- | --- |
| [agent-mcts](https://github.com/natsu0529/mcts-llm-agent) | An MIT-licensed test-time MCTS search harness that turns coding agents (Claude Code first) into tree-searching agents — UCT over isolated git worktrees, test pass-ratio as the value function, live terminal tree. [On PyPI](https://pypi.org/project/agent-mcts/). |
| [cc-plan-tree](https://github.com/natsu0529/cc-plan-tree) | A Claude Code plugin + Python CLI that turns plan mode into a visual design tree, verifies the tree against the implemented diff, and embeds it as Mermaid in PR bodies. [On PyPI](https://pypi.org/project/cc-plan-tree/). |
| [original_LLM](https://github.com/natsu0529/original_LLM) | A small Japanese decoder-only Transformer trained from scratch in PyTorch without pretrained models or fine-tuning. |
| [Ramen Radar](https://github.com/natsu0529/ramen-radar) | A Flutter application that combines Google ratings and real travel distance to rank nearby ramen shops. |

## Technical interests

- **Machine learning:** MCTS, AlphaZero-style systems, reinforcement learning, deep learning, and GBDTs
- **Backend:** Go, Python, Django REST Framework, PostgreSQL, REST APIs, and Docker
- **Client:** Flutter, Riverpod, Next.js, and TypeScript
- **Infrastructure:** AWS, Render, Supabase, GitHub Actions, and CMake

## Affiliation

- Undergraduate Researcher, **Takenawa Laboratory**
- 4th-year undergraduate, **Tokyo University of Marine Science and Technology (TUMSAT)**
- Major: Logistics and Information Engineering

## Contact

I'm open to conversations about ML research, open-source collaboration, and engineering opportunities.

- Website: [suzukioff.com](https://suzukioff.com)
- LinkedIn: [Natsuhiro Suzuki](https://www.linkedin.com/in/natsuhiro-suzuki-1b6a90382/)
- Email: [suzuki@suzukioff.com](mailto:suzuki@suzukioff.com)
