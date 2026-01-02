# Jump Run – Simple JavaScript Jumping Game

A small browser-based jumping game where you control a hero that jumps over a moving enemy using the spacebar.

## Demo Overview

- Press **Spacebar** to make the hero jump.
- A wolf (the “villain”) runs from right to left.
- If the wolf reaches the hero while the hero is on the ground, the game shows **“Game over. Press spacebar to start”** and you can try again.

The game is implemented with plain HTML, CSS, and vanilla JavaScript—no frameworks.

---

## Tech Stack

- **HTML5** – game layout and structure
- **CSS3** – styling, background, and animations
- **JavaScript (vanilla)** – input handling, jump animation trigger, collision detection
- **Assets** – simple GIF/PNG sprites in `images/`

---

## Project Structure

```text
jump-run/
├─ index.html      # Main page and game markup
├─ styles.css      # Styling and animations
├─ script.js       # Game logic
├─ images/         # hero, wolf, and background assets
└─ package.json    # Basic npm metadata (no build tooling required)
```
##Getting Started

1. Clone or download

```
git clone <your-repo-url>
cd jump-run
```
2. Open in a browser

No build step is required.

•  Open index.html directly in your browser, or
•  Use a simple static server, e.g.:
```
# with npx
npx serve .

# or with Python
python -m http.server 8000
```
Then visit: http://localhost:8000/index.html
How It Works

Markup (index.html)

•  .game – container for the hero and villain.
•  .hero – wrapper for the hero sprite.
•  .vilan – wrapper for the wolf sprite.

The text “Press spacebar to start” explains the main control.

Styling & Animations (styles.css)

Key parts:

•  Layout:
◦  Full-height section centered using flexbox.
◦  Background image (images/forest1.gif) for the game container.
•  Hero:
◦  Positioned near the left bottom of the game area.
◦  Jump animation defined via @keyframes jump and applied by .animate.
•  Villain:
◦  Positioned on the right and animated with @keyframes move when the game is active.

Game Logic (script.js)

Main pieces:

•  Jump:
◦  jump() adds the animate class to .hero, triggering the CSS jump animation.
◦  After 300ms, it removes animate to allow another jump.
◦  Also starts the wolf animation (vilan.style.animation = "move 1s infinite linear").
•  Controls:
◦  document.addEventListener("keydown", ...) listens for Space and calls jump().
•  Collision Detection:
◦  A setInterval every 10ms reads:
▪  heroTop – hero’s vertical position (top CSS property).
▪  vilanLeft – wolf’s horizontal position (left CSS property).
◦  If the wolf is close (vilanLeft < 40 && vilanLeft > 20) and the hero is low (heroTop >= 130), the game is considered a collision:
▪  Wolf animation is stopped.
▪  An alert shows: “Game over. Press spacebar to start”.



Ideas for Improvement

If you want to extend the game:

•  Add a score that increases over time or per dodge.
•  Add difficulty levels by speeding up the wolf.
•  Replace alert() with a custom in-page modal or overlay.
•  Add sound effects for jumps and collisions.
•  Support mobile/touch controls (tap to jump).
