# How Websites Work

## 🌐 How Websites Work

### Key Components

- **Front End (Client-Side):**
    - What users see and interact with (HTML, CSS, JavaScript).
    - Rendered by the browser.
- **Back End (Server-Side):**
    - Handles client requests, processes data, and returns responses.
    - Runs on a web server (a remote computer responding to browser requests).

### Browser–Server Interaction

1. Browser sends a request (HTTP/HTTPS) to a web server.
2. Server responds with data (HTML, CSS, JS, images).
3. Browser renders the received data for the user.

## 🧱 HTML (HyperText Markup Language)

### Purpose

- Defines **structure and content** of web pages.
- Built from **elements/tags**, e.g. `<p>`, `<h1>`, `<img>`.

### Basic Structure

```html
<!DOCTYPE html>
<html>
  <head>...</head>
  <body>...</body>
</html>
```

### Common Tags & Attributes

- `<h1>` → heading
- `<p>` → paragraph
- `<img src="...">` → image source
- `<button>` → clickable button
- `class="..."` → reusable styling identifier
- `id="..."` → unique identifier for JS or CSS

**Tip:** You can view any webpage’s HTML using *View Page Source*.

## ⚙️ JavaScript (JS)

### Purpose

- Adds **interactivity and dynamic behavior** to web pages.
- Executes in the browser (client-side).
- Works with HTML elements via the **Document Object Model (DOM)**.

### Example Uses

```jsx
document.getElementById("demo").innerHTML = "Hack the Planet";
```

- Changes page content dynamically.

**Event Example:**

```html
<button onclick='document.getElementById("demo").innerHTML="Button Clicked";'>Click Me!</button>
```

- Executes JS when the button is clicked.

JS can be embedded directly in `<script>` tags or loaded externally using:

```html
<script src="file.js"></script>
```

## 🔐 Sensitive Data Exposure

### Description

- Occurs when **confidential information** is left visible in source code (HTML/JS).
- Common causes: developers forgetting to remove credentials or hidden links.

### Example Risks

- Exposed admin URLs, passwords, or API keys in HTML comments or scripts.
- Can allow attackers to escalate privileges or access backend systems.

### Mitigation:

Always review the page source for hidden data and remove or protect sensitive content.

## 💉 HTML Injection

### Definition

- A **client-side vulnerability** where unsanitized user input is rendered as HTML.
- Allows attackers to inject their own HTML or JavaScript into a page.

### Cause

- Website fails to **sanitize** (filter) user input before displaying it.

### Example

If input `" <h1>Hacked!</h1> "` is echoed back on the page, the browser will render the injected HTML.

### Prevention

- Never trust user input.
- Sanitize all input (e.g., escape or strip HTML tags) before rendering or processing.