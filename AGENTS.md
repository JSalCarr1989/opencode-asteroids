# AGENTS.md — Asteroids

## Project

Single-file HTML5 Canvas Asteroids clone. No framework, no bundler, no dependencies, no build step.

## Commands

- Run: open `index.html` directly in a browser, or `npx serve .` → http://localhost:3000.
- No lint, typecheck, test, or build commands exist. Do not invent them.

## Structure

- `index.html` — page shell: 800x600 canvas (`#canvas`) + loads `game.js`. Inline CSS only.
- `game.js` — all game logic in a single file (ES6+, `'use strict'`, top-level constants, classes).
- `favicon.svg` — page icon.

## Architecture notes

- Game state lives in module-level mutable state (`ship`, `bullets`, `asteroids`, `particles`, `score`, `lives`, `level`, `state`). No framework/state library.
- Main loop is `requestAnimationFrame` (`loop(ts)`); `dt` is clamped to 0.05s max.
- `update(dt)` / `draw()` split; state machine: `'playing' | 'dead' | 'gameover'`.
- World is toroidal (wrap): positions wrap via modulo against `W=800`, `H=600`.
- Collision: bullet vs asteroid uses `dist(b, a) < a.radius`; ship vs asteroid uses `dist(ship, a) < ship.radius + a.radius * 0.82`.

## Conventions

- Code identifiers in English; comments and user-facing strings in Spanish (keep existing style).
- Scoring/speed tables are module-level arrays indexed by asteroid `size` (`RADII`, `SPEEDS`, `POINTS`).

## Verification

- No automated tests. Verify changes by opening the game in a browser (prefer `npx serve .`) and exercising the loop manually.
