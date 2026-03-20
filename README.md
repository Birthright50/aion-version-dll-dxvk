# Aion-Version-Dll
Aion No-IP and Windows 10/11 camera fix based on Beyond.

Features:
- Allows the game client to connect to non-official game server IPs (prevents the error message "No game server is available to the authorization server (6)").
- Fixes the camera movement issue on Windows 10/11 (introduced by the Fall Creators Update 2017) without needing to run a separate program.
- Enables all graphics options sliders (shadows, water quality, etc) which are otherwise disabled at high resolutions.
- [DXVK support](https://github.com/doitsujin/dxvk)

## Building
This project depends on [MS Detours](https://github.com/Microsoft/Detours). Since it's served via NuGet, you should be able to build the project straight away.

## Installation
1. Download latest [DXVK](https://github.com/doitsujin/dxvk) release.
2. Copy `d3d9.dll` into respective bin32 or bin64 folder.
3. Place `version.dll` (from this repository) into the same folder
4. (Optional but recommended) create `dxvk.conf` in the **game root directory**
> If you don't want to use DXVK, you can skip steps 1 and 2.

## ⚙️ Recommended DXVK Configuration

Create a file named `dxvk.conf` in the **game root directory** (NOT `bin32/bin64`):

```ini
dxvk.hud = fps

# Performance
d3d9.cachedDynamicBuffers = true
d3d9.deferSurfaceCreation = true

# Quality
d3d9.samplerAnisotropy = 16

# Compatibility / shader fixes
d3d9.forceSamplerTypeSpecConstants = true

# Optional (only for legacy engines with broken VRAM detection)
# d3d9.maxAvailableMemory = 4096
