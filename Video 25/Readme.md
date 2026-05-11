# 📋 CSS List Styling — Complete Reference

A full guide to styling `<ul>`, `<ol>`, and `<li>` elements in CSS — with examples for every property.

---

## Table of Contents

1. [list-style-type](#1-list-style-type)
2. [list-style-position](#2-list-style-position)
3. [list-style-image](#3-list-style-image)
4. [list-style (shorthand)](#4-list-style-shorthand)
5. [Removing Default Styles](#5-removing-default-styles)
6. [Custom Bullets with ::before](#6-custom-bullets-with-before)
7. [Horizontal Navigation List](#7-horizontal-navigation-list)
8. [Styled Ordered List (Counter)](#8-styled-ordered-list-counter)
9. [Nested Lists](#9-nested-lists)
10. [Common Patterns / Cheatsheet](#10-common-patterns--cheatsheet)

---

## 1. `list-style-type`

Controls the bullet or numbering style.

### Unordered List Types

```css
ul.disc   { list-style-type: disc; }     /* ● default */
ul.circle { list-style-type: circle; }   /* ○ */
ul.square { list-style-type: square; }   /* ■ */
ul.none   { list-style-type: none; }     /* no bullet */
```

```html
<ul class="disc">
  <li>Disc bullet</li>
</ul>

<ul class="circle">
  <li>Circle bullet</li>
</ul>

<ul class="square">
  <li>Square bullet</li>
</ul>
```

### Ordered List Types

```css
ol.decimal      { list-style-type: decimal; }        /* 1, 2, 3 */
ol.alpha-lower  { list-style-type: lower-alpha; }    /* a, b, c */
ol.alpha-upper  { list-style-type: upper-alpha; }    /* A, B, C */
ol.roman-lower  { list-style-type: lower-roman; }    /* i, ii, iii */
ol.roman-upper  { list-style-type: upper-roman; }    /* I, II, III */
ol.greek        { list-style-type: lower-greek; }    /* α, β, γ */
```

```html
<ol class="roman-upper">
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ol>
```

---

## 2. `list-style-position`

Controls whether the bullet/marker is **inside** or **outside** the list item box.

```css
ul.outside { list-style-position: outside; } /* default */
ul.inside  { list-style-position: inside; }
```

```html
<ul class="outside">
  <li>Marker is outside the content box. Text wraps under text, not under the marker.</li>
</ul>

<ul class="inside">
  <li>Marker is inside the content box. Text wraps under the marker on the next line.</li>
</ul>
```

> **Tip:** `outside` is the default and looks cleaner. Use `inside` when you need the bullet to be part of the text flow (e.g., centered lists).

---

## 3. `list-style-image`

Replaces the bullet with a custom image.

```css
ul.custom-image {
  list-style-image: url('star.png');
}
```

```html
<ul class="custom-image">
  <li>Custom image bullet</li>
  <li>Another item</li>
</ul>
```

> **Note:** Image sizing is hard to control with this property. Using `::before` with `background-image` gives you much more control (see Section 6).

---

## 4. `list-style` (Shorthand)

Combines `list-style-type`, `list-style-position`, and `list-style-image` in one line.

```css
/* Syntax: list-style: <type> <position> <image> */

ul {
  list-style: square inside none;
}

ol {
  list-style: upper-roman outside;
}

/* Remove everything */
ul {
  list-style: none;
}
```

---

## 5. Removing Default Styles

Browsers add default padding/margin to lists. Always reset them when building custom UIs.

```css
ul, ol {
  list-style: none;
  margin: 0;
  padding: 0;
}
```

```html
<ul>
  <li>No bullets</li>
  <li>No margin</li>
  <li>No padding</li>
</ul>
```

---

## 6. Custom Bullets with `::before`

The best way to create custom bullets — full control over color, size, and spacing.

### Emoji Bullet

```css
ul.emoji-list {
  list-style: none;
  padding: 0;
}

ul.emoji-list li::before {
  content: "🔥 ";
}
```

```html
<ul class="emoji-list">
  <li>Frontend Development</li>
  <li>CSS Animations</li>
  <li>GSAP ScrollTrigger</li>
</ul>
```

---

### Custom Color Bullet

```css
ul.color-bullets {
  list-style: none;
  padding-left: 1.5rem;
}

ul.color-bullets li {
  position: relative;
  margin-bottom: 8px;
}

ul.color-bullets li::before {
  content: "";
  position: absolute;
  left: -1.2rem;
  top: 50%;
  transform: translateY(-50%);
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #ff3cac;
}
```

```html
<ul class="color-bullets">
  <li>Pink dot bullet</li>
  <li>Fully customizable</li>
  <li>Works great with dark themes</li>
</ul>
```

---

### Custom Arrow Bullet

```css
ul.arrow-list {
  list-style: none;
  padding-left: 1.5rem;
}

ul.arrow-list li::before {
  content: "→ ";
  color: #00f5d4;
  font-weight: bold;
}
```

```html
<ul class="arrow-list">
  <li>Arrow styled item</li>
  <li>Clean and minimal</li>
</ul>
```

---

## 7. Horizontal Navigation List

Turn a vertical list into a horizontal nav bar.

```css
ul.nav {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 24px;
  background: #111;
  padding: 16px 24px;
}

ul.nav li a {
  color: #fff;
  text-decoration: none;
  font-size: 15px;
  letter-spacing: 0.05em;
  transition: color 0.2s;
}

ul.nav li a:hover {
  color: #ff3cac;
}
```

```html
<ul class="nav">
  <li><a href="#">Home</a></li>
  <li><a href="#">About</a></li>
  <li><a href="#">Projects</a></li>
  <li><a href="#">Contact</a></li>
</ul>
```

---

## 8. Styled Ordered List (Counter)

Use CSS `counter` to fully control number styling.

```css
ol.styled-counter {
  list-style: none;
  counter-reset: my-counter;
  padding-left: 0;
}

ol.styled-counter li {
  counter-increment: my-counter;
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

ol.styled-counter li::before {
  content: counter(my-counter);
  background: #ff3cac;
  color: #fff;
  font-weight: bold;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  flex-shrink: 0;
}
```

```html
<ol class="styled-counter">
  <li>Learn HTML Fundamentals</li>
  <li>Master CSS Styling</li>
  <li>Practice JavaScript</li>
  <li>Build Real Projects</li>
</ol>
```

---

## 9. Nested Lists

Styling parent and child lists differently.

```css
ul.nested-list {
  list-style: disc;
  padding-left: 1.5rem;
}

ul.nested-list ul {
  list-style: circle;
  padding-left: 1.5rem;
  margin-top: 6px;
}

ul.nested-list ul ul {
  list-style: square;
}
```

```html
<ul class="nested-list">
  <li>Frontend
    <ul>
      <li>HTML
        <ul>
          <li>Semantic Tags</li>
          <li>Forms</li>
        </ul>
      </li>
      <li>CSS</li>
      <li>JavaScript</li>
    </ul>
  </li>
  <li>Backend</li>
</ul>
```

---

## 10. Common Patterns / Cheatsheet

| Property | Values | Use Case |
|---|---|---|
| `list-style-type` | `disc`, `circle`, `square`, `none`, `decimal`, `lower-alpha`, `upper-roman`, etc. | Change bullet/number style |
| `list-style-position` | `inside`, `outside` | Control marker placement |
| `list-style-image` | `url('img.png')` | Image as bullet |
| `list-style` | shorthand for all 3 | Reset or set all at once |
| `::before` + `content` | any string/emoji | Full custom bullet control |
| `counter-reset` + `counter-increment` | custom counter name | Styled number lists |

### Quick Reset

```css
ul, ol {
  list-style: none;
  margin: 0;
  padding: 0;
}
```

### Quick Flex Nav

```css
ul {
  list-style: none;
  display: flex;
  gap: 16px;
  padding: 0;
  margin: 0;
}
```

### Custom Dot Bullet

```css
li::before {
  content: "";
  display: inline-block;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #ff3cac;
  margin-right: 10px;
  vertical-align: middle;
}
```

---

> 💡 **Pro Tip:** Always reset `list-style`, `margin`, and `padding` on `ul`/`ol` at the top of your CSS. Browser defaults vary and will break your layouts.