# Install or remove Clif Tape

Use the **Clif Tape** entry in the OpenPlugin catalog and choose Install. The catalog downloads a ready-built ARMv7 package with the skin, thumbnail and presets. Compatible OS 3.x community plugin hosting is required.

Manual installation: download `Clif-Tape-0.2.0-mpc-armv7.zip` from Releases, extract it on the device and run `sh Clif-Tape-0.2.0/install.sh -y`. Save your current project first; the music application restarts. Add Clif Tape as an **effect insert**, not an instrument.

The installed folder is normally `Synths/MagicStino - VST - Clif Tape` on the storage selected by the installer. Keep the extracted package: `sh Clif-Tape-0.2.0/uninstall.sh -y` unregisters and removes it, then restarts the application.

## Compatible plugin platform

For setup instructions and compatible community software, see:

- [Force OpenPlugin — firmware, Plugin Manager and catalog](https://magicstino.github.io/force-openplugin/)
- [sd88me MPC plugins — supported systems and installation instructions](https://github.com/sd88me/mpc-vst-plugins)

Clif Tape is supplied as a ready-built installer; no compiling is needed.

## Windows / macOS desktop VST3

[Windows download](https://github.com/MagicStino/Clif-Tape/releases/download/v0.2.0/Clif-Tape-0.2.0-Windows-VST3.zip) · [Mac download](https://github.com/MagicStino/Clif-Tape/releases/download/v0.2.0/Clif-Tape-0.2.0-macOS-VST3.zip)

These are ready-built ZIP bundles, not installer applications. No AU version is supplied; Logic cannot load VST3 directly.

Download the matching ready-built VST3 ZIP from [Releases](https://github.com/MagicStino/Clif-Tape/releases/tag/v0.2.0), then extract it.

- **Windows 10/11 x64:** copy the complete `ClifTape.vst3` folder into `C:\Program Files\Common Files\VST3`.
- **macOS:** copy `ClifTape.vst3` into `~/Library/Audio/Plug-Ins/VST3`. The bundle supports Apple Silicon and Intel. The build targets macOS 10.15+ on Intel and 11+ on Apple Silicon. It is ad-hoc signed, not notarized.

Rescan plugins in your DAW and insert Clif Tape as a stereo effect. The desktop plugin uses the same four-page control layout and artwork. Use the arrows at the top to select presets; drag knobs vertically and click switches to toggle. Every control supports DAW automation and saved-project recall.

To uninstall, remove the `ClifTape.vst3` bundle from that folder. This does not delete your DAW projects.

Windows requires the current [Microsoft Visual C++ v14 x64 runtime](https://aka.ms/vc14/vc_redist.x64.exe). Install it if your DAW reports missing `MSVCP140` or `VCRUNTIME140` DLLs.

## Linux x86-64 VST3

[Download the Linux VST3 ZIP](https://github.com/MagicStino/Clif-Tape/releases/download/v0.2.0/Clif-Tape-0.2.0-Linux-VST3.zip). Extract it and copy the entire `ClifTape.vst3` directory into `~/.vst3/` (create that directory if needed). Keep its `Contents` folder and resources together. Rescan VST3 plugins in your DAW and add Clif Tape as a stereo insert effect.

Requires x86-64 Linux with glibc 2.34 or newer and an X11-compatible plugin UI environment (XWayland may be used by compatible hosts). Runtime libraries include XCB, xcb-util, xcb-cursor, xcb-xkb, xkbcommon-x11, Cairo, Pango, GLib and Fontconfig. Install missing libraries through your distribution's package manager. This is not an ARM build.

To uninstall, close your DAW and remove `~/.vst3/ClifTape.vst3`. Your projects remain untouched. The package includes a SHA256 checksum, licensing information and an installation guide. Linux passed 47 VST3 validator tests and the interface/DSP smoke check; individual DAW compatibility still depends on the host.
