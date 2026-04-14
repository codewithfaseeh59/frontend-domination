# How HTML, CSS & JavaScript Work Behind the Scenes 🧠

---

## 🌐 The Big Picture

When you open a website in a browser, three things happen:

1. **HTML** gives the page **structure** (the skeleton)
2. **CSS** gives it **style** (the skin & clothes)
3. **JavaScript** gives it **behavior** (the brain & muscles)

But what actually happens *under the hood*? Let's break it down step by step.

---

## 🔵 Step 1 — The Browser Fetches the Files

When you type a URL and hit Enter:

1. Browser makes an **HTTP/HTTPS request** to a server
2. Server responds with an **HTML file**
3. Browser starts **parsing** (reading) the HTML
4. As it finds `<link>` tags → fetches **CSS files**
5. As it finds `<script>` tags → fetches **JS files**

> 📌 This is why you put `<link>` in `<head>` and `<script>` before `</body>` — so CSS loads early and JS doesn't block rendering.

---

## 🟠 HTML Behind the Scenes — The DOM

### What is Parsing?

The browser reads HTML top to bottom, character by character. It **tokenizes** it (breaks it into meaningful chunks like tags, attributes, text), then builds a tree structure.

### The DOM (Document Object Model)

The browser converts your HTML into a **tree of objects** in memory called the **DOM**.

```html
<div class="hero">
  <h1>Hello World</h1>
  <p>Welcome</p>
</div>
```

becomes this in memory:

```
Document
  └── html
        ├── head
        └── body
              └── div.hero
                    ├── h1 → "Hello World"
                    └── p → "Welcome"
```

Every tag becomes a **Node**. JavaScript can read and manipulate these nodes — that's how dynamic websites work.

### Important DOM Facts

- The DOM is **not** the HTML file — it's a live in-memory representation
- The DOM can be **changed by JS** without touching the original HTML file
- `document.querySelector()`, `getElementById()` etc. all access this DOM tree

---

## 🟣 CSS Behind the Scenes — CSSOM & The Cascade

### CSSOM (CSS Object Model)

Just like HTML becomes the DOM, CSS gets parsed into its own tree: the **CSSOM**.

The browser reads your CSS and builds a map of which styles apply to which selectors.

```css
.hero h1 {
  font-size: 48px;
  color: #fff;
}
```

This becomes a structured object in memory telling the browser: *"any `h1` inside `.hero` gets these rules."*

### The Cascade (How CSS Decides Which Style Wins)

When multiple rules target the same element, CSS uses this priority order:

1. **Importance** → `!important` wins everything (avoid abusing it)
2. **Specificity** → More specific selector wins
   - Inline style: `1000` points
   - ID (`#id`): `100` points
   - Class (`.class`): `10` points
   - Tag (`div`): `1` point
3. **Source Order** → Last rule wins if specificity is equal

### Specificity Example

```css
p { color: black; }          /* specificity: 1 */
.text { color: blue; }       /* specificity: 10 */
#main p { color: red; }      /* specificity: 101 */
```

The `#main p` rule wins because `100 (ID) + 1 (tag) = 101`.

---

## 🟡 The Render Pipeline — How the Browser Draws the Page

After parsing HTML & CSS, the browser follows these steps:

### 1. Combine DOM + CSSOM = Render Tree

The browser merges both trees. Elements with `display: none` are **excluded** from the Render Tree.

### 2. Layout (Reflow)

The browser calculates the **exact position and size** of every element on the screen.

- Where does this `div` start?
- How wide is this `h1`?
- Does this text wrap?

This is called **Layout** (also called **Reflow**). It's expensive — avoid triggering it repeatedly with JavaScript.

### 3. Paint

The browser fills in pixels — colors, borders, shadows, text, images. Each element gets painted onto layers.

### 4. Composite

Layers are combined and sent to the **GPU** to be displayed on screen.

> ⚡ **Performance Tip:** CSS properties like `transform` and `opacity` skip Layout & Paint and go straight to Compositing — that's why they're butter-smooth for animations (that's why GSAP loves them!).

---

## 🔴 JavaScript Behind the Scenes — The Engine

### The JS Engine

Every browser has a JS engine:
- Chrome/Edge → **V8**
- Firefox → **SpiderMonkey**
- Safari → **JavaScriptCore**

### How JS Executes Your Code

#### 1. Parsing
JS code is read and converted into an **AST (Abstract Syntax Tree)** — a structured representation of your code's logic.

#### 2. Compilation (JIT)
Modern engines use **Just-In-Time (JIT) Compilation** — they compile JS to machine code *on the fly* while running it, making it much faster than pure interpretation.

#### 3. Execution
Code runs in the **Call Stack** — a Last In, First Out (LIFO) stack of function calls.

```javascript
function greet() {
  console.log("Hello");
}
function init() {
  greet();
}
init();
```

Call Stack flow:
```
init()  ← pushed
greet() ← pushed on top
console.log() ← pushed on top
console.log() ← popped (done)
greet() ← popped (done)
init()  ← popped (done)
```

---

## 🔁 The Event Loop — How JS Handles Async

JavaScript is **single-threaded** — it can only do one thing at a time. But websites do many things at once (fetch data, handle clicks, run animations). How?

### The Answer: Event Loop + Web APIs

```
Call Stack → Web APIs → Callback Queue → Event Loop → back to Call Stack
```

1. `setTimeout`, `fetch`, event listeners are handed off to **Web APIs** (browser handles them)
2. When done, their callbacks go into the **Callback Queue** (or Microtask Queue for Promises)
3. The **Event Loop** checks: *"Is the Call Stack empty?"* → If yes, push the next callback in

```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
console.log("3");

// Output: 1, 3, 2
// Even with 0ms delay, setTimeout goes through the Event Loop
```

---

## ⚙️ How JS Manipulates the DOM

When JS touches the DOM, it can trigger the render pipeline again:

| JS Action | Triggers |
|---|---|
| `el.style.color = 'red'` | Paint |
| `el.style.width = '200px'` | Layout + Paint + Composite |
| `el.style.transform = '...'` | Composite only ✅ |
| `el.style.opacity = '0'` | Composite only ✅ |

> 💡 **This is why GSAP's `transform`-based animations are performant** — they bypass Layout and Paint entirely.

---

## 🧩 Putting It All Together — Full Flow Summary

```
1. User enters URL
       ↓
2. Browser fetches HTML from server
       ↓
3. HTML is parsed → DOM is built
       ↓
4. CSS files fetched → parsed → CSSOM built
       ↓
5. DOM + CSSOM → Render Tree
       ↓
6. Layout → Paint → Composite → 🖥️ Page visible!
       ↓
7. JS is parsed, compiled, executed
       ↓
8. JS can modify DOM/CSS → triggers re-render pipeline
       ↓
9. Event Loop handles async tasks (clicks, fetches, timers)
```

---

## 🚀 Key Takeaways

- **HTML** → parsed into the **DOM** (a live tree of nodes)
- **CSS** → parsed into the **CSSOM** (a map of styles)
- Both merge into a **Render Tree** → Layout → Paint → Composite
- **JavaScript** runs on a single thread via the **Call Stack**
- **Async** is handled by the **Event Loop + Web APIs**
- For smooth animations → use `transform` & `opacity` (GPU compositing, no layout/paint cost)
- JS modifying the DOM can trigger expensive re-layouts — **minimize reflows!**

---

*Understanding this flow makes you a better developer — you write faster code, debug smarter, and build animations that don't jank.* 💪