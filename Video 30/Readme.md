# 📱 CSS Media Queries — Complete Reference
### Frontend Domination Course

---

## 📌 What is a Media Query?

A **media query** lets you apply CSS styles **only when certain conditions are true** — like screen width, device type, orientation, or resolution.

Think of it like an `if` statement but for CSS:

```css
/* "If the screen is 600px or smaller, apply this CSS" */
@media (max-width: 600px) {
  body {
    background-color: black;
  }
}
```

---

## 🧱 Basic Syntax

```css
@media media-type and (media-feature) {
  /* CSS rules go here */
}
```

| Part | What it does |
|---|---|
| `@media` | Starts the media query |
| `media-type` | What type of device (screen, print, etc.) |
| `and` | Combines multiple conditions |
| `(media-feature)` | The actual condition (width, height, orientation, etc.) |

---

## 🖥️ Media Types

```css
@media screen { }   /* Screens (phones, laptops, desktops) */
@media print { }    /* When user prints the page */
@media all { }      /* All devices (default if you skip media-type) */
```

> 💡 **99% of the time** you'll just use `screen` or skip the type entirely.

---

## 📐 Media Features (The Conditions)

### 1. `width` and `height`

```css
/* Exact width (rarely used) */
@media (width: 768px) { }

/* Maximum width — applies when screen is <= 768px */
@media (max-width: 768px) { }

/* Minimum width — applies when screen is >= 768px */
@media (min-width: 768px) { }

/* Range — applies between 480px and 768px */
@media (min-width: 480px) and (max-width: 768px) { }
```

### 2. `orientation`

```css
/* Phone held vertically */
@media (orientation: portrait) { }

/* Phone held horizontally / landscape */
@media (orientation: landscape) { }
```

### 3. `resolution` / `device-pixel-ratio`

```css
/* Retina / high-DPI screens */
@media (-webkit-min-device-pixel-ratio: 2),
       (min-resolution: 192dpi) { }
```

### 4. `hover`

```css
/* Device supports hover (mouse) */
@media (hover: hover) {
  .btn:hover {
    background: red;
  }
}

/* Device doesn't support hover (touch screens) */
@media (hover: none) {
  .btn {
    background: red; /* always show the active state */
  }
}
```

### 5. `prefers-color-scheme`

```css
@media (prefers-color-scheme: dark) {
  body {
    background: #0a0a0a;
    color: #ffffff;
  }
}

@media (prefers-color-scheme: light) {
  body {
    background: #ffffff;
    color: #0a0a0a;
  }
}
```

### 6. `prefers-reduced-motion`

```css
/* Respect users who have motion sensitivity */
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## 📏 Standard Breakpoints (Industry Standard)

```css
/* ── Mobile First (recommended) ── */

/* Base styles — Mobile (< 480px) */
/* write your default styles here, no media query needed */

/* Large Mobile */
@media (min-width: 480px) { }

/* Tablet */
@media (min-width: 768px) { }

/* Small Laptop / Large Tablet */
@media (min-width: 1024px) { }

/* Desktop */
@media (min-width: 1280px) { }

/* Large Desktop */
@media (min-width: 1536px) { }
```

---

## 📱 Mobile First vs Desktop First

### ✅ Mobile First (Recommended)
Start with mobile styles, then **add** styles for bigger screens using `min-width`.

```css
/* Base: Mobile */
.container {
  width: 100%;
  padding: 16px;
}

/* Tablet and above */
@media (min-width: 768px) {
  .container {
    width: 720px;
    padding: 24px;
    margin: 0 auto;
  }
}

/* Desktop and above */
@media (min-width: 1280px) {
  .container {
    width: 1200px;
    padding: 40px;
  }
}
```

### Desktop First (Old approach)
Start with desktop styles, then **reduce** for smaller screens using `max-width`.

```css
/* Base: Desktop */
.container {
  width: 1200px;
  margin: 0 auto;
}

