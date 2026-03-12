# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the app

Open `tictactoe.html` directly in a browser — no build step, server, or dependencies required.

## Architecture

The entire application is a single self-contained HTML file with three sections:

- **CSS** (`<style>`): Dark-themed UI using CSS Grid for the 3×3 board. Cell states (`.x`, `.o`, `.taken`, `.win`) are toggled via class names.
- **HTML** (`<body>`): Static shell — board cells are generated dynamically by JavaScript on each render.
- **JavaScript** (`<script>`): Vanilla JS with no frameworks. Key globals:
  - `board` — flat 9-element array (`null | 'X' | 'O'`)
  - `current` — whose turn it is (`'X'` or `'O'`)
  - `gameOver` — boolean flag
  - `scores` — `{ X, O, draw }` object persisted across games in the same session
  - `WINS` — hardcoded array of all 8 winning index triplets
  - `render()` reconstructs all board cells from scratch on every move (full re-render pattern, no diffing)
  - `checkWinner()` returns `{ winner, line }` on terminal state, or `null` if game continues
