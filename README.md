# Cube Solver — any N×N, step by step

A free, single-file web app that solves any Rubik's-style cube from **2×2 up to 10×10**, shows you every move with arrows on a 3D view, and teaches you to solve cubes yourself.

No installs, no server, no internet connection needed after the page loads. Everything runs in your browser.

**▶ Live demo:** `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/` *(replace with your GitHub Pages link)*

---

## Features

### Solver
- **Any size cube:** 2×2, 3×3, 4×4, 5×5 … 10×10.
- **Three ways to enter your cube:**
  - paste a sticker state (URFDLB order, the format most cube sites export),
  - paste a scramble (`R U' 2R Rw2 …`),
  - or paint stickers by clicking them on the unfolded view.
- **Validity check before solving:** catches wrong colour counts, impossible or duplicated pieces, twisted corners, flipped edges and swapped pieces, and marks the problem stickers with a red ✗.
- **Short solutions:** about 20 moves for a 3×3, ~100 for a 4×4, ~150–170 for a 5×5.
- **Step-by-step player:**
  - the next move in big letters plus a plain-English description,
  - direction arrows on the 3D views and the unfolded view,
  - the turning layer highlighted,
  - step or move forward and back, auto-play at 1–8 seconds per move, and keyboard shortcuts.
- **Two notations:** slice style (`2R`) or WCA wide style (`Rw R'`).
- **Fireworks** when the cube is solved 🎉

### Learn to solve
- Switch to **Learn to solve** mode for a tutorial for each cube size.
- Several methods per cube, each with its own steps and algorithms:
  - **2×2:** Layer by layer, Ortega, CLL, EG
  - **3×3:** Beginner, CFOP (2-look OLL/PLL, F2L), Roux, ZZ, Petrus
  - **4×4:** Reduction (with OLL and PLL parity), Yau, Hoya, Cage
  - **5×5:** Reduction (with edge parity), Yau5, Free-slice, Cage
  - **6×6 and bigger:** Reduction, Yau-style, Cage
- **▶ Show me** sets up the exact case on the cube and plays the algorithm with arrows, so you can read and watch side by side.

### Other
- Shareable links: the cube state is kept in the page address.
- Works on desktop and phones, in light and dark mode.
- Click the **Cube Solver** title to start over.

---

## How to use

1. **Pick your cube size** at the top. It starts on 3×3.
2. **Enter your cube** by pasting a state string or a scramble, or by painting stickers, then press **Apply**.
3. Check that the **Cube check** panel says **Valid cube**.
4. Press **Solve this cube**.
5. **Hold your cube like the front view:** top colour on top, front colour facing you. Then follow the moves with **›** or the **→** key.

### State string format

There are 6 × N × N letters, one per sticker, in the order **U R F D L B**, with each face read row by row:
- **U (top):** viewed from above, with the back edge at the top.
- **R, F, L, B:** viewed straight on, with the top edge at the top.
- **D (bottom):** viewed from below, with the front edge at the top.

Use the letters `U R F D L B` for the colour of each face's centre. Any 6 distinct symbols also work.

A solved 3×3 looks like this:
```
UUUUUUUUURRRRRRRRRFFFFFFFFFDDDDDDDDDLLLLLLLLLBBBBBBBBB
```

### Move notation

| Move | Meaning |
|---|---|
| `R U F L D B` | Turn that outer face a quarter turn clockwise, as seen looking at that face |
| `R'`, `R2` | Counter-clockwise quarter turn; half turn |
| `2R`, `3U` | Turn only that one inner layer (counted in from the face) |
| `2-3R` | Turn inner layers 2 to 3 together |
| `Rw`, `3Rw` | WCA wide turn: the outer 2 (or 3) layers together |
| `M E S` | 3×3 middle layers |
| `x y z` | Rotate the whole cube |

Keyboard: **← / →** one move, **Shift + ← / →** one step, **Space** play or pause.

---

## How the solver works

The solver uses **reduction**, the same idea people use for big cubes:

1. **Centres** are built with a beam search over all layer turns, then finished with short centre commutators.
2. **Edges** are paired with "slice, flip, unslice" moves that keep the centres intact.
3. The remaining **3×3** (corners and edges) is solved with a two-phase (Kociemba-style) search, usually in about 20 moves.
4. Any **leftover edge pieces** are fixed with pure commutators, which also takes care of 4×4/5×5 parity.

For small cubes it runs several search settings and keeps the shortest solution. Every result is checked by simulation before it is shown.

---

## Hosting

The app is one file, `index.html`, with no dependencies, so any static host works: GitHub Pages, Netlify, Vercel, or just opening the file from your computer.

## Limitations

- Solutions are good, not optimal. Expert human or record-solver move counts need large precomputed tables.
- Bigger cubes (7×7+) need several hundred to over a thousand moves, and solving can take up to ~10 seconds.
- The Learn section lists the 2-look and beginner algorithms. Full expert sets (57 OLL, 21 PLL, 42 CLL…) are described but not listed one by one.

## License

Add a license of your choice, for example MIT, if you want others to reuse the code.
