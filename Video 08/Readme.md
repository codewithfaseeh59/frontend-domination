# 🎯 HTML `id` and `class` — Complete Guide

A detailed reference covering everything you need to know about `id` and `class` attributes in HTML.

---

## 📌 Table of Contents

1. [What are `id` and `class`?](#what-are-id-and-class)
2. [The `id` Attribute](#the-id-attribute)
3. [The `class` Attribute](#the-class-attribute)
4. [Key Differences](#key-differences)
5. [Naming Rules & Conventions](#naming-rules--conventions)
6. [Using `id` and `class` in CSS](#using-id-and-class-in-css)
7. [Using `id` and `class` in JavaScript](#using-id-and-class-in-javascript)
8. [Multiple Classes on One Element](#multiple-classes-on-one-element)
9. [Same Class on Multiple Elements](#same-class-on-multiple-elements)
10. [Specificity & Priority](#specificity--priority)
11. [Best Practices](#best-practices)
12. [Common Mistakes to Avoid](#common-mistakes-to-avoid)

---

## What are `id` and `class`?

`id` and `class` are **HTML global attributes** — meaning they can be applied to any HTML element. They are used to:

- **Target elements** with CSS for styling
- **Select elements** with JavaScript for manipulation
- **Identify sections** for anchor navigation (`id`)
- **Group elements** that share styling or behavior (`class`)

---

## The `id` Attribute

### Definition

The `id` attribute assigns a **unique identifier** to a single HTML element on the page.

### Syntax

```html
<div id="uniqueName">Content here</div>
```

### Key Rules

- Must be **unique** — no two elements on the same page can share the same `id`
- Each element can only have **one `id`**
- Is case-sensitive (`myId` ≠ `myid`)

### Example

```html
<header id="main-header">
  <h1>Welcome to My Site</h1>
</header>

<section id="about">
  <p>This is the about section.</p>
</section>

<footer id="site-footer">
  <p>© 2025</p>
</footer>
```

### Using `id` for Anchor Navigation

One powerful use of `id` is creating **in-page anchor links**:

```html
<!-- Link that jumps to the section -->
<a href="#about">Go to About Section</a>

<!-- The target section -->
<section id="about">
  <h2>About Us</h2>
</section>
```

---

## The `class` Attribute

### Definition

The `class` attribute assigns one or more **class names** to an element. Multiple elements can share the same class.

### Syntax

```html
<div class="className">Content here</div>
```

### Key Rules

- **Reusable** — the same class can be applied to many elements
- One element can have **multiple classes** (space-separated)
- Is case-sensitive (`btn` ≠ `Btn`)

### Example

```html
<button class="btn">Default Button</button>
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-danger">Danger Button</button>

<p class="text-lg bold-text highlight">Important paragraph</p>
```

---

## Key Differences

| Feature               | `id`                          | `class`                         |
|-----------------------|-------------------------------|----------------------------------|
| Uniqueness            | Must be unique per page       | Can be reused on many elements  |
| Per element limit     | Only one `id` per element     | Multiple classes allowed        |
| CSS selector          | `#idName`                     | `.className`                    |
| JS selector           | `getElementById()`            | `getElementsByClassName()` / `querySelectorAll()` |
| Specificity           | Higher (0,1,0,0)              | Lower (0,0,1,0)                 |
| Anchor links          | ✅ Yes                        | ❌ No                           |
| Best used for         | Unique landmarks, JS hooks    | Styling groups, reusable styles |

---

## Naming Rules & Conventions

### Valid Names (Both `id` and `class`)

- Must **not** start with a number
- Can contain letters, digits, hyphens (`-`), and underscores (`_`)
- No spaces (for `id`); spaces separate multiple classes in `class`
- Should be descriptive and meaningful

```html
<!-- ✅ Valid -->
<div id="hero-section">
<div class="card-wrapper">
<div id="nav_bar">
<div class="item1">

<!-- ❌ Invalid -->
<div id="1section">       <!-- starts with number -->
<div id="my section">     <!-- space in id name -->
```

### Common Naming Conventions

```html
<!-- kebab-case (most common in HTML/CSS) -->
<div id="main-content" class="card-item">

<!-- camelCase (common in JavaScript) -->
<div id="mainContent" class="cardItem">

<!-- BEM (Block Element Modifier) — popular in large projects -->
<div class="card">
  <div class="card__title">Title</div>
  <div class="card__body card__body--highlighted">Body</div>
</div>
```

---

## Using `id` and `class` in CSS

### Selecting by `id`

Use `#` prefix:

```css
#main-header {
  background-color: #111;
  color: #fff;
  padding: 20px;
}

#about {
  margin-top: 60px;
  font-size: 18px;
}
```

### Selecting by `class`

Use `.` prefix:

```css
.btn {
  padding: 10px 20px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.btn-primary {
  background-color: #007bff;
  color: white;
}

.btn-danger {
  background-color: #dc3545;
  color: white;
}
```

### Combining Selectors

```css
/* Element with a specific class */
p.highlight {
  background-color: yellow;
}

/* Element with a specific id AND class */
#hero .headline {
  font-size: 48px;
  font-weight: 700;
}

/* Multiple classes together */
.card.featured {
  border: 2px solid gold;
}
```

---

## Using `id` and `class` in JavaScript

### Selecting by `id`

```javascript
// Returns a single element (or null)
const header = document.getElementById("main-header");
header.style.backgroundColor = "navy";

// Also works with querySelector
const header2 = document.querySelector("#main-header");
```

### Selecting by `class`

```javascript
// Returns an HTMLCollection (live)
const buttons = document.getElementsByClassName("btn");

// Returns a NodeList (static) — preferred modern approach
const buttons2 = document.querySelectorAll(".btn");

// Loop through all matched elements
buttons2.forEach(btn => {
  btn.addEventListener("click", () => {
    console.log("Button clicked!");
  });
});
```

### Manipulating Classes with JavaScript

```javascript
const box = document.getElementById("myBox");

// Add a class
box.classList.add("active");

// Remove a class
box.classList.remove("hidden");

// Toggle a class (adds if absent, removes if present)
box.classList.toggle("open");

// Check if class exists
if (box.classList.contains("active")) {
  console.log("Box is active!");
}

// Replace a class
box.classList.replace("old-class", "new-class");
```

---

## Multiple Classes on One Element

An element can have **multiple classes** at once, separated by spaces:

```html
<div class="card featured dark large">
  This div has 4 classes applied simultaneously.
</div>
```

```css
.card        { border-radius: 8px; padding: 20px; }
.featured    { border: 2px solid gold; }
.dark        { background: #1a1a1a; color: white; }
.large       { font-size: 20px; min-height: 200px; }
```

All four sets of styles will apply to this single element — this is the real power of classes.

---

## Same Class on Multiple Elements

The same class can style or target many elements at once:

```html
<p class="highlight">First paragraph</p>
<p class="highlight">Second paragraph</p>
<h2 class="highlight">A heading too</h2>
<span class="highlight">And a span!</span>
```

```css
.highlight {
  background-color: #fffb00;
  padding: 2px 6px;
}
```

All four elements get the same yellow highlight. Change `.highlight` once in CSS — all four update instantly.

---

## Specificity & Priority

When CSS rules conflict, **specificity** determines which one wins:

| Selector Type          | Specificity Score |
|------------------------|-------------------|
| Inline style           | 1,0,0,0           |
| `id` selector (`#id`)  | 0,1,0,0           |
| `class` (`.class`)     | 0,0,1,0           |
| Element (`div`, `p`)   | 0,0,0,1           |

### Example

```html
<p id="intro" class="text-red">Hello</p>
```

```css
p           { color: black; }    /* specificity: 0,0,0,1 */
.text-red   { color: red; }      /* specificity: 0,0,1,0 */
#intro      { color: blue; }     /* specificity: 0,1,0,0 — WINS */
```

The text will be **blue** because `id` has higher specificity.

> 💡 **Tip:** Avoid overusing `id` in CSS for this reason — it makes overriding styles harder. Prefer `class` for styling and reserve `id` for JS hooks or anchor links.

---

## Best Practices

### ✅ DO

```html
<!-- Use id for unique landmarks and JS targets -->
<nav id="main-nav">...</nav>
<section id="contact">...</section>

<!-- Use class for reusable styling -->
<div class="card">...</div>
<div class="card featured">...</div>

<!-- Use meaningful, descriptive names -->
<button class="btn btn-submit">Submit</button>

<!-- Use BEM for scalable class naming -->
<div class="modal">
  <div class="modal__header">Title</div>
  <div class="modal__body modal__body--scrollable">Content</div>
</div>
```

### ❌ DON'T

```html
<!-- Don't reuse the same id -->
<div id="box">First</div>
<div id="box">Second</div>  <!-- ❌ Invalid! -->

<!-- Don't use vague names -->
<div id="d1" class="x y z">...</div>  <!-- ❌ Meaningless -->

<!-- Don't overuse id for CSS styling -->
#button { color: red; }  /* ❌ Hard to override */
.button { color: red; }  /* ✅ Much better */
```

---

## Common Mistakes to Avoid

| Mistake | Problem | Fix |
|---|---|---|
| Duplicate `id` on a page | Breaks JS `getElementById()`, invalid HTML | Ensure every `id` is unique |
| Using `id` for all CSS styling | Extremely high specificity, hard to override | Use `class` for styling |
| Spaces inside an `id` | Invalid HTML | Use hyphens or underscores instead |
| Starting names with a number | Invalid selector in CSS | Start with a letter |
| Forgetting `#` or `.` in CSS/JS | Selector won't match | `#myId` for id, `.myClass` for class |
| Case mismatch | `myClass` ≠ `MyClass` | Be consistent with casing |

---

## Quick Reference Cheat Sheet

```
HTML:       <div id="myId" class="myClass another-class">

CSS id:     #myId { ... }
CSS class:  .myClass { ... }

JS by id:   document.getElementById("myId")
            document.querySelector("#myId")

JS by class: document.getElementsByClassName("myClass")
             document.querySelectorAll(".myClass")

classList:  .add()  .remove()  .toggle()  .contains()  .replace()
```

---