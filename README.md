# RefMatch 0.5.23 — Session Reset + UI Polish

UI-only polish pass on 0.5.19. Fixes clipped controls and spacing in the top action/player row, widens the graph-range selector, removes the duplicated frequency-label row, simplifies graph annotations, and cleans up the Tone EQ header so the interface tracks the supplied reference mockup more closely. DSP and matching behaviour are unchanged from 0.5.19.


## 0.5.23 changes

- MATCH now stays on **MATCHED** after a successful match.
- RESET now clears MIX/REF captures and learned match state, returning the workflow to a fresh-session state.
- New reset icon uses a clean parameter-controls symbol rather than the old circular arrow.
- Reference transport (-5 / PLAY / +5) is re-aligned and evenly spaced.
- LOOP, PLAY, RESET and Reset All use a softer shared action-button treatment.
- The large Tone EQ button has been removed; the Tone section is controlled directly by **TONE ON**.
- Small spacing/overlap fixes across the Match and Loop views.
- Fixed cleared loop state so LOOP cannot be re-enabled until a new valid range is selected.
- Creating a new loop range now restores a valid selection after CLEAR.
- MATCH shows READY TO MATCH and softly pulses once both MIX and REF captures are ready.
- MATCHED confirmation pulse remains after applying a match.
