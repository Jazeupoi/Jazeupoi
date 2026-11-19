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
| ✅ | [#21525](https://github.com/boykopovar/AnyPS5/pull/21525) | LibreSSL builds on macOS |
| ✅ | [#21767](https://github.com/boykopovar/AnyPS5/pull/21767) | LibreSSL3: missing `<initializer_list>` |
| ✅ | [#22313](https://github.com/boykopovar/AnyPS5/pull/22313) | `select` test waits for the loopback datagram (failed 19 of 20 runs on macOS) |
| ✅ | [#22859](https://github.com/boykopovar/AnyPS5/pull/22859) | NKWebKit: fix a test that crashed on macOS (clang called the test's own constructor instead of the export) |
| 👍 | [#21766](https://github.com/boykopovar/AnyPS5/pull/21766) | Relinker: Syobon Action from 7.5 to 29.5 FPS under Rosetta |
| 👍 | [#21972](https://github.com/boykopovar/AnyPS5/pull/21972) | AGC: fewer label stores on macOS (SuperTuxKart frame time 147 → 132 ms) |
| 👍 | [#22572](https://github.com/boykopovar/AnyPS5/pull/22572) | AGC: reject command-buffer jump loops at once (`agc_driver` 24–194 s → 12 s on Windows) |

✅ merged · 👍 approved · 🟡 in review

### Game reports

| Game | Result on Windows / RTX 2060 |
|---|---|
| [Clone Hero: Encore](https://github.com/boykopovar/AnyPS5/discussions/23570) | First report in AnyPS5: menu, song list and a song at ~120 FPS, audio checked against the song's stems |
| [Afterglow](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19730524) | Still stops before the first frame with a warm cache on NVIDIA (on AMD a warm cache gets past it) |

I also test other contributors' pull requests on macOS and Windows, with Vulkan validation and negative controls.