/* Tablet */
@media (max-width: 1024px) {
  .container {
    width: 100%;
    padding: 24px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .container {
    padding: 16px;
  }
}
```

> 💡 **Go Mobile First.** Google uses it. It's better for performance and cleaner logic.

---

## 🔗 Combining Conditions with `and`, `or`, `,`

```css
/* AND — both conditions must be true */
@media (min-width: 768px) and (orientation: landscape) {
  /* tablets in landscape only */
}

/* OR — comma = or */
@media (max-width: 480px), (orientation: portrait) {
  /* mobile OR portrait mode */
}

/* NOT — inverts the query */
@media not screen and (max-width: 768px) {
  /* everything EXCEPT small screens */
}
```

---

## 💡 Full HTML + CSS Examples

---

### Example 1 — Responsive Navigation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Responsive Nav</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Poppins, sans-serif;
      background: #0a0a0a;
      color: #ffffff;
    }

    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 40px;
      background: #111111;
    }

    .logo {
      font-size: 22px;
      font-weight: 700;
      color: #ffffff;
    }

    .nav-links {
      display: flex;
      list-style: none;
      gap: 32px;
    }

    .nav-links a {
      color: #aaaaaa;
      text-decoration: none;
      font-size: 14px;
      transition: color 0.3s;
    }

    .nav-links a:hover {
      color: #ffffff;
    }

    .hamburger {
      display: none;          /* hidden on desktop */
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
    }

    .hamburger span {
      width: 28px;
      height: 2px;
      background: #ffffff;
      border-radius: 2px;
    }

    /* ── Mobile ── */
    @media (max-width: 768px) {
      nav {
        padding: 16px 20px;
      }

      .hamburger {
        display: flex;         /* show on mobile */
      }

      .nav-links {
        display: none;         /* hide links on mobile */
        position: absolute;
        top: 64px;
        left: 0;
        width: 100%;
        flex-direction: column;
        background: #111111;
        padding: 24px 20px;
        gap: 20px;
      }

      .nav-links.open {
        display: flex;         /* JS toggles this class */
      }
    }
  </style>
</head>
<body>
  <nav>
    <div class="logo">VROO.</div>
    <ul class="nav-links" id="navLinks">
      <li><a href="#">Home</a></li>
      <li><a href="#">Work</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <div class="hamburger" onclick="document.getElementById('navLinks').classList.toggle('open')">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </nav>
</body>
</html>
```

---

### Example 2 — Responsive Card Grid

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Card Grid</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Poppins, sans-serif;
      background: #f5f5f5;
      padding: 40px 20px;
    }

    .grid {
      display: grid;
      gap: 20px;

      /* Mobile: 1 column */
      grid-template-columns: 1fr;
    }

    /* Tablet: 2 columns */
    @media (min-width: 600px) {
      .grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    /* Desktop: 3 columns */
    @media (min-width: 1024px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
        max-width: 1200px;
        margin: 0 auto;
      }
    }

    .card {
      background: #ffffff;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    }

    .card-img {
      width: 100%;
      height: 200px;
      background: #d0d0d0;
      object-fit: cover;
    }

    .card-body {
      padding: 20px;
    }

    .card-title {
      font-size: 18px;
      font-weight: 600;
      margin-bottom: 8px;
      color: #111111;
    }

    .card-text {
      font-size: 14px;
      color: #666666;
      line-height: 1.6;
    }

    /* Mobile only: card layout changes to horizontal */
    @media (max-width: 599px) {
      .card {
        display: flex;
        flex-direction: row;
      }

      .card-img {
        width: 120px;
        height: auto;
        flex-shrink: 0;
      }
    }
  </style>
</head>
<body>
  <div class="grid">
    <div class="card">
      <img class="card-img" src="https://picsum.photos/400/200?random=1" alt="Card" />
      <div class="card-body">
        <h3 class="card-title">Project KULT</h3>
        <p class="card-text">Streetwear drop page with pinned scroll animations.</p>
      </div>
    </div>
    <div class="card">
      <img class="card-img" src="https://picsum.photos/400/200?random=2" alt="Card" />
      <div class="card-body">
        <h3 class="card-title">Project PETALS</h3>
        <p class="card-text">Luxury skincare with horizontal scroll experience.</p>
      </div>
    </div>
    <div class="card">
      <img class="card-img" src="https://picsum.photos/400/200?random=3" alt="Card" />
      <div class="card-body">
        <h3 class="card-title">Project VOID</h3>
        <p class="card-text">Web3 neon dark theme NFT marketplace.</p>
      </div>
    </div>
  </div>
</body>
</html>
```

---

### Example 3 — Responsive Hero Section

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Hero Section</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Poppins, sans-serif;
      background: #0a0a0a;
      color: #ffffff;
    }

    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      padding: 40px 20px;
      text-align: center;          /* mobile: centered */
      flex-direction: column;
      justify-content: center;
      gap: 24px;
    }

    .hero-tag {
      font-size: 11px;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: #888888;
    }

    .hero-title {
      font-size: clamp(36px, 8vw, 96px);  /* fluid font sizing */
      font-weight: 800;
      line-height: 1.05;
    }

    .hero-title span {
      color: transparent;
      -webkit-text-stroke: 1px #ffffff;
    }

    .hero-desc {
      font-size: clamp(14px, 2vw, 18px);
      color: #888888;
      max-width: 500px;
      line-height: 1.7;
    }

    .hero-btn {
      display: inline-block;
      padding: 14px 36px;
      background: #ffffff;
      color: #0a0a0a;
      font-size: 14px;
      font-weight: 600;
      text-decoration: none;
      border-radius: 4px;
    }

    /* Tablet and up: left-aligned split layout */
    @media (min-width: 768px) {
      .hero {
        flex-direction: row;
        text-align: left;
        padding: 60px 60px;
        justify-content: space-between;
      }

      .hero-content {
        max-width: 55%;
      }

      .hero-visual {
        width: 360px;
        height: 360px;
        border-radius: 50%;
        background: linear-gradient(135deg, #1a1a1a, #333333);
        flex-shrink: 0;
      }
    }

    /* Desktop */
    @media (min-width: 1280px) {
      .hero {
        padding: 0 120px;
        max-width: 1440px;
        margin: 0 auto;
      }

      .hero-visual {
        width: 480px;
        height: 480px;
      }
    }
  </style>
</head>
<body>
  <section class="hero">
    <div class="hero-content">
      <p class="hero-tag">Frontend Developer</p>
      <h1 class="hero-title">not your <span>vibe</span> coder.</h1>
      <p class="hero-desc">
        Building cinematic web experiences that hit different.
        GSAP. ScrollTrigger. Pure CSS. No frameworks.
      </p>
      <a class="hero-btn" href="#">View Work</a>
    </div>
    <div class="hero-visual"></div>
  </section>
</body>
</html>
```

---

### Example 4 — Responsive Typography with `clamp()`

```css
/*
  clamp(MIN, PREFERRED, MAX)
  — no media query needed for fluid type!
*/

h1 {
  font-size: clamp(28px, 5vw, 72px);
}

h2 {
  font-size: clamp(22px, 3.5vw, 48px);
}

p {
  font-size: clamp(14px, 1.5vw, 18px);
}

.hero-padding {
  padding: clamp(20px, 5vw, 100px);
}
```

> 💡 `clamp()` is like a media query for a single property. Use it for font sizes, padding, gaps.

---

### Example 5 — Responsive Flexbox Layout

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Flex Layout</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Poppins, sans-serif;
    }

    .section {
      display: flex;
      gap: 40px;
      padding: 60px 20px;
      align-items: center;

      /* Mobile: stack vertically */
      flex-direction: column;
    }

    .section-img {
      width: 100%;
      max-width: 400px;
      aspect-ratio: 4 / 3;
      background: #dddddd;
      border-radius: 12px;
    }

    .section-text {
      flex: 1;
    }

    .section-text h2 {
      font-size: 32px;
      margin-bottom: 16px;
    }

    .section-text p {
      font-size: 16px;
      color: #555555;
      line-height: 1.8;
    }

    /* Tablet+: side by side */
    @media (min-width: 768px) {
      .section {
        flex-direction: row;
        padding: 80px 60px;
      }

      .section-img {
        width: 45%;
        max-width: none;
      }
    }

    /* Reverse layout for even sections */
    .section.reverse {
      flex-direction: column;
    }

    @media (min-width: 768px) {
      .section.reverse {
        flex-direction: row-reverse;
      }
    }
  </style>
