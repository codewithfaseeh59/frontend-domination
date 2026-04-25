# 🎨 CSS — Fonts, Text & Color Properties
> **Frontend Domination** | Reference Guide

---

## 📌 Table of Contents

1. [CSS Fonts](#css-fonts)
2. [CSS Text Properties](#css-text-properties)
3. [CSS Color Properties](#css-color-properties)
4. [Google Fonts — How to Use](#google-fonts--how-to-use)
5. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

---

## 🔤 CSS Fonts

Font properties control the **typeface, size, weight, style, and variant** of text.

---

### `font-family`

Defines the typeface. Always provide a **fallback font**.

```css
p {
  font-family: "Poppins", sans-serif;
}

h1 {
  font-family: "Georgia", "Times New Roman", serif;
}
```

> 💡 **Font stack order:** Specific font → Generic fallback  
> `sans-serif` = clean modern look | `serif` = classic/editorial | `monospace` = code

---

### `font-size`

Controls how big or small the text is.

| Unit | Meaning | Example |
|------|---------|---------|
| `px` | Fixed pixel size | `font-size: 16px` |
| `rem` | Relative to root `<html>` font size | `font-size: 1.5rem` |
| `em` | Relative to parent element font size | `font-size: 1.2em` |
| `%` | Percentage of parent font size | `font-size: 120%` |
| `vw` | Relative to viewport width | `font-size: 4vw` |

```css
html {
  font-size: 16px; /* 1rem = 16px */
}

h1 {
  font-size: 3rem;   /* 48px */
}

p {
  font-size: 1rem;   /* 16px */
}

.hero-text {
  font-size: 8vw;    /* scales with screen width */
}
```

---

### `font-weight`

Controls the **thickness/boldness** of text.

```css
p {
  font-weight: 400;   /* normal */
}

h1 {
  font-weight: 700;   /* bold */
}

.thin {
  font-weight: 100;   /* extra thin */
}

.black {
  font-weight: 900;   /* extra bold / black */
}
```

> 💡 Common values: `100` `200` `300` `400` `500` `600` `700` `800` `900`  
> Keywords: `normal` (400) | `bold` (700) | `lighter` | `bolder`

---

### `font-style`

Makes text **italic or oblique**.

```css
em {
  font-style: italic;
}

.quote {
  font-style: oblique;
}

.reset {
  font-style: normal;
}
```

---

### `font-variant`

Converts lowercase text to **small caps**.

```css
.label {
  font-variant: small-caps;
}

/* Output: "hello world" → "HELLO WORLD" (but smaller) */
```

---

### `font` — Shorthand

Combine multiple font properties in one line.

```css
/* Syntax: font: style variant weight size/line-height family */

p {
  font: italic small-caps 600 16px/1.6 "Poppins", sans-serif;
}

h1 {
  font: 700 3rem "Montserrat", sans-serif;
}
```

> ⚠️ `font-size` and `font-family` are **required** in shorthand. Rest are optional.

---

## 📝 CSS Text Properties

Text properties control **alignment, spacing, decoration, and transformation** of text content.

---

### `color`

Sets the **foreground/text color**.

```css
h1 {
  color: #ff6b35;           /* hex */
}

p {
  color: rgb(30, 30, 30);   /* rgb */
}

.muted {
  color: rgba(0, 0, 0, 0.5); /* rgba — with transparency */
}

.accent {
  color: hsl(200, 80%, 50%); /* hsl */
}
```

---

### `text-align`

Aligns text **horizontally** inside its container.

```css
h1 {
  text-align: center;
}

p {
  text-align: left;     /* default */
}

.receipt {
  text-align: right;
}

.justified {
  text-align: justify;  /* stretches lines to fill width */
}
```

---

### `text-decoration`

Adds or removes **lines** on text (underline, overline, strikethrough).

```css
a {
  text-decoration: none;          /* removes default underline */
}

.underline {
  text-decoration: underline;
}

.strikethrough {
  text-decoration: line-through;
}

.overline {
  text-decoration: overline;
}

/* Styled decoration */
.fancy-link {
  text-decoration: underline wavy #ff6b35;
}
```

---

### `text-transform`

Controls **capitalization** of text.

```css
.uppercase {
  text-transform: uppercase;   /* hello → HELLO */
}

.lowercase {
  text-transform: lowercase;   /* HELLO → hello */
}

.capitalize {
  text-transform: capitalize;  /* hello world → Hello World */
}

.normal {
  text-transform: none;
}
```

---

### `text-indent`

Adds **indentation** to the first line of a paragraph.

```css
p {
  text-indent: 40px;
}

.hanging {
  text-indent: -20px;  /* negative = hanging indent */
  padding-left: 20px;
}
```

---

### `letter-spacing`

Controls **space between individual characters**.

```css
h1 {
  letter-spacing: 0.1em;   /* slightly spread */
}

.tagline {
  letter-spacing: 0.3em;   /* wide tracking — luxury feel */
}

.tight {
  letter-spacing: -0.02em; /* tight — modern/bold headlines */
}
```

---

### `word-spacing`

Controls **space between words**.

```css
p {
  word-spacing: 0.2em;
}

.tight-paragraph {
  word-spacing: -2px;
}
```

---

### `line-height`

Controls **vertical spacing between lines** of text.

```css
body {
  line-height: 1.6;    /* unitless — recommended — 1.6x font-size */
}

h1 {
  line-height: 1.1;    /* tighter for large headings */
}

.readable {
  line-height: 1.8;    /* airy/spacious for body text */
}
```

> 💡 Use **unitless values** (like `1.5`) — they scale proportionally with font size.

---

### `text-shadow`

Adds a **shadow** behind text.

```css
/* Syntax: text-shadow: offset-x offset-y blur color */

h1 {
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.glow {
  text-shadow: 0 0 20px #00ffcc, 0 0 40px #00ffcc;
}

.cinematic {
  text-shadow: 4px 4px 0px #000, 6px 6px 0px rgba(0,0,0,0.2);
}
```

---

### `white-space`

Controls how **whitespace and line breaks** are handled.

```css
.no-wrap {
  white-space: nowrap;     /* text won't wrap to next line */
}

.preserve {
  white-space: pre;        /* preserves spaces and line breaks */
}

.pre-wrap {
  white-space: pre-wrap;   /* preserves + allows wrapping */
}
```

---

### `overflow` + `text-overflow`

Handles text that **overflows** its container.

```css
.card-title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;  /* shows "..." when text is cut */
}
```

---

### `word-break` / `overflow-wrap`

Controls how **long words break** across lines.

```css
.url-box {
  word-break: break-all;      /* breaks anywhere */
}

.safe-break {
  overflow-wrap: break-word;  /* breaks only if necessary */
}
```

---

## 🌈 CSS Color Properties

---

### Color Formats

```css
.box {
  /* 1. Named colors */
  color: red;
  color: tomato;
  color: dodgerblue;

  /* 2. Hex */
  color: #ff6b35;
  color: #fff;             /* shorthand for #ffffff */

  /* 3. RGB */
  color: rgb(255, 107, 53);

  /* 4. RGBA (with alpha/transparency) */
  color: rgba(255, 107, 53, 0.5);  /* 50% transparent */

  /* 5. HSL (hue, saturation, lightness) */
  color: hsl(16, 100%, 60%);

  /* 6. HSLA */
  color: hsla(16, 100%, 60%, 0.7);
}
```

---

### `background-color`

Sets the **background fill** of an element.

```css
body {
  background-color: #0a0a0a;  /* dark */
}

.card {
  background-color: #1a1a2e;
}

.highlight {
  background-color: rgba(255, 200, 0, 0.15);  /* subtle tint */
}
```

---

### `background` — Shorthand

```css
.hero {
  background: #1a1a2e;

  /* with image */
  background: url("bg.jpg") center/cover no-repeat;

  /* with gradient */
  background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
}
```

---

### CSS Gradients

#### Linear Gradient

```css
.banner {
  background: linear-gradient(to right, #ff6b35, #f7c59f);
}

.dark-fade {
  background: linear-gradient(180deg, #000 0%, transparent 100%);
}

.diagonal {
  background: linear-gradient(135deg, #667eea, #764ba2);
}
```

#### Radial Gradient

```css
.glow-bg {
  background: radial-gradient(circle at center, #1a237e, #000);
}

.spotlight {
  background: radial-gradient(ellipse at top, #1b2838, #0a0a0a);
}
```

#### Conic Gradient

```css
.pie {
  background: conic-gradient(#ff6b35 0% 40%, #ffe66d 40% 70%, #4ecdc4 70% 100%);
  border-radius: 50%;
}
```

---

### CSS Custom Properties (Variables) for Colors

```css
:root {
  --clr-primary: #ff6b35;
  --clr-dark: #0a0a0a;
  --clr-light: #f5f5f5;
  --clr-accent: #00ffcc;
  --clr-muted: rgba(255, 255, 255, 0.4);
}

h1 {
  color: var(--clr-primary);
}

body {
  background-color: var(--clr-dark);
  color: var(--clr-light);
}

a:hover {
  color: var(--clr-accent);
}
```

> 💡 **Always define your color palette in `:root`** — makes theming and dark mode super easy.

---

### `opacity`

Makes the **entire element** (including children) transparent.

```css
.overlay {
  opacity: 0.5;   /* 50% transparent */
}

.hidden {
  opacity: 0;     /* invisible but still takes space */
}

.visible {
  opacity: 1;     /* fully visible */
}
```

> ⚠️ Use `rgba()` for color-only transparency. Use `opacity` when you want the whole element to fade.

---

## 🔗 Google Fonts — How to Use

### Step 1 — Link in HTML `<head>`

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
```

### Step 2 — Use in CSS

```css
body {
  font-family: "Poppins", sans-serif;
}
```

### Multiple Fonts

```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@400;500&display=swap" rel="stylesheet">
```

```css
h1 {
  font-family: "Bebas Neue", sans-serif;  /* display/heading */
}

p {
  font-family: "Inter", sans-serif;       /* body */
}
```

---

## ⚡ Quick Reference Cheatsheet

### Font Properties

| Property | Values | Example |
|----------|--------|---------|
| `font-family` | font name, stack | `"Poppins", sans-serif` |
| `font-size` | px, rem, em, vw | `1.5rem` |
| `font-weight` | 100–900, bold, normal | `700` |
| `font-style` | normal, italic, oblique | `italic` |
| `font-variant` | normal, small-caps | `small-caps` |

### Text Properties

| Property | Values | Example |
|----------|--------|---------|
| `color` | hex, rgb, hsl | `#ff6b35` |
| `text-align` | left, right, center, justify | `center` |
| `text-decoration` | none, underline, line-through | `none` |
| `text-transform` | uppercase, lowercase, capitalize | `uppercase` |
| `letter-spacing` | px, em | `0.1em` |
| `line-height` | unitless, px | `1.6` |
| `text-shadow` | x y blur color | `2px 2px 4px #000` |
| `text-indent` | px, em | `40px` |
| `text-overflow` | clip, ellipsis | `ellipsis` |
| `white-space` | normal, nowrap, pre | `nowrap` |

### Color Properties

| Property | Values | Example |
|----------|--------|---------|
| `color` | any color format | `rgba(255,255,255,0.8)` |
| `background-color` | any color format | `#0a0a0a` |
| `background` | color, gradient, image | `linear-gradient(...)` |
| `opacity` | 0 to 1 | `0.5` |

---

## 🧠 Pro Tips

- Use **`rem`** for font sizes (scales with user browser settings — better accessibility)
- Use **`line-height: 1.5–1.7`** for body text — easier to read
- Use **CSS variables** for your full color palette in `:root`
- **`letter-spacing: 0.05–0.15em`** on uppercase text = instant polished look
- **`text-overflow: ellipsis`** — always pair with `white-space: nowrap` + `overflow: hidden`
- Avoid using more than **2 font families** on one page
- Use **`font-display: swap`** with Google Fonts for better performance

---