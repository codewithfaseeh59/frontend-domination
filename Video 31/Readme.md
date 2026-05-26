# CSS Variables (Custom Properties) 🎨
### Frontend Domination

---

## 📌 What are CSS Variables?

CSS Variables (officially called **CSS Custom Properties**) are entities defined by developers that hold reusable values throughout a stylesheet.

```css
/* Syntax */
--variable-name: value;
```

- Always start with `--` (double dash)
- **Case-sensitive** → `--Color` ≠ `--color`
- Accessed using the `var()` function

---

## 📌 Declaring Variables

### Global Scope — using `:root`

```css
:root {
  --primary-color: #ff6b35;
  --font-size-base: 16px;
  --spacing-lg: 2rem;
}
```

> `:root` is the `<html>` element — highest scope, accessible everywhere.

### Local Scope — inside a selector

```css
.card {
  --card-bg: #1a1a2e;
  --card-radius: 12px;

  background: var(--card-bg);
  border-radius: var(--card-radius);
}
```

> Local variables are **only available** inside that selector and its children.

---

## 📌 Using Variables — `var()`

```css
element {
  property: var(--variable-name);
}
```

### Basic Usage

```css
:root {
  --accent: #e63946;
}

h1 {
  color: var(--accent);
}

button {
  background: var(--accent);
}
```

### With Fallback Value

```css
/* If --brand-color is not defined, use #333 */
color: var(--brand-color, #333);

/* Fallback can also be another variable */
color: var(--brand-color, var(--default-color, black));
```

---

## 📌 Scope & Inheritance

CSS Variables follow the **cascade** — child elements inherit variables from their parents.

```css
:root {
  --text-color: white;
}

.section {
  --text-color: black; /* overrides for this scope */
}

p {
  color: var(--text-color); /* white everywhere, black inside .section */
}
```

---

## 📌 Overriding Variables

### Per Component

```css
:root {
  --btn-bg: #444;
}

.btn-primary {
  --btn-bg: #0077ff;
  background: var(--btn-bg);
}

.btn-danger {
  --btn-bg: #e63946;
  background: var(--btn-bg);
}
```

### With Inline Styles

```html
<div style="--gap: 40px;">
  ...
</div>
```

```css
div {
  gap: var(--gap, 16px);
}
```

---

## 📌 Theming with CSS Variables

The most popular use case — **light/dark mode themes**.

### Define Both Themes

```css
:root {
  --bg: #ffffff;
  --text: #111111;
  --card: #f4f4f4;
}

[data-theme="dark"] {
  --bg: #0f0f0f;
  --text: #eeeeee;
  --card: #1a1a1a;
}
```

### Apply in HTML

```html
<html data-theme="dark">
```

### Toggle with JavaScript

```js
const html = document.documentElement;

toggleBtn.addEventListener("click", () => {
  const current = html.getAttribute("data-theme");
  html.setAttribute("data-theme", current === "dark" ? "light" : "dark");
});
```

---

## 📌 CSS Variables vs Preprocessor Variables

| Feature | CSS Variables | SASS/LESS Variables |
|---|---|---|
| Runtime changeable | ✅ Yes | ❌ No (compile-time only) |
| JavaScript access | ✅ Yes | ❌ No |
| Inherits in cascade | ✅ Yes | ❌ No |
| Browser native | ✅ Yes | ❌ Needs compilation |
| Scope | ✅ Dynamic | Static |

---

## 📌 JavaScript Interoperability

### Read a Variable

```js
const root = document.documentElement;
const color = getComputedStyle(root).getPropertyValue("--primary-color");
// returns " #ff6b35" (note the space — use .trim())
console.log(color.trim()); // "#ff6b35"
```

### Set / Update a Variable

```js
document.documentElement.style.setProperty("--primary-color", "#00b4d8");
```

### On a Specific Element

```js
const card = document.querySelector(".card");
card.style.setProperty("--card-bg", "#2a2a4a");
```

