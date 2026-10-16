# Touchline Tactics

An interactive 11-a-side football tactics board. Pick a formation, drag players into position, draw runs and passes, and step through phases of play before a match.

Everything is in one file, `index.html`. There is no build step and nothing to install.

## Running it

- **Locally:** open `index.html` in any modern browser (Chrome, Firefox, Safari or Edge).
- **Online:** https://pattson22.github.io/ModernFootballFormation/ (GitHub Pages, public).

It works on phones and on desktop. On a phone, the pitch sits above the squad panel.

## Features

### Formations
Choose from 4-3-3, 4-4-2, 4-2-3-1, 4-1-4-1, 4-4-1-1, 3-5-2, 3-4-3 and 5-3-2. Your team attacks up the pitch. Picking a formation repositions the players in the current phase and updates their position labels.

### Players and names
- Tap a player on the pitch to select them. A box above the pitch shows their position and shirt number, and you can type their name there.
- Press **Enter** or tap **Next ›** to move to the next player, so you can fill in all 11 quickly.
- You can also edit names and numbers in the **Starting XI** list.
- **Bench:** add substitutes. To make a substitution, select a starter, choose a sub and tap **Swap**.

### Movement
| Tool | Shortcut | What it does |
|------|----------|--------------|
| Move | `V` | Drag players, opponents and the ball |
| Run | `R` | Draw a white arrow for a player's run |
| Pass | `P` | Draw a yellow dashed arrow for a pass |
| Press | `X` | Draw a red arrow for pressing |
| Erase | `E` | Tap an arrow to remove it |

An arrow that starts on a player snaps to that player. When a player is selected, the arrow keys nudge them 1 m, or 5 m with Shift held.

**Team shape buttons:** Push up, Drop, Narrow and Widen move all outfield players at once.

### Phases
A plan is a sequence of phases, such as *Base shape → In possession → Out of possession*.
- **+ Add phase** copies the current phase so you can adjust it.
- Each phase has its own name, notes and arrows.
- **▶ Play moves** (or `Space`) animates the players from one phase to the next.
- **Trails** shows where each player stood in the previous phase.

### Opponents
Turn on **Opponents** to place the other team in any formation and drag them around.

### Kits
Set the colours for your outfield players, your goalkeeper and the opponents.

## Saving

Your plan is saved automatically in your browser's local storage. That means:
- it stays on the device and browser you used, and isn't synced anywhere
- other people who open the link start with their own copy
- clearing your browser data erases it

**Start over** (tap twice to confirm) resets the board to the example plan.

## Project structure

```
index.html   # the whole app: markup, styles and script
README.md
```

The pitch is an SVG measured in metres (68 × 105). The app state (players, bench, phases, kits) is a plain JSON object stored under the `touchline-v1` key in local storage.
