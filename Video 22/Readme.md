# 📐 CSS Sizing Units — Complete Reference


## 🗂️ Table of Contents

1. [Absolute Units](#absolute-units)
2. [Relative Units — Font-based](#relative-units--font-based)
3. [Relative Units — Viewport-based](#relative-units--viewport-based)
4. [Relative Units — Container-based](#relative-units--container-based)
5. [Percentage](#percentage)
6. [Intrinsic / Content-based Keywords](#intrinsic--content-based-keywords)
7. [Quick Comparison Cheatsheet](#quick-comparison-cheatsheet)
8. [When to Use What](#when-to-use-what)

---

## Absolute Units

These are fixed — they don't change based on anything. Mostly used for print or when you need pixel-perfect control.

| Unit | Full Name   | Equivalent         |
|------|-------------|---------------------|
| `px` | Pixel       | 1px = 1/96 of 1 inch |
| `pt` | Point       | 1pt = 1/72 of 1 inch |
| `cm` | Centimeter  | 1cm = 37.8px        |
| `mm` | Millimeter  | 1mm = 3.78px        |
| `in` | Inch        | 1in = 96px          |
| `pc` | Pica        | 1pc = 16px          |

### Example

```css
.box {
  width: 300px;
  border: 2pt solid black;
  padding: 1cm;
  font-size: 12pt;
}
```

> ⚠️ **Tip:** Use `px` for screens. Use `pt`, `cm`, `mm` for print stylesheets (`@media print`).

---

## Relative Units — Font-based

These scale relative to font size. Great for responsive typography and spacing.

---

### `em`

Relative to the **font-size of the current element**.

```css
.parent {
  font-size: 16px;
}

.child {
  font-size: 1.5em;   /* 16 × 1.5 = 24px */
  padding: 1em;        /* 24px (relative to its own font-size now) */
  margin: 0.5em;       /* 12px */
}
```

> ⚠️ **Watch out:** `em` compounds when nested — a child inside a child can get huge fast.

---

### `rem`

Relative to the **root element's font-size** (`<html>`). No compounding.

```css
html {
  font-size: 16px; /* 1rem = 16px */
}

h1 { font-size: 3rem; }     /* 48px */
p  { font-size: 1rem; }     /* 16px */
small { font-size: 0.75rem; } /* 12px */
```

> ✅ **Best practice:** Use `rem` for font sizes across the project. Consistent and predictable.

---

### `ch`

Relative to the **width of the "0" character** of the current font.

```css
input {
  width: 20ch; /* roughly fits 20 characters */
}

p {
  max-width: 65ch; /* ideal reading line length */
}
```

> ✅ **Great for:** Input fields and limiting line length for readability.

---

### `ex`

Relative to the **x-height** of the current font (height of lowercase "x"). Rarely used.

```css
.superscript {
  vertical-align: 1ex;
  font-size: 0.75em;
}
```

---

### `cap`

Relative to the **cap height** (height of uppercase letters). Still gaining browser support.

```css
.icon-align {
  height: 1cap; /* matches the height of capital letters */
}
```

---

### `lh` / `rlh`

- `lh` — relative to the **line-height of the element**
- `rlh` — relative to the **line-height of the root element**

```css
.spaced-block {
  margin-bottom: 1lh; /* exactly one line's worth of space */
}
```

---

## Relative Units — Viewport-based

Relative to the browser viewport (the visible screen area).

---

### `vw` / `vh`

- `vw` — 1% of the **viewport width**
- `vh` — 1% of the **viewport height**

```css
.hero {
  width: 100vw;
  height: 100vh;
}

.half-screen {
  width: 50vw;
  height: 50vh;
}

h1 {
  font-size: 8vw; /* scales with screen width */
}
```

---

### `svh` / `lvh` / `dvh` (and `svw`, `lvw`, `dvw`)

Mobile browsers have a collapsing address bar. These new units handle it:

| Unit  | Stands for         | Behavior                            |
|-------|--------------------|--------------------------------------|
| `svh` | Small Viewport Height | Smallest possible viewport (bar visible) |
| `lvh` | Large Viewport Height | Largest possible viewport (bar hidden) |
| `dvh` | Dynamic Viewport Height | Updates dynamically as bar shows/hides |

```css
/* Old way — caused layout bugs on mobile */
.hero {
  height: 100vh;
}

/* New way — safe on mobile */
.hero {
  height: 100svh; /* won't get cut off by browser chrome */
}

/* Fully dynamic — tracks bar movement */
.hero {
  height: 100dvh;
}
```

> ✅ **Pro tip bro:** Always use `100svh` or `100dvh` instead of `100vh` for mobile-first hero sections.

---

### `vmin` / `vmax`

- `vmin` — 1% of the **smaller** viewport dimension
- `vmax` — 1% of the **larger** viewport dimension

```css
.square {
  width: 50vmin;  /* 50% of the shorter side — stays square on any screen */
  height: 50vmin;
}

.full-bleed-bg {
  font-size: 10vmax; /* always based on the bigger dimension */
}
```

---

## Relative Units — Container-based

Relative to a **parent container**, not the viewport. Requires `container-type` on the parent.

| Unit  | Relative to             |
|-------|--------------------------|
| `cqw` | Container query width    |
| `cqh` | Container query height   |
| `cqi` | Container inline size    |
| `cqb` | Container block size     |
| `cqmin` | Smaller of cqi/cqb    |
| `cqmax` | Larger of cqi/cqb     |

```css
/* Step 1: Define the container */
.card-wrapper {
  container-type: inline-size;
}

/* Step 2: Size children relative to that container */
.card h2 {
  font-size: 5cqw; /* 5% of the card's width */
}

.card p {
  font-size: clamp(14px, 3cqw, 18px);
}
```

> ✅ **Use case:** Component-level responsiveness — the card adapts based on *its own size*, not the screen.

---

## Percentage

Relative to the **parent element's** corresponding dimension.

```css
.parent {
  width: 800px;
  height: 400px;
}

.child {
  width: 50%;     /* 400px */
  height: 75%;    /* 300px — only works if parent has explicit height */
  padding: 5%;    /* 40px — padding % is always relative to parent WIDTH */
  font-size: 120%; /* 120% of parent's font-size */
}
```

> ⚠️ **Gotcha:** `height: 50%` won't work unless the parent has an explicit height defined.

---

## Intrinsic / Content-based Keywords

These aren't number units but they control sizing based on content.

| Value          | Behavior |
|----------------|----------|
| `auto`         | Browser figures it out |
| `min-content`  | Shrinks to smallest possible size |
| `max-content`  | Expands to fit content fully |
| `fit-content`  | Uses available space but won't exceed max-content |
| `fit-content(X)` | Like fit-content but capped at X |

```css
.tag {
  width: max-content;   /* wraps tightly around text */
}

.sidebar {
  width: min-content;   /* as narrow as possible */
}

.button {
  width: fit-content;   /* fills space but hugs content if space is tight */
}

.tooltip {
  width: fit-content(200px); /* max 200px, shrinks if content is smaller */
}
```

---

## `clamp()` — The GOAT of responsive sizing

Combines min, preferred, and max in one line. Works with any unit.

```css
/* Syntax: clamp(min, preferred, max) */

h1 {
  font-size: clamp(1.5rem, 5vw, 4rem);
  /* min: 24px | scales with viewport | max: 64px */
}

.container {
  width: clamp(320px, 90%, 1200px);
  /* never smaller than 320px, never bigger than 1200px */
}

p {
  line-height: clamp(1.4, 1.2 + 0.5vw, 1.8);
}
```

> ✅ **This replaces a ton of media queries.** Use it everywhere for fluid typography and layout.

---

## Quick Comparison Cheatsheet

```
px      → fixed pixels. predictable, not scalable
em      → relative to current element's font-size. compounds when nested
rem     → relative to root font-size. consistent across components
%       → relative to parent. great for layout, tricky for height
vh/vw   → relative to viewport. great for full-screen sections
svh/dvh → viewport-aware for mobile. use instead of vh in hero sections
ch      → character width. great for input sizing & readable line lengths
cqw     → container query units. component-level responsiveness
clamp() → responsive range. replaces media queries for fluid scaling
```

---

## When to Use What

| Scenario                              | Recommended Unit          |
|---------------------------------------|---------------------------|
| Font sizes (global)                   | `rem`                     |
| Font sizes (component-relative)       | `em`                      |
| Full-screen hero section              | `100svh` or `100dvh`      |
| Fluid heading typography              | `clamp(rem, vw, rem)`     |
| Input field width                     | `ch`                       |
| Readable paragraph width             | `ch` or `clamp()`         |
| Layout widths                         | `%` or `clamp()`          |
| Spacing (padding/margin)              | `rem` or `em`             |
| Component-level responsiveness        | `cqw`, `cqi`              |
| Print styles                          | `pt`, `cm`, `mm`          |
| Animations / transforms               | `px` or `%`               |
| Keeping aspect ratio on any screen    | `vmin`                    |

---

## 🔗 Further Reading

- [MDN — CSS Values and Units](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units)
- [MDN — Viewport Units](https://developer.mozilla.org/en-US/docs/Web/CSS/length#viewport-percentage_lengths)
- [MDN — Container Query Units](https://developer.mozilla.org/en-US/docs/Web/CSS/length#container_query_length_units)
- [MDN — clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)

---