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
