# HTML Entities & Common Tags — Beginner Reference

---

## 🔣 HTML Entities

HTML Entities are used when you want to display **special characters** that either have reserved meaning in HTML or can't be typed easily.

**Syntax:** `&name;` or `&#number;`

```html
<!-- Example -->
<p>Copyright &copy; 2025</p>
<p>5 &lt; 10 and 10 &gt; 5</p>
```

### Full Entities Table

| Character | Entity Name | Entity Number | Description |
|-----------|-------------|---------------|-------------|
| `©` | `&copy;` | `&#169;` | Copyright |
| `®` | `&reg;` | `&#174;` | Registered trademark |
| `™` | `&trade;` | `&#8482;` | Trademark |
| `<` | `&lt;` | `&#60;` | Less than |
| `>` | `&gt;` | `&#62;` | Greater than |
| `&` | `&amp;` | `&#38;` | Ampersand |
| `"` | `&quot;` | `&#34;` | Double quotation mark |
| `'` | `&apos;` | `&#39;` | Single quote / Apostrophe |
| `"` | `&ldquo;` | `&#8220;` | Left double curly quote |
| `"` | `&rdquo;` | `&#8221;` | Right double curly quote |
| `'` | `&lsquo;` | `&#8216;` | Left single curly quote |
| `'` | `&rsquo;` | `&#8217;` | Right single curly quote |
| ` ` | `&nbsp;` | `&#160;` | Non-breaking space |
| `—` | `&mdash;` | `&#8212;` | Em dash (long dash) |
| `–` | `&ndash;` | `&#8211;` | En dash (short dash) |
| `→` | `&rarr;` | `&#8594;` | Right arrow |
| `←` | `&larr;` | `&#8592;` | Left arrow |
| `↑` | `&uarr;` | `&#8593;` | Up arrow |
| `↓` | `&darr;` | `&#8595;` | Down arrow |
| `•` | `&bull;` | `&#8226;` | Bullet point |
| `·` | `&middot;` | `&#183;` | Middle dot |
| `★` | — | `&#9733;` | Filled star |
| `☆` | — | `&#9734;` | Empty star |
| `♥` | `&hearts;` | `&#9829;` | Heart |
| `♠` | `&spades;` | `&#9824;` | Spade |
| `°` | `&deg;` | `&#176;` | Degree symbol |
| `±` | `&plusmn;` | `&#177;` | Plus or minus |
| `×` | `&times;` | `&#215;` | Multiplication sign |
| `÷` | `&divide;` | `&#247;` | Division sign |
| `½` | `&frac12;` | `&#189;` | One half |
| `¼` | `&frac14;` | `&#188;` | One quarter |
| `¾` | `&frac34;` | `&#190;` | Three quarters |
| `€` | `&euro;` | `&#8364;` | Euro sign |
| `£` | `&pound;` | `&#163;` | Pound sign |
| `¥` | `&yen;` | `&#165;` | Yen sign |
| `¢` | `&cent;` | `&#162;` | Cent sign |
| `…` | `&hellip;` | `&#8230;` | Ellipsis (three dots) |
| `‼` | — | `&#8252;` | Double exclamation mark |

### Example Usage

```html
<p>Price: 5 &times; 3 = 15 &nbsp;&nbsp; (use &amp; for ampersands)</p>
<p>&ldquo;Never stop coding.&rdquo; &mdash; Someone wise</p>
<p>Temperature: 37&deg;C</p>
<p>Visit us &rarr; <a href="#">Click here</a></p>
<p>&copy; 2025 YourBrand. All rights &reg; reserved.</p>
```

---

## 🏷️ Common HTML Tags

---

### `<br>` — Line Break

Inserts a single line break. It is a **self-closing** tag — no closing tag needed.

```html
<p>Line one<br>Line two<br>Line three</p>
```

**Output:**
```
Line one
Line two
Line three
```

> ⚠️ Don't use `<br><br>` to add spacing between paragraphs. Use CSS `margin` instead.

---

### `<hr>` — Horizontal Rule

Draws a horizontal divider line. Also self-closing.

```html
<p>Section One</p>
<hr>
<p>Section Two</p>
```

---

### `<p>` — Paragraph

Wraps a block of text as a paragraph. Adds spacing above and below automatically.

```html
<p>This is a paragraph of text.</p>
<p>This is another paragraph.</p>
```

---

### `<h1>` to `<h6>` — Headings

6 levels of headings. `<h1>` is the largest, `<h6>` is the smallest.

```html
<h1>Main Heading</h1>
<h2>Sub Heading</h2>
<h3>Section Title</h3>
<h4>Sub Section</h4>
<h5>Small Heading</h5>
<h6>Smallest Heading</h6>
```

> ✅ Use only **one `<h1>`** per page — it's important for SEO.

---

### `<strong>` and `<b>` — Bold Text

