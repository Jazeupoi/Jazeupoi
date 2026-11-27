<p align="center">
  <img src="banner-linux.svg" alt="C++ · macOS · Windows · Linux" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white" alt="macOS">
  <img src="https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows11&logoColor=white" alt="Windows">
  <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Vulkan-AC162C?style=for-the-badge&logo=vulkan&logoColor=white" alt="Vulkan">
</p>

### Contributing to [AnyPS5](https://github.com/boykopovar/AnyPS5)

Building, testing and fixing it on an Apple M4 (Rosetta 2, MoltenVK), on Windows with an NVIDIA RTX 2060, and on Linux (Ubuntu 24.04 under WSL2 on the same PC).

#### Highlights

| | Result |
|---|---|
| 🎮 | PS5SX2 (PCSX2 port) boots its PS2 BIOS to the language screen on Windows / RTX 2060 ([#26600](https://github.com/boykopovar/AnyPS5/pull/26600), [#26653](https://github.com/boykopovar/AnyPS5/pull/26653) merged, with #27327 and #27140) |
| 🎮 | ProsperoCraft (Minecraft Java launcher): its Java runtime starts and its downloads finish on Windows ([#27330](https://github.com/boykopovar/AnyPS5/pull/27330), [#26653](https://github.com/boykopovar/AnyPS5/pull/26653) merged) |
| 🎮 | osu! no longer closes after 2 s on macOS; with #17611 a map plays at 55–60 FPS ([#24792](https://github.com/boykopovar/AnyPS5/pull/24792), merged) |
| 🎮 | Syobon Action from 7.5 to 29.5 FPS under Rosetta ([#21766](https://github.com/boykopovar/AnyPS5/pull/21766), merged) |
| 🎮 | Half-Life (XashPS5) reaches its first map on macOS (with #17611) and on Windows at 60 FPS ([#25658](https://github.com/boykopovar/AnyPS5/pull/25658), merged) |

<details>
<summary><b>More results (6)</b></summary>

| | Result |
|---|---|
| 🎮 | Savage Wind (Breath of the Wild port) no longer crashes at startup on macOS ([#25091](https://github.com/boykopovar/AnyPS5/pull/25091)) |
| 🔍 | PS5SX2 frame time measured: 38 GPU round trips per frame, and a fast/slow start mode ([#25912](https://github.com/boykopovar/AnyPS5/issues/25912#issuecomment-7216827537)) |
| 🔍 | Afterglow on NVIDIA: found the change that broke `APS5_ASYNC_PIPELINE_WORDS` ([#26186](https://github.com/boykopovar/AnyPS5/issues/26186)) |
| 🧪 | `guest_net_ctl` abort reproduced on Windows; the fix cites the numbers ([#27408](https://github.com/boykopovar/AnyPS5/issues/27408)) |
| 🧪 | First Linux run of [#25589](https://github.com/boykopovar/AnyPS5/pull/25589#pullrequestreview-6081352719): DOOM converts twice with the fix |
| 🧪 | 8 mesh-shader titles start on macOS with #17611 ([review](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6006646487)); Clone Hero: Encore, first report, ~120 FPS ([report](https://github.com/boykopovar/AnyPS5/discussions/23570)) |

</details>

#### Pull requests in review

| | Pull request | What it does |
|---|---|---|
| 👍 | [#22572](https://github.com/boykopovar/AnyPS5/pull/22572) | AGC: reject command-buffer jump loops at once (`agc_driver` 24–194 s → 12 s) |
| 👍 | [#24311](https://github.com/boykopovar/AnyPS5/pull/24311) | `guest_math`: read only the standard exception flags (failed on every macOS run) |
| 👍 | [#24967](https://github.com/boykopovar/AnyPS5/pull/24967) | Relinker: macOS loads games at 0x400000 (Ruffle Flash no longer crashes) |
| 🔧 | [#25017](https://github.com/boykopovar/AnyPS5/pull/25017) | libkernel: `SOCK_SEQPACKET` socketpairs on macOS (Parallax Browser gets past its socket probe) |
| 👍 | [#25091](https://github.com/boykopovar/AnyPS5/pull/25091) | libc: macOS memory hints in the sealed range go to the top of the arena (Savage Wind starts) |
| 👍 | [#26593](https://github.com/boykopovar/AnyPS5/pull/26593) | Shader: an image a shader stores to is read back through its storage binding |
| 👍 | [#26600](https://github.com/boykopovar/AnyPS5/pull/26600) | AGC: NGG vertex programs draw line lists (PS5SX2's PS2 menu) |
| 🔧 | [#27330](https://github.com/boykopovar/AnyPS5/pull/27330) | libc: Windows memory hints in the system reserved range are placed at the hint (ProsperoCraft's JVM starts) |
| 🔧 | [#27801](https://github.com/boykopovar/AnyPS5/pull/27801) | libkernel: `sceKernelRaiseException` waits while the target thread blocks the signal |

👍 approved · 🟡 in review · 🔧 changes made, waiting for re-review

<details>
<summary><b>Merged pull requests (14)</b></summary>

| | Pull request | What it does |
|---|---|---|
| ✅ | [#24201](https://github.com/boykopovar/AnyPS5/pull/24201) | Shader: a barrier before a scratch pool slot is released on MoltenVK (`agc_driver_scratch_pool` failed 17 of 20 runs on the M4; 50 of 50 pass) |
| ✅ | [#26653](https://github.com/boykopovar/AnyPS5/pull/26653) | libkernel: `SA_SIGINFO` handlers run for `SIGSEGV` and `SIGBUS` faults (PS5SX2's fastmem crashed 3 of 3 times as its PS2 system menu started; ran 8 min without an error; ProsperoCraft's Java runtime stopped in 5 of 5 downloads, now downloads all 576 MB); [merged with `main` after #27140](https://github.com/boykopovar/AnyPS5/pull/26653#issuecomment-7203255577); [review fixes](https://github.com/boykopovar/AnyPS5/pull/26653#issuecomment-7205520027): `si_code` matches between Windows and Linux (also for no-access pages) and the handler gets the thread's signal mask, tested on both (200 of 200 runs each; the new tests fail without the fixes); approved |
| ✅ | [#25658](https://github.com/boykopovar/AnyPS5/pull/25658) | Shader: link user-data tails through copied pointers, branching bodies and geometry fronts (XashPS5 stopped at three shader tails; Half-Life now draws its first map). |
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
<summary><b>Bug reports (7)</b></summary>

| Issue | Found |
|---|---|
| [#27336](https://github.com/boykopovar/AnyPS5/issues/27336) | Windows: once an elevated process creates `%TEMP%\AnyPS5`, unelevated runs that use named shared memory abort with "Access is denied" until the directory is removed by hand. Both fixes in review pass the report's steps here ([#27394](https://github.com/boykopovar/AnyPS5/pull/27394#pullrequestreview-6074746504), [#27432](https://github.com/boykopovar/AnyPS5/pull/27432#pullrequestreview-6074746844)); only #27394 also copes with a directory an older elevated run left behind |
| [#26186](https://github.com/boykopovar/AnyPS5/issues/26186) | Since #25434, `APS5_ASYNC_PIPELINE_WORDS` no longer defers a slow first-visit pipeline, so Afterglow exits again on NVIDIA (4 of 4 runs; 3 of 3 run with #25434 reverted); the maintainer's fix, [#26196](https://github.com/boykopovar/AnyPS5/pull/26196), keeps it running |
| [#23708](https://github.com/boykopovar/AnyPS5/issues/23708) | `agc_storage_write_back_host_retile` failed 3 runs in 4 on Windows / RTX 2060; bisected to the pull request that added it. The cause is a race in the test; the fix, [#23751](https://github.com/boykopovar/AnyPS5/pull/23751), passes on five other NVIDIA cards and is in review |
| [#24728](https://github.com/boykopovar/AnyPS5/issues/24728) | SuperTuxKart at ~10 FPS on macOS: one GPU round trip per draw, and Rosetta's cost of re-protecting watched memory (~0.2 ms per MiB); a 1 MiB fault-ahead block gains ~3–8 % |
| [#22565](https://github.com/boykopovar/AnyPS5/issues/22565) | `agc_driver` took up to 123 s on Windows because its self-linking buffer check ran to the timeout; the fix, [#22572](https://github.com/boykopovar/AnyPS5/pull/22572), is approved |
| [#22270](https://github.com/boykopovar/AnyPS5/issues/22270) | macOS: guest paths near `PATH_MAX` fail with `ENAMETOOLONG` because the host prefix makes them longer |
| [#22317](https://github.com/boykopovar/AnyPS5/issues/22317) | macOS: `sceNetConnect` with a timeout to a bound, non-listening loopback port returned `EAGAIN` (closed, resolved) |

</details>

<details>
<summary><b>Game reports (11)</b></summary>

| Game | Result |
|---|---|
| [PS5SX2](https://github.com/boykopovar/AnyPS5/pull/27140#pullrequestreview-6072198106) | Its PS2 system menu stops at four points on Windows: PCSX2's fastmem faults (#26653), a SIGPROF from its own profiler (#27140), a `v_interp_mov` P10 read (#1413, fixed by #27327) and NGG line lists (#26600). With the four, and no local workaround, it reaches its language screen at ~10 FPS; without #26600 or #27140 it stops 2 of 2 times. [Where the frame goes](https://github.com/boykopovar/AnyPS5/issues/25912#issuecomment-7198082557): 38 GPU round trips per frame |
| [15 mesh-shader titles](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6006646487) | With #17611 on macOS, 8 that stopped on `main` now start (SpeedBreaker, PSXS5, SwanStation, DevilutionX, PSFlyCast, OGBox, Mario 64, FBNeo); the four N64 recompilations ask for 8x MSAA, which the Mac does not offer |
| [Crux2](https://github.com/boykopovar/AnyPS5/discussions/18182#discussioncomment-19796785) | First macOS report: needs `ROSETTA_ADVERTISE_AVX=1` to pass its AVX2 check, then stops at its first present on mesh shaders (#17611) |
| Afterglow ([macOS](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19797074), [Windows](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19730524), [cause on NVIDIA](https://github.com/boykopovar/AnyPS5/discussions/13019#discussioncomment-19830592)) | macOS: the Metal compiler runs out of memory on a 30 MB MSL shader; `APS5_FAST_F32=1` shrinks it to 7–9 MB and it compiles, but the title still exits before its first frame. Windows / RTX 2060: the NVIDIA driver takes ~40 s to compile the pipeline of its large pixel shader, while the title gives up after 2 s, so the compile never finishes or gets cached; once it has been compiled, the title starts at 60 FPS |
| [osu! ProjectCadence](https://github.com/boykopovar/AnyPS5/discussions/17969#discussioncomment-19788361) | First macOS report: closed after 2 s; fixed the cause in #24792 (merged), and with #17611 a map plays at 55–60 FPS on the M4 |
| vkQuake ([NVIDIA](https://github.com/boykopovar/AnyPS5/pull/21708#pullrequestreview-5956522777), [macOS](https://github.com/boykopovar/AnyPS5/pull/17611#pullrequestreview-6002155105)) | Black screen on NVIDIA, fixed by #21708 (merged). On macOS it plays at ~44 FPS with #17611; ccleste and PSteroid5 still need barycentrics (#9387) |
| [Clone Hero: Encore](https://github.com/boykopovar/AnyPS5/discussions/23570) | First report in AnyPS5: menu, song list and a song at ~120 FPS on Windows / RTX 2060, audio checked against the song's stems |
| [SudokuZen](https://github.com/boykopovar/AnyPS5/discussions/12236#discussioncomment-19745687) | Quits at its first draw whenever NVIDIA's driver shader cache is empty (4/4 runs; 5/5 fine with a warm cache): the #4399 shader still hits ps5-opengl's 2 s wait on `main` |
| [Brogue CE](https://github.com/boykopovar/AnyPS5/discussions/23592), [Dungeon Crawl](https://github.com/boykopovar/AnyPS5/discussions/23591), [NetHack](https://github.com/boykopovar/AnyPS5/discussions/23590), [ClanBomber](https://github.com/boykopovar/AnyPS5/discussions/23589), [Towelket](https://github.com/boykopovar/AnyPS5/discussions/23593) | First reports in AnyPS5, all playable on Windows / RTX 2060; Brogue, Dungeon Crawl and Towelket also on macOS. Towelket's itch.io download fails in the game itself |
| [SuperTuxKart](https://github.com/boykopovar/AnyPS5/discussions/17047#discussioncomment-19662997) | Was drawn purple on macOS and Windows / NVIDIA after #16053; fixed on `main` by #20827: the menu draws correctly on macOS at 44 FPS |
| [Syobon Action](https://github.com/boykopovar/AnyPS5/discussions/5932#discussioncomment-19661388) | Slow on macOS; cause found and fixed in #21766 (7.5 → 29.5 FPS) |

</details>

I also test other contributors' pull requests on macOS and Windows, with Vulkan validation and negative controls.
