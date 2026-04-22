# 🎨 CSS — Introduction & Basics

> **Cascading Style Sheets** — the language that makes HTML look good.

---

## 📌 What is CSS?

CSS (Cascading Style Sheets) is used to style HTML elements — colors, fonts, spacing, layouts, animations, all of it is controlled through CSS. Without CSS, every website would just be plain black text on a white background.

---

## 🔗 How to Add CSS to HTML?

### 1. External CSS *(Recommended)*
```html
<link rel="stylesheet" href="style.css">
```

### 2. Internal CSS
```html
<style>
  h1 { color: red; }
</style>
```

### 3. Inline CSS
```html
<h1 style="color: red;">Hello</h1>
```

---

## 🧱 CSS Syntax

```css
selector {
  property: value;
}
```

**Example:**
```css
h1 {
  color: #ff0000;
  font-size: 32px;
}
```

---

## 🎯 Selectors

| Selector | Example | What it targets |
|----------|---------|-----------------|
| Element | `p { }` | All `<p>` tags |
| Class | `.box { }` | Elements with class `box` |
| ID | `#hero { }` | Element with id `hero` |
| Universal | `* { }` | Everything |
| Group | `h1, h2 { }` | Multiple elements at once |
| Descendant | `div p { }` | `<p>` inside a `<div>` |

---

## 🎨 Colors

```css
/* Named color */
color: red;

/* Hex */
color: #ff6600;

/* RGB */
color: rgb(255, 100, 0);

/* RGBA — with transparency */
color: rgba(255, 100, 0, 0.5);
```

---

## 📐 The Box Model

Every element on the page is a box. The box model has 4 layers:

```
┌──────────────────────────┐
│          MARGIN          │
│   ┌──────────────────┐   │
│   │      BORDER      │   │
│   │  ┌────────────┐  │   │
│   │  │  PADDING   │  │   │
│   │  │ ┌────────┐ │  │   │
│   │  │ │CONTENT │ │  │   │
│   │  │ └────────┘ │  │   │
│   │  └────────────┘  │   │
│   └──────────────────┘   │
└──────────────────────────┘
```

```css
div {
  width: 300px;
  padding: 20px;       /* space inside the border */
  border: 2px solid #000;
  margin: 30px;        /* space outside the border */
}
```

---

## 📏 Units

| Unit | Type | Example | Notes |
|------|------|---------|-------|
| `px` | Absolute | `16px` | Fixed size |
| `%` | Relative | `50%` | Relative to parent |
| `em` | Relative | `1.5em` | Relative to parent font-size |
| `rem` | Relative | `1rem` | Relative to root font-size |
| `vw` | Viewport | `100vw` | % of viewport width |
| `vh` | Viewport | `100vh` | % of viewport height |

---

## ✏️ Typography

```css
p {
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  font-weight: 700;
  font-style: italic;
  line-height: 1.6;
  letter-spacing: 2px;
  text-align: center;       /* left | right | center | justify */
  text-transform: uppercase;
  text-decoration: underline;
  color: #333333;
}
```

---

## 🖼️ Backgrounds

```css
div {
  background-color: #f0f0f0;
  background-image: url('image.jpg');
  background-size: cover;       /* cover | contain | auto */
  background-position: center;
  background-repeat: no-repeat;

  /* Shorthand */
  background: #f0f0f0 url('image.jpg') no-repeat center / cover;
}
```

---

## 📦 Display Property

```css
/* Block — takes full width, starts on new line */
div { display: block; }

/* Inline — sits in line with text, no width/height */
span { display: inline; }

/* Inline-block — inline but accepts width/height */
img { display: inline-block; }

/* None — hides the element completely */
.hidden { display: none; }

/* Flex — modern layout tool */
.container { display: flex; }
```

---

## 💪 Flexbox (Quick Intro)

```css
.container {
  display: flex;
  justify-content: center;   /* horizontal alignment */
  align-items: center;       /* vertical alignment */
  gap: 20px;
  flex-direction: row;       /* row | column */
  flex-wrap: wrap;
}
```

---

## 🔲 Position

```css
/* Default — normal document flow */
div { position: static; }

/* Relative — offset from its normal position */
div { position: relative; top: 10px; left: 20px; }

/* Absolute — positioned relative to nearest positioned parent */
div { position: absolute; top: 0; right: 0; }

/* Fixed — stays fixed on screen while scrolling */
nav { position: fixed; top: 0; width: 100%; }

/* Sticky — sticks after a scroll threshold */
header { position: sticky; top: 0; }
```

---

## ✨ Borders & Border Radius

```css
div {
  border: 2px solid #ff6600;
  border-radius: 10px;       /* rounded corners */
  border-radius: 50%;        /* perfect circle */

  /* Individual sides */
  border-top: 3px dashed red;
  border-bottom: 1px solid #ccc;
}
```

---

## 🌑 Box Shadow & Text Shadow

```css
/* Box Shadow: x  y  blur  spread  color */
div {
  box-shadow: 4px 4px 10px 0px rgba(0, 0, 0, 0.3);
}

/* Text Shadow: x  y  blur  color */
h1 {
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
}
```

---

## 🔁 Transitions

```css
button {
  background-color: #ff6600;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #cc5200;
}
```

---

## 🎬 Basic Animations

```css
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}

div {
  animation: fadeIn 1s ease forwards;
}
```

---

## 🔍 Pseudo-classes & Pseudo-elements

```css
/* Pseudo-classes — element states */
a:hover         { color: orange; }
a:visited       { color: purple; }
li:first-child  { font-weight: bold; }
li:nth-child(2) { color: red; }

/* Pseudo-elements — style parts of an element */
p::first-letter { font-size: 2em; }
p::before       { content: "→ "; }
p::after        { content: " ✓"; }
```

---

## ⚡ CSS Specificity (Priority Order)

When two rules conflict, the more **specific** one wins.

```
Inline styles          →  highest priority  (1,0,0,0)
ID selectors           →  high              (0,1,0,0)
Class / pseudo-class   →  medium            (0,0,1,0)
Element selectors      →  low               (0,0,0,1)
```

```css
/* This wins over just 'p' */
.container p { color: red; }

/* !important overrides everything — use sparingly */
p { color: blue !important; }
```

---

## 📱 Media Queries (Responsive Design)

```css
/* Styles for screens 768px or smaller */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }

  h1 {
    font-size: 24px;
  }
}
```

---

## 🧹 CSS Reset (Always Do This)

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

---

## 📚 Quick Reference Cheat Sheet

| Property | What it does |
|----------|-------------|
| `color` | Text color |
| `background-color` | Background color |
| `font-size` | Text size |
| `font-weight` | Bold / thin |
| `margin` | Space outside element |
| `padding` | Space inside element |
| `border` | Element border |
| `border-radius` | Rounded corners |
| `display` | Block / flex / inline |
| `position` | Static / relative / absolute / fixed |
| `width / height` | Element dimensions |
| `opacity` | Transparency (0 to 1) |
| `overflow` | Handle overflowing content |
| `z-index` | Stack order of elements |
| `cursor` | Mouse cursor style |
| `transition` | Smooth property changes |
| `animation` | Keyframe animations |

---

> 💡 **Pro Tip:** Always add `box-sizing: border-box` to everything — it makes layouts way easier to manage.