# Bingo Caller App

## Project Info
- **Live URL:** https://jake7337.github.io/Bingo/
- **GitHub:** https://github.com/Jake7337/Bingo
- **Creator:** Jake - creates all art/videos/ideas with AI tools

## Current State
- Single file: `index.html` (embedded CSS/JS, no dependencies, no build step)
- This is the whole repo — no portal page, no trivia apps, no media manager, no video/image assets
- Built for Bellwood FOE 1859 Aerie (Fraternal Order of Eagles)
- Designed for TV display at club (same screen doubles as the caller's control panel)

## Features
- Full-screen 75-ball board (horizontal B/I/N/G/O rows) — takes up most of the screen
- Slim right sidebar: Last Call (large), Now Playing (pattern name + mini grid), Choose Game,
  Rotate toggle, Pace Delay slider, Call/Reset/Full Screen buttons
- "Choose Game" opens a pattern picker modal (presets + custom cell-by-cell editor)
- Confirming a pattern shows a full-screen "Let's Play" reveal (name + big grid) before
  dropping back into the board
- Voice announces every call via the Web Speech API (always on, no toggle)
- Pace delay control (0-15s) between calls
- Wake Lock keeps the screen from sleeping
- Fullscreen toggle

### Pattern animation
Many patterns can legally be played in more than one orientation/position. The ROTATE
ON/OFF sidebar button controls whether the "Now Playing" preview (and the Let's Play
reveal) cycles through those variants, or freezes on one static frame:
- **Standard shapes** (T, L, X, Corners, Heart, Kite, Field Goal, etc.) rotate through
  every distinct 90° orientation via `getOrientations()`.
- **Missing Link** — full outside border, cycles through each single edge cell being
  the "missing" one.
- **Postage Stamp** — 2x2 corner blocks. Choose 1-4 stamps in the modal ("How Many
  Stamps?" buttons); count 4 is static (any corner counts), 1-3 cycles through every
  combination of that many corners.
- **Block of 6** — a 2x3 rectangle, cycles through all 24 valid positions, alternating
  3-wide/2-high and 2-wide/3-high every frame (interleaved, not grouped) so both
  orientations show up fast.
- **Block of 9** — a 3x3 square, cycles through its 9 valid positions.
- All of the above naturally light up the center free space when a placement covers it.

Symmetric patterns (Full Card, X, Corners, Plus, Inside/Outside Box) collapse to a
single frame automatically since rotating them looks identical — no wasted animation.

## Notes
- Jake likes to share code openly to help others
- No video/image assets of any kind — removed 2026-07-01 after 6 months of testing
  showed they weren't used. Don't re-add media features without Jake asking.
