# Motion boards, labs and Doop: lessons

- When the owner says "board", they mean a Doop page, not only an inline chat preview. If the work exists only in chat, say so plainly and build the Doop frames.
- Motion systems: build an interactive HTML lab (speed 1x/0.5x/0.25x, reduced-motion toggle, product-mode toggle, level toggle for progressive disclosure, token sliders with live CSS export, a button that copies the chosen tokens so the owner can paste them back). Publish it as an Artifact so the owner can open it anywhere. Then build a STATIC Doop version: key frames labelled with ms timestamps, light and dark. Doop frames run inline scripts, so a small live demo can sit next to the stills, but the stills are what get reviewed.
- In still frames, motions under ~5% scale or a few px (sound pulses, 2 px bobs) look identical. Draw them exaggerated and say so on the card.
- Check that frame timestamps agree with the tokens (draw + stagger arithmetic, fade overlaps) before shipping. QA has caught mismatches every time.
- Springs: measure, don't guess. The time to peak is not the settle time. Sweep stiffness and damping (semi-implicit Euler) and report overshoot %, peak ms and rest ms. Over ~10% overshoot reads as wobble.
- Rendering QA outside Doop: open the lab in a browser the host offers and screenshot it, or use a headless Chromium such as Playwright's `chrome-headless-shell` with `--headless --hide-scrollbars --force-device-scale-factor=1.5 --window-size=W,H --screenshot=out.png file://...`. Add a `--still` variant with animations off so the screenshot shows final frames.
- Keep lab sources and generators in the strategist's lab folder (see "Your space" in the agent), never only in a temp folder.
- Doop layout pitfalls: two side-by-side light/dark panels overflow narrow cards (stack them, or give them fixed widths). Wrapping captions misalign rows (use justify-content:flex-end on columns). Draw script characters from stroke data rather than font text when stroke order matters. Frames don't scroll for viewers, so resize them to the content.
- Shape semantics: once a shape carries a meaning, every later use of it must keep that mapping.
