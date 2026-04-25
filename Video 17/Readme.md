# 🎯 CSS Selectors — Complete Reference

> All CSS selectors in one place with explanations and examples.  
> Part of the **Frontend Domination** course.

---

## 📌 Table of Contents

1. [Basic Selectors](#1-basic-selectors)
2. [Combinator Selectors](#2-combinator-selectors)
3. [Attribute Selectors](#3-attribute-selectors)
4. [Pseudo-Class Selectors](#4-pseudo-class-selectors)
5. [Pseudo-Element Selectors](#5-pseudo-element-selectors)
6. [Grouping & Universal](#6-grouping--universal)
7. [Specificity Cheatsheet](#7-specificity-cheatsheet)

---

## 1. Basic Selectors

---

### 🔹 Universal Selector `*`

Selects **every element** on the page.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

---

### 🔹 Type Selector (Element Selector)

Selects all elements of a given **HTML tag**.

```css
p {
  font-size: 16px;
  color: #333;
}

h1 {
  font-size: 48px;
}
```

```html
<p>This paragraph gets styled.</p>
<h1>This heading gets styled.</h1>
```

---

### 🔹 Class Selector `.classname`

Selects all elements with a specific **class** attribute.

```css
.card {
  background: #fff;
  border-radius: 8px;
  padding: 20px;
}
```

```html
<div class="card">I am a card.</div>
<p class="card">I am also a card.</p>
```

---

### 🔹 ID Selector `#idname`

Selects the **one unique element** with that ID. IDs should be unique per page.

```css
#navbar {
  position: fixed;
  top: 0;
  width: 100%;
}
```

```html
<nav id="navbar">I'm the navbar.</nav>
```

> ⚠️ Avoid overusing IDs for styling — they have very high specificity and are hard to override.

---

## 2. Combinator Selectors

---

### 🔹 Descendant Selector `A B`

Selects **all B elements inside A**, no matter how deeply nested.

```css
section p {
  color: gray;
}
```

```html
<section>
  <p>I get styled.</p>       <!-- ✅ -->
  <div>
    <p>Me too!</p>            <!-- ✅ -->
  </div>
</section>
<p>I don't get styled.</p>   <!-- ❌ outside section -->
```

---

### 🔹 Child Selector `A > B`

Selects **direct children only** — not deeper descendants.

```css
ul > li {
  list-style: none;
}
```

```html
<ul>
  <li>Direct child ✅</li>
  <li>
    <ol>
      <li>NOT a direct child of ul ❌</li>
    </ol>
  </li>
</ul>
```

---

### 🔹 Adjacent Sibling Selector `A + B`

Selects the **immediately next sibling** of A.

```css
h1 + p {
  margin-top: 0;
  font-size: 18px;
}
```

```html
<h1>Heading</h1>
<p>I come right after h1 — I get styled. ✅</p>
<p>I'm the second p — I don't. ❌</p>
```

---

### 🔹 General Sibling Selector `A ~ B`

Selects **all siblings** of A that come after it (not before).

```css
h1 ~ p {
  color: #888;
}
```

```html
<h1>Heading</h1>
<p>Styled ✅</p>
<p>Also styled ✅</p>
<div>Not a p, skipped</div>
<p>Still styled ✅</p>
```

---

## 3. Attribute Selectors

---

### 🔹 `[attr]` — Has the attribute

```css
input[required] {
  border: 2px solid red;
}
```

```html
<input type="text" required />  <!-- ✅ styled -->
<input type="text" />           <!-- ❌ not styled -->
```

---

### 🔹 `[attr="value"]` — Exact match

```css
input[type="email"] {
  background: #f0f8ff;
}
```

```html
<input type="email" />  <!-- ✅ -->
<input type="text" />   <!-- ❌ -->
```

---

### 🔹 `[attr~="value"]` — Word in space-separated list

```css
[class~="btn"] {
  padding: 10px 20px;
}
```

```html
<div class="btn primary">Styled ✅</div>
<div class="btn-large">NOT styled ❌</div>
```

---

### 🔹 `[attr|="value"]` — Exact or starts with `value-`

Commonly used for language attributes.

```css
[lang|="en"] {
  font-family: serif;
}
```

```html
<p lang="en">Styled ✅</p>
<p lang="en-US">Also styled ✅</p>
<p lang="fr">Not styled ❌</p>
```

---

### 🔹 `[attr^="value"]` — Starts with

```css
a[href^="https"] {
  color: green;
}
```

```html
<a href="https://google.com">Secure ✅</a>
<a href="http://old.com">Not styled ❌</a>
```

---

### 🔹 `[attr$="value"]` — Ends with

```css
a[href$=".pdf"] {
  color: red;
}
```

```html
<a href="resume.pdf">PDF link ✅</a>
<a href="photo.jpg">Not styled ❌</a>
```

---

### 🔹 `[attr*="value"]` — Contains anywhere

```css
a[href*="youtube"] {
  color: crimson;
}
```

```html
<a href="https://youtube.com/watch">YouTube ✅</a>
<a href="https://google.com">Google ❌</a>
```

---

## 4. Pseudo-Class Selectors

These select elements based on their **state or position**.

---

### 🔹 `:hover`

When mouse is over the element.

```css
button:hover {
  background: #000;
  color: #fff;
}
```

---

### 🔹 `:focus`

When an element is focused (clicked or tabbed into).

```css
input:focus {
  outline: 2px solid blue;
}
```

---

### 🔹 `:active`

While the element is being clicked.

```css
button:active {
  transform: scale(0.97);
}
```

---

### 🔹 `:visited` / `:link`

For anchor tags — `:link` = unvisited, `:visited` = already visited.

```css
a:link    { color: blue; }
a:visited { color: purple; }
```

---

### 🔹 `:checked`

For checkboxes or radio buttons that are checked.

```css
input[type="checkbox"]:checked {
  accent-color: green;
}
```

---

### 🔹 `:disabled` / `:enabled`

```css
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

input:enabled {
  background: white;
}
```

---

### 🔹 `:not(selector)`

Selects everything **except** the given selector.

```css
li:not(.active) {
  opacity: 0.5;
}
```

```html
<li class="active">Full opacity ✅</li>
<li>Half opacity ✅</li>
<li>Half opacity ✅</li>
```

---

### 🔹 `:first-child` / `:last-child`

Selects the first or last child of its parent.

```css
li:first-child { font-weight: bold; }
li:last-child  { color: red; }
```

---

### 🔹 `:nth-child(n)`

Selects the nth child. `n` can be a number, keyword, or formula.

```css
li:nth-child(2)      { color: blue; }     /* 2nd item */
li:nth-child(odd)    { background: #eee; } /* odd rows */
li:nth-child(even)   { background: #fff; } /* even rows */
li:nth-child(3n)     { color: red; }       /* every 3rd */
li:nth-child(3n+1)   { color: green; }     /* 1st, 4th, 7th... */
```

---

### 🔹 `:nth-last-child(n)`

Same as `:nth-child` but counts from the **end**.

```css
li:nth-last-child(1) { /* same as :last-child */ }
li:nth-last-child(2) { color: orange; } /* second from last */
```

---

### 🔹 `:first-of-type` / `:last-of-type`

Selects first/last element of a **specific tag type** inside parent — ignores other element types.

```css
p:first-of-type { font-size: 20px; }
p:last-of-type  { color: gray; }
```

```html
<div>
  <h2>Heading</h2>
  <p>First p ✅</p>   <!-- first-of-type -->
  <p>Middle p</p>
  <p>Last p ✅</p>    <!-- last-of-type -->
</div>
```

---

### 🔹 `:nth-of-type(n)`

Like `:nth-child` but only counts elements of that **type**.

```css
p:nth-of-type(2) {
  color: purple;
}
```

---

### 🔹 `:only-child`

Selects an element that is the **only child** of its parent.

```css
p:only-child {
  font-style: italic;
}
```

```html
<div><p>Only child ✅</p></div>
<div><p>Not only</p><p>child ❌</p></div>
```

---

### 🔹 `:only-of-type`

Element that is the only one of its **type** in the parent.

```css
img:only-of-type {
  display: block;
  margin: auto;
}
```

---

### 🔹 `:empty`

Selects elements with **no children** (not even text).

```css
div:empty {
  display: none;
}
```

---

### 🔹 `:root`

The root element of the document — usually `<html>`. Best used for CSS variables.

```css
:root {
  --primary: #ff4444;
  --bg: #0a0a0a;
}
```

---

### 🔹 `:is()`

Matches any element in the list. Great for grouping.

```css
:is(h1, h2, h3) {
  font-family: 'Poppins', sans-serif;
}

/* Same as writing: */
h1, h2, h3 { font-family: 'Poppins', sans-serif; }
```

---

### 🔹 `:where()`

Same as `:is()` but has **zero specificity**. Easier to override.

```css
:where(h1, h2, h3) {
  margin-bottom: 1rem;
}
```

---

### 🔹 `:has()`

Selects a parent **based on its children**. A game changer!

```css
/* Style a card that contains an img */
.card:has(img) {
  padding: 0;
}

/* Style form with invalid input */
form:has(input:invalid) {
  border: 2px solid red;
}
```

---

### 🔹 `:placeholder-shown`

Targets an input while its placeholder is visible (i.e., input is empty).

```css
input:placeholder-shown {
  border-color: #ccc;
}
```

---

### 🔹 `:valid` / `:invalid`

For form inputs based on HTML validation rules.

```css
input:valid   { border-color: green; }
input:invalid { border-color: red; }
```

---

### 🔹 `:required` / `:optional`

```css
input:required { border-left: 4px solid red; }
input:optional { border-left: 4px solid #ccc; }
```

---

### 🔹 `:in-range` / `:out-of-range`

For `<input type="number">` with `min` and `max`.

```css
input:in-range    { background: #e0ffe0; }
input:out-of-range { background: #ffe0e0; }
```

```html
<input type="number" min="1" max="10" value="5" />
```

---

### 🔹 `:fullscreen`

When an element is displayed in fullscreen mode.

```css
video:fullscreen {
  object-fit: cover;
}
```

---

### 🔹 `:target`

Selects the element whose ID matches the current **URL hash**.

```css
section:target {
  background: #fffde7;
  border-left: 4px solid gold;
}
```

```html
<!-- URL: page.html#about -->
<section id="about">This section gets highlighted ✅</section>
```

---

### 🔹 `:scope`

Refers to the element that is the context for the selector. Most useful in JS `querySelector`.

```css
:scope > p {
  color: red; /* direct p children of the scoped element */
}
```

---

## 5. Pseudo-Element Selectors

These create **virtual elements** or target specific parts of an element. Always use `::` (double colon).

---

### 🔹 `::before`

Inserts content **before** the element's actual content.

```css
.section-title::before {
  content: "// ";
  color: #ff4444;
}
```

```html
<h2 class="section-title">About Me</h2>
<!-- Renders as: // About Me -->
```

---

### 🔹 `::after`

Inserts content **after** the element's actual content.

```css
.btn::after {
  content: " →";
}
```

> 💡 `::before` and `::after` are heavily used for decorative overlays, underline animations, and icons without adding extra HTML.

---

### 🔹 `::placeholder`

Styles the placeholder text of an input.

```css
input::placeholder {
  color: #aaa;
  font-style: italic;
}
```

---

### 🔹 `::selection`

Styles the text that the user **highlights/selects**.

```css
::selection {
  background: #ff4444;
  color: #fff;
}
```

---

### 🔹 `::first-line`

Targets only the **first line** of text in a block element.

```css
p::first-line {
  font-weight: bold;
  font-size: 18px;
}
```

---

### 🔹 `::first-letter`

Targets only the **first letter** of a block element. Good for drop caps.

```css
p::first-letter {
  font-size: 3rem;
  float: left;
  line-height: 1;
  margin-right: 8px;
}
```

---

### 🔹 `::marker`

Styles the bullet or number of a list item.

```css
li::marker {
  color: red;
  font-size: 1.2em;
}
```

---

### 🔹 `::backdrop`

The backdrop behind a `<dialog>` or fullscreen element.

```css
dialog::backdrop {
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(4px);
}
```

---

### 🔹 `::file-selector-button`

Styles the button part of `<input type="file">`.

```css
input[type="file"]::file-selector-button {
  background: #000;
  color: #fff;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
}
```

---

## 6. Grouping & Universal

---

### 🔹 Grouping Selector `,`

Apply the same styles to **multiple selectors** at once.

```css
h1, h2, h3, h4, h5, h6 {
  font-family: 'Poppins', sans-serif;
  line-height: 1.2;
}
```

---

### 🔹 Combining Selectors

You can chain selectors without spaces for **more specificity**.

```css
/* Element with BOTH classes */
.btn.primary {
  background: blue;
}

/* p element with class highlight */
p.highlight {
  background: yellow;
}

/* input that is type email AND required */
input[type="email"]:required {
  border: 2px solid red;
}
```

---

## 7. Specificity Cheatsheet

Specificity decides which CSS rule **wins** when there's a conflict.

| Selector              | Specificity Value |
|-----------------------|-------------------|
| `*`                   | 0-0-0             |
| `div`, `p`, `h1`      | 0-0-1             |
| `.class`, `[attr]`, `:hover` | 0-1-0      |
| `#id`                 | 1-0-0             |
| Inline style          | 1-0-0-0           |
| `!important`          | Overrides all ☠️  |

### How to read specificity: `(IDs) - (Classes/Attrs/Pseudo-classes) - (Elements/Pseudo-elements)`

```css
/* 0-0-1 */    p { }
/* 0-1-0 */    .card { }
/* 1-0-0 */    #hero { }
/* 0-1-1 */    div.card { }
/* 0-2-1 */    div.card:hover { }
/* 1-1-1 */    #hero .card p { }
```

> ⚠️ Avoid `!important` — it breaks the cascade and makes debugging a nightmare. Fix specificity instead.

---

## 🧠 Quick Selector Memory Tricks

| Pattern      | Remember As                        |
|--------------|------------------------------------|
| `A B`        | "B anywhere inside A"              |
| `A > B`      | "B direct child of A"              |
| `A + B`      | "B immediately after A"            |
| `A ~ B`      | "All B's after A (same level)"     |
| `[attr^=]`   | `^` = starts (like start of line in regex) |
| `[attr$=]`   | `$` = ends (like end of line in regex)     |
| `[attr*=]`   | `*` = anywhere (like wildcard)             |
| `:nth-child` | Counts all children                |
| `:nth-of-type`| Counts only matching tag types   |
| `::before`   | Before the content                 |
| `::after`    | After the content                  |

---