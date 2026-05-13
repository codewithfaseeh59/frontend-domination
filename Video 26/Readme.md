# 🌊 CSS Overflow Property

## What is Overflow?

Overflow happens when the **content inside an element is bigger than the element itself.**

By default, content will just spill out. The `overflow` property lets you **control what happens in that case.**

---

## Syntax

```css
selector {
  overflow: value;
}
```

---

## Overflow Values

### `overflow: visible` *(default)*
Content **spills outside** the box. No clipping, no scrollbar.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: visible; /* default — content overflows freely */
}
```

> 🧠 Even though content spills out, it does NOT affect the layout of other elements around it.

---

### `overflow: hidden`
Content that **exceeds the box is clipped** (cut off). Nothing scrollable.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: hidden; /* extra content is invisible */
}
```

> 💡 **Common use case:** Hiding overflowing text, clipping images inside cards, or containing floats.

---

### `overflow: scroll`
**Always shows scrollbars** — both horizontal and vertical — even if content fits.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: scroll; /* scrollbars always present */
}
```

> ⚠️ Even if content fits perfectly, scrollbars will still appear (and look ugly). Use `auto` instead in most cases.

---

### `overflow: auto`
**Scrollbars appear only when needed.** If content fits, no scrollbar. If it overflows, scrollbar shows up.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: auto; /* scrollbar only if needed */
}
```

> ✅ **Best practice:** Use `auto` over `scroll` for cleaner UI.

---

### `overflow: clip` *(modern)*
Similar to `hidden` — content is clipped. But unlike `hidden`, it **does NOT create a new formatting context**.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: clip;
}
```

> 🧪 Newer value. Good browser support now. Useful when you want clipping without the side effects of `hidden`.

---

## Axis-Specific Overflow

You can control horizontal and vertical overflow **separately.**

```css
/* Only control horizontal overflow */
overflow-x: hidden;

/* Only control vertical overflow */
overflow-y: scroll;
```

### All values work the same:
| Property | Controls |
|---|---|
| `overflow-x` | Left / Right (horizontal) |
| `overflow-y` | Top / Bottom (vertical) |

```css
.box {
  overflow-x: auto;   /* horizontal scrollbar if needed */
  overflow-y: hidden; /* vertical content gets clipped */
}
```

---

## Shorthand — Two Values

When you write **two values**, the first is `overflow-x` and second is `overflow-y`:

```css
.box {
  overflow: auto hidden;
  /* overflow-x: auto | overflow-y: hidden */
}
```

---

## `overflow: visible` vs `overflow: hidden` — Visual Difference

```
┌──────────────┐          ┌──────────────┐
│  Box 200px   │          │  Box 200px   │
│              │          │              │
│  Short text  │          │  Short text  │
│  that fits   │ visible  │  that fits   │ hidden
└──────────────┘          └──────────────┘

┌──────────────┐          ┌──────────────┐
│  Box 200px   │          │  Box 200px   │
│              │          │              │
│  Very long   │          │  Very long   │
│  text that   │ visible  │  text that   │ hidden
│  overflows   │          │  overflows   │
│  outside ────┼──▶       └──────────────┘
└──────────────┘          (clipped/hidden)
```

---

## Overflow and `text-overflow`

To handle **single-line text overflow** with ellipsis (`...`), you need three properties together:

```css
.box {
  width: 200px;
  white-space: nowrap;      /* prevent text from wrapping */
  overflow: hidden;         /* clip the overflow */
  text-overflow: ellipsis;  /* show "..." at the end */
}
```

> ⚡ `text-overflow` alone does nothing. It needs `overflow: hidden` + `white-space: nowrap` to work.

---

## Overflow Creates a New Block Formatting Context (BFC)

When `overflow` is set to anything **other than `visible`**, the element becomes a **Block Formatting Context (BFC)**.

This means:
- It **contains floated children** (classic float clearfix trick)
- It **prevents margin collapse**

```css
/* Old-school float clearfix */
.parent {
  overflow: hidden; /* contains floated children inside */
}
```

---

## Quick Reference

| Value | Clips Content | Scrollbar | Notes |
|---|---|---|---|
| `visible` | ❌ | ❌ | Default. Content spills out |
| `hidden` | ✅ | ❌ | Content cut off, no scroll |
| `scroll` | ✅ | ✅ Always | Scrollbar always visible |
| `auto` | ✅ | ✅ If needed | Scrollbar only when needed |
| `clip` | ✅ | ❌ | Like hidden, no BFC created |

---

## Common Use Cases

```css
/* 1. Card image clipping */
.card {
  overflow: hidden;
  border-radius: 12px;
}

/* 2. Scrollable sidebar */
.sidebar {
  height: 100vh;
  overflow-y: auto;
}

/* 3. Horizontal scroll gallery */
.gallery {
  display: flex;
  overflow-x: auto;
  overflow-y: hidden;
}

/* 4. Truncate long text */
.title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* 5. Contain floated children */
.container {
  overflow: hidden; /* BFC trick */
}
```

---

## Things to Remember 🧠

- `overflow: visible` → default, content spills freely
- `overflow: hidden` → clips content, creates BFC, used for image clipping + float containing
- `overflow: auto` → cleanest scroll option, only shows scrollbar when needed
- `overflow: scroll` → always shows scrollbar (avoid in most cases)
- `overflow-x` / `overflow-y` → axis-specific control
- `text-overflow: ellipsis` needs `overflow: hidden` + `white-space: nowrap` to work
- Setting overflow (except `visible`) creates a **Block Formatting Context**