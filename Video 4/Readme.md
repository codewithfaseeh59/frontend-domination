# HTML Tags — Use Cases Guide

A quick reference for how and when to use **Heading**, **Paragraph**, and **Anchor** tags in a website.

---

## 🔠 Heading Tags — `<h1>` to `<h6>`

Heading tags define the **hierarchy and structure** of your page content. Think of them like chapters in a book.

### Use Cases

| Tag | Use Case |
|-----|----------|
| `<h1>` | Main page title — used **once per page** (e.g., hero section headline) |
| `<h2>` | Section titles (e.g., "About Us", "Our Services", "Projects") |
| `<h3>` | Sub-section headings inside an `<h2>` section |
| `<h4>` | Card titles, feature names, team member names |
| `<h5>` | Labels, sidebar headings, small callout titles |
| `<h6>` | Fine-print headers, footnote titles, rarely used |

### Real-World Examples

```html
<!-- Hero Section -->
<h1>We Build Digital Experiences</h1>

<!-- Services Section -->
<h2>Our Services</h2>

  <!-- Individual Service Card -->
  <h3>UI/UX Design</h3>

<!-- Blog Post -->
<h2>Top 10 Web Design Trends in 2025</h2>
  <h3>1. Glassmorphism</h3>
    <h4>How to implement it</h4>
```

### Key Rules
- Never skip levels (don't jump from `<h1>` to `<h4>`)
- Only **one `<h1>`** per page — it's your SEO anchor
- Headings affect **accessibility** — screen readers use them for navigation
- Style with CSS — don't pick a heading level based on font size

---

## 📝 Paragraph Tag — `<p>`

The `<p>` tag wraps **blocks of text content**. Every chunk of readable text on your page lives inside a `<p>`.

### Use Cases

| Context | Example |
|---------|---------|
| Hero description | Tagline or short intro under the main `<h1>` |
| About section | Brand story or company description |
| Service/feature description | What each card/service actually does |
| Blog/article body | Main readable content |
| Footer info | Copyright text, small descriptions |
| Error messages | User-facing feedback text |
| Form hints | Helper text below inputs |

### Real-World Examples

```html
<!-- Hero -->
<h1>KULT — Drop Culture, Redefined.</h1>
<p>Limited drops. No restocks. Pure streetwear chaos.</p>

<!-- About Section -->
<h2>About Us</h2>
<p>
  We are a creative studio obsessed with pushing the boundaries
  of digital design. From concept to code, we build it all.
</p>

<!-- Feature Card -->
<h3>Smooth Animations</h3>
<p>Every interaction is crafted with GSAP for butter-smooth performance.</p>

<!-- Footer -->
<p>&copy; 2025 KULT. All rights reserved.</p>
```

### Key Rules
- Don't use `<p>` for non-paragraph content (use `<span>`, `<div>`, or `<li>` instead)
- Avoid empty `<p>` tags just for spacing — use CSS `margin` instead
- Nest inline elements like `<strong>`, `<em>`, `<span>` inside `<p>`, not block elements like `<div>`

---

## 🔗 Anchor Tag — `<a>`

The `<a>` tag creates **links** — the backbone of the web. It connects pages, sections, files, emails, and more.

### Use Cases

| Use Case | Example |
|----------|---------|
| Internal page navigation | Link to another page on your site |
| Smooth scroll to section | Jump to `#section` on the same page |
| External link | Open a social profile or resource |
| Download link | Trigger a file download |
| Email link | Open the user's mail client |
| Phone link | Tap-to-call on mobile |
| CTA Button | "View Project", "Hire Me", "Get Started" |
| Navbar links | All nav items are anchor tags |

### Real-World Examples

```html
<!-- Internal Page Link -->
<a href="/about.html">About Us</a>

<!-- Smooth Scroll to Section (same page) -->
<a href="#projects">View Projects</a>

<!-- External Link (opens in new tab) -->
<a href="https://github.com/yourusername" target="_blank" rel="noopener noreferrer">
  GitHub
</a>

<!-- CTA Button styled as a link -->
<a href="/contact.html" class="btn">Hire Me</a>

<!-- Email Link -->
<a href="mailto:hello@yourdomain.com">Send an Email</a>

<!-- Phone Link -->
<a href="tel:+923001234567">Call Us</a>

<!-- Download Link -->
<a href="/assets/resume.pdf" download>Download Resume</a>

<!-- Navbar -->
<nav>
  <a href="#home">Home</a>
  <a href="#work">Work</a>
  <a href="#about">About</a>
  <a href="#contact">Contact</a>
</nav>
```

### Key Attributes

| Attribute | Purpose |
|-----------|---------|
| `href` | Destination URL, `#id`, `mailto:`, `tel:`, or file path |
| `target="_blank"` | Open in a new tab |
| `rel="noopener noreferrer"` | Security best practice with `target="_blank"` |
| `download` | Forces the browser to download the linked file |
| `class` | Style it as a button, nav link, etc. |

### Key Rules
- Always add `rel="noopener noreferrer"` when using `target="_blank"` — prevents security exploits
- Don't use `<a href="#">` as a placeholder in production — use `button` or handle with JS
- Links should describe their destination — avoid generic "click here" text (bad for SEO + accessibility)

---

## 🧩 Putting It All Together

```html
<section id="services">

  <h2>What We Do</h2>
  <p>We craft immersive digital experiences that leave a lasting impression.</p>

  <div class="card">
    <h3>Web Design</h3>
    <p>
      Custom, hand-coded websites with zero templates.
      Built for speed, style, and scroll-stopping animations.
    </p>
    <a href="/web-design.html" class="btn">Learn More</a>
  </div>

  <div class="card">
    <h3>Brand Identity</h3>
    <p>
      From logo to color palette — we build brands that
      people remember long after they leave the page.
    </p>
    <a href="/branding.html" class="btn">See Our Work</a>
  </div>

</section>
```

---

## 📌 Quick Summary

| Tag | Purpose | Key Rule |
|-----|---------|----------|
| `<h1>`–`<h6>` | Page & section structure | One `<h1>` per page, don't skip levels |
| `<p>` | Body text & descriptions | No block elements inside, no empty tags |
| `<a>` | Links, CTAs, navigation | Always use `rel` with `target="_blank"` |

---

> **Pro Tip 🚀** — These three tags form the **skeleton of every webpage**. Get them right and your HTML structure, SEO, and accessibility will all be solid by default.