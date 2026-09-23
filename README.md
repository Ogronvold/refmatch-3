# RefMatch 0.5.28 — Reference Player Cleanup

Built on 0.5.23. DSP and matching behaviour are unchanged.

## 0.5.28 changes
- Repositioned -5 s / PLAY / +5 s so the controls no longer sit over the reference mini-waveform.
- Shortened the decorative B waveform to leave a clean transport lane.
- Added tiny live signal activity indicators to A and B. A follows the plug-in input peak; B follows the existing system-reference peak analysis.
- Indicators are deliberately minimal, colour-coded orange/purple, and fade close to invisible at silence.

- Reworked B/reference card to match the supplied compact player reference: artwork + metadata left, mini waveform beneath, and -5 / icon play-pause / +5 transport grouped cleanly on the right.


## 0.5.28
- Clean, symmetric -5 s / play-pause / +5 s reference transport.
- Play/pause icon is now drawn directly (no broken Unicode glyph).
- Removed transport tooltips that could cover the player card.
- Reference signal activity meter moved away from transport controls.


### 0.5.28
- Removed the decorative B-card waveform.
- Moved -5 s / play / +5 s into the former waveform row.
- Kept the B live activity indicator but integrated it into the metadata area.
- Lifted dark cover artwork slightly so it does not look disabled.
