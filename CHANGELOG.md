# 0.2.0

Fixed duplicate gate touch handling that toggled back immediately. Fade In 1–10 seconds (default 2), Fade Out 0–15 seconds (default 8). Version 6 state converts version 5 normalized timing to retain seconds, clamping old subsecond fade-in to the new one-second minimum. Older presets use new defaults.

# 0.1.5

Added separate Silence Gate screen and Q-Links; shared fade for Crackle, Noise and Mechanical with adjustable 0–10 second times. Default fade-in 1 second, fade-out 10 seconds, enabled. Fade controls disabled when Off. Version 5 saved state retains gate settings and loads older versions 3/4. Regression tests cover five sample rates, all textures and unchanged music.

# 0.1.4

- Gentle saturation-dependent low-mid trim centred at 480 Hz for Video 2 (up to 2.5 dB), Video 3 (2 dB), Tape (1.8 dB). Smoothly follows Saturate; zero Saturate preserves measured curves. Other models and Digital remain unchanged.
- Includes the Wow/Flutter refinement from 0.1.3.

# 0.1.3

- Wow now uses smoothly wandering speed and an asymmetric waveform, informed by reference pitch measurements.
- Flutter uses approximately 41 Hz with a smaller 16 Hz component, replacing the old 7.3 Hz wobble.
- Upper-half response adds a smooth depth lift, reaching +20% at maximum. Full combined delay excursion remains below the 8 ms base delay.
- Motion has its own phases and random generator, leaving mechanical texture and noise randomness unchanged.

# 0.1.2

- Tape models replaced with independently fitted multi-stage filters matching measured magnitude curves; saturation moved before them based on measured harmonic behavior. Model positions retained with descriptive labels.
- DEGRADE now combines sample-rate aging with bandwidth reduction; removed deep bit-depth quantization.
- Noise white blend spans 7–30%; Clean Start Noise Level is 10% with Noise Sound off.
- Crackle below 35% fades in at minimum event rate; 35/50/100% rates are 0.5/1/1.5 times the previous 50% rate. Individual-event gain caps at 50%.

# 0.1.1

- Model selector reads its canonical current position immediately, including arrow taps before the next audio block.
- Crackle uses short band-limited noise bursts with a softened onset instead of abrupt impulses. Level and density reduced. At full crackle and half Failure, ten-second silence test peaks fell from 0.645 to 0.0513 (about 22 dB); subjective acceptance pending.
- Regression tests exercise all model positions, immediate arrow readback, UI echo, model frequency responses and crackle peak bounds.
- Noise starts dark and blends into white between 20% and 40% Noise Level. Maximum white-noise amplitude reduced to one-third. Audio regression checks cover every active effect path, noise spectral progression and maximum level.
- Mechanical recreated as band-limited motor whirr with irregular chatter, or harmonic electrical buzz. Spectrum and peak checks reject sub-only or excessive output.
- Mechanical output high-passed at 240 Hz and maximum gain reduced to one-third of the replacement texture level.
