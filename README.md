# RefMatch 0.5.16 — 200% Amount + coloured applied curve

## 0.5.16 changes
- Match Amount now runs from 0–200%. 100% remains the normal full learned match; 100–200% intentionally exaggerates it.
- The applied EQ response is no longer a plain white line: near-zero correction stays almost white, then stronger correction moves through mint into cyan/blue.
- The purple curve remains the fixed 100% target for orientation.
- Added a DSP regression test that verifies the response continues increasing through 150% and 200%.


## 0.5.12 changes

- Groups the persistent loop ON/OFF control and ACTIVE/WAITING status beside the LOOP tab.
- Renames the A-side comparison control to BYPASS MATCH; bypass keeps A gain while Match EQ and Tone EQ are bypassed.
- Shows MATCHED / MATCH BYPASSED under YOUR MIX.
- Pins the 30 Hz Match EQ low handle to the left edge at its minimum, mirroring the 20 kHz high handle.
- Makes LOW/HIGH SHELF/BELL controls compact and visually integrated with the Tone EQ band headers.
- Uses ASCII frequency-range labels to avoid mojibake in plugin UI.

AU/VST3 plugin only; no helper or standalone app. Uses the working system-media
transport and 20 ms mix fade, with orange MIX and purple REFERENCE accents.

## 0.5.9 changes

- Updated the DSP regression test so it validates the new Max Correction behaviour instead of the legacy behaviour that ignored the limit.

Loop remains enabled within the plugin instance until you turn it off. RECORD REF,
metadata outages, failed seek, A/B, pause and source changes do not clear the toggle.
It waits and retries. Invalid edits preserve the last valid range. On a shorter new
track it waits for compatible In/Out values. Scrub and +/-5 seconds stay inside the
active region; disable Loop to seek elsewhere.

The header pulses LOOP ACTIVE for confirmed running loop state and shows steady
LOOP WAITING while paused or awaiting position/seek. Loop remains selected while the
editor is closed; a new plugin instance starts with Loop off.

Capture AudioBufferList storage is reused per serial callback delegate, growing only
when needed. Internal CoreMedia allocations are not eliminated by this change.

A separate manual release workflow prepares Developer ID signing, an installer PKG,
AU validation and Apple notarization. See RELEASE-SETUP.md. It has not been run and
requires your Apple credentials. Normal test builds and local signing remain available.

## Retained from 0.5.4

TONE ON independently bypasses the three manual bands, retaining their gains and
frequencies. Switching uses the existing approximately 20 ms coefficient transition.
The main EQ ON remains the master bypass. The new Tone enable parameter is saved
with the project and defaults ON for compatibility with existing Tone settings.

Graph range is now manually selected: +/-12, 24, 48 or 96 dB, default +/-24 dB.
Smooth, Amount and Tone edits never change the axis. Range is saved with the project.
If a curve exceeds the chosen range, it is clipped at the plot boundary and the
caption asks for a wider range. This affects only the view, never the sound.

## Retained from 0.5.3

- PLAY from A uses the B-switch sequence: mute MIX, then start reference. It cannot
  intentionally start the reference while leaving the plugin's MIX path audible.
- Reference meters, spectrum and RECORD REF use their own internal analysis thread.
  They continue when Logic's transport stops or its audio callback is suspended.
  MIX still needs host input; its live display clears when host callbacks stop.
- Drag the white timeline playhead to select a seek position; release to send it.
  Region selection and loop-edge dragging are retained, as are +/-5 second buttons.
- AUTO GAIN and METERS buttons removed. Capture starts when opening the editor or
  recording REF, and ends when the plugin is destroyed (not when Logic stops).
- Smooth continuously changes the breadth of the match, recomputing from the stored
  MIX/REF profiles. No re-recording required. Fine retains more narrow detail.
- Expand TONE EQ for three broad parametric bands, each with gain and frequency.
  These process after the matched EQ and are independent of Match Amount. EQ ON
  bypasses both. RESET TONE zeroes these gains; main RESET clears/bypasses the match.
- Orange/purple gradients, cleaner labels, aligned signal indicators and accurate
  frequency tick positions. Cover art and metadata are retained when supplied by macOS.

Match EQ view is 640x580; expanded Tone is 640x660; Loop is 640x430, plus host toolbar.

## Match workflow

RECORD MIX -> STOP MIX, RECORD REF -> STOP REF, MATCH. Choose A to audition EQ.
Capture representative sections. At least 0.5 s of non-silent data is required.
Amount scales the learned correction. Smooth adjusts detail. Tone is an additional
three-band correction, so Amount 0% can still alter sound if Tone gains are nonzero.
Project state stores profiles, learned EQ and all Smooth/Tone parameters.

## Build

Upload the extracted RefMatch folder over the existing folder, plus the root documents
and .github/workflows/main.yml. Build in GitHub Actions, then follow INSTALL-DA.txt,
including signing commands. This is a source candidate, not a locally tested binary.

## Boundaries

System-media transport and seek target the active player, not a Spotify account.
Metadata, position and artwork depend on macOS. Seeking happens on mouse release;
the time ruler is not an audio waveform or sample-accurate DAW scrubber.
EQ matches broad spectral balance, not instruments, dynamics or identical audio.
MIX measurement cannot invent audio when Logic sends none. REF requires capture permission.
## 0.5.12 UI/DSP cleanup
- Match Amount now scales the fully limited correction from 0-100%, avoiding the early visual/audio plateau caused by Max Correction.
- Applied EQ graph shows a dim 100% target plus the bright currently-applied curve.
- LOW/HIGH Tone EQ Shelf/Bell buttons are actual toggles and the Tone layout has more spacing.
- Removed the duplicate Loop enable switch from the Loop page; the quick toggle beside the Loop tab is the single loop on/off control.
- Replaced the ambiguous Before/After checkbox with an explicit MATCH ON / BYPASSED state button; A gain stays active while matching is bypassed.


## 0.5.16 visual polish
- Darker, cleaner panel hierarchy with softer borders and inner highlights.
- Subtle orange/purple bloom around selected source cards and active controls.
- Cleaner button rendering and more restrained gradients.
- Pill-style quick Loop and EQ toggles.
- Softer graph/tone cards and slider glow.
- DSP and matching behaviour unchanged from 0.5.13.


## 0.5.16 visual depth pass
- Circular SWITCH control with bidirectional-arrow icon, inner highlight and subtle bloom.
- SWITCH/CANCEL state label separated below the control for a cleaner hierarchy.
- Denser logarithmic Match EQ grid with major/minor frequency guides and a clearer 0 dB line.
- Applied response now has soft multi-pass bloom while retaining its magnitude-sensitive colour.
- 100% target curve gets a subtle filled area and glow for more depth.
- Live before/after spectrum traces get translucent area fills for a richer graph without changing DSP.

## 0.5.16 UI polish
- Tone EQ redesigned with cleaner cards, section labels, separated GAIN/FREQ rows and tidier shelf/Q controls.
- MATCH ON now has a clearly illuminated active state; BYPASSED is visually subdued.
- RECORD MIX / RECORD REF now use dedicated record icons and cleaner button typography.
