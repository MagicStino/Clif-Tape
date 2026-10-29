# Install or remove Clif Tape

Use the **Clif Tape** entry in the OpenPlugin catalog and choose Install. The catalog downloads a ready-built ARMv7 package with the skin, thumbnail and presets. Compatible OS 3.x community plugin hosting is required.

Manual installation: download `Clif-Tape-0.2.0-mpc-armv7.zip` from Releases, extract it on the device and run `sh Clif-Tape-0.2.0/install.sh -y`. Save your current project first; the music application restarts. Add Clif Tape as an **effect insert**, not an instrument.

The installed folder is normally `Synths/MagicStino - VST - Clif Tape` on the storage selected by the installer. Keep the extracted package: `sh Clif-Tape-0.2.0/uninstall.sh -y` unregisters and removes it, then restarts the application.

## Replacing older versions

Clif Tape replaces the older Clif Loss listing. Back up your projects and user presets before removing old versions. The original Clif Loss engine has a different plugin ID; projects using it require manual replacement and may sound different. Clif Loss Clean shares Clif Tape's parameter IDs and saved-state format, but the display name and install path change. Reinsert Clif Tape if a host cannot resolve the old name/path. This is not a promise of automatic migration for every host.

On the development Force, old installations are backed up before removal. Catalog removal does not delete users' projects.
