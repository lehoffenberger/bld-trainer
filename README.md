<div align="center">

<img src="icons/icon-512.png" width="128" alt="BLD Trainer icon">

# BLD Trainer

**A 3×3 blindfolded-solving practice tool: scramble, memorize, execute.**

It works out the letter-pair solution for your method and buffers, then checks every pair you type against the actual cube state.

[**▶ Open the trainer**](https://lehoffenberger.github.io/bld-trainer/)

![Installable PWA](https://img.shields.io/badge/PWA-installable-33507a?style=flat-square)
![Works offline](https://img.shields.io/badge/offline-ready-177a3c?style=flat-square)
![Zero dependencies](https://img.shields.io/badge/dependencies-zero-68686f?style=flat-square)
![Lettering](https://img.shields.io/badge/lettering-Speffz-8d1f2b?style=flat-square)

<br>

<img src="screenshots/home.png" width="240" alt="Cube state and scramble">&nbsp;&nbsp;
<img src="screenshots/memo.png" width="240" alt="Memo with live pair checking">&nbsp;&nbsp;
<img src="screenshots/scramble-dark.png" width="240" alt="Scramble-from-solved walkthrough, dark mode">

</div>

---

## What it does

The trainer splits blindfolded solving into three practice branches, so you can drill each skill on its own:

| Branch | What you practice |
|---|---|
| 🔀 **Scramble** | Scramble a solved cube using letter pairs, one algorithm at a time, with a diagram of what your cube should look like after each step. No move notation needed. |
| 🧠 **Memorize** | Trace the scramble and type your pairs. Edges and corners each get a field from the start, and each pair is checked the moment you type it. Pairs can be hidden (you derive them) or shown (you memorize them). |
| ⚡ **Execute** | Solve your physical cube from memory or sighted, timed or not, then step through the solution to review it. |

## Highlights

- **Checks against the real cube.** Your pairs are checked against the actual cube state, not one stored answer. Any helper that's part of *some* shortest solution is accepted, including breaking into a new cycle mid-trace. When a pair doesn't work, the hint says why: already solved, wrong sticker on the right piece, or costs extra pairs.
- **Every diagram is a real cube.** Pieces are tracked as whole cubies, so every state shown is one you could actually hold, including parity.
- **Your method, your buffers.** Choose a method per group, then change buffers and parity swaps freely. The whole solution recomputes.
- **3D floating-sticker view** (default) or a flat 2D net, with optional Speffz letters on every sticker.
- **Timers per group or one overall.** When you finish edges, the cursor jumps to corners and the corner timer takes over.
- **Paste your own scramble**, or step back and forth through scramble history.
- **Light and dark mode**, keyboard shortcuts (<kbd>←</kbd> <kbd>→</kbd> between buttons, <kbd>Enter</kbd> to advance), and a built-in guide with worked examples.

## Methods

| Group | Method | Default buffer | Parity alg |
|---|---|---|---|
| Corners | Old Pochmann | UBL · **A** | R-perm |
| Corners | Orozco / EKA / 3-Style | UFR · **C** | J-perm |
| Edges | Old Pochmann | UR · **B** | follows corners |
| Edges | M2 | DF · **U** | follows corners |
| Edges | Orozco / EKA / 3-Style | UF · **C** | follows corners |

Parity is one algorithm that swaps two corners *and* two edges. It runs **last** in a solution, which puts it **first** when scrambling. Your corner method picks the default alg, and you can override it or build a custom swap.

## Put it on your phone

It's a Progressive Web App, so it installs straight from the browser and then runs full screen and offline, with no app store and no account.

**iPhone**: open the link in **Safari** → Share → **Add to Home Screen**

**Android**: open the link in **Chrome** → ⋮ → **Install app**

<div align="center">
<img src="screenshots/guide.png" width="560" alt="Built-in guide with the Speffz lettering diagram">
<br><sub>The built-in guide, with every sticker's Speffz letter on a 3D cube</sub>
</div>

## Run it locally

No build step and no dependencies: the whole app is one HTML file.

```bash
git clone https://github.com/lehoffenberger/bld-trainer.git
cd bld-trainer
python3 -m http.server 8000     # then open http://localhost:8000
```

Opening `index.html` directly works too. The service worker (offline mode) only runs when the files are served over `http://localhost` or HTTPS.

## Project layout

```
index.html            the entire app: cube model, solver, validator, UI, guide
manifest.webmanifest  install metadata (name, icons, colors)
sw.js                 offline cache; updates land on the next launch
icons/                app icons (standard, maskable, Apple touch)
screenshots/          images for this README
```

## Credits

- **Cube model**: cubie representation and facelet indexing follow [cube.js](https://github.com/ldez/cubejs) (MIT License, © 2013-2017 Petri Lehtinen, © 2018 Ludovic Fernandez; the full notice is in the app's guide) and [Herbert Kociemba](http://kociemba.org/cube.htm)'s permutation-and-orientation model.
- **Lettering**: [Speffz](https://www.speedsolving.com/wiki/index.php/Speffz), by Ville Seppänen and Rob Holt.
- **Methods**: Old Pochmann and M2 by Stefan Pochmann; 3-Style (Beyer–Hardwick) by Chris Hardwick and Daniel Beyer; Orozco by Gabriel Alejandro Orozco Casillas; Eka.
- **Tutorials**: [J Perm's BLD guide](https://www.jperm.net/bld) is a great place to learn the methods.
- **Typefaces**: Instrument Sans and IBM Plex Mono (SIL Open Font License), via Google Fonts.

<div align="center">
<br>
<sub>Built by <a href="https://github.com/lehoffenberger">@lehoffenberger</a> for blindfolded practice.</sub>
</div>
