# 🚀 SEO & Core Web Vitals in HTML
> A complete, hand-coded reference guide for frontend developers — covering everything from semantic structure to performance metrics, zero frameworks, zero fluff.

---

## 📋 Table of Contents

1. [What is SEO?](#what-is-seo)
2. [HTML Document Structure for SEO](#html-document-structure-for-seo)
3. [Essential Meta Tags](#essential-meta-tags)
4. [Open Graph & Social Meta Tags](#open-graph--social-meta-tags)
5. [Semantic HTML Elements](#semantic-html-elements)
6. [Heading Hierarchy](#heading-hierarchy)
7. [Image Optimization for SEO](#image-optimization-for-seo)
8. [Links & Anchor Tags](#links--anchor-tags)
9. [Structured Data (Schema.org)](#structured-data-schemaorg)
10. [Core Web Vitals Overview](#core-web-vitals-overview)
11. [LCP – Largest Contentful Paint](#lcp--largest-contentful-paint)
12. [INP – Interaction to Next Paint](#inp--interaction-to-next-paint)
13. [CLS – Cumulative Layout Shift](#cls--cumulative-layout-shift)
14. [Performance HTML Techniques](#performance-html-techniques)
15. [Resource Hints](#resource-hints)
16. [Accessibility & SEO Overlap](#accessibility--seo-overlap)
17. [Mobile SEO](#mobile-seo)
18. [Checklist](#-full-checklist)

---

## What is SEO?

**Search Engine Optimization (SEO)** is the practice of structuring your HTML and content so search engines like Google can:

- **Crawl** — discover and read your pages
- **Index** — store and categorize your content
- **Rank** — surface your page for relevant queries

Good HTML is the foundation. No plugin, no tool, no shortcut replaces well-structured markup.

---

## HTML Document Structure for SEO

Every SEO-optimized page starts with a clean, valid HTML5 skeleton.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />

  <title>Page Title – Brand Name</title>
  <meta name="description" content="A concise, compelling summary of this page — ideally 150–160 characters." />
  <link rel="canonical" href="https://yourdomain.com/page-slug" />

  <!-- Favicon -->
  <link rel="icon" href="/favicon.ico" type="image/x-icon" />
  <link rel="apple-touch-icon" href="/apple-touch-icon.png" />
</head>
<body>

  <!-- Semantic page structure -->
  <header>...</header>
  <nav>...</nav>
  <main>
    <article>...</article>
    <aside>...</aside>
  </main>
  <footer>...</footer>

</body>
</html>
```

### Key Rules
| Element | SEO Importance | Notes |
|---|---|---|
| `<html lang="">` | ✅ High | Helps Google serve correct language |
| `<title>` | ✅ Critical | Shown in SERPs; keep 50–60 chars |
| `<meta description>` | ✅ High | Shown in SERPs; keep 150–160 chars |
| `<link rel="canonical">` | ✅ Critical | Prevents duplicate content penalties |
| `<meta charset>` | ✅ Required | UTF-8 ensures special chars render correctly |

---

## Essential Meta Tags

```html
<!-- Core SEO -->
<title>How to Build Scroll Animations – Not Your Vibe Coder</title>
<meta name="description" content="Step-by-step guide on building cinematic scroll animations using GSAP and ScrollTrigger. Hand-coded, no templates." />
<meta name="keywords" content="GSAP, scroll animations, frontend, HTML, CSS, JavaScript" />
<meta name="author" content="Not Your Vibe Coder" />
<meta name="robots" content="index, follow" />

<!-- Canonical URL — always self-reference on every page -->
<link rel="canonical" href="https://notyourvibecoder.com/gsap-scroll-guide" />

<!-- Prevent indexing (use only on private/staging pages) -->
<!-- <meta name="robots" content="noindex, nofollow" /> -->
```

### `robots` Meta Directives

| Value | Meaning |
|---|---|
| `index, follow` | Default — crawl this page and follow its links |
| `noindex, follow` | Don't rank this page but follow links |
| `noindex, nofollow` | Completely block this page from Google |
| `noarchive` | Don't show cached version in search results |

---

## Open Graph & Social Meta Tags

Open Graph controls how your page appears when shared on WhatsApp, LinkedIn, Twitter/X, Snapchat, etc.

```html
<!-- Open Graph (Facebook, WhatsApp, LinkedIn) -->
<meta property="og:type" content="website" />
<meta property="og:title" content="Page Title Here" />
<meta property="og:description" content="Page description — same as meta description is fine." />
<meta property="og:image" content="https://yourdomain.com/og-image.jpg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:url" content="https://yourdomain.com/page-slug" />
<meta property="og:site_name" content="Not Your Vibe Coder" />
<meta property="og:locale" content="en_US" />

<!-- Twitter / X Cards -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="Page Title Here" />
<meta name="twitter:description" content="Page description here." />
<meta name="twitter:image" content="https://yourdomain.com/twitter-card.jpg" />
<meta name="twitter:site" content="@yourhandle" />
<meta name="twitter:creator" content="@yourhandle" />
```

### OG Image Specs
| Platform | Recommended Size | Aspect Ratio |
|---|---|---|
| Facebook / WhatsApp | 1200 × 630px | 1.91:1 |
| Twitter / X | 1200 × 628px | ~1.91:1 |
| LinkedIn | 1200 × 627px | ~1.91:1 |

---

## Semantic HTML Elements

Semantic tags tell search engines **what your content means**, not just what it looks like.

```html
<body>

  <!-- Site-wide header — logo, nav, CTA -->
  <header>
    <a href="/" aria-label="Home">
      <img src="/logo.svg" alt="Not Your Vibe Coder Logo" width="160" height="40" />
    </a>
    <nav aria-label="Main Navigation">
      <ul>
        <li><a href="/work">Work</a></li>
        <li><a href="/tutorials">Tutorials</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <!-- Main content — only ONE <main> per page -->
  <main id="main-content">

    <!-- Self-contained piece of content -->
    <article>
      <h1>Building a Cinematic Scroll Website from Scratch</h1>
      <p>Published on <time datetime="2025-04-19">April 19, 2025</time></p>
      <p>Learn how to combine GSAP, ScrollTrigger, and Locomotive Scroll...</p>

      <!-- Logical section within content -->
      <section aria-labelledby="setup-heading">
        <h2 id="setup-heading">Project Setup</h2>
        <p>...</p>
      </section>
    </article>

    <!-- Related / supplemental content -->
    <aside aria-label="Related Tutorials">
      <h2>You Might Also Like</h2>
      <ul>...</ul>
    </aside>

  </main>

  <!-- Site-wide footer -->
  <footer>
    <p>&copy; 2025 Not Your Vibe Coder</p>
  </footer>

</body>
```

### Semantic Elements Reference

| Tag | Use Case |
|---|---|
| `<header>` | Site-wide or section header |
| `<nav>` | Navigation links |
| `<main>` | Primary page content (one per page) |
| `<article>` | Standalone content (blog post, tutorial) |
| `<section>` | Thematic grouping within an article/page |
| `<aside>` | Sidebar / tangentially related content |
| `<footer>` | Site-wide or section footer |
| `<figure>` + `<figcaption>` | Images with captions |
| `<time datetime="">` | Dates/times machine-readable |
| `<address>` | Contact info for nearest `<article>` or `<body>` |

---

## Heading Hierarchy

Google reads your headings to understand page structure. **Only one `<h1>` per page.**

```html
<h1>GSAP Scroll Animations – Complete Guide</h1>       <!-- Page topic — only ONE -->

  <h2>What is GSAP?</h2>                               <!-- Major section -->
    <h3>GSAP vs CSS Animations</h3>                    <!-- Subsection -->
    <h3>When to Use ScrollTrigger</h3>

  <h2>Setting Up Your Project</h2>
    <h3>Linking GSAP via CDN</h3>
      <h4>Using a Specific Version</h4>                <!-- Sub-subsection -->
    <h3>File Structure</h3>

  <h2>Building Your First Animation</h2>
```

### Heading Rules
- ❌ Never skip levels (h1 → h3 skipping h2)
- ❌ Never use headings just for font size — use CSS for styling
- ✅ Include your primary keyword naturally in `<h1>`
- ✅ Use `<h2>` for major sections that support the h1 topic
- ✅ Keep headings descriptive and concise

---

## Image Optimization for SEO

```html
<!-- ✅ Optimized image -->
<img
  src="/images/gsap-scrolltrigger-demo.webp"
  alt="GSAP ScrollTrigger pinned section demo on a dark background"
  width="1200"
  height="675"
  loading="lazy"
  decoding="async"
  fetchpriority="low"
/>

<!-- ✅ Hero / above-the-fold image — do NOT lazy load -->
<img
  src="/images/hero-banner.webp"
  alt="Cinematic scroll website hero section with golden particle effects"
  width="1920"
  height="1080"
  loading="eager"
  fetchpriority="high"
  decoding="sync"
/>

<!-- ✅ Responsive images with srcset -->
<img
  src="/images/project-card.webp"
  srcset="
    /images/project-card-480.webp 480w,
    /images/project-card-800.webp 800w,
    /images/project-card-1200.webp 1200w
  "
  sizes="(max-width: 600px) 480px, (max-width: 1024px) 800px, 1200px"
  alt="KULT streetwear drop page — GSAP scroll storytelling project"
  width="1200"
  height="675"
  loading="lazy"
/>

<!-- ✅ Decorative images — empty alt, so screen readers skip it -->
<img src="/icons/divider.svg" alt="" role="presentation" />

<!-- ✅ Figure with caption (good for blog/tutorial images) -->
<figure>
  <img src="/images/locomotive-demo.webp" alt="Locomotive Scroll smooth scrolling demo" width="900" height="500" loading="lazy" />
  <figcaption>Locomotive Scroll v4 integrated with GSAP ScrollTrigger</figcaption>
</figure>
```

### Image Format Guide

| Format | Best For | Transparency | Animation |
|---|---|---|---|
| `.webp` | ✅ All web images | ✅ Yes | ✅ Yes |
| `.avif` | ✅ Highest compression | ✅ Yes | ❌ Limited |
| `.svg` | ✅ Icons, logos, illustrations | ✅ Yes | ✅ Via CSS |
| `.jpg` | Photos (legacy fallback) | ❌ No | ❌ No |
| `.png` | Legacy transparency | ✅ Yes | ❌ No |

---

## Links & Anchor Tags

```html
<!-- ✅ Internal link — descriptive anchor text -->
<a href="/tutorials/gsap-scroll">Learn GSAP ScrollTrigger from scratch</a>

<!-- ❌ Bad anchor text — tells Google nothing -->
<a href="/tutorials/gsap-scroll">Click here</a>

<!-- ✅ External link — noopener for security, noreferrer for privacy -->
<a href="https://gsap.com" target="_blank" rel="noopener noreferrer">GSAP Official Site</a>

<!-- ✅ Sponsored / paid links — tell Google it's an ad -->
<a href="https://partner.com" rel="sponsored">Check out our partner</a>

<!-- ✅ User-generated content (forum posts, comments) -->
<a href="https://usersite.com" rel="ugc">User's website</a>

<!-- ✅ Tell Google NOT to follow this link -->
<a href="https://internal-only.com" rel="nofollow">Internal Resource</a>

<!-- ✅ Skip navigation link (accessibility + SEO) -->
<a href="#main-content" class="skip-link">Skip to main content</a>
```

### `rel` Attribute Reference

| Value | Use Case |
|---|---|
| `noopener noreferrer` | External links opening in new tab |
| `nofollow` | Links you don't want to endorse |
| `sponsored` | Paid/affiliate links |
| `ugc` | User-generated content |
| `canonical` | On `<link>` tag to declare canonical URL |

---

## Structured Data (Schema.org)

Structured data gives Google rich context — can unlock **rich results** in SERPs (star ratings, breadcrumbs, FAQs, etc.).

```html
<!-- JSON-LD in <head> or before </body> — Google prefers JSON-LD -->

<!-- Website Schema -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Not Your Vibe Coder",
  "url": "https://notyourvibecoder.com",
  "description": "Hand-coded, animation-heavy websites and frontend tutorials.",
  "author": {
    "@type": "Person",
    "name": "Not Your Vibe Coder"
  }
}
</script>

<!-- Article / Tutorial Blog Post Schema -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Building a Cinematic Scroll Website with GSAP",
  "description": "A complete guide to hand-coding scroll animations using GSAP and ScrollTrigger.",
  "image": "https://notyourvibecoder.com/images/gsap-guide-og.jpg",
  "author": {
    "@type": "Person",
    "name": "Not Your Vibe Coder",
    "url": "https://notyourvibecoder.com"
  },
  "datePublished": "2025-04-19",
  "dateModified": "2025-04-19",
  "publisher": {
    "@type": "Organization",
    "name": "Not Your Vibe Coder",
    "logo": {
      "@type": "ImageObject",
      "url": "https://notyourvibecoder.com/logo.png"
    }
  }
}
</script>

<!-- FAQ Schema — unlocks collapsible FAQ in Google results -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is GSAP ScrollTrigger?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "ScrollTrigger is a GSAP plugin that lets you trigger animations based on the user's scroll position."
      }
    },
    {
      "@type": "Question",
      "name": "Do I need a bundler to use GSAP?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. GSAP works perfectly via CDN with no build tools required."
      }
    }
  ]
}
</script>

<!-- Breadcrumb Schema -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://notyourvibecoder.com" },
    { "@type": "ListItem", "position": 2, "name": "Tutorials", "item": "https://notyourvibecoder.com/tutorials" },
    { "@type": "ListItem", "position": 3, "name": "GSAP Scroll Guide", "item": "https://notyourvibecoder.com/tutorials/gsap-scroll" }
  ]
}
</script>
```

---

## Core Web Vitals Overview

Core Web Vitals are Google's real-user experience metrics that **directly affect search rankings** as of 2021+.

| Metric | What It Measures | Good | Needs Work | Poor |
|---|---|---|---|---|
| **LCP** | Largest Contentful Paint — loading speed | ≤ 2.5s | 2.5–4.0s | > 4.0s |
| **INP** | Interaction to Next Paint — responsiveness | ≤ 200ms | 200–500ms | > 500ms |
| **CLS** | Cumulative Layout Shift — visual stability | ≤ 0.1 | 0.1–0.25 | > 0.25 |

> **INP replaced FID (First Input Delay) as an official Core Web Vital in March 2024.**

You can measure them using:
- [Google PageSpeed Insights](https://pagespeed.web.dev)
- Chrome DevTools → Lighthouse tab
- Chrome DevTools → Performance tab
- [web.dev/measure](https://web.dev/measure)
- Chrome User Experience Report (CrUX)

---

## LCP – Largest Contentful Paint

LCP measures **how fast the largest visible element** (hero image, heading, video poster) loads.

### Common LCP Elements
- `<img>` (especially hero images)
- `<video>` poster image
- Block-level element with a CSS background image
- Large `<h1>` text block

### HTML Optimizations for LCP

```html
<!-- ✅ 1. Preload your LCP image — most impactful fix -->
<link rel="preload" as="image" href="/images/hero.webp" fetchpriority="high" />

<!-- ✅ 2. Mark the LCP image as high priority -->
<img
  src="/images/hero.webp"
  alt="Hero image"
  width="1920"
  height="1080"
  fetchpriority="high"
  loading="eager"
  decoding="sync"
/>

<!-- ✅ 3. Never lazy-load the LCP element -->
<!-- ❌ BAD — adds delay to the most important image -->
<img src="/images/hero.webp" loading="lazy" />

<!-- ✅ 4. Use <picture> for WebP with JPEG fallback -->
<picture>
  <source srcset="/images/hero.avif" type="image/avif" />
  <source srcset="/images/hero.webp" type="image/webp" />
  <img src="/images/hero.jpg" alt="Hero" width="1920" height="1080" fetchpriority="high" loading="eager" />
</picture>

<!-- ✅ 5. Inline critical CSS for above-the-fold content -->
<style>
  /* Only styles needed to render the hero section */
  body { margin: 0; font-family: 'Poppins', sans-serif; background: #0a0a0a; }
  .hero { width: 100%; height: 100svh; position: relative; overflow: hidden; }
  .hero__img { width: 100%; height: 100%; object-fit: cover; }
</style>

<!-- ✅ 6. Preconnect to font or image CDN origin -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
```

### LCP Killers to Avoid
- ❌ Lazy-loading the hero image
- ❌ Loading fonts without `font-display: swap`
- ❌ Render-blocking `<script>` tags before content
- ❌ Large uncompressed images (use WebP/AVIF)
- ❌ No `width`/`height` on images (causes layout recalcs)

---

## INP – Interaction to Next Paint

INP measures the **delay between user interaction** (click, tap, keypress) **and the next visual update**. It replaced FID in March 2024.

### HTML Techniques That Help INP

```html
<!-- ✅ 1. Defer non-critical JavaScript -->
<script src="/js/animations.js" defer></script>
<script src="/js/analytics.js" defer></script>

<!-- ✅ 2. Async for truly independent scripts -->
<script src="/js/chat-widget.js" async></script>

<!-- ✅ 3. Never block parsing with scripts in <head> without defer/async -->
<!-- ❌ BAD — blocks HTML parsing -->
<head>
  <script src="/js/app.js"></script>
</head>

<!-- ✅ GOOD -->
<head>
  <script src="/js/app.js" defer></script>
</head>

<!-- ✅ 4. Use native HTML elements for interactivity (faster than JS) -->
<!-- Native <button> has built-in keyboard, focus, and event handling -->
<button type="button" id="open-menu">Menu</button>

<!-- ✅ 5. Mark time-sensitive visual updates with a loading state -->
<button
  type="button"
  aria-busy="false"
  aria-label="Submit form"
  id="submit-btn"
>
  Submit
</button>

<!-- ✅ 6. Load third-party scripts last -->
<!-- Analytics, chat widgets, ad scripts — always at end of <body> -->
<body>
  <!-- All your content first -->

  <!-- Third-party last -->
  <script src="https://www.googletagmanager.com/gtag/js" async></script>
</body>
```

### Script Loading Reference

| Attribute | Behavior | Use When |
|---|---|---|
| _(none)_ | Blocks HTML parsing | Never — unless inline critical JS |
| `async` | Downloads in parallel, executes immediately | Independent scripts (analytics) |
| `defer` | Downloads in parallel, executes after DOM | Most app scripts |
| `type="module"` | Deferred by default + strict mode | ES modules |

---

## CLS – Cumulative Layout Shift

CLS measures **unexpected layout jumps** — elements moving around after the page loads. Very annoying UX and bad for rankings.

### HTML Fixes for CLS

```html
<!-- ✅ 1. ALWAYS set width and height on images — this reserves space -->
<img src="/images/card.webp" alt="Project card" width="600" height="400" loading="lazy" />

<!-- ❌ BAD — no dimensions = layout shift when image loads -->
<img src="/images/card.webp" alt="Project card" loading="lazy" />

<!-- ✅ 2. Reserve space for video -->
<video
  width="1280"
  height="720"
  autoplay
  muted
  loop
  playsinline
  poster="/images/video-poster.webp"
>
  <source src="/video/hero.webm" type="video/webm" />
  <source src="/video/hero.mp4" type="video/mp4" />
</video>

<!-- ✅ 3. Reserve space for iframes (embeds, maps) -->
<!-- Use CSS aspect-ratio or explicit dimensions -->
<div style="aspect-ratio: 16/9; width: 100%;">
  <iframe
    src="https://www.youtube.com/embed/VIDEO_ID"
    width="560"
    height="315"
    loading="lazy"
    allowfullscreen
    title="GSAP Tutorial Video"
    style="width: 100%; height: 100%; border: none;"
  ></iframe>
</div>

<!-- ✅ 4. Font loading — use font-display: swap to prevent invisible text -->
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
<!-- The "display=swap" parameter applies font-display: swap automatically -->

<!-- ✅ 5. Avoid injecting content above existing content -->
<!-- If you show a cookie banner or notification, use position: fixed -->
<!-- so it doesn't push existing content down -->
<div
  id="cookie-banner"
  role="dialog"
  aria-label="Cookie consent"
  style="position: fixed; bottom: 0; left: 0; right: 0;"
>
  We use cookies. <button>Accept</button>
</div>
```

### CLS Causes & Fixes

| Cause | Fix |
|---|---|
| Images without dimensions | Add `width` and `height` attributes |
| Dynamically injected banners/ads | Use `position: fixed` or reserve space with `min-height` |
| Fonts causing FOUT | Use `font-display: swap` |
| Embeds without dimensions | Wrap in `aspect-ratio` container |
| Animations moving layout elements | Use `transform` and `opacity` only (composited layers) |

---

## Performance HTML Techniques

### Script & Style Loading Order

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- 1. Critical inline CSS (above-the-fold styles only) -->
  <style>
    body { margin: 0; background: #0a0a0a; color: #fff; }
    .hero { height: 100svh; }
  </style>

  <!-- 2. Preconnect to critical origins -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link rel="preconnect" href="https://cdnjs.cloudflare.com" />

  <!-- 3. Preload critical resources -->
  <link rel="preload" as="image" href="/images/hero.webp" fetchpriority="high" />
  <link rel="preload" as="font" href="/fonts/Poppins-Regular.woff2" type="font/woff2" crossorigin />

  <!-- 4. Non-critical stylesheet (loaded async via JS trick) -->
  <link rel="stylesheet" href="/css/styles.css" media="print" onload="this.media='all'" />
  <noscript><link rel="stylesheet" href="/css/styles.css" /></noscript>

  <!-- 5. Deferred scripts -->
  <script src="/js/gsap.min.js" defer></script>
  <script src="/js/main.js" defer></script>
</head>
```

### Lazy Loading

```html
<!-- Images below the fold -->
<img src="/images/section-2.webp" alt="Section 2 visual" width="800" height="450" loading="lazy" decoding="async" />

<!-- Native lazy load for iframes -->
<iframe src="https://maps.google.com/..." loading="lazy" title="Location map"></iframe>
```

---

## Resource Hints

Resource hints tell the browser to prepare connections or fetch files **before they're needed**.

```html
<head>
  <!-- dns-prefetch: Resolve DNS early for third-party domains -->
  <link rel="dns-prefetch" href="https://www.googletagmanager.com" />
  <link rel="dns-prefetch" href="https://cdnjs.cloudflare.com" />

  <!-- preconnect: Full connection (DNS + TCP + TLS) for critical origins -->
  <!-- Only use for 2–3 most critical third-party origins -->
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link rel="preconnect" href="https://cdnjs.cloudflare.com" />

  <!-- preload: Fetch this resource ASAP at high priority -->
  <!-- Use for: hero images, critical fonts, above-fold CSS/JS -->
  <link rel="preload" as="image" href="/images/hero.webp" fetchpriority="high" />
  <link rel="preload" as="font" href="/fonts/Poppins-Bold.woff2" type="font/woff2" crossorigin />
  <link rel="preload" as="script" href="/js/gsap.min.js" />

  <!-- prefetch: Fetch a likely next-page resource at low priority -->
  <!-- Use for pages the user will probably visit next -->
  <link rel="prefetch" href="/tutorials/locomotive-scroll" />

  <!-- prerender: Fully render a likely next page in background (expensive) -->
  <!-- Only use if you're very confident user will navigate there -->
  <link rel="prerender" href="/work" />
</head>
```

### Resource Hints Comparison

| Hint | Connection | Fetch | Priority | Use Case |
|---|---|---|---|---|
| `dns-prefetch` | DNS only | ❌ | Low | Analytics, font CDNs |
| `preconnect` | DNS + TCP + TLS | ❌ | Medium | Critical CDNs |
| `preload` | ✅ | ✅ | **High** | Hero image, critical font |
| `prefetch` | ✅ | ✅ | Low | Next-page resources |
| `prerender` | ✅ | ✅ Full render | Lowest | Very confident next page |

---

## Accessibility & SEO Overlap

Accessibility and SEO are deeply connected — Google's crawler is essentially a screen reader.

```html
<!-- ✅ ARIA labels for non-obvious interactive elements -->
<button type="button" aria-label="Open mobile navigation menu">
  <!-- SVG hamburger icon — no visible text -->
  <svg viewBox="0 0 24 24" width="24" height="24" aria-hidden="true">
    <line x1="3" y1="6" x2="21" y2="6" stroke="currentColor" stroke-width="2"/>
    <line x1="3" y1="12" x2="21" y2="12" stroke="currentColor" stroke-width="2"/>
    <line x1="3" y1="18" x2="21" y2="18" stroke="currentColor" stroke-width="2"/>
  </svg>
</button>

<!-- ✅ landmark roles for navigation -->
<nav aria-label="Main Navigation">...</nav>
<nav aria-label="Footer Navigation">...</nav>

<!-- ✅ Skip link for keyboard users -->
<a href="#main-content" class="skip-link">Skip to main content</a>
<main id="main-content">...</main>

<!-- ✅ aria-current for active nav link -->
<nav>
  <ul>
    <li><a href="/" aria-current="page">Home</a></li>
    <li><a href="/work">Work</a></li>
  </ul>
</nav>

<!-- ✅ Language attribute on inline foreign language content -->
<p>The word <span lang="ur">خوش آمدید</span> means "welcome."</p>

<!-- ✅ Accessible form labels (Google reads forms too) -->
<label for="email-input">Email Address</label>
<input
  type="email"
  id="email-input"
  name="email"
  placeholder="you@example.com"
  autocomplete="email"
  required
  aria-describedby="email-hint"
/>
<span id="email-hint">We'll never share your email.</span>

<!-- ✅ Table with proper headers (Google can read data tables) -->
<table>
  <caption>GSAP Animation Comparison</caption>
  <thead>
    <tr>
      <th scope="col">Method</th>
      <th scope="col">Use Case</th>
      <th scope="col">Performance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>gsap.to()</td>
      <td>Animate to values</td>
      <td>⚡ Excellent</td>
    </tr>
  </tbody>
</table>
```

---

## Mobile SEO

```html
<!-- ✅ Viewport meta — required for mobile ranking -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />

<!-- ✅ Theme color — affects browser chrome on mobile -->
<meta name="theme-color" content="#0a0a0a" />
<meta name="theme-color" content="#ffffff" media="(prefers-color-scheme: light)" />

<!-- ✅ PWA manifest for installability signals -->
<link rel="manifest" href="/manifest.json" />

<!-- ✅ Apple-specific mobile meta -->
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
<meta name="apple-mobile-web-app-title" content="Not Your Vibe Coder" />
<link rel="apple-touch-icon" href="/icons/apple-touch-icon.png" />

<!-- ✅ Responsive images for mobile bandwidth -->
<img
  src="/images/hero-mobile.webp"
  srcset="
    /images/hero-mobile.webp 480w,
    /images/hero-tablet.webp 768w,
    /images/hero-desktop.webp 1200w
  "
  sizes="(max-width: 480px) 480px, (max-width: 768px) 768px, 1200px"
  alt="Hero section"
  width="1200"
  height="675"
  loading="eager"
  fetchpriority="high"
/>
```

### Mobile SEO Checklist
- ✅ Viewport meta tag set
- ✅ No horizontal scroll on small screens
- ✅ Touch targets are at least 44×44px
- ✅ Font size minimum 16px to prevent auto-zoom on iOS
- ✅ Images are responsive with `srcset`
- ✅ No interstitials that block content on mobile

---

## ✅ Full Checklist

### Document & Meta
- [ ] `<!DOCTYPE html>` declared
- [ ] `<html lang="en">` set with correct language
- [ ] Unique `<title>` on every page (50–60 chars)
- [ ] Unique `<meta name="description">` (150–160 chars)
- [ ] `<link rel="canonical">` on every page
- [ ] `<meta name="robots" content="index, follow">`
- [ ] Favicon and Apple touch icon linked

### Open Graph & Social
- [ ] `og:title`, `og:description`, `og:image`, `og:url`, `og:type`
- [ ] `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`
- [ ] OG image is 1200×630px

### Semantic HTML
- [ ] Only one `<h1>` per page
- [ ] Logical heading hierarchy (h1 → h2 → h3)
- [ ] `<header>`, `<main>`, `<nav>`, `<footer>` used correctly
- [ ] `<article>` for standalone content, `<section>` for thematic groups
- [ ] `<time datetime="">` for all dates

### Images
- [ ] All images have descriptive `alt` text
- [ ] Decorative images have `alt=""`
- [ ] All images have `width` and `height` attributes
- [ ] Hero image has `loading="eager"` and `fetchpriority="high"`
- [ ] Below-fold images have `loading="lazy"` and `decoding="async"`
- [ ] Using WebP or AVIF format
- [ ] `srcset` used for responsive images

### Performance & Core Web Vitals
- [ ] LCP image is preloaded with `<link rel="preload">`
- [ ] No `loading="lazy"` on LCP element
- [ ] All scripts use `defer` or `async`
- [ ] Critical CSS is inlined in `<head>`
- [ ] Fonts use `font-display: swap`
- [ ] `preconnect` to critical third-party origins
- [ ] No layout shifts from images, fonts, or injected banners

### Structured Data
- [ ] WebSite or Person schema in `<head>`
- [ ] Article schema on blog/tutorial pages
- [ ] BreadcrumbList schema on deep pages
- [ ] FAQ schema where applicable
- [ ] Validated with [Google Rich Results Test](https://search.google.com/test/rich-results)

### Accessibility & Mobile
- [ ] Skip link present
- [ ] All interactive elements have accessible labels
- [ ] `aria-label` on icon-only buttons
- [ ] `<meta name="viewport">` set
- [ ] Touch targets ≥ 44×44px
- [ ] No horizontal scroll on mobile

---

## 📚 Resources

| Resource | URL |
|---|---|
| Google Search Central | https://developers.google.com/search |
| PageSpeed Insights | https://pagespeed.web.dev |
| Rich Results Test | https://search.google.com/test/rich-results |
| Schema.org Reference | https://schema.org |
| web.dev Core Web Vitals | https://web.dev/vitals |
| Chrome DevTools | chrome://inspect |
| Open Graph Debugger | https://developers.facebook.com/tools/debug |
| Twitter Card Validator | https://cards-dev.twitter.com/validator |

---
