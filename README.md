# Aion-Version-Dll
⚠️ This branch contains an experimental mouse input fix.
> It is NOT part of the original Beyond implementation.

Aion No-IP and Windows 10/11 camera fix based on Beyond and raw input mouse fix from [Marisa-Chan](https://github.com/Marisa-Chan/Aion-Version-Dll)

Features:
- Allows the game client to connect to non-official game server IPs (prevents the error message "No game server is available to the authorization server (6)").
- Fixes the camera movement issue on Windows 10/11 (introduced by the Fall Creators Update 2017) without needing to run a separate program. This branch is based on the original Beyond version.dll mouse fix, but replaces the cursor-based camera movement with a Raw Input–based approach.
On some systems, the original cursor-based fix can still result in unstable camera movement or cursor repositioning due to OS-level input race conditions.
This branch attempts to fully decouple camera movement from the Windows cursorby using Raw Input.
- Enables all graphics options sliders (shadows, water quality, etc) which are otherwise disabled at high resolutions.
- [DXVK support](https://github.com/doitsujin/dxvk)
### Key Differences from Beyond

- Uses Raw Input (`WM_INPUT`) to track mouse movement deltas
- Does NOT rely on `WM_MOUSEMOVE` delivery
- Camera rotation is independent from the actual cursor position
- Prevents cursor repositioning issues when using overlays or window capture
### Limitations / Risks

- This is a more invasive approach than the original Beyond fix
- Raw Input changes the input model from cursor-based to delta-based
- UI interactions relying on cursor position may behave differently
- Anti-cheat compatibility is not guaranteed
### When to Use This Branch

- If the original Beyond mouse fix still causes camera instability
- If cursor repositioning issues occur frequently
- If window capture or overlay software interferes with mouse input

Otherwise, the original Beyond implementation is recommended.
## Building
This project depends on [MS Detours](https://github.com/Microsoft/Detours). Since it's served via NuGet, you should be able to build the project straight away.

## Installation
To install, copy each version.dll to the respective bin32 or bin64 folder under the Aion client root.

If you want DXVK support, put [d3d9.dll](https://github.com/doitsujin/dxvk) to the respective bin32 or bin64 folder under the Aion client root.

Tested with the Aion 4.6 game client on Windows 11.