This is super powerful for **dynamic theming**, **animations**, and **user-controlled UI**.

---

## 📌 CSS Variables in Animations

Variables can be used inside `@keyframes` and updated dynamically.

```css
:root {
  --move-x: 0px;
}

.box {
  transform: translateX(var(--move-x));
  transition: transform 0.4s ease;
}
```

```js
box.addEventListener("mousemove", (e) => {
  box.style.setProperty("--move-x", e.clientX + "px");
});
```

---

## 📌 CSS Variables with `calc()`

```css
:root {
  --base-size: 16px;
  --scale: 1.5;
}

h1 {
  font-size: calc(var(--base-size) * var(--scale) * 2); /* 48px */
}

.container {
  padding: calc(var(--base-size) / 2); /* 8px */
}
```

---

## 📌 CSS Variables with `clamp()`

```css
:root {
  --fluid-text: clamp(1rem, 2.5vw, 2rem);
  --fluid-gap: clamp(12px, 3vw, 40px);
}

h2 {
  font-size: var(--fluid-text);
}

section {
  gap: var(--fluid-gap);
}
```

---

## 📌 Design Token Pattern (Pro Practice)

Organize variables in tiers — great for large projects.

```css
:root {
  /* Tier 1 — Raw values (primitives) */
  --color-blue-500: #0077ff;
  --color-red-500: #e63946;
  --size-4: 1rem;
  --size-8: 2rem;

  /* Tier 2 — Semantic tokens (meaning-based) */
  --color-primary: var(--color-blue-500);
  --color-danger: var(--color-red-500);
  --spacing-md: var(--size-4);
  --spacing-lg: var(--size-8);

  /* Tier 3 — Component tokens */
  --btn-primary-bg: var(--color-primary);
  --btn-danger-bg: var(--color-danger);
}
```

This keeps your styles **scalable, maintainable, and consistent**.

---

## 📌 Common Variable Naming Conventions

```css
:root {
  /* Colors */
  --color-primary: #0077ff;
  --color-secondary: #ff6b35;
  --color-bg: #0f0f0f;
  --color-text: #eeeeee;

  /* Typography */
  --font-heading: "Syne", sans-serif;
  --font-body: "Poppins", sans-serif;
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.25rem;
  --font-size-xl: 2rem;

  /* Spacing */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 2rem;
  --space-xl: 4rem;

  /* Border */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 4px rgba(0,0,0,0.1);
  --shadow-md: 0 4px 16px rgba(0,0,0,0.2);

  /* Transitions */
  --transition-fast: 0.2s ease;
  --transition-base: 0.4s ease;
  --transition-slow: 0.8s ease;

  /* Z-index */
  --z-base: 1;
  --z-dropdown: 100;
  --z-modal: 1000;
  --z-toast: 9999;
}
```

---

## 📌 Invalid / Unset Variable Behavior

```css
:root {
  --gap: 20px;
}

.box {
  /* If --gap doesn't exist → uses fallback */
  margin: var(--gap, 10px);

  /* If --undefined-var has no fallback → invalid value → browser uses initial/inherit */
  color: var(--undefined-var);
}
```

> ⚠️ CSS doesn't throw errors for undefined variables — it silently uses the **initial value** of that property.

---

## 📌 Browser Support

CSS Variables are supported in **all modern browsers** (Chrome, Firefox, Safari, Edge).

```css
/* Fallback for very old browsers (rare edge case) */
color: #ff6b35;             /* old browsers */
color: var(--accent);       /* modern browsers */
```

---

## 📌 Quick Cheatsheet

```css
/* Declare */
:root { --name: value; }

/* Use */
property: var(--name);

/* With fallback */
property: var(--name, fallback);

/* In calc */
property: calc(var(--name) * 2);

/* Override locally */
.component { --name: new-value; }

/* JS — Read */
getComputedStyle(el).getPropertyValue("--name").trim();

/* JS — Write */
el.style.setProperty("--name", "new-value");
```

---
