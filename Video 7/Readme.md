# HTML Block vs Inline Elements — Complete Guide

> A detailed breakdown of block-level and inline elements, their differences, use cases, and which HTML tags fall under each category.

---

## Table of Contents

1. [What are Block Elements?](#what-are-block-elements)
2. [What are Inline Elements?](#what-are-inline-elements)
3. [Key Differences](#key-differences)
4. [Block Element Tags](#block-element-tags)
5. [Inline Element Tags](#inline-element-tags)
6. [Use Cases](#use-cases)
7. [Examples](#examples)
8. [Bonus: Inline-Block](#bonus-inline-block)

---

## What are Block Elements?

A **block-level element** always starts on a **new line** and takes up the **full width** available (stretches from left to right as far as it can). Even if you place two block elements side by side in your HTML, they will still stack on top of each other vertically.

Think of block elements as **building blocks** — they define the structure and layout of the page.

```html
<div>I am a block element</div>
<div>I will always start on a new line</div>
```

**Output:**
```
[ I am a block element         ]
[ I will always start on a new ]
[ line                         ]
```

---

## What are Inline Elements?

An **inline element** does **not** start on a new line. It only takes up as much width as its content requires. Inline elements sit **within the flow of text** and sit next to each other horizontally.

Think of inline elements as **words in a sentence** — they flow naturally inside a line of text.

```html
<span>I am inline</span>
<span>I sit right next to the previous element</span>
```

**Output:**
```
I am inline I sit right next to the previous element
```

---

## Key Differences

| Feature | Block Elements | Inline Elements |
|---|---|---|
| Starts on new line | ✅ Yes | ❌ No |
| Takes full width | ✅ Yes (by default) | ❌ No (only as wide as content) |
| Can contain block elements | ✅ Yes | ❌ No (generally) |
| Can contain inline elements | ✅ Yes | ✅ Yes |
| Width & Height settable via CSS | ✅ Yes | ❌ No (ignored) |
| Top/Bottom margin & padding | ✅ Yes | ⚠️ Partially (doesn't push other elements) |
| Left/Right margin & padding | ✅ Yes | ✅ Yes |
| Used for | Page structure & layout | Styling text & small content |

---

## Block Element Tags

These are the most commonly used block-level HTML tags:

### Structural / Layout Tags
| Tag | Description |
|---|---|
| `<div>` | Generic container, used for layout and grouping |
| `<header>` | Top section of a page or section |
| `<footer>` | Bottom section of a page or section |
| `<main>` | Main content area of the page |
| `<section>` | Thematic grouping of content |
| `<article>` | Self-contained piece of content (blog post, news article) |
| `<aside>` | Sidebar content, tangentially related to main content |
| `<nav>` | Navigation links container |

### Heading Tags
| Tag | Description |
|---|---|
| `<h1>` | Largest heading — main page title |
| `<h2>` | Second-level heading |
| `<h3>` | Third-level heading |
| `<h4>` | Fourth-level heading |
| `<h5>` | Fifth-level heading |
| `<h6>` | Smallest heading |

### Text & Content Tags
| Tag | Description |
|---|---|
| `<p>` | Paragraph of text |
| `<blockquote>` | Long quote from an external source |
| `<pre>` | Preformatted text (preserves whitespace & line breaks) |
| `<hr>` | Horizontal rule / divider line |

### List Tags
| Tag | Description |
|---|---|
| `<ul>` | Unordered (bullet) list |
| `<ol>` | Ordered (numbered) list |
| `<li>` | List item (inside `ul` or `ol`) |
| `<dl>` | Description list |
| `<dt>` | Term in a description list |
| `<dd>` | Description of a term in a description list |

### Form & Media Tags
| Tag | Description |
|---|---|
| `<form>` | Input form container |
| `<table>` | Table container |
| `<video>` | Video embed |
| `<audio>` | Audio embed |
| `<canvas>` | Drawing surface (used with JavaScript) |
| `<figure>` | Self-contained media content (image + caption) |
| `<figcaption>` | Caption for a `<figure>` element |

---

## Inline Element Tags

These are the most commonly used inline HTML tags:

### Text Formatting Tags
| Tag | Description |
|---|---|
| `<span>` | Generic inline container, used for styling text |
| `<a>` | Anchor / hyperlink |
| `<strong>` | Bold text (semantically important) |
| `<b>` | Bold text (purely visual, no semantic meaning) |
| `<em>` | Italic text (semantically emphasized) |
| `<i>` | Italic text (purely visual) |
| `<u>` | Underlined text |
| `<s>` | Strikethrough text |
| `<mark>` | Highlighted text |
| `<small>` | Smaller text (fine print, disclaimers) |
| `<sub>` | Subscript text (e.g., H₂O) |
| `<sup>` | Superscript text (e.g., x²) |
| `<del>` | Deleted / removed text (shown as strikethrough) |
| `<ins>` | Inserted text (shown as underline) |
| `<abbr>` | Abbreviation or acronym with a tooltip |
| `<cite>` | Citation / title of a work |
| `<code>` | Inline code snippet |
| `<kbd>` | Keyboard input (e.g., Press `Ctrl + C`) |
| `<var>` | Variable in math or programming |
| `<q>` | Short inline quotation |
| `<time>` | Machine-readable date/time |

### Media / Embed Tags
| Tag | Description |
|---|---|
| `<img>` | Image |
| `<input>` | Form input field |
| `<button>` | Clickable button |
| `<label>` | Label for a form element |
| `<select>` | Dropdown selector |
| `<textarea>` | Multi-line text input |
| `<br>` | Line break |

---

## Use Cases

### When to use Block Elements

- **Page layout** — Use `<div>`, `<section>`, `<main>`, `<header>`, `<footer>` to build the skeleton of your page.
- **Headings** — Use `<h1>` to `<h6>` to define content hierarchy.
- **Paragraphs** — Use `<p>` for any chunk of readable text.
- **Lists** — Use `<ul>` / `<ol>` for navigation menus, bullet points, steps.
- **Forms** — Use `<form>` to wrap all your input fields.

```html
<header>
  <nav>...</nav>
</header>
<main>
  <section>
    <h1>Welcome to My Website</h1>
    <p>This is a paragraph of text explaining what the site is about.</p>
  </section>
</main>
<footer>
  <p>© 2025 My Website</p>
</footer>
```

---

### When to use Inline Elements

- **Styling a word or phrase** inside a paragraph — Use `<span>`, `<strong>`, `<em>`.
- **Links** — Use `<a>` to make text clickable without breaking the line flow.
- **Code mentions** — Use `<code>` inside a sentence.
- **Highlighting** — Use `<mark>` to highlight specific words.
- **Images inside text** — Use `<img>` to embed images inline with text.

```html
<p>
  This is a <strong>very important</strong> concept in HTML.
  You can read more about it <a href="#">here</a>.
  The CSS property is called <code>display</code>.
</p>
```

---

## Examples

### Example 1 — Block vs Inline Side by Side

```html
<!-- BLOCK: Each div takes full width and stacks vertically -->
<div style="background: #f0f0f0; padding: 10px;">Block 1</div>
<div style="background: #ddd; padding: 10px;">Block 2</div>

<!-- INLINE: Each span sits next to each other horizontally -->
<span style="background: #f0f0f0; padding: 5px;">Inline 1</span>
<span style="background: #ddd; padding: 5px;">Inline 2</span>
```

---

### Example 2 — Inline Elements Inside a Block Element ✅

```html
<!-- Correct: inline elements inside a block element -->
<p>
  My name is <strong>Voldemort</strong> and I build
  <em>hand-coded</em> websites. Check out my work
  <a href="#">here</a>.
</p>
```

---

### Example 3 — Block Element Inside Inline Element ❌ (Invalid HTML)

```html
<!-- WRONG: Never put a block element inside an inline element -->
<span>
  <div>This is invalid HTML and will break layouts</div>
</span>

<!-- CORRECT: Do it the other way around -->
<div>
  <span>This is perfectly valid</span>
</div>
```

---

### Example 4 — Width & Height on Inline Elements (Doesn't Work)

```css
/* This will NOT work on a <span> */
span {
  width: 200px;   /* ignored */
  height: 50px;   /* ignored */
}

/* This WILL work on a <div> */
div {
  width: 200px;   /* works */
  height: 50px;   /* works */
}
```

---

### Example 5 — Real World Navbar (Block + Inline combined)

```html
<nav>                          <!-- Block element: full width bar -->
  <a href="#">Home</a>         <!-- Inline: sits next to each other -->
  <a href="#">About</a>        <!-- Inline -->
  <a href="#">Projects</a>     <!-- Inline -->
  <a href="#">Contact</a>      <!-- Inline -->
</nav>
```

---

## Bonus: Inline-Block

There is a third display value worth knowing — **`display: inline-block`**.

It combines the best of both worlds:
- Like **inline** → it sits next to other elements (does not force a new line)
- Like **block** → you can set `width`, `height`, `margin`, and `padding` on it

```css
.card {
  display: inline-block;
  width: 200px;
  height: 150px;
  margin: 10px;
}
```

```html
<!-- These three cards will sit side by side but respect width/height -->
<div class="card">Card 1</div>
<div class="card">Card 2</div>
<div class="card">Card 3</div>
```

### Quick Summary

| | `block` | `inline` | `inline-block` |
|---|---|---|---|
| New line | ✅ | ❌ | ❌ |
| Full width | ✅ | ❌ | ❌ |
| Set width/height | ✅ | ❌ | ✅ |
| Top/bottom margin | ✅ | ❌ | ✅ |

---

> **Remember:** HTML is about **structure and semantics**. Use block elements to define the page layout and sections. Use inline elements to style and add meaning to content within those sections. Never nest block elements inside inline elements.