# 🎯 CSS Specificity & The Cascade

> **Frontend Domination** — CSS Deep Dive  
> Topic: How browsers decide which styles win

---

## 📌 Table of Contents

1. [What is the Cascade?](#what-is-the-cascade)
2. [The 4 Cascade Factors](#the-4-cascade-factors)
3. [What is Specificity?](#what-is-specificity)
4. [Specificity Score System](#specificity-score-system)
5. [Calculating Specificity — Examples](#calculating-specificity--examples)
6. [Specificity Wars — Who Wins?](#specificity-wars--who-wins)
7. [The `!important` Rule](#the-important-rule)
8. [Inheritance vs Cascade](#inheritance-vs-cascade)
9. [Source Order (Last Rule Wins)](#source-order-last-rule-wins)
10. [Practical Tips & Gotchas](#practical-tips--gotchas)
11. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

---

## What is the Cascade?

The **cascade** is the algorithm browsers use to decide which CSS rule applies to an element when multiple rules are targeting it.

The word *cascade* literally means "waterfall" — styles flow down from multiple sources, and the browser picks the **winning** rule based on a priority system.

```css
/* Both rules target h1 — which one wins? */

h1 {
  color: red;
}

h1 {
  color: blue; /* ✅ This wins — same specificity, but comes LAST */
}
```

---

## The 4 Cascade Factors

The browser evaluates rules in this order. A higher factor **completely overrides** lower ones.

| Priority | Factor | Description |
|----------|--------|-------------|
| 1st (Highest) | **Origin + Importance** | Where the CSS comes from + `!important` |
| 2nd | **Specificity** | How specific the selector is |
| 3rd | **Source Order** | Which rule appears later in the code |
| 4th (Lowest) | **Inheritance** | Styles passed down from parent elements |

---

## What is Specificity?

**Specificity** is a score/weight that determines how "powerful" a CSS selector is.

When two rules target the same element, the one with the **higher specificity score wins**, regardless of source order.

```html
<p class="intro" id="hero-text">Hello World</p>
```

```css
p {
  color: black;       /* Low specificity */
}

.intro {
  color: blue;        /* Medium specificity */
}

#hero-text {
  color: red;         /* High specificity — ✅ WINS */
}
```

Even though `p` and `.intro` come first, the `#id` selector wins because of higher specificity.

---

## Specificity Score System

Specificity is calculated using a **4-column scoring system**:

```
  [A]  [B]  [C]  [D]
   |    |    |    |
   |    |    |    └── Element selectors & pseudo-elements  (0,0,0,1)
   |    |    └─────── Class, attribute & pseudo-class selectors  (0,0,1,0)
   |    └──────────── ID selectors  (0,1,0,0)
   └───────────────── Inline styles  (1,0,0,0)
```

| Selector Type | Example | Score |
|--------------|---------|-------|
| Universal selector | `*` | `0,0,0,0` |
| Element / tag | `div`, `p`, `h1` | `0,0,0,1` |
| Pseudo-element | `::before`, `::after` | `0,0,0,1` |
| Class | `.card`, `.btn` | `0,0,1,0` |
| Attribute | `[type="text"]` | `0,0,1,0` |
| Pseudo-class | `:hover`, `:nth-child()` | `0,0,1,0` |
| ID | `#hero`, `#navbar` | `0,1,0,0` |
| Inline style | `style="color:red"` | `1,0,0,0` |
| `!important` | `color: red !important` | Overrides everything |

> ⚠️ **Note:** `!important` is NOT part of the specificity score — it's a completely separate override mechanism.

---

## Calculating Specificity — Examples

### Example 1 — Simple selectors

```css
h1                   /* 0,0,0,1 — 1 element */
.title               /* 0,0,1,0 — 1 class */
#main                /* 0,1,0,0 — 1 ID */
```

### Example 2 — Combined selectors

```css
div p                /* 0,0,0,2 — 2 elements */
div.card             /* 0,0,1,1 — 1 class + 1 element */
#nav .link           /* 0,1,1,0 — 1 ID + 1 class */
#nav .link:hover     /* 0,1,2,0 — 1 ID + 1 class + 1 pseudo-class */
```

### Example 3 — Full breakdown

```css
.container ul li a.active:hover
```

Let's count:
- `.container` → 1 class → `0,0,1,0`
- `ul` → 1 element → `0,0,0,1`
- `li` → 1 element → `0,0,0,1`
- `a` → 1 element → `0,0,0,1`
- `.active` → 1 class → `0,0,1,0`
- `:hover` → 1 pseudo-class → `0,0,1,0`

**Total: `0,0,3,3`**

---

## Specificity Wars — Who Wins?

### Battle 1

```html
<button class="btn" id="submit-btn">Click Me</button>
```

```css
button {
  background: gray;       /* 0,0,0,1 */
}

.btn {
  background: blue;       /* 0,0,1,0 */
}

#submit-btn {
  background: green;      /* 0,1,0,0 — ✅ WINS */
}
```

**Winner: `#submit-btn` → green background**

---

### Battle 2

```html
<p class="text highlight">Hello</p>
```

```css
p.highlight {
  color: orange;      /* 0,0,1,1 */
}

.text.highlight {
  color: purple;      /* 0,0,2,0 — ✅ WINS */
}
```

**Winner: `.text.highlight` → purple**

Why? Compare column by column:
- Column C: `2` > `1` → `.text.highlight` wins!

---

### Battle 3

```html
<a href="#" class="link">Visit</a>
```

```css
a:hover {
  color: red;         /* 0,0,1,1 */
}

.link {
  color: blue;        /* 0,0,1,0 */
}
```

**Winner: `a:hover` → red** (when hovered)  
Both have 1 in column C, but `a:hover` also has 1 in column D → `0,0,1,1` beats `0,0,1,0`

---

## The `!important` Rule

`!important` **overrides ALL specificity rules** and forces a style to apply.

```css
p {
  color: black !important;   /* This wins no matter what */
}

#hero p {
  color: red;                /* ❌ Loses to !important above */
}
```

### When `!important` battles `!important`

If both rules use `!important`, then **specificity decides** again:

```css
p {
  color: black !important;      /* 0,0,0,1 + !important */
}

.text {
  color: purple !important;     /* 0,0,1,0 + !important — ✅ WINS */
}
```

### ⚠️ When to use `!important`

| Use Case | Recommendation |
|----------|---------------|
| Utility classes (`.hidden`, `.sr-only`) | ✅ Acceptable |
| Overriding 3rd party CSS you can't edit | ✅ Acceptable |
| Your own styles fighting each other | ❌ Bad practice — fix specificity instead |
| Every other rule in your file | ❌ Code smell — refactor your CSS |

---

## Inheritance vs Cascade

**Inheritance** means some CSS properties automatically pass from **parent → child**.

```html
<div class="wrapper">
  <p>This paragraph inherits color from wrapper.</p>
</div>
```

```css
.wrapper {
  color: teal;
  font-family: 'Georgia', serif;
  border: 2px solid black;  /* ❌ NOT inherited */
}

/* The <p> gets color and font-family automatically */
/* But NOT the border — borders don't inherit */
```

### Commonly Inherited Properties

```
color          font-family      font-size
font-weight    line-height      text-align
letter-spacing visibility       cursor
```

### NOT Inherited by Default

```
margin         padding          border
background     width            height
display        position         box-shadow
```

### Force Inheritance with `inherit`

```css
p {
  border: inherit;       /* Force border to inherit from parent */
  margin: inherit;       /* Force margin to inherit */
}
```

### Reset Inheritance with `initial` / `unset`

```css
p {
  color: initial;    /* Resets to browser default (usually black) */
  color: unset;      /* If inherited → inherit; if not → initial */
}
```

---

## Source Order (Last Rule Wins)

When two rules have **exactly the same specificity**, the one that appears **later in the CSS** wins.

```css
/* Both have specificity: 0,0,1,0 */

.box {
  color: red;
}

.box {
  color: blue;    /* ✅ WINS — comes last */
}
```

### In External Stylesheets

```html
<head>
  <link rel="stylesheet" href="base.css">      <!-- Loaded first -->
  <link rel="stylesheet" href="theme.css">     <!-- Loaded second — overrides base -->
  <link rel="stylesheet" href="custom.css">    <!-- Loaded last — highest priority -->
</head>
```

Rules in `custom.css` will override same-specificity rules in `base.css`.

---

## Practical Tips & Gotchas

### 1. Avoid ID selectors in CSS

```css
/* ❌ Bad — Too much specificity, hard to override */
#navbar #menu .item {
  color: white;
}

/* ✅ Better — Easier to manage */
.navbar-menu-item {
  color: white;
}
```

### 2. Don't chain unnecessary elements

```css
/* ❌ Overly specific */
div.container > ul.list > li.item > a.link {
  color: red;
}

/* ✅ Cleaner */
.link {
  color: red;
}
```

### 3. `:is()` and `:where()` — Specificity difference

```css
/* :is() takes the specificity of its MOST SPECIFIC argument */
:is(h1, h2, h3) { color: red; }    /* 0,0,0,1 */
:is(#hero, .box) { color: red; }   /* 0,1,0,0 — takes ID's specificity */

/* :where() ALWAYS has 0 specificity */
:where(h1, h2, h3) { color: red; } /* 0,0,0,0 — great for resets */
```

### 4. Inline styles always beat external CSS

```html
<!-- This red will override ANY class or ID rule -->
<p style="color: red;">Hello</p>
```

```css
#main p {
  color: blue;    /* ❌ Loses to inline style */
}
```

### 5. The `:not()` pseudo-class

```css
/* :not() itself has no specificity — but its ARGUMENT does */
p:not(.special)     /* 0,0,1,1 — p(0,0,0,1) + .special(0,0,1,0) */
p:not(#hero)        /* 0,1,0,1 — p(0,0,0,1) + #hero(0,1,0,0) */
```

---

## Quick Reference Cheatsheet

```
SPECIFICITY SCORE:   [Inline] [ID] [Class/Attr/Pseudo-class] [Element/Pseudo-el]

Universal *          →  0,0,0,0
div                  →  0,0,0,1
div p                →  0,0,0,2
.class               →  0,0,1,0
div.class            →  0,0,1,1
:hover               →  0,0,1,0
[type="text"]        →  0,0,1,0
#id                  →  0,1,0,0
#id .class           →  0,1,1,0
#id .class div       →  0,1,1,1
style=""             →  1,0,0,0
!important           →  Overrides all (specificity tiebreak applies)
```

```
CASCADE ORDER (High → Low):
1. !important (user agent → user → author)
2. Inline styles
3. ID selectors
4. Class / Attribute / Pseudo-class
5. Element / Pseudo-element
6. Universal selector
7. Inherited styles
```

---

## 💡 Golden Rules to Remember

- **Specificity beats source order** — a later rule only wins if specificity is equal
- **`!important` beats specificity** — but use it sparingly
- **Inline styles beat everything** — except `!important`
- **IDs are nuclear** — one `#id` beats infinite `.classes`
- **Keep specificity low** — makes code easier to override and maintain
- **Use `:where()` for resets** — zero specificity, full power

---