# RefMatch 0.5.22 — Loop Clear + Ready to Match

UI-only polish pass on 0.5.19. Fixes clipped controls and spacing in the top action/player row, widens the graph-range selector, removes the duplicated frequency-label row, simplifies graph annotations, and cleans up the Tone EQ header so the interface tracks the supplied reference mockup more closely. DSP and matching behaviour are unchanged from 0.5.19.


## 0.5.22 changes
- Fixed cleared loop state so LOOP cannot be re-enabled until a new valid range is selected.
- Creating a new loop range now restores a valid selection after CLEAR.
- MATCH shows READY TO MATCH and softly pulses once both MIX and REF captures are ready.
- MATCHED confirmation pulse remains after applying a match.
