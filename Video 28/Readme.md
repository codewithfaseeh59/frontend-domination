# CSS Position Property — Complete Reference

> **Frontend Domination** | CSS Deep Dives

---

## Table of Contents

- [What is Position?](#what-is-position)
- [position: static](#1-position-static)
- [position: relative](#2-position-relative)
- [position: absolute](#3-position-absolute)
- [position: fixed](#4-position-fixed)
- [position: sticky](#5-position-sticky)
- [Offset Properties](#offset-properties-top-right-bottom-left)
- [z-index & Stacking Context](#z-index--stacking-context)
- [Common Patterns](#common-real-world-patterns)
- [Common Gotchas](#common-gotchas)
- [Quick Reference Table](#quick-reference-table)

---

## What is Position?

The `position` property controls **how an element is placed** in the document. It determines:

- Whether the element stays in the **normal document flow** or gets taken out
- What it is **positioned relative to** (itself, parent, viewport)
- Whether `top`, `right`, `bottom`, `left` offsets have any effect

```css
/* Syntax */
position: static | relative | absolute | fixed | sticky;
```

---

## 1. `position: static`

### Definition
The **default** value for every element. Elements are placed according to the normal document flow — block elements stack vertically, inline elements sit side by side.

### Key Rules
- `top`, `right`, `bottom`, `left` have **zero effect**
- `z-index` has **zero effect**
- Cannot act as a positioning context for absolute children

### Example

```html
<div class="box-a">Box A</div>
<div class="box-b">Box B</div>
<div class="box-c">Box C</div>
```

```css
/* Static is the default — no need to write it explicitly */
.box-a,
.box-b,
.box-c {
  position: static; /* same as not writing position at all */
  top: 20px;        /* IGNORED — has no effect */
  z-index: 99;      /* IGNORED — has no effect */
}
```

### When to Use
- You never explicitly set `static` — elements are already static by default
- You might use it to **reset** a position value inherited from a class

```css
/* Resetting position on a specific element */
.override {
  position: static;
}
```

---

## 2. `position: relative`

### Definition
The element stays in the **normal document flow**, but you can **nudge it** using `top`, `right`, `bottom`, `left`. The original space the element occupied is **preserved** — other elements don't move to fill the gap.

### Key Rules
- Element stays in flow (takes up its original space)
- Offsets move it **relative to its own normal position**
- Acts as a **positioning context** for absolutely positioned children
- `z-index` works

### Example

```html
<div class="box-a">Box A</div>
<div class="box-b">Box B</div>
<div class="box-c">Box C</div>
```

```css
.box-b {
  position: relative;
  top: 20px;   /* moves DOWN by 20px from its original position */
  left: 30px;  /* moves RIGHT by 30px from its original position */
}
```

> Box B visually shifts, but Box A and Box C don't move — the original space of Box B is still reserved.

### Negative Offsets

```css
.box-b {
  position: relative;
  top: -10px;  /* moves UP */
  left: -20px; /* moves LEFT */
}
```

### Most Common Use Case — Positioning Context

```css
/* Parent as anchor for absolute child */
.card {
  position: relative; /* makes this the reference point */
}

.card .badge {
  position: absolute; /* positioned relative to .card */
  top: 10px;
  right: 10px;
}
```

---

## 3. `position: absolute`

### Definition
The element is **removed from the normal document flow** — it takes up no space and other elements behave as if it doesn't exist. It positions itself relative to the **nearest positioned ancestor** (an ancestor with any `position` value other than `static`). If no positioned ancestor exists, it falls back to the `<html>` element.

### Key Rules
- Removed from flow (takes up no space)
- Positioned relative to **nearest non-static ancestor**
- If no positioned ancestor → positioned relative to `<html>`
- `z-index` works
- Element becomes a block-level box regardless of its original display type

### Example — With a Positioned Parent

```html
<div class="parent">
  <p>Some content here</p>
  <div class="badge">NEW</div>
</div>
```

```css
.parent {
  position: relative; /* anchor point */
  width: 300px;
  height: 200px;
}

.badge {
  position: absolute;
  top: 0;
  right: 0;
  /* sits at top-right corner of .parent */
}
```

### Example — Without a Positioned Parent

```html
<div class="container">
  <!-- no position set on container -->
  <div class="floater">I float!</div>
</div>
```

```css
.container {
  /* position: static — default, no positioning context */
}

.floater {
  position: absolute;
  top: 50px;
  left: 50px;
  /* positions relative to <html>, not .container */
}
```

### Centering with Absolute

```css
.overlay {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  /* perfectly centered inside positioned parent */
}
```

### Stretching to Fill Parent

```css
.full-cover {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  /* covers entire parent — same as inset: 0; */
}
```

### Use Cases
- Tooltips and popovers
- Badge / notification dot on an icon
- Dropdown menus
- Custom cursor
- Image overlays and captions

---

## 4. `position: fixed`

### Definition
The element is **removed from flow** and positioned relative to the **viewport** (browser window). It stays in the same position even when the page scrolls — it's anchored to the screen, not the document.

### Key Rules
- Removed from flow (takes up no space)
- Positioned relative to the **viewport**
- **Does not move on scroll**
- `z-index` works
- Body needs `padding` to prevent content from hiding behind fixed elements

### Example

```html
<nav class="navbar">My Site</nav>
<main class="content">... lots of content ...</main>
```

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background: #111;
  z-index: 1000;
}

.content {
  padding-top: 60px; /* prevent content hiding behind navbar */
}
```

### Floating Action Button

```css
.fab {
  position: fixed;
  bottom: 24px;
  right: 24px;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: #7F77DD;
  z-index: 100;
}
```

### Use Cases
- Fixed navigation bars
- Cookie consent banners
- Floating action buttons (FAB)
- Chat widgets
- "Back to top" buttons
- Side drawers / offcanvas menus

---

## 5. `position: sticky`

### Definition
A **hybrid** of `relative` and `fixed`. The element behaves like `relative` in normal flow until it reaches a defined scroll threshold, then it "sticks" like `fixed` — **but only within the bounds of its parent container**. When the parent scrolls out of view, the sticky element goes with it.

### Key Rules
- Stays in **normal flow** (takes up its original space)
- Needs at least one **offset value** to work (`top`, `left`, etc.)
- Sticks within its **parent container** only
- Parent must **not** have `overflow: hidden` or `overflow: auto` (breaks sticky)
- Parent must be **tall enough** to scroll past the element

### Example — Sticky Header

```html
<section class="section">
  <h2 class="section-title">Section A</h2>
  <p>Content...</p>
  <p>More content...</p>
</section>
<section class="section">
  <h2 class="section-title">Section B</h2>
  <p>Content...</p>
</section>
```

```css
.section-title {
  position: sticky;
  top: 0; /* sticks when it hits the top of the viewport */
  background: #fff;
  padding: 12px 0;
  z-index: 10;
}
```

### Example — Sticky Sidebar

```css
.sidebar {
  position: sticky;
  top: 20px; /* stays 20px from top of viewport while scrolling */
  height: fit-content;
}
```

### Example — Sticky Table Header

```css
thead th {
  position: sticky;
  top: 0;
  background: #1a1a1a;
  z-index: 1;
}
```

### Use Cases
- Section headers in long pages (contacts app style A–Z)
- Sticky table headers
- Sidebar that follows you while scrolling
- Sticky "Add to Cart" button on product pages
- Chapter headers in documentation

---

## Offset Properties: `top`, `right`, `bottom`, `left`

These properties define **how far** to move the element from a reference edge. They only work when `position` is **not** `static`.

```css
.element {
  position: relative; /* or absolute, fixed, sticky */
  top: 20px;    /* move 20px away from top edge */
  right: 10px;  /* move 10px away from right edge */
  bottom: 0;    /* align to bottom edge */
  left: 50%;    /* move 50% from left edge */
}
```

### Shorthand — `inset`

`inset` is a modern shorthand for all four offsets:

```css
/* Long way */
.element {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

/* Shorthand */
.element {
  inset: 0;          /* all four = 0 */
  inset: 10px 20px;  /* top/bottom: 10px, left/right: 20px */
  inset: 5px 10px 15px 20px; /* top right bottom left */
}
```

### Negative Values

Negative values move the element in the **opposite** direction:

```css
.element {
  position: relative;
  top: -10px;  /* moves UP */
  left: -20px; /* moves LEFT */
}
```

---

## `z-index` & Stacking Context

`z-index` controls which elements appear **on top** when they overlap. It only works on positioned elements (`relative`, `absolute`, `fixed`, `sticky`).

```css
.behind { z-index: 1; }
.infront { z-index: 2; }   /* renders on top of .behind */
.overlay { z-index: 9999; } /* very high — use sparingly */
```

### Stacking Context

A **stacking context** is an isolated layer. Elements with the following properties create a new stacking context:

- `position: relative/absolute/fixed/sticky` + a `z-index` value (other than `auto`)
- `opacity` less than 1
- `transform`, `filter`, `perspective` applied
- `will-change` set to certain values

```css
/* This creates a new stacking context */
.modal-wrapper {
  position: fixed;
  z-index: 1000;
  /* children z-index values are now relative to THIS, not the document */
}

.modal-content {
  position: relative;
  z-index: 1; /* relative to .modal-wrapper, not the page */
}
```

> **Pro tip:** Don't use arbitrary high z-index values like `9999999`. Use a scale: `10`, `20`, `100`, `200`, `1000` for navbars, modals, tooltips, etc.

---

## Common Real-World Patterns

### Pattern 1 — Badge on Icon

```html
<div class="icon-wrapper">
  <img src="bell.svg" alt="Notifications" />
  <span class="badge">3</span>
</div>
```

```css
.icon-wrapper {
  position: relative;
  display: inline-block;
}

.badge {
  position: absolute;
  top: -6px;
  right: -6px;
  width: 18px;
  height: 18px;
  background: red;
  border-radius: 50%;
  font-size: 11px;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

---

### Pattern 2 — Full-Screen Overlay

```css
.overlay {
  position: fixed;
  inset: 0; /* top: 0; right: 0; bottom: 0; left: 0; */
  background: rgba(0, 0, 0, 0.6);
  z-index: 500;
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 501;
  background: white;
  padding: 40px;
  border-radius: 12px;
}
```

---

### Pattern 3 — Tooltip

```html
<div class="tooltip-wrapper">
  Hover me
  <div class="tooltip">I am a tooltip</div>
</div>
```

```css
.tooltip-wrapper {
  position: relative;
  display: inline-block;
}

.tooltip {
  position: absolute;
  bottom: 100%;   /* sits above the parent */
  left: 50%;
  transform: translateX(-50%);
  background: #111;
  color: #fff;
  padding: 6px 12px;
  border-radius: 6px;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s;
}

.tooltip-wrapper:hover .tooltip {
  opacity: 1;
}
```

---

### Pattern 4 — Sticky Sidebar Layout

```html
<div class="layout">
  <main class="main-content">...</main>
  <aside class="sidebar">...</aside>
</div>
```

```css
.layout {
  display: flex;
  gap: 40px;
  align-items: flex-start;
}

.sidebar {
  position: sticky;
  top: 20px;
  width: 260px;
  flex-shrink: 0;
}
```

---

### Pattern 5 — Image with Overlay Text

```html
<div class="card">
  <img src="photo.jpg" alt="..." />
  <div class="card-label">Photography</div>
</div>
```

```css
.card {
  position: relative;
  overflow: hidden;
  border-radius: 12px;
}

.card img {
  width: 100%;
  display: block;
}

.card-label {
  position: absolute;
  bottom: 16px;
  left: 16px;
  color: white;
  font-size: 14px;
  font-weight: 600;
  background: rgba(0, 0, 0, 0.5);
  padding: 4px 10px;
  border-radius: 20px;
}
```

---

## Common Gotchas

### 1. Absolute child with no positioned parent
```css
/* PROBLEM — .child will position relative to <html> */
.container { /* no position set */ }
.child { position: absolute; top: 0; right: 0; }

/* FIX */
.container { position: relative; }
.child { position: absolute; top: 0; right: 0; }
```

---

### 2. `overflow: hidden` breaks sticky
```css
/* PROBLEM — sticky won't work */
.parent {
  overflow: hidden; /* this kills sticky on children */
}
.child {
  position: sticky;
  top: 0;
}

/* FIX — remove overflow: hidden from parent */
.parent {
  /* overflow: hidden; — remove this */
}
```

---

### 3. `transform` on ancestor breaks `position: fixed`
```css
/* PROBLEM — .fixed-nav won't be fixed to viewport */
.some-ancestor {
  transform: translateX(0); /* creates new stacking context */
}
.fixed-nav {
  position: fixed; /* now behaves like absolute relative to .some-ancestor */
  top: 0;
}

/* FIX — move fixed element outside the transformed ancestor */
```

---

### 4. Forgetting padding-top for fixed navbar
```css
/* PROBLEM — content hides behind navbar */
.navbar { position: fixed; height: 60px; top: 0; }
body { /* no padding */ }

/* FIX */
body { padding-top: 60px; }
/* OR */
.page-wrapper { margin-top: 60px; }
```

---

### 5. Sticky needs a defined `top` value
```css
/* PROBLEM — won't stick */
.header {
  position: sticky;
  /* no top value — element won't stick */
}

/* FIX */
.header {
  position: sticky;
  top: 0; /* this is required */
}
```

---

## Quick Reference Table

| Value | In Flow? | Positioned Relative To | Scroll Behavior | `top/left` Works? | `z-index` Works? |
|---|---|---|---|---|---|
| `static` | ✅ Yes | — | Scrolls with page | ❌ No | ❌ No |
| `relative` | ✅ Yes | Its own normal position | Scrolls with page | ✅ Yes | ✅ Yes |
| `absolute` | ❌ No | Nearest positioned ancestor | Scrolls with page | ✅ Yes | ✅ Yes |
| `fixed` | ❌ No | Viewport | Stays fixed | ✅ Yes | ✅ Yes |
| `sticky` | ✅ Yes (hybrid) | Scroll container | Sticks at threshold | ✅ Yes | ✅ Yes |

---

## Summary

```
static   → default, no positioning powers
relative → stay in flow, nudge yourself, be a parent context
absolute → pop out of flow, pin to positioned ancestor
fixed    → pop out of flow, pin to viewport forever
sticky   → stay in flow, stick when threshold hit, within parent
```

The golden rule:

> **`absolute` always needs a `relative` parent.** Otherwise it'll latch onto the `<html>` element and ruin your layout.

---
