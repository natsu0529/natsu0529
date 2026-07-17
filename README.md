# Hi, I'm Natsuhiro Suzuki 👋

I'm a Machine Learning Engineer and undergraduate researcher at the Takenawa Laboratory, Tokyo University of Marine Science and Technology. I enjoy turning research ideas into reliable software, especially where search algorithms, machine learning, and backend systems meet.

- **Research:** Monte Carlo Tree Search (MCTS), reinforcement learning, GBDTs, and efficient search
- **Engineering:** Go, Python, CMake, PostgreSQL, Flutter, and cloud infrastructure
- **Current focus:** search-budget optimization and lightweight learning systems

## Open-source contributions

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

## Selected projects

| Project | What it demonstrates |
| --- | --- |
| [Pet Platform API](https://github.com/natsu0529/pet-app) | A deployed Go/PostgreSQL API with Firebase authentication, SQL migrations, Docker, and documented `curl` examples. |
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
