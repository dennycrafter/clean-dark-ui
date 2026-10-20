---
name: clean-dark-ui
description: Use when designing, building or restyling any app or page UI. Clean dark look in the spirit of Apple-style product design, the "not tacky" rules, approved layout patterns, and how to review UI changes with the user.
---

# Clean dark UI

The blueprint is Apple-style product design: calm, precise, nothing extra. Goal for every build: it should look like a UI designer made it, not "AI". Clean, not clunky. Playful and dramatic moments are welcome, but never over the top.

## How to review UI with the user (follow every time)
- The user decides by SEEING it, not by reading about it. Never ask them to approve a design in words.
- Bigger changes go on a separate branch. Build, then send screenshots (desktop and phone width) or a short screen recording for anything animated. Use made-up data, never real personal data.
- Before/after pairs side by side work best.
- Only merge and publish after they say yes. If they say "leave it as it is", park the branch, don't delete it, don't bring it back unless asked.
- When asked "why does this look bad?", give an honest, numbered diagnosis (what, why it reads badly, the fix) before changing anything.
- Use plain words and short steps. No em dashes anywhere (UI text included).
- Small fixes can go straight to main, but still run the checks first.
- Record every shipped change and every parked experiment in the project's handoff notes.

## The "not tacky" rules
1. **Small corners.** Boxes 8px, buttons and inputs 6px. Big round corners everywhere feel toy-like. Pill shapes only where they mean something (a status pill, a streak pill), never for every fact.
2. **Few greys, on purpose.** Four shades only: page background, box surface, inner surface (buttons, chips, hovers), outline. Inputs sit on the page background. Many slightly different greys read as mud.
3. **One accent colour, one job.** The brand colour is only for the ONE main action per screen. Everything else is neutral (white underline for active tabs, silver for selection). If the main action changes (e.g. after a draft exists), move the accent with it.
4. **Plain font for words, display font for numbers.** System font (-apple-system, Inter fallback) for text, titles and labels. A bold or stretched display font (like Saira) only for big numbers and celebration screens. A display font on headlines gives a cheap gaming feel.
5. **Flat pop-ups.** Menus, dropdowns and cards: inner surface colour, thin outline, light shadow (0 6px 16px rgba(0,0,0,.3)). No heavy shadows.
6. **Plain text over chips.** Facts in a list row are plain muted text joined with dots ("London · Hybrid · Full time"). Colour only for what needs attention, as a small coloured dot plus text, no box: amber warning, red overdue, blue pending, green done.
7. **Never say the same thing twice.** If a tag already shows a value (e.g. the city), strip it from other text on the same row. Watch for data that repeats itself.

## Layout patterns that work
- **Lists like an inbox:** all rows in one box with thin dividers, not a stack of separate cards. One item per row at every screen width; two side by side feels overwhelming.
- **Row anatomy:** small square badge or icon on the left, muted category line, bold title, plain-text facts line, warning lines, then actions in one row on the right (below the text on narrow screens).
- **Buttons by weight:** main action filled accent, secondary plain, tertiary as quiet text buttons ("Open", "Skip"). On phones the two main actions go on top.
- **Notes:** a quiet "+ Add a note" line that becomes a box when clicked and grows as you type. Saves on blur.
- **Stats:** one strip split by thin 1px lines (gap 1px on the outline colour), not separate boxes. Keep the numbers big.
- **Top bar:** sticky, frosted dark, full width. Left: logo, then section tabs with counts and an underline on the active one. Right: small status pill (e.g. streak) and a profile circle with a menu for settings-type pages.
- **Secondary metrics** (streaks etc.) as a pill in the top bar with a hover card (tap on phones), not as another tile.
- **Add actions** open a floating window (click outside, X or Escape closes; close on success with a toast; stay open on errors), not a big always-visible box.
- **Full width:** max width around 1760px with a gutter of clamp(16px, 2.6vw, 40px). Check it still reads at first glance on a real screen.
- **Document previews** (CVs, PDFs etc.): no box around the paper, real reading size, zoom (buttons, pinch, Cmd/Ctrl + - 0, double-click to toggle fit), tools in a slim side column, a full-screen view with the item's own buttons in the header.
- **Custom dropdowns:** styled like the profile menu, with the real select hidden as the source of truth, full keyboard support (arrows, Home/End, first letter, Enter, Escape, Tab). A filter that is on gets a lighter outline.

## Playful, but clean
- One burst, not four: one shockwave, one burst of sparks and confetti, a slam title and a light shake. More than that is over the top.
- Short: auto close after about 6s; click, Enter or Escape closes; can be replayed from the thing that triggered it.
- Small rewards on each action (a puff and "+1" where you clicked, the number bumps).
- Always a reduced-motion version.
- Never copy another product's artwork one for one; make your own in the same spirit.
- Sound only after a click, and ask the user first.

## Logos and images
- Flat colours, no shine, glow, smoke or 3D effects: those blur at real top-bar size (30 to 40px).
- No badges that look like another brand's logo.
- Transparent background, cropped tight, sized for the slot (top bar mark around 38px tall, 32px on phones).
- Show options at TRUE display size side by side before choosing.
- If the user makes images in another tool, give them concrete prompts: flat, no glow, tight crop, what to remove.

## Behaviour details
- An undo must undo its side effects (moving an item back clears any dates and counts it changed).
- Sort choices and zoom level remembered per device (localStorage wrapped in try/catch).
- Phones: no sideways scrolling anywhere, nav swipes sideways, main actions first.
- Visible focus outline, keyboard paths for every menu, aria labels on icon buttons.

## Starter tokens (dark only)
```css
:root {
  color-scheme: dark;
  --bg: #0b0b0d;        /* page */
  --surface: #121215;   /* boxes, with the thin outline */
  --surface-2: #1c1c20; /* things inside boxes, pop-ups */
  --line: #2a2a30;      /* outlines, pressed/selected fill */
  --fg: #f2f2f4; --muted: #9a9aa3; --silver: #e8e8ea;
  --accent: #e8231a; --accent-ink: #ff5a4e; /* brand colour: main action only */
  --ok: #34d65c; --warn: #ffb547; --bad: #ff6f66; --info: #6ab8ff;
  --r: 8px; /* boxes; buttons and inputs 6px */
}
```
Swap the accent for the project's brand colour; keep the rest of the system.

## Before showing anything
- Run the page checks with made-up data; add a check for each new feature.
- Screenshot desktop and phone width. Make sure the real fonts are installed for screenshots (otherwise they fall back and look wrong).
- Look at the screenshots yourself first and fix anything that breaks these rules.
