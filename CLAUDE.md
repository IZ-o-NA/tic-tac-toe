# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file browser Tic Tac Toe game (`tic-tac-toe.html`) with no build step, no dependencies, and no package manager. Open the file directly in a browser to run it.

## Architecture

Everything lives in `tic-tac-toe.html` — inline CSS, HTML, and JavaScript in one file. Key JS structure:

- `board`: flat 9-element array (`''`, `'X'`, or `'O'`)
- `WINS`: hardcoded array of winning index triples used by both the UI and AI
- `handleClick(i)` → `place()` → `checkWinner()` → `endGame()` is the main game flow
- `minimax(b, player)` runs unbeatable AI as `'O'`; called via `computerMove()` with a 350ms delay
- `checkWinnerFor(b)` is a pure-board version of `checkWinner()` used only by minimax (operates on an arbitrary board snapshot, not the live DOM)

## Git Workflow

Commit every meaningful change with a descriptive message and push to `origin/main`:

```bash
git add .
git commit -m "short description of what changed and why"
git push
```

To revert to a previous state:

```bash
git log --oneline          # find the commit hash
git revert <hash>          # safe, creates a new undo commit
```
