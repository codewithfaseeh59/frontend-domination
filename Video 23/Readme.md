# 🎨 CSS `display` Property — Complete Guide

> Everything you need to know about CSS `display` — with clear explanations and practical examples.

---

## 📌 What is `display`?

The `display` property in CSS controls **how an element is rendered** in the document flow — whether it takes up full width, sits inline, becomes a flex/grid container, or disappears entirely.

```css
selector {
  display: value;
}
```

---

## 📋 Table of Contents

1. [block](#1-block)
2. [inline](#2-inline)
3. [inline-block](#3-inline-block)
4. [none](#4-none)
5. [flex](#5-flex)
6. [inline-flex](#6-inline-flex)
7. [grid](#7-grid)
8. [inline-grid](#8-inline-grid)
9. [contents](#9-contents)
10. [table & table variants](#10-table--table-variants)
11. [list-item](#11-list-item)
12. [flow-root](#12-flow-root)
13. [Quick Comparison Table](#-quick-comparison-table)

---

## 1. `block`

### 📖 Explanation
- Takes up the **full width** of its parent container
- Always starts on a **new line**
- You can set `width`, `height`, `margin`, and `padding` freely
- Default for elements like `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`, etc.

### ✅ Example
```html
<div style="display: block; background: tomato; padding: 10px;">
  I am a block element
</div>
<div style="display: block; background: steelblue; padding: 10px;">
  I start on a new line
</div>
```

**Output behavior:**
```
[ I am a block element          ]
[ I start on a new line         ]
```

---

## 2. `inline`

### 📖 Explanation
- Takes up only as **much width as its content**
- Does **not** start on a new line — sits alongside other elements
- You **cannot** set `width` or `height`
- Top/bottom `margin` and `padding` have limited effect
- Default for `<span>`, `<a>`, `<strong>`, `<em>`, etc.

### ✅ Example
```html
<span style="display: inline; background: gold;">Hello</span>
<span style="display: inline; background: lightgreen;">World</span>
```

**Output behavior:**
```
[Hello] [World]  ← sit side by side
```

---

## 3. `inline-block`

### 📖 Explanation
- Sits **inline** like text (no forced new line)
- But behaves like a **block** — you CAN set `width`, `height`, `margin`, `padding`
- Best of both worlds 🙌
- Common for nav items, buttons, custom badges

### ✅ Example
```html
<div style="display: inline-block; width: 100px; height: 50px; background: coral; margin: 5px;"></div>
<div style="display: inline-block; width: 100px; height: 50px; background: mediumpurple; margin: 5px;"></div>
<div style="display: inline-block; width: 100px; height: 50px; background: teal; margin: 5px;"></div>
```

**Output behavior:**
```
[coral] [purple] [teal]  ← inline, but with custom sizes
```

---

## 4. `none`

### 📖 Explanation
- **Completely hides** the element
- Removed from the document flow — **no space** is reserved
- Different from `visibility: hidden` (which hides but keeps space)
- Used for modals, dropdowns, toggling UI

### ✅ Example
```html
<p style="display: none;">You can't see me 👻</p>
<p>But you can see this!</p>
```

```css
/* Toggle with JavaScript */
document.querySelector('.menu').style.display = 'block';  /* show */
document.querySelector('.menu').style.display = 'none';   /* hide */
```

---

## 5. `flex`

### 📖 Explanation
- Makes the element a **flex container**
- Direct children become **flex items**
- Enables powerful 1D layout — horizontal **or** vertical
- Key properties: `flex-direction`, `justify-content`, `align-items`, `gap`

### ✅ Example
```html
<div style="display: flex; justify-content: space-between; align-items: center; background: #111; padding: 10px;">
  <span style="color: white;">Logo</span>
  <nav style="display: flex; gap: 20px;">
    <a href="#" style="color: white;">Home</a>
    <a href="#" style="color: white;">About</a>
    <a href="#" style="color: white;">Contact</a>
  </nav>
</div>
```

**Common Flex patterns:**
```css
/* Center anything */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Horizontal nav */
.nav {
  display: flex;
  flex-direction: row;
  gap: 16px;
}

/* Vertical stack */
.stack {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
```

---

## 6. `inline-flex`

### 📖 Explanation
- Same as `flex` but the **container itself** behaves like an inline element
- Useful for flex-powered buttons, badges, tags that sit inline with text

### ✅ Example
```html
<p>
  Click this
  <button style="display: inline-flex; align-items: center; gap: 6px;">
    <span>🚀</span> Launch
  </button>
  to get started.
</p>
```

---

## 7. `grid`

### 📖 Explanation
- Makes the element a **grid container**
- Enables powerful **2D layout** — rows AND columns simultaneously
- Key properties: `grid-template-columns`, `grid-template-rows`, `gap`, `grid-area`

### ✅ Example
```html
<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px;">
  <div style="background: coral; padding: 20px;">1</div>
  <div style="background: skyblue; padding: 20px;">2</div>
  <div style="background: lightgreen; padding: 20px;">3</div>
  <div style="background: plum; padding: 20px;">4</div>
  <div style="background: peachpuff; padding: 20px;">5</div>
  <div style="background: khaki; padding: 20px;">6</div>
</div>
```

**Output:**
```
[ 1 ] [ 2 ] [ 3 ]
[ 4 ] [ 5 ] [ 6 ]
```

**Common Grid patterns:**
```css
/* 3 equal columns */
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

/* Holy Grail layout */
.layout {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 200px 1fr 200px;
}
```

---

## 8. `inline-grid`

### 📖 Explanation
- Same as `grid` but the **container itself** is inline
- The grid container wraps tightly around its content

### ✅ Example
```css
.tag-grid {
  display: inline-grid;
  grid-template-columns: auto auto;
  gap: 4px;
}
```

---

## 9. `contents`

### 📖 Explanation
- The element itself **doesn't generate a box** — it disappears from layout
- But its **children are still rendered** and participate in the parent's layout
- Useful for semantic wrappers that shouldn't affect flex/grid layout

### ✅ Example
```html
<div style="display: flex; gap: 10px;">
  <div style="display: contents;">
    <!-- This wrapper vanishes, but its children join the flex container -->
    <span style="background: coral; padding: 8px;">A</span>
    <span style="background: skyblue; padding: 8px;">B</span>
  </div>
  <span style="background: lightgreen; padding: 8px;">C</span>
</div>
```

**Output:** A, B, C all appear as direct flex children

> ⚠️ **Note:** `display: contents` can cause accessibility issues in some browsers — use with care.

---

## 10. `table` & Table Variants

### 📖 Explanation
These mimic the layout behavior of HTML table elements using CSS — useful for legacy browsers or non-table HTML.

| Value | Equivalent HTML Tag |
|---|---|
| `table` | `<table>` |
| `table-row` | `<tr>` |
| `table-cell` | `<td>` / `<th>` |
| `table-caption` | `<caption>` |
| `table-column` | `<col>` |
| `table-column-group` | `<colgroup>` |
| `table-header-group` | `<thead>` |
| `table-footer-group` | `<tfoot>` |
| `table-row-group` | `<tbody>` |

### ✅ Example
```html
<div style="display: table; width: 100%; border-collapse: collapse;">
  <div style="display: table-row;">
    <div style="display: table-cell; padding: 8px; border: 1px solid #ccc;">Name</div>
    <div style="display: table-cell; padding: 8px; border: 1px solid #ccc;">Age</div>
  </div>
  <div style="display: table-row;">
    <div style="display: table-cell; padding: 8px; border: 1px solid #ccc;">Voldemort</div>
    <div style="display: table-cell; padding: 8px; border: 1px solid #ccc;">23</div>
  </div>
</div>
```

---

## 11. `list-item`

### 📖 Explanation
- Makes the element behave like an `<li>` — generates a **block box** + a **marker box** (bullet point or number)
- Rarely used directly; default for `<li>` elements

### ✅ Example
```css
.custom-list div {
  display: list-item;
  list-style-type: disc;
  margin-left: 20px;
}
```

```html
<div class="custom-list">
  <div>Item One</div>
  <div>Item Two</div>
  <div>Item Three</div>
</div>
```

---

## 12. `flow-root`

### 📖 Explanation
- Creates a new **Block Formatting Context (BFC)**
- Fixes **float clearing** issues without hacks like `overflow: hidden` or clearfix
- The container wraps around floated children properly

### ✅ Example

**❌ Without `flow-root` — container collapses:**
```html
<div style="background: lightblue;">
  <img style="float: left; width: 80px;" src="photo.jpg" />
  <!-- container height collapses! -->
</div>
```

**✅ With `flow-root` — container wraps floats:**
```html
<div style="display: flow-root; background: lightblue;">
  <img style="float: left; width: 80px;" src="photo.jpg" />
  <!-- container properly wraps around the float -->
</div>
```

---

## 📊 Quick Comparison Table

| Value | New Line? | Set Width/Height? | Creates Container? | Use Case |
|---|---|---|---|---|
| `block` | ✅ Yes | ✅ Yes | ❌ No | Divs, paragraphs, sections |
| `inline` | ❌ No | ❌ No | ❌ No | Spans, links, text styling |
| `inline-block` | ❌ No | ✅ Yes | ❌ No | Buttons, nav items |
| `none` | — | — | — | Hide elements |
| `flex` | ✅ Yes | ✅ Yes | ✅ Flex | 1D layouts, navbars |
| `inline-flex` | ❌ No | ✅ Yes | ✅ Flex | Inline flex buttons/badges |
| `grid` | ✅ Yes | ✅ Yes | ✅ Grid | 2D layouts, cards, pages |
| `inline-grid` | ❌ No | ✅ Yes | ✅ Grid | Compact grid widgets |
| `contents` | — | — | — | Semantic wrappers |
| `table` | ✅ Yes | ✅ Yes | ✅ Table | Table-like layouts |
| `list-item` | ✅ Yes | ✅ Yes | ❌ No | Custom list styling |
| `flow-root` | ✅ Yes | ✅ Yes | ✅ BFC | Float clearing |

---

## 💡 Pro Tips

```css
/* Center a div — the classic way */
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Full page center */
body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

/* Responsive grid auto-fit */
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

/* Hide on mobile, show on desktop */
.desktop-only {
  display: none;
}
@media (min-width: 768px) {
  .desktop-only {
    display: block;
  }
}
```

---

## 🔗 Resources

- [MDN — display property](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
- [CSS Tricks — A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS Tricks — A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

---