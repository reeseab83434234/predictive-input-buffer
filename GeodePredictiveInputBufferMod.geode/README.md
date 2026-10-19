# Predictive Input Buffer — Geode Mod Prototype

This is a native C++ Geode mod project, not a standalone console app.

## Included
- F6 cycles Stage 1 (2/2) → Stage 2 (4/4) → Stage 3 (8/8) → Stage 4 (16/8) → OFF.
- F7 toggles the prototype on/off.
- F8 opens the in-game console popup.
- Popup buttons log +1, +2, and +3 tick-save events, apply the current preset, and clear the console.
- Keybinds are configurable in Geode's mod settings.

## Important behavior limitation
This is a **UI and input-event prototype**. It does not yet alter Geometry Dash's actual input timing or game engine tick handling. The “saved ticks” buttons record console events; they do not delay or buffer gameplay inputs. Implementing true predictive input buffering needs a verified, version-compatible hook into the relevant input path and careful testing against the target Geometry Dash version.

## Build on Windows
1. Install Geometry Dash and Geode.
2. Install the Geode SDK following the official setup docs: https://docs.geode-sdk.org/getting-started/installation/
3. Follow the Windows IDE setup guide: https://docs.geode-sdk.org/getting-started/ide-setup/
4. Set the `GEODE_SDK` environment variable to the SDK folder.
5. Open this folder in VS Code with CMake Tools (or Visual Studio / CLion configured for Geode).
6. Configure and build the CMake project. The Geode package target should package/install the mod if your SDK environment is set up correctly.

The `mod.json` currently targets Geode v4 and Geometry Dash Windows `2.2074`. If your installed game/Geode version differs, adjust the target metadata to match your SDK and game version before building.

## Project structure
- `mod.json` — Geode metadata, version target, keybind settings
- `CMakeLists.txt` — Geode SDK build configuration
- `src/main.cpp` — popup UI, stage cycling, and console log
