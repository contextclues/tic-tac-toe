# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file browser game — all HTML, CSS, and JavaScript live in `index.html`. Open it directly in any browser; no build step, no dependencies, no package manager.

## Architecture

Everything is in one `<script>` block inside `index.html`:

- **State** — `cells` (9-element array), `current` (active player), `gameOver`, `vsCPU`, `scores`
- **`init()`** — resets state and re-renders the board
- **`render()`** — rebuilds all 9 `.cell` divs from `cells[]`; attaches click listeners
- **`handleClick(i)`** — handles human moves; delegates to `cpuMove()` after a 350ms delay in CPU mode
- **`cpuMove()`** — greedy 3-step AI: win → block → center → random (via `findBest()` + `randomEmpty()`)
- **`checkWin()`** — iterates `WINS` (8 hardcoded index combos) to find a winning line
- **`endGame(winCombo)`** — marks winner cells with `.win` class and updates the persistent score display

## Git & GitHub

- Remote: `https://github.com/contextclues/tic-tac-toe`
- Branch: `master`
- Commit style: conventional commits (`feat:`, `fix:`, `refactor:`, etc.)
- After every significant change: commit and push to `origin/master`
