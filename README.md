<p align="center">
  <img src="banner.svg" alt="C++ · macOS · Windows" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white" alt="macOS">
  <img src="https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows11&logoColor=white" alt="Windows">
  <img src="https://img.shields.io/badge/Vulkan-AC162C?style=for-the-badge&logo=vulkan&logoColor=white" alt="Vulkan">
</p>

### Contributing to [AnyPS5](https://github.com/boykopovar/AnyPS5)

Building, testing and fixing it on an Apple M4 (Rosetta 2, MoltenVK) and on Windows with an NVIDIA RTX 2060.

| | Pull request | What it does |
|---|---|---|
| ✅ | [#21972](https://github.com/boykopovar/AnyPS5/pull/21972) | AGC: fewer label stores on macOS (SuperTuxKart frame time 147 → 132 ms) |
| ✅ | [#21766](https://github.com/boykopovar/AnyPS5/pull/21766) | Relinker: Syobon Action from 7.5 to 29.5 FPS under Rosetta |
| ✅ | [#22859](https://github.com/boykopovar/AnyPS5/pull/22859) | NKWebKit: fix a test that crashed on macOS (clang called the test's own constructor instead of the export) |
| ✅ | [#22313](https://github.com/boykopovar/AnyPS5/pull/22313) | `select` test waits for the loopback datagram (failed 19 of 20 runs on macOS) |
| ✅ | [#21767](https://github.com/boykopovar/AnyPS5/pull/21767) | LibreSSL3: missing `<initializer_list>` |
| ✅ | [#21525](https://github.com/boykopovar/AnyPS5/pull/21525) | LibreSSL builds on macOS |
| 👍 | [#22572](https://github.com/boykopovar/AnyPS5/pull/22572) | AGC: reject command-buffer jump loops at once (`agc_driver` 24–194 s → 12 s on Windows) |
| 🟡 | [#24201](https://github.com/boykopovar/AnyPS5/pull/24201) | Shader: a barrier before a scratch pool slot is released on MoltenVK (`agc_driver_scratch_pool` failed 17 of 20 runs on the M4; 50 of 50 pass) |
| 🟡 | [#24223](https://github.com/boykopovar/AnyPS5/pull/24223) | libcurl: a real `socketpair` for multi wakeups on macOS (`guest_curl_sockets` failed 19 of 20 runs; 50 of 50 pass) |
| 👍 | [#24320](https://github.com/boykopovar/AnyPS5/pull/24320) | libc: `floorl`, `ceill` and `truncl` raise inexact when they round on macOS, as the console does |
| 👍 | [#24311](https://github.com/boykopovar/AnyPS5/pull/24311) | `guest_math`: read only the standard exception flags (failed on every macOS run) |

✅ merged · 👍 approved · 🟡 in review

### Bug reports

| Issue | Found |
|---|---|
| [#23708](https://github.com/boykopovar/AnyPS5/issues/23708) | `agc_storage_write_back_host_retile` failed 3 runs in 4 on Windows / RTX 2060; bisected to the pull request that added it. The cause is a race in the test; the fix, [#23751](https://github.com/boykopovar/AnyPS5/pull/23751), is in review |

### Game reports

| Game | Result |
|---|---|
| [Clone Hero: Encore](https://github.com/boykopovar/AnyPS5/discussions/23570) | First report in AnyPS5: menu, song list and a song at ~120 FPS on Windows / RTX 2060, audio checked against the song's stems |
| [SudokuZen](https://github.com/boykopovar/AnyPS5/discussions/12236#discussioncomment-19745687) | Quits at its first draw whenever NVIDIA's driver shader cache is empty (4/4 runs; 5/5 fine with a warm cache): the #4399 shader still hits ps5-opengl's 2 s wait on `main` |
| [Afterglow](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19730524) | Still stops before the first frame with a warm cache on Windows / RTX 2060 (on AMD a warm cache gets past it) |
| [vkQuake](https://github.com/boykopovar/AnyPS5/pull/21708#pullrequestreview-5956522777) | Black screen on `main` on NVIDIA; with #21708 it loads and plays (review) |
| [SuperTuxKart](https://github.com/boykopovar/AnyPS5/discussions/17047#discussioncomment-19662997) | Was drawn purple on macOS and Windows / NVIDIA after #16053; fixed on `main` by #20827: the menu draws correctly on macOS at 44 FPS |
| [Syobon Action](https://github.com/boykopovar/AnyPS5/discussions/5932#discussioncomment-19661388) | Slow on macOS; cause found and fixed in #21766 (7.5 → 29.5 FPS) |

I also test other contributors' pull requests on macOS and Windows, with Vulkan validation and negative controls.
