# Orbit Shot

A gravity puzzle game for the browser. Sling a probe past planets and let their gravity bend its path into the glowing gate. Blue planets pull, pink planets push.

Orbit Shot is a single HTML file. It has no dependencies, no build step and no server.

**Play it:** https://thanushi-paranagama.github.io/orbit-shot/ (available once GitHub Pages is switched on, see below)

## How to play

1. Press anywhere on the screen and drag backwards, like a slingshot.
2. A dotted line previews the first part of the path. Judge the rest yourself.
3. Release to launch.
4. Reach the amber gate to finish the level.

Crashing into a planet or leaving the screen resets the probe at no cost. Only launches are counted.

| Launches | Stars |
|----------|-------|
| 1        | 3     |
| 2 to 3   | 2     |
| 4 or more | 1    |

### Controls

| Input | Action |
|-------|--------|
| Mouse or touch drag | Aim and launch |
| `R` or the Retry button | Reset the probe |
| Levels button | Open the level menu |

Your stars are saved in the browser (`localStorage`), so they stay on the device you played on.

## Run it locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser (Chrome, Edge, Firefox or Safari).

The fonts (Unbounded and Manrope) load from Google Fonts, so the first load needs an internet connection. Without it the game falls back to a system font and still works.

## Publish it with GitHub Pages

1. Push `index.html` and this README to a repository named `orbit-shot`.
2. In the repository, open **Settings**, then **Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then save.
4. After a minute or two the game is live at the link at the top of this file.

## Customize

Everything is in `index.html`.

| What | Where |
|------|-------|
| Add or edit levels | The `LEVELS` array. `s` is the start, `g` is the gate, `b` is the list of planets (`x`, `y`, `r`, and `rep:1` for a planet that pushes). The play area is 1000 by 600. |
| Gravity strength | `K` |
| Launch power and maximum pull | `POWER` and `MAXPULL` |
| Aim preview length | The `46` in the aim preview loop (smaller is harder) |
| Gate size | The `< 30` check in the win test |
| Colours | The `:root` block in the CSS |

## How it works

- The game is drawn on a single `<canvas>` and scales to fit any screen.
- Each planet pulls or pushes the probe with a force that depends on the planet's size and falls off with distance squared.
- The probe is updated four times per frame for stable motion, and the aim preview uses the same physics.

## Project structure

```
orbit-shot/
├── index.html   # the whole game: markup, styles and code
└── README.md
```
