# HTML Boilerplate — Line by Line

A beginner-friendly breakdown of the standard HTML5 boilerplate structure.

---

## 📄 Full Boilerplate

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

</body>
</html>
```

---

## 🔍 Line by Line Explanation

### `<!DOCTYPE html>`
Tells the browser **"Hey, this is an HTML5 document."**  
Without this, the browser goes into *quirks mode* and renders things inconsistently.  
Always the **first line** of every HTML file.

---

### `<html lang="en">`
This is the **root element** — every single thing on your page lives inside it.  
`lang="en"` tells the browser (and screen readers) that the page content is in **English**.  
Good for **accessibility** and **SEO**.

---

### `<head>`
This section is **invisible to the user.**  
It holds *information about* the page — metadata, title, links to CSS/JS files, etc.  
Think of it as the **brain behind the scenes.**

---

### `<meta charset="UTF-8">`
Sets the **character encoding** of the page.  
UTF-8 supports virtually every character on earth — English, emojis, symbols, etc.  
Without this, special characters can break or display as garbage.

---

### `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
This line makes your website **responsive.**

| Attribute | What it does |
|---|---|
| `width=device-width` | Matches the screen's actual width |
| `initial-scale=1.0` | Doesn't zoom in or out by default |

Without this, your page looks **zoomed out and tiny on mobile.**

---

### `<title>Document</title>`
Sets the **tab name** in the browser.  
You'd change `Document` to something like `"KULT — Drop Page"`.  
It also shows up in **Google search results.**

---

### `</head>`
Closes the head section.  
Everything from here goes **visible on screen.**

---

### `<body>`
Everything inside `<body>` is what the **user actually sees** —  
text, images, buttons, animations, all of it.

---

### `</body>` & `</html>`
Just **closing tags** — wrapping everything up properly.  
Browsers are forgiving if you skip these, but **always close your tags.**  
Clean code = pro coder. 🔥

---

## 💡 Quick Tip

This boilerplate is the **skeleton.**  