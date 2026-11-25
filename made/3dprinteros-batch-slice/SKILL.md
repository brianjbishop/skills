---
name: "3dprinteros-batch-slice"
description: "Slice STL files in 3DPrinterOS MultiSlicer for the Bambu Lab P2S using the 'ITP IMA - Multislicer' profile, one file after another. Use when asked to slice, queue or prep STLs in a 3DPrinterOS project."
---

# Batch-slice STLs in 3DPrinterOS (Bambu Lab P2S)

Outcome: every requested STL in a 3DPrinterOS project gets a sliced `gcode` (BAMBU_P2S) and `3mf` saved next to it in the same project, using the ITP IMA MultiSlicer profile.

## Setup
- Use the browser tools (Claude in Chrome by default, or the built-in browser if the user prefers). Read pages as text/DOM; do not click by screen coordinates.
- Open `https://cloud.3dprinteros.com/#/projects` (the user is signed in with their school account). If a sign-in wall appears, stop and ask the user to sign in.
- Expand the target project (e.g. "ShoulderPad"). Ask which project/files if not stated. Files already showing a `gcode` + `3mf` pair with the same name are already sliced; skip them unless asked to redo.

## Per-file loop
For each STL row that needs slicing:
1. Click the green **Slice** button on that STL's row. The MultiSlicer (Beta) dialog opens with the file name at the top-left.
2. **Printer type**: open the dropdown (defaults to Bambu Lab A1) and choose **Bambu Lab P2S**. Verify it reads P2S, not A1.
3. **Profile**: open the Profile dropdown and choose **ITP IMA - Multislicer** (listed under "My Slicing Profiles"). Verify the profile name appears. Selecting it applies the filament (Bambu PLA), process (0.20mm Standard @BBL P2S) and support settings (tree(auto) support on build plate only); leave those as the profile sets them.
4. Click **Slice** (bottom right of the viewer).
5. A "Save this project?" dialog appears. Choose **Save & slice** (keeps the edited file in the library under the same project). Only choose "Slice without saving" if the user asks.
6. Wait for slicing to finish (roughly 30-60 seconds for a plate; larger parts take longer). The dialog closes and the project list refreshes with a new `gcode` row (BAMBU_P2S, showing print time) and a `3mf` row above the STL. Confirm both appeared before moving on.
7. Move to the next STL and repeat.

## Rules
- Do not click **Print**. Slicing only; printing needs explicit user approval.
- Do not delete files or change printer/profile settings beyond the steps above.
- If the printer or profile option is missing, or slicing errors out, report which file failed and continue to the next only if it's independent.

## Finish
Report a short list: which files were sliced, print time shown for each gcode, and any that were skipped or failed.