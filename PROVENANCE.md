# DSP implementation notes

Clif Tape uses C++ signal processing for delay interpolation, low/high-pass filtering, saturation, sample-rate reduction, generated noise and stereo modulation. The implementation is inspectable in `src/dsp.hpp`.

Tone profiles use optimized parametric filters fitted to measured audio magnitude responses. Saturation behaviour was refined using input-level and harmonic-response tests.

The plugin runs its DSP directly and requires no additional sound files. Existing host, preset and skin integration was adapted for Clif Tape. Third-party tooling retains its attribution and license.
