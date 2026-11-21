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

#### Highlights

| | Result |
|---|---|
| 🎮 | Syobon Action from 7.5 to 29.5 FPS under Rosetta ([#21766](https://github.com/boykopovar/AnyPS5/pull/21766), merged) |
| 🎮 | osu! no longer closes 2 s after launch on macOS ([#24792](https://github.com/boykopovar/AnyPS5/pull/24792), merged); with #17611 a map plays at 55–60 FPS |
| 🎮 | Savage Wind (Breath of the Wild port) no longer crashes at startup on macOS ([#25091](https://github.com/boykopovar/AnyPS5/pull/25091), approved) |
| 🧪 | 8 titles that stop on mesh shaders start on macOS with #17611 ([review](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6006646487)) |
| 🧪 | Clone Hero: Encore, first report in AnyPS5: plays at ~120 FPS on Windows / RTX 2060 ([report](https://github.com/boykopovar/AnyPS5/discussions/23570)) |

#### Pull requests in review

| | Pull request | What it does |
|---|---|---|
| 👍 | [#22572](https://github.com/boykopovar/AnyPS5/pull/22572) | AGC: reject command-buffer jump loops at once (`agc_driver` 24–194 s → 12 s on Windows) |
| 👍 | [#24201](https://github.com/boykopovar/AnyPS5/pull/24201) | Shader: a barrier before a scratch pool slot is released on MoltenVK (`agc_driver_scratch_pool` failed 17 of 20 runs on the M4; 50 of 50 pass) |
| 👍 | [#24311](https://github.com/boykopovar/AnyPS5/pull/24311) | `guest_math`: read only the standard exception flags (failed on every macOS run) |
| 🟡 | [#24967](https://github.com/boykopovar/AnyPS5/pull/24967) | Relinker: macOS loads games at 0x400000 like Linux and Windows (Ruffle Flash no longer crashes when its imports load) |
| 🟡 | [#25017](https://github.com/boykopovar/AnyPS5/pull/25017) | libkernel: `SOCK_SEQPACKET` socketpairs on macOS (Parallax Browser stopped 2 s after launch; now gets past its socket probe) |
| 👍 | [#25091](https://github.com/boykopovar/AnyPS5/pull/25091) | libc: macOS memory hints inside the unmappable range go to the top of the arena (Savage Wind crashed at startup; now starts and creates its Vulkan device) |

👍 approved · 🟡 in review

<details>
<summary><b>Merged pull requests (11)</b></summary>

| | Pull request | What it does |
|---|---|---|
| ✅ | [#25031](https://github.com/boykopovar/AnyPS5/pull/25031) | Relinker: macOS loads `.sprx` dependencies and `libkernel_sys` (Kodi stopped before starting; now runs its own code) |
| ✅ | [#25093](https://github.com/boykopovar/AnyPS5/pull/25093) | libwebrtc: `main` builds again with Apple clang (a `const` cast in `RtpPacketReceived` stopped the macOS build) |
| ✅ | [#24792](https://github.com/boykopovar/AnyPS5/pull/24792) | Relinker: a macOS game can `mprotect` its own image (osu! closed 2 s after launch on macOS) |
| ✅ | [#21972](https://github.com/boykopovar/AnyPS5/pull/21972) | AGC: fewer label stores on macOS (SuperTuxKart frame time 147 → 132 ms) |
| ✅ | [#21766](https://github.com/boykopovar/AnyPS5/pull/21766) | Relinker: Syobon Action from 7.5 to 29.5 FPS under Rosetta |
| ✅ | [#22859](https://github.com/boykopovar/AnyPS5/pull/22859) | NKWebKit: fix a test that crashed on macOS (clang called the test's own constructor instead of the export) |
| ✅ | [#22313](https://github.com/boykopovar/AnyPS5/pull/22313) | `select` test waits for the loopback datagram (failed 19 of 20 runs on macOS) |
| ✅ | [#21767](https://github.com/boykopovar/AnyPS5/pull/21767) | LibreSSL3: missing `<initializer_list>` |
| ✅ | [#21525](https://github.com/boykopovar/AnyPS5/pull/21525) | LibreSSL builds on macOS |
| ✅ | [#24223](https://github.com/boykopovar/AnyPS5/pull/24223) | libcurl: a real `socketpair` for multi wakeups on macOS (`guest_curl_sockets` failed 19 of 20 runs; 50 of 50 pass) |
| ✅ | [#24320](https://github.com/boykopovar/AnyPS5/pull/24320) | libc: `floorl`, `ceill` and `truncl` raise inexact when they round on macOS, as the console does |

</details>

<details>
<summary><b>Bug reports (5)</b></summary>

| Issue | Found |
|---|---|
| [#23708](https://github.com/boykopovar/AnyPS5/issues/23708) | `agc_storage_write_back_host_retile` failed 3 runs in 4 on Windows / RTX 2060; bisected to the pull request that added it. The cause is a race in the test; the fix, [#23751](https://github.com/boykopovar/AnyPS5/pull/23751), is in review |
| [#24728](https://github.com/boykopovar/AnyPS5/issues/24728) | SuperTuxKart at ~10 FPS on macOS: one GPU round trip per draw, and Rosetta's cost of re-protecting watched memory (~0.2 ms per MiB); a 1 MiB fault-ahead block gains ~3–8 % |
| [#22565](https://github.com/boykopovar/AnyPS5/issues/22565) | `agc_driver` took up to 123 s on Windows because its self-linking buffer check ran to the timeout; the fix, [#22572](https://github.com/boykopovar/AnyPS5/pull/22572), is approved |
| [#22270](https://github.com/boykopovar/AnyPS5/issues/22270) | macOS: guest paths near `PATH_MAX` fail with `ENAMETOOLONG` because the host prefix makes them longer |
| [#22317](https://github.com/boykopovar/AnyPS5/issues/22317) | macOS: `sceNetConnect` with a timeout to a bound, non-listening loopback port returned `EAGAIN` (closed, resolved) |

</details>

<details>
<summary><b>Game reports (10)</b></summary>

| Game | Result |
|---|---|
| [15 mesh-shader titles](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6006646487) | With #17611 on macOS, 8 that stopped on `main` now start (SpeedBreaker, PSXS5, SwanStation, DevilutionX, PSFlyCast, OGBox, Mario 64, FBNeo); the four N64 recompilations ask for 8x MSAA, which the Mac does not offer |
| [Crux2](https://github.com/boykopovar/AnyPS5/discussions/18182#discussioncomment-19796785) | First macOS report: needs `ROSETTA_ADVERTISE_AVX=1` to pass its AVX2 check, then stops at its first present on mesh shaders (#17611) |
| Afterglow ([macOS](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19797074), [Windows](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19730524)) | macOS: the Metal compiler runs out of memory on a 30 MB MSL shader; `APS5_FAST_F32=1` shrinks it to 7–9 MB and it compiles, but the title still exits before its first frame. Windows / RTX 2060: still stops before the first frame with a warm cache (on AMD a warm cache gets past it) |
| [osu! ProjectCadence](https://github.com/boykopovar/AnyPS5/discussions/17969#discussioncomment-19788361) | First macOS report: closed after 2 s; fixed the cause in #24792 (merged), and with #17611 a map plays at 55–60 FPS on the M4 |
| vkQuake ([NVIDIA](https://github.com/boykopovar/AnyPS5/pull/21708#pullrequestreview-5956522777), [macOS](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6002155105)) | Black screen on NVIDIA, fixed by #21708 (merged). On macOS it plays at ~44 FPS with #17611; ccleste and PSteroid5 still need barycentrics (#9387) |
| [Clone Hero: Encore](https://github.com/boykopovar/AnyPS5/discussions/23570) | First report in AnyPS5: menu, song list and a song at ~120 FPS on Windows / RTX 2060, audio checked against the song's stems |
| [SudokuZen](https://github.com/boykopovar/AnyPS5/discussions/12236#discussioncomment-19745687) | Quits at its first draw whenever NVIDIA's driver shader cache is empty (4/4 runs; 5/5 fine with a warm cache): the #4399 shader still hits ps5-opengl's 2 s wait on `main` |
| [Brogue CE](https://github.com/boykopovar/AnyPS5/discussions/23592), [Dungeon Crawl](https://github.com/boykopovar/AnyPS5/discussions/23591), [NetHack](https://github.com/boykopovar/AnyPS5/discussions/23590), [ClanBomber](https://github.com/boykopovar/AnyPS5/discussions/23589), [Towelket](https://github.com/boykopovar/AnyPS5/discussions/23593) | First reports in AnyPS5, all playable on Windows / RTX 2060; Brogue, Dungeon Crawl and Towelket also on macOS. Towelket's itch.io download fails in the game itself |
| [SuperTuxKart](https://github.com/boykopovar/AnyPS5/discussions/17047#discussioncomment-19662997) | Was drawn purple on macOS and Windows / NVIDIA after #16053; fixed on `main` by #20827: the menu draws correctly on macOS at 44 FPS |
| [Syobon Action](https://github.com/boykopovar/AnyPS5/discussions/5932#discussioncomment-19661388) | Slow on macOS; cause found and fixed in #21766 (7.5 → 29.5 FPS) |

</details>

I also test other contributors' pull requests on macOS and Windows, with Vulkan validation and negative controls.
