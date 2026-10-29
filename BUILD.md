# Build and test

Build directly from the included C++ source.

Desktop Linux development build (tested):
```
make test
```

Optional CMake build:
```
cmake -S . -B build/local -DCMAKE_BUILD_TYPE=Release
cmake --build build/local
ctest --test-dir build/local --output-on-failure
```

ARMv7 build with Zig (tested target glibc 2.31, cortex-a17):
```
mkdir -p build/arm
zig c++ -std=c++17 -O2 -target arm-linux-gnueabihf.2.31 -mcpu=cortex_a17 -fPIC -shared -fvisibility=hidden src/plugin.cpp -Wl,--no-undefined -o build/arm/clif_tape.so
python3 tools/export_native_presets.py
python3 tools/packaging/release.py --so build/arm/clif_tape.so --skin 'skin/MagicStino - VST - Clif Tape' --entry pluginlist-entry.xml --version 0.2.0 --id clif-tape --repo MagicStino/Clif-Tape --license MIT -o dist
```

The native DSP tests cover five sample rates (8–192 kHz), aligned dry audio, stereo motion, crackle, degradation and finite output during rapid control changes. Host tests cover all fifteen programs, UI notification echo, independent noise switches, increasing DEGRADE, saved-state round trip and rejection of malformed state. ARM host loading was also tested under emulation with the Force runtime. This does not establish real hardware audio performance.

Silence Gate native skin additions are regenerated with `python3 tools/silence_gate_ui.py` after base skin generation. Render `vst/art/silence-gate.svg` at 1280×628 to `Plugin Skins/silence-gate-bg.png` before packaging. The checked-in native skin includes the generated fourth page and disabled-control variants.

## Desktop VST3

Users can install the ready-built Windows/macOS ZIPs from Releases. For development, extract `Clif-Tape-desktop-source.zip`. The `.github/workflows/desktop.yml` workflow pins the VST3 SDK revision, builds Windows x64 and universal macOS natively, runs the SDK validator and packages the matching custom editor.

The Linux development build also provides `clif-smoke`, which renders all four pages (both engine states and gate-off), checks switch behavior and verifies active audio processing. Build with `cmake -S desktop/vst3 -B desktop/vst3/build -DVST3_SDK_ROOT=/path/to/vst3sdk -DCMAKE_BUILD_TYPE=Release`.

Validation is automated; it does not replace testing in individual Windows/macOS DAWs.

## Linux desktop VST3

The ready-built Linux download is linked from the homepage; users do not need to build it. For developers, [Clif-Tape-Linux-source.zip](https://github.com/MagicStino/Clif-Tape/releases/download/v0.2.0/Clif-Tape-Linux-source.zip) contains the matching desktop DSP/UI source and `desktop/package-linux.py`.

Use the pinned VST3 SDK revision `3cdf9ca5d1f5b1b21e0a86832aa4abe55607bd96` with its submodules, a C++17 toolchain, CMake 3.25+, and the XCB, xkbcommon, Cairo, Pango, GLib and Fontconfig development libraries. Configure `desktop/vst3` with `-DVST3_SDK_ROOT=/path/to/vst3sdk -DCMAKE_BUILD_TYPE=Release`, build, run the SDK validator against `build/VST3/Release/ClifTape.vst3`, then run `python3 desktop/package-linux.py` from the extracted source root. The published binary requires glibc 2.34+ and targets x86-64. Release checks: 47 validator tests plus UI controls, six screen renders and active DSP.
