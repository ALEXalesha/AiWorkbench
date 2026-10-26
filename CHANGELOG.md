# Changelog

What changed for the user in each release. The full text of each release, with the download
table, is on the [releases page](https://github.com/ALEXalesha/AiWorkbench/releases).

## 1.4.0 - 2026-09-25 - The window opens where it was closed, at the same size

The place, size and maximized state are written to `window.json` in the data folder when you quit, and put back at the next start. If that monitor is gone or the title bar would land off every screen, the window opens in the middle of the main screen as before. It is a separate file from `ui.json` (theme and accent), which the server writes, so the two never overwrite each other.

The portable zip of this build is a real zip again: the build script packs it with the Windows `tar` by full path, because started from Git Bash it picked up GNU tar, which ignores `-a` and writes a plain tar under the `.zip` name.

283 tests green before the build.

## 1.3.1 - 2026-09-23 - No transparent frame around the window

Up to 1.3.0 the page drew the window 8 px inside its own area to leave room for a shadow, and on the desktop that margin read as a second, transparent frame around the window. Now the window fills its whole area: the 10 px rounding and the thin border stay, the outer shadow is gone. The resize zones sit on top of the page at the very edge and did not need the margin.

271 tests green before the build.

## 1.3.0 - 2026-09-22

First public release on GitHub.

**Guess the drawing reads several symbols.** The network was trained on single symbols and used to see the whole canvas as one 28×28 frame, so "65" came out as "W". The server now cuts the drawing into symbols and reads the string as a number or a word; "10", "101", "70", "ABC" are read reliably. How it works: [README](README.md#reading-several-symbols-from-one-drawing).

**LM Studio is faster to reach.** The app always calls `127.0.0.1`: Windows tries `localhost` over IPv6 first and spent about 2 seconds on that on every request. A stopped LM Studio is now detected in 0.5 s instead of 2.
