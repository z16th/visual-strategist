---
name: option-boards
description: "Use when proposing design options for an owner to choose from (icon systems, motion, illustration, feedback signs, type, palettes) as coded pick-and-mix boards in Doop with an inline preview in chat."
metadata:
  strategist: visual
---

# Design option boards (chat preview + Doop)

Class: any proposal of design directions for an owner to choose from: icon systems, motion systems, illustration, feedback signs, type, palettes. Load the project brief (`<project>-brief`) first; it says which Doop canvas and pages are yours.

## Always-on rules
- **Every proposal lands in Doop, not only in chat.** An inline preview is for quick review; the owner checks Doop. When asked for options (even "in the meantime"), build the Doop frames in the same turn and finish by naming the page and frames to check. Don't pause the Doop build waiting on someone else's answer when you can draw palette-neutral work now.
- **Palette-neutral until roles are assigned.** If colour roles are open, draw in neutral ink per mode and say so on the board; then nothing needs redrawing when colours land.
- **Light and dark on every card**, stacked (light on top) inside the card. Side-by-side panels overflow a ~430 px card.
- **Coded cards** (1A, 1B…) with: idea, preview, Motion, Gains, Gives up, colour-vision swatches (normal/deutan/protan/tritan per mode, Machado 2009), plus 2–3 ready-made combinations with one marked recommended.
- **Board copy in the product's language**, which the brief names. Chat to the owner in their own language.
- **Every duration on a card must be a motion token** (or add the token). Mismatches get caught in review and undermine the spec.

## Procedure
1. Read the brief and the live colour/type sources, and check the project repo's recent commits for what changed. Keep working on what doesn't depend on open answers.
2. Doop setup: `get_guide` once per session, then `get_canvas` with a fixed `agent_name` ("Visual Strategist") and read the canvas style guides (`get_guidelines`). Note who touched each frame and when; don't edit frames another actor is working on. `set_status` when you start and when your focus shifts.
3. Chat preview: show the board (or the part under discussion) inline with whatever visual tool the host offers, or as an Artifact for a larger interactive lab. Render tiny signs alone at 160 px to judge their shape.
4. Doop build: put the work on your page of the canvas (create the page with `set_canvas_pages` if the brief says it doesn't exist yet), one frame per decision. Stream each board with `append_frame_html`, one card or row per chunk, `start=true` first and `done=true` last. Fix a broken card with `edit_frame_html` on that card; never rebuild a mostly-good board. When a board is generated from data (swatches, sweeps), keep the generator as a Python script in the project's lab folder and paste its output in, so it can be regenerated.
5. QA: `get_frame_screenshot` after the first row and again at the end, check it against the pitfalls below plus fit (clipping, dead space), contrast and alignment, fix, re-shoot. Resize the frame to its content with `update_frame`.
6. Record the owner's design feedback from chat with `save_decision` so the canvas memory has it.
7. Reply: which page and frames to check, what was fixed in QA, what's still open, the decision needed.

## Pitfalls (semantic, caught only by looking)
- **Small marks can change what a character means.** Check any dot, ring or badge against the product's writing systems, and move it if it could read as a diacritic.
- **Hand-drawn characters drift into other characters.** Draw them from stroke or font data, and check that nothing covers a stroke.
- **One shape, one meaning.** Once a shape carries a meaning, every later use must keep it. Check the same shape isn't also feedback and progress; differentiate (dotted/partial ring) or say so on the card.
- **A sign that merges two symbols can read as something else.** Look at it small, and test it with people from each culture in the brief.
- **Faint early stages** (dotted rings at 0.3 opacity) vanish on dark; keep ≥0.75 opacity and 2 px.
- **Decorative tints on dark** need about 2.5–3:1 to be seen at all; say they carry no meaning.
- Flag options that drift toward the brand's anti-reference on the card itself with a visible tag and the reason.

More lessons from motion boards and labs: `references/motion-and-board-lessons.md`.