</head>
<body>
  <div class="section">
    <div class="section-img"></div>
    <div class="section-text">
      <h2>Design First</h2>
      <p>Every pixel is a decision. Build layouts that breathe, move, and feel alive. Mobile first, always.</p>
    </div>
  </div>

  <div class="section reverse">
    <div class="section-img"></div>
    <div class="section-text">
      <h2>Code Second</h2>
      <p>Clean semantic HTML. No framework crutches. Just you, CSS, and a vision.</p>
    </div>
  </div>
</body>
</html>
```

---

## 🧠 The `<meta viewport>` Tag — Don't Forget This!

```html
<!-- ALWAYS put this in your <head> -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Without this tag, mobile browsers will zoom out and render your site like a desktop page. **Media queries won't work properly without it.**

---

## ⚡ Quick Reference Cheat Sheet

```css
/* ── Breakpoints ── */
@media (max-width: 480px) { }   /* Small mobile */
@media (max-width: 768px) { }   /* Mobile / tablet */
@media (min-width: 768px) { }   /* Tablet and up */
@media (min-width: 1024px) { }  /* Laptop and up */
@media (min-width: 1280px) { }  /* Desktop */

/* ── Orientation ── */
@media (orientation: portrait) { }
@media (orientation: landscape) { }

/* ── User Preferences ── */
@media (prefers-color-scheme: dark) { }
@media (prefers-color-scheme: light) { }
@media (prefers-reduced-motion: reduce) { }

/* ── High DPI / Retina ── */
@media (-webkit-min-device-pixel-ratio: 2) { }
@media (min-resolution: 192dpi) { }

/* ── Combining ── */
@media (min-width: 768px) and (max-width: 1024px) { } /* Tablet range only */
@media (max-width: 600px), (orientation: portrait) { } /* OR */
```

---

## 🎯 Common Mistakes to Avoid

| ❌ Mistake | ✅ Fix |
|---|---|
| Forgetting `<meta viewport>` | Always add it in `<head>` |
| Using `px` only for font sizes | Use `clamp()` or `rem` |
| Writing desktop styles first | Write mobile styles first |
| Too many breakpoints | Stick to 3–4 max |
| Relying on device-specific breakpoints | Use content-based breakpoints |
| Not testing on real mobile | Use DevTools + actual phone |

---

## 📖 Summary

- Media queries = **conditional CSS**
- Always add `<meta viewport>` tag
- **Mobile first** → use `min-width`
- **Desktop first** → use `max-width`
- Use `clamp()` for fluid typography
- Combine conditions with `and` / `,`
- Use `prefers-color-scheme` for dark mode
- Use `prefers-reduced-motion` for accessibility

---
