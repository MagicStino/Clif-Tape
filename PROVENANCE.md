# Development record — 29 October 2026

The original repository was cloned locally as a starting point. Its release ZIPs, engine blobs, disassembly and firmware preparation scripts are excluded from the new public snapshot. Existing host/preset/skin integration was adapted; required third-party tooling attribution remains.

The implementation author had prior exposure to the original firmware project. The user requested grey-room development. The new engine was written from general signal-processing techniques and the product-level control specification; no firmware DSP routine or extracted table was translated or copied into it. No strict clean-room certification or exact sound equivalence is asserted.

Delay interpolation, low/high-pass smoothing, tanh drive, quantization/sample hold, pseudo-random wear/noise and stereo phase offsets are explicit inspectable code in src/dsp.hpp. Tone-profile cutoffs are independently selected constants. The runtime performs no dynamic executable-code loading.

0.1.2 uses independently optimized parametric filters fitted to measured reference magnitude responses. The optimizer reads rendered audio measurements, not firmware coefficient tables. The study documents conditions, errors and limits. Saturation ordering follows an input-level/harmonic experiment. This remains reference-informed development.
