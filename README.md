# Touchline Tactics

An interactive 11-a-side football tactics board. Pick a formation, drag players into position, draw runs and passes, step through phases of play, and send the lineup to your team before a match.

Everything is in one file, `index.html`. There is no build step and nothing to install.

**Open it:** https://pattson22.github.io/ModernFootballFormation/

## Running it

- **Online:** use the GitHub Pages link above. It works on phones and computers, and it's the version to share with your team.
- **Locally:** open `index.html` in any modern browser (Chrome, Firefox, Safari or Edge).

On a phone, the pitch sits above the squad panel. If the page looks out of date after an update, pull down to refresh, or close the tab and open the link again.

## Features

### Formations
Choose from 4-3-3, 4-4-2, 4-2-3-1, 4-1-4-1, 4-4-1-1, 3-5-2, 3-4-3 and 5-3-2. Your team attacks up the pitch. Picking a formation repositions the players in the current phase and updates their position labels.

### Players and names
- Tap a player on the pitch. A box above the pitch shows their position and shirt number, and you can type their name there.
- Press **Enter** or tap **Next ›** to move to the next player, so you can fill in all 11 quickly.
- You can also type names and numbers straight into the **Starting XI** list.
- **Bench:** type your subs' names and numbers, and use **Add sub** for more rows (up to 12). To make a substitution, select a starter, choose a sub and tap **Swap**.

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

## Using it on a phone

- **Scrolling:** swipe on the grass to scroll the page.
- **Dragging:** touch a player or the ball and drag. The page won't scroll while you do.
- **Drawing:** in Run, Pass or Press mode, touching the pitch draws an arrow. To scroll, swipe outside the pitch or switch back to **Move**.

## Sharing the lineup

Tap **Share lineup** at the top. It builds a message with:
- the starting XI (position, number and name), the subs, and each phase's notes
- optionally, a link that opens the full board (formation, phases and arrows) on a teammate's phone, where they can press **▶ Play moves**

Send it with one of:
- **Share…**, which opens your phone's share menu. It only shows on devices that support it.
- **Send on WhatsApp**, which opens the WhatsApp app on a phone, or WhatsApp Web on a computer, with the message filled in.
- **Copy message**, then paste it into any group chat.

The whole plan is packed into the link, so nothing is uploaded anywhere. When a teammate opens it, a banner lets them go back to their own plan. Links from tampered or broken messages are checked and rejected safely.

Share from the GitHub Pages site. Other places that host the page, such as a Claude artifact, can block the phone share menu and WhatsApp links.

## Saving an image

Tap **Save image** in the toolbar to save the current phase as a PNG picture (1080 px wide). It includes:
- the team names, formation and phase name
- the pitch with every player's number and name, the opponents if they're shown, the ball and the arrows
- your named subs and the phase's notes

On Android and computers the picture downloads. On iPhone and iPad your share menu opens instead: tap **Save Image** to add it to Photos, or send it straight to WhatsApp. To save a different phase, select it first.

## Saving your plan

Your plan is saved automatically in your browser's local storage. That means:
- it stays on the device and browser you used, and isn't synced anywhere
- other people who open the site start with their own copy (use **Share lineup** to send them yours)
- clearing your browser data erases it

**Start over** (tap twice to confirm) resets the board to the example plan.

## Project structure

```
index.html   # the whole app: markup, styles and script
README.md
```

- The pitch is an SVG measured in metres (68 × 105, viewBox `-1.5 -2.5 71 110`).
- Players and the ball get invisible HTML "grab handles" placed over the SVG. Browsers ignore `touch-action` on SVG shapes, so the handles let a drag on a player block scrolling while a swipe on the grass still scrolls.
- The app state (players, bench, phases, kits) is a plain JSON object stored under the `touchline-v1` key in local storage. Share links carry the same object, compressed and base64url-encoded, in `#plan=…`.

## Deploying

GitHub Pages serves the `main` branch root. Push to `main` and the site updates within a minute or two.

The page includes its own `<!doctype>`, charset and viewport tags, and a `[hidden] { display: none !important }` rule, so it doesn't rely on any host to add them.
