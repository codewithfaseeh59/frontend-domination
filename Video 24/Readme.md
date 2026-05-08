# 🟦 CSS Box Shadow & Outline — Complete Reference


## 📦 Box Shadow

### Syntax

```css
box-shadow: offset-x  offset-y  blur-radius  spread-radius  color;
```

| Value           | Required | Description                                    |
|----------------|----------|------------------------------------------------|
| `offset-x`     | ✅        | Horizontal shift. Positive = right, Negative = left |
| `offset-y`     | ✅        | Vertical shift. Positive = down, Negative = up |
| `blur-radius`  | ❌        | Softness of shadow. `0` = sharp edge           |
| `spread-radius`| ❌        | Grows or shrinks the shadow size               |
| `color`        | ❌        | Shadow color. Defaults to `currentColor`       |
| `inset`        | ❌        | Moves shadow **inside** the element            |

---

### Basic Examples

```css
/* Simple drop shadow */
box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.3);

/* Sharp shadow (no blur) */
box-shadow: 6px 6px 0px #000;

/* Inset shadow (inner glow) */
box-shadow: inset 0 0 15px rgba(0, 0, 0, 0.5);

/* No offset — glowing effect */
box-shadow: 0 0 20px #ff6ec7;

/* Negative spread — shrinks the shadow */
box-shadow: 0 10px 15px -5px rgba(0, 0, 0, 0.4);
```

---

### Multiple Shadows

You can stack shadows using a comma-separated list. They render **front to back**.

```css
box-shadow:
  0 0 10px #ff6ec7,
  0 0 30px #a855f7,
  0 0 60px #6366f1;
```

> 💡 Pro tip: Layering 3 shadows with increasing blur and decreasing opacity = insane neon glow effect.

---

### Common Patterns

#### 🔴 Neon Glow
```css
box-shadow:
  0 0 5px #ff3cac,
  0 0 15px #ff3cac,
  0 0 40px #ff3cac;
```

#### 🔵 Neumorphism (Soft UI)
```css
background: #e0e5ec;
box-shadow:
  6px 6px 12px #b8bec7,
  -6px -6px 12px #ffffff;
```

#### ⚫ Brutal Shadow
```css
box-shadow: 5px 5px 0px #000000;
```

#### 🎨 Layered Depth
```css
box-shadow:
  0 1px 2px rgba(0,0,0,0.07),
  0 2px 4px rgba(0,0,0,0.07),
  0 4px 8px rgba(0,0,0,0.07),
  0 8px 16px rgba(0,0,0,0.07);
```

#### ✨ Inset Inner Glow
```css
box-shadow: inset 0 0 25px rgba(255, 110, 199, 0.4);
```

---

### `box-shadow` vs `filter: drop-shadow()`

| Feature              | `box-shadow`              | `filter: drop-shadow()`      |
|---------------------|--------------------------|------------------------------|
| Follows border-radius | ✅                        | ✅                            |
| Follows clipped shape | ❌ (box only)             | ✅ (pixel-perfect)            |
| Works on SVG / PNG  | ❌                        | ✅                            |
| Multiple shadows    | ✅ (comma-separated)      | ❌ (one at a time)            |
| `inset` support     | ✅                        | ❌                            |
| Performance         | ✅ GPU-accelerated        | ⚠️ Slightly heavier           |

```css
/* drop-shadow follows actual visible shape (great for PNGs/SVGs) */
filter: drop-shadow(4px 4px 6px rgba(0, 0, 0, 0.5));
```

---

## 🔲 Outline

### Syntax

```css
outline: width  style  color;
```

> ⚠️ `outline` is **not** part of the box model — it doesn't affect layout or take up space.

| Value   | Required | Description                          |
|---------|----------|--------------------------------------|
| `width` | ❌        | Thickness of the outline             |
| `style` | ✅        | `solid`, `dashed`, `dotted`, `double`, `none` |
| `color` | ❌        | Color of the outline                 |

---

### Basic Examples

```css
/* Simple outline */
outline: 2px solid #ff6ec7;

/* Dashed outline */
outline: 3px dashed #a855f7;

/* Dotted outline */
outline: 2px dotted #fff;

/* Remove default focus outline (always pair with custom) */
outline: none;
```

---

### `outline-offset`

Pushes the outline **away from the element border**. Can even go negative (inward).

```css
outline: 2px solid #ff3cac;
outline-offset: 6px;   /* pushes outline 6px outside the border */

outline: 2px solid #fff;
outline-offset: -4px;  /* pushes outline 4px inside */
```

---

### Outline vs Border

| Feature            | `border`                      | `outline`                        |
|--------------------|-------------------------------|----------------------------------|
| Affects layout     | ✅ Yes                         | ❌ No                             |
| Part of box model  | ✅ Yes                         | ❌ No                             |
| `border-radius`    | ✅ Yes                         | ✅ (modern browsers only)         |
| Individual sides   | ✅ `border-top`, etc.          | ❌ All 4 sides only               |
| `offset` support   | ❌                             | ✅ `outline-offset`               |
| Best for           | Layout/design borders         | Focus states, overlays           |

---

### Accessibility — `:focus` Outline

Never just do `outline: none` without a replacement. Always style `:focus` for keyboard users.

```css
/* ❌ Bad — kills accessibility */
button:focus {
  outline: none;
}

/* ✅ Good — custom styled focus */
button:focus-visible {
  outline: 2px solid #ff6ec7;
  outline-offset: 4px;
}
```

> 💡 Use `:focus-visible` instead of `:focus` — it only triggers for keyboard navigation, not mouse clicks.

---

### Creative Outline Tricks

#### Fake Border Without Affecting Layout
```css
/* Use outline as a second border */
border: 2px solid #ff3cac;
outline: 2px solid #a855f7;
outline-offset: 4px;
```

#### Double Ring Effect
```css
outline: 3px solid #fff;
outline-offset: 5px;
box-shadow: 0 0 0 8px #ff3cac; /* fake third ring using box-shadow */
```

#### Glowing Focus Ring
```css
button:focus-visible {
  outline: 2px solid #ff6ec7;
  outline-offset: 3px;
  box-shadow: 0 0 0 4px rgba(255, 110, 199, 0.3);
}
```

---

## 🔁 Quick Comparison: Shadow Methods

| Method                   | Follows Shape | Inset | SVG/PNG | Multiple |
|--------------------------|--------------|-------|---------|---------|
| `box-shadow`             | Box only     | ✅    | ❌       | ✅       |
| `filter: drop-shadow()`  | Pixel-perfect| ❌    | ✅       | ❌       |
| `text-shadow`            | Text shape   | ❌    | ❌       | ✅       |
| `outline` + offset       | Border edge  | ❌    | ❌       | ❌       |

---

## ⚡ Quick Cheat Sheet

```css
/* Glow */
box-shadow: 0 0 20px #ff6ec7;

/* Raised card */
box-shadow: 0 4px 24px rgba(0, 0, 0, 0.15);

/* Brutal flat shadow */
box-shadow: 4px 4px 0 #000;

/* Inset pressed state */
box-shadow: inset 2px 2px 6px rgba(0,0,0,0.4);

/* Neon layered */
box-shadow: 0 0 5px #a855f7, 0 0 20px #a855f7, 0 0 50px #a855f7;

/* Outline with gap */
outline: 2px solid #fff;
outline-offset: 5px;

/* Accessible focus */
outline: 2px solid #ff6ec7;
outline-offset: 3px;
```

---