```html
<p>This is <strong>important text</strong> (semantic bold).</p>
<p>This is <b>bold text</b> (visual bold only).</p>
```

> 💡 Prefer `<strong>` over `<b>` — it tells the browser this text is *important*, not just visually bold.

---

### `<em>` and `<i>` — Italic Text

```html
<p>This is <em>emphasized text</em> (semantic italic).</p>
<p>This is <i>italic text</i> (visual italic only).</p>
```

---

### `<u>` — Underline

```html
<p>This is <u>underlined text</u>.</p>
```

---

### `<mark>` — Highlighted Text

```html
<p>Remember to <mark>submit before Friday</mark>.</p>
```

---

### `<small>` — Small Text

```html
<p>Normal text. <small>This is smaller text.</small></p>
```

---

### `<del>` and `<ins>` — Deleted & Inserted Text

```html
<p>Price: <del>$100</del> <ins>$75</ins></p>
```

**Output:** Price: ~~$100~~ $75

---

### `<sup>` and `<sub>` — Superscript & Subscript

```html
<!-- Superscript: exponents, footnotes -->
<p>E = mc<sup>2</sup></p>
<p>Note<sup>1</sup></p>

<!-- Subscript: chemical formulas -->
<p>H<sub>2</sub>O</p>
<p>CO<sub>2</sub></p>
```

---

### `<blockquote>` — Block Quote

Used for long quotes from an external source.

```html
<blockquote cite="https://source.com">
  "The best way to predict the future is to create it."
</blockquote>
```

---

### `<q>` — Inline Quote

For short, inline quotes. Browser auto-adds quotation marks.

```html
<p>He said <q>I'll be back.</q></p>
```

**Output:** He said "I'll be back."

---

### `<abbr>` — Abbreviation

Shows full form on hover using the `title` attribute.

```html
<p><abbr title="HyperText Markup Language">HTML</abbr> is the backbone of the web.</p>
<p><abbr title="Graphics Animation and Scrolling Platform">GSAP</abbr> is great for animations.</p>
```

---

### `<code>` — Inline Code

For displaying a single line of code inline within text.

```html
<p>Use the <code>gsap.to()</code> method to animate elements.</p>
<p>Set <code>display: flex</code> on the parent container.</p>
```

---

### `<pre>` — Preformatted Text

Preserves whitespace and line breaks. Usually combined with `<code>` for code blocks.

```html
<pre>
  <code>
    const tl = gsap.timeline();
    tl.to(".box", { x: 100 })
      .to(".box", { y: 100 });
  </code>
</pre>
```

---

### `<kbd>` — Keyboard Input

Displays text as a keyboard key.

```html
<p>Press <kbd>Ctrl</kbd> + <kbd>S</kbd> to save.</p>
<p>Hit <kbd>Enter</kbd> to confirm.</p>
```

---

### `<samp>` — Sample Output

Shows sample output from a program.

```html
<p>The terminal returned: <samp>Error: File not found</samp></p>
```

---

### `<var>` — Variable

Represents a variable in math or programming.

```html
<p>The area is <var>width</var> &times; <var>height</var>.</p>
```

---

### `<details>` and `<summary>` — Collapsible Section

Creates a native expand/collapse toggle — no JS needed!

```html
<details>
  <summary>Click to see the answer</summary>
  <p>GSAP stands for GreenSock Animation Platform.</p>
</details>
```

---

### `<address>` — Contact Info

Wraps contact or address information.

```html
<address>
  Made by <a href="mailto:you@email.com">Your Name</a><br>
  Peshawar, Pakistan
</address>
```

---

### `<time>` — Date & Time

Semantic tag for dates/times. Helps browsers and SEO understand time values.

```html
<p>Published on <time datetime="2025-04-18">April 18, 2025</time></p>
```

---

## ✅ Quick Cheatsheet

```html
<!-- Text Formatting -->
<b>Bold</b>                <strong>Important Bold</strong>
<i>Italic</i>              <em>Emphasized Italic</em>
<u>Underline</u>           <mark>Highlight</mark>
<del>Strikethrough</del>   <ins>Inserted</ins>
<sup>Superscript</sup>     <sub>Subscript</sub>
<small>Small text</small>  <code>inline code</code>

<!-- Quotes -->
<q>Inline quote</q>
<blockquote>Block quote for longer content</blockquote>

<!-- Technical -->
<kbd>Ctrl</kbd>   <samp>output</samp>   <var>variable</var>

<!-- Structure -->
<br>                 <!-- line break -->
<hr>                 <!-- horizontal line -->
<pre>preformatted</pre>

<!-- Semantic Info -->
<abbr title="full form">SHORT</abbr>
<time datetime="2025-04-18">April 18</time>
<address>Contact info here</address>
<details><summary>Toggle</summary>Hidden content</details>
```