# Matrix Mystics Solutions — CodersHigh

> A single-file, interactive HTML learning companion for the **Matrix Mystics** course — teaching linear algebra, matrices, and their real-world applications through guided questions, GeoGebra visualizations, and collapsible explanations.

Made with ❤️ for the love of teaching & learning.

---

## 📑 Contents of this markdown file

- [Overview](#-overview)
- [Features](#-features)
- [Curriculum at a Glance](#-curriculum-at-a-glance)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [How to Use](#-how-to-use)
- [UI & Layout](#-ui--layout)
- [External Resources](#-external-resources)
- [Customization](#-customization)
- [Browser Support](#-browser-support)
- [Credits & Acknowledgments](#-credits--acknowledgments)

---

## 🧭 Overview

**Matrix Mystics Solutions (`CodersHigh.html`)** is a self-contained, dependency-light web page that hosts the entire question bank of the *CodersHigh* module under the **Matrix Mystics** learning track.

The page lays out **53 curated questions across 6 modules**, walking learners from the very basics of plotting points and lines, all the way to advanced applications like **PageRank**, **Recommender Systems**, and **Principal Component Analysis (PCA)**.

Every question is rendered as a card with a **"Reveal Explanation"** toggle. Explanations use **KaTeX** for beautiful math rendering and **GeoGebra** links for hands-on visualization. All **53 questions** now have fully worked solutions — the question bank is complete.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🗂 **Sidebar Navigation** | Sticky sidebar with collapsible `<details>` elements grouping questions by module. All modules are open by default for quick access. *Note:* By design — for viewer friendliness — the **"Question 1"** entry of each module links to the module heading anchor (`#M1`, `#M2`, …) so you land on the module overview first; all other **"Question N"** links go directly to their question card (`#M1Q2`, `#M2Q3`, …). |
| 🧮 **KaTeX Math Rendering** | Inline and display math (LaTeX) is rendered automatically on page load using `renderMathInElement`. |
| 🎴 **Question Cards** | Each question lives in its own card with an ID like `M1Q1`, `M2Q3`, etc. (also used as anchor links for deep-linking). |
| 👁 **Toggle Explanations** | Click the caret button on any card to instantly show or hide its worked solution. The toggle button itself has a smooth 180° rotation when opened (`transform` transition, 0.3s ease), while the answer panel snaps open/closed via the native `hidden` attribute for a snappy, lag-free feel. |
| 🎆 **Fireworks Easter Egg** | Click the *"Made with ❤️ …"* footer to launch a colorful fireworks animation (Canvas-based). |
| 📱 **Responsive Layout** | Flexbox layout with a sticky sidebar and scrollable main panel. Overscroll behavior is disabled for a cleaner feel. |
| 🎨 **Warm Theme** | Beige / cream / warm-brown color palette (`#f5efe3`, `#6b4f2a`, `#9d7a4b`) for a paper-like reading experience. |
| ⛓ **Deep-Linkable** | Every question has a stable `id` (`#M1Q1`, `#M2Q7`, …) so you can link directly to a specific question. |
| 🔗 **External Hub Links** | Quick-access buttons at the top of the sidebar for **GeoGebra**, the **Discourse forum**, and the **Samagama** portal. |

---

## 📚 Curriculum at a Glance

The course is organized into **6 modules** with a total of **53 questions**:

### Module 1 — *Foundations of Plots, Functions & Matrices* (16 questions)
From real-world data → algebraic relationships → plotting on a coordinate plane. Introduces lines through the origin, slope, intercept, simultaneous equations as `Ax = b`, and the notion of a matrix as a function.

Highlights: **M1Q1** (Ram & Lakshman savings story), **M1Q7** (matrix form of simultaneous equations), **M1Q16** (matrix sending multiple points to the origin).

### Module 2 — *Applications: Ciphers & Markov Chains* (7 questions)
- **Hill Cipher** decryption using matrix inverse.
- The *Baker's Cafe* simultaneous-equations story.
- Over/under-determined systems & why they may have no exact solution.
- Markov chains: long-term distribution of 1000 people across states.

### Module 3 — *Vectors, Subspaces & the Null Space* (15 questions)
Perpendicular vectors, parametric spans, column space, row space, null space, and the famous realization: **"B collapses a dimension."**

### Module 4 — *Four Fundamental Subspaces* (7 questions)
Null space, column space, range, and the orthogonal relationships: `C(M) ⊥ N(Mᵀ)`, `R(M) ⊥ N(M)`. Examples for ranks 0 through 4.

### Module 5 — *Subspaces of ℝ³* (5 questions)
Constructing 2-D subspaces, their orthogonal complements, and building a matrix with prescribed null-space and column-space.

### Module 6 — *Real-World Applications* (3 questions)
- **Recommender Systems** — Matrix Factorization & SVD.
- **PageRank** — Google's link analysis as a Markov-chain stationary distribution.
- **Dimensionality Reduction** — PCA, eigen-decomposition, Eigenfaces.

---

## 🛠 Tech Stack

This project is intentionally **zero-build** — open the file and you're done.

| Layer | Choice |
|---|---|
| Markup | HTML5 |
| Styling | Hand-written CSS (no preprocessor) |
| Behavior | Vanilla JavaScript (ES2015+) |
| Math Rendering | [KaTeX 0.16.11](https://katex.org/) (CDN) |
| Visualization | [GeoGebra](https://www.geogebra.org/) (external) |
| Animation | HTML5 Canvas + CSS transitions |

---

## 🗂 Project Structure

```
MatrixMystics/
├── CodersHigh.html      # The entire app (HTML + CSS + JS in one file)
└── readme.md            # ← this file
```

The HTML file is organized into the following logical sections (see the source):

1. `<head>` — meta tags, KaTeX CDN links, inline `<style>`.
2. `<aside class="sidebar">` — module index & external links.
3. `<main class="main">` — module headings + question cards.
4. `<canvas class="fireworks">` — overlay for the fireworks easter egg.
5. Three `<script>` blocks at the bottom of the file:
   - **Reveal/hide toggle** — wires each caret button to its `answer-wrap` (with ARIA `aria-controls` / `aria-expanded` for accessibility).
   - **Smooth-scroll sidebar** — intercepts in-page anchor clicks, uses `scrollIntoView` inside a double `requestAnimationFrame`, and updates the URL with `history.pushState`.
   - **Fireworks animation** — Canvas-based particle system triggered by clicking the *"Made with ❤️…"* footer.

---

## 🚀 Getting Started

### Option 1 — Open Directly
Just double-click `CodersHigh.html` (or right-click → *Open with…* your browser).

### Option 2 — Serve Locally (recommended for cleaner module loading)
From the `MatrixMystics/` directory, run any one of:

```bash
# Python 3
python -m http.server 8000

# Node.js (no install needed if you have npx)
npx serve .

# PHP
php -S localhost:8000
```

Then visit: **http://localhost:8000/CodersHigh.html**

### Option 3 — Just Read the Source
The file is fully readable as plain text — no transpilation step required.

---

## 🖱 How to Use

1. **Browse the sidebar** to jump to any module / question.
2. **Read the question** in the card.
3. **Open GeoGebra** (link at the top of the sidebar) and try to solve it visually.
4. **Click "Reveal Explanation"** to see the worked solution.
5. **Discuss** difficult questions in the [Matrix Mystics Discourse forum](https://vicharanashala.discourse.group/t/matrix-mystics-discussion-forum/516).
6. **Easter egg:** Click the *"Made with ❤️ …"* line at the top of the main panel to enjoy a fireworks show. 🎆

> 💡 Tip: Each question has a stable `id` (e.g., `#M3Q9`). Append it to the URL to share a direct link to a specific question.

---

## 🎨 UI & Layout

### Color Palette
| Role | Hex |
|---|---|
| Page background | `#f5efe3` (warm cream) |
| Card background | `#fbf7ef` |
| Accent / headings | `#6b4f2a` (warm brown) |
| Border / dividers | `#d8c8a8` |
| Math highlight | `#f2eadb` (with `#9d7a4b` left bar) |

### Typography
- Body: **Inter**, with system-ui / Segoe UI / Roboto fallbacks.
- Mono ("Made with…" line): `ui-monospace, 'SF Mono', 'Cascadia Code', Consolas, Monaco, monospace`.

### Layout
- **Desktop:** Two-column flex layout — 260px sticky sidebar + flexible main panel.
- **Mobile:** The sidebar scrolls independently; the main column takes the remaining width. (A media query to fully collapse the sidebar on narrow screens is a future enhancement.)

---

## 🌐 External Resources

These are linked directly from the sidebar:

- **[GeoGebra](https://www.geogebra.org)** — Interactive math visualization.
- **[Matrix Mystics Discussion Forum](https://vicharanashala.discourse.group/t/matrix-mystics-discussion-forum/516)** — Discourse-based community Q&A.
- **[Samagama](https://samagama.in/)** — Companion learning portal.

Two figures used in Module 2 are loaded from the [sudarshansudarshan.github.io/codershigh](https://sudarshansudarshan.github.io/codershigh/assets/) asset host:
- `assets/markov2.png`
- `assets/markov3.png`

---

## 🧩 Customization

Because everything lives in one file, customization is straightforward:

| What | Where |
|---|---|
| Theme colors | Inline `<style>` block — search for the hex codes listed in [UI & Layout](#-ui--layout). |
| Add a question | Copy any `<div class="card" id="MxQy">…</div>` block and update the `id`, question text, and explanation. |
| Add a new module | Append a `<details>` to the sidebar and a new `<div class="module-heading" id="M7">Module 7</div>` in `<main>`. |
| Replace the fireworks | Edit the third `<script>` block at the bottom of the file. |
| Change fonts | Update the `font-family` in the `body` selector inside the inline `<style>`. |
| Pin a question open | Override the `hidden` attribute for that specific card (e.g. set `wrap.hidden = false` directly in the initialization script) and add the `open` class to its caret button so the rotation animation matches the visible state. |

---

## 🌎 Browser Support

Tested conceptually against modern evergreen browsers:

- ✅ Chrome / Edge (Chromium) 100+
- ✅ Firefox 100+
- ✅ Safari 15+
- ⚠️ Older browsers may not support `requestAnimationFrame` timing the way the toggle animation expects; KaTeX itself requires a modern engine.

Requires JavaScript enabled. No internet is needed *except* to load KaTeX from `cdn.jsdelivr.net` and the two Module-2 image assets. To make it fully offline, download KaTeX locally and replace the three `<script>`/`<link>` tags in the `<head>`.

---

## 🙏 Credits & Acknowledgments

- **Course & Question Design:** Professor S.R.S Iyengar, the CodersHigh team and the broader VLED community.
- **Math Rendering:** [KaTeX](https://katex.org/) — the fastest math typesetting library for the web.
- **Visualization Tool:** [GeoGebra](https://www.geogebra.org/).
- **Community Hub:** [Samagama](https://samagama.in/) & the [Matrix Mystics Discourse forum](https://vicharanashala.discourse.group/t/matrix-mystics-discussion-forum/516).

---

## 📄 License

This educational material is provided as-is for the love of teaching & learning. Please attribute *Matrix Mystics* and the original authors when redistributing.

---

*Happy learning! May the matrix be with you.* 🧮✨
