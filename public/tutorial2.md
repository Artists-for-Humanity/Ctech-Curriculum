# 🎨 **Part 2 — Adding CSS to Style Your Creative Tech ID Card**

Now that you have a complete and working **HTML structure**, it’s time to make it **look amazing** using CSS.

This tutorial will teach you:

✔ How to add a **separate CSS file**
✔ How to apply **classes** to your HTML
✔ How to style layout, colors, spacing, borders, fonts, and more
✔ What every new CSS property means — explained simply

We will add **classes** to your HTML one section at a time, *then* create the matching CSS in your `style.css`.

---

# ⭐ 1. Create Your CSS File

Inside the same folder as `index.html`:

1. **Right-click → New File**
2. Name it: **`style.css`**

Now connect it to your HTML.

At the top of your HTML `<head>`, add this line:

```html
<link rel="stylesheet" href="style.css">
```

This tells the browser to “go load my CSS file”.

---

# ⭐ 2. Add Reset and Global Styling

Inside **style.css**, start with this:

```css
* {
    box-sizing: border-box;
}
```

### **What this means**

| Code                     | Explanation                           |
| ------------------------ | ------------------------------------- |
| `*`                      | Means “select everything on the page” |
| `box-sizing: border-box` | Makes width/height easier to control  |

This is a very common starting point for all web pages.

---

# ⭐ 3. Add CSS Variables (Custom Colors)

Still at the top of your CSS, add:

```css
:root {
    --dark-bg-color: linear-gradient(180deg, rgba(2, 0, 36, 0.40) 0%, rgba(9, 9, 121, 0.35) 50%, rgba(149, 0, 255, 0.90) 100%);
    --dark-primary: rgb(50, 35, 100);
    --dark-primary-transparent: rgba(50, 35, 100, 0.3);
    --dark-secondary: #DCD0F6;
}
```

### **What these new things mean**

| Term                   | Explanation                                                                       |
| ---------------------- | --------------------------------------------------------------------------------- |
| `:root`                | This is like the “top level” of your site (similar to saying **global settings**) |
| `--dark-primary`       | This is a **CSS variable** — a reusable value                                     |
| `linear-gradient(...)` | A smooth fade between colors                                                      |

Using variables makes your CSS cleaner and easier to edit later.

---

# ⭐ 4. Style the Page Background

Add this next:

```css
body {
    font-family: Poppins, sans-serif;
    margin: 0;
    padding: 0;
    min-width: 100vw;
    min-height: 100vh;
    background-image: linear-gradient(180deg, #1E1E1E 0%, #1E1E1E 100%), var(--dark-bg-color);
    background-blend-mode: overlay;
    background-size: cover;
    background-position: center;
    display: flex;
    justify-content: center;
    align-items: center;
    color: var(--dark-secondary);
}
```

### **New CSS Explained**

| Property                | Meaning                                               |
| ----------------------- | ----------------------------------------------------- |
| `font-family`           | Changes the font                                      |
| `min-height: 100vh`     | Makes the body at least the height of the full screen |
| `display: flex`         | Turns the body into a flexbox container               |
| `justify-content`       | Centers items horizontally                            |
| `align-items`           | Centers items vertically                              |
| `background-image`      | Applies a gradient background                         |
| `background-blend-mode` | Mixes two backgrounds                                 |
| `color`                 | Sets text color                                       |

Now your page has a full dark gradient background.

---

# ⭐ 5. Style the Card Container

## Step 1 — Add a class to your HTML

In your `<main>` tag, add the class:

```html
<main class="card">
```

## Step 2 — Add the matching CSS:

```css
.card {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: stretch;
    padding: 29px 28px 21px 33px;
    border-radius: 25px;
    border: 1px solid #DCD0F6;
    background: rgba(255, 255, 255, 0.30);
    box-shadow: 4px 4px 4px 0 rgba(0, 0, 0, 0.25);
    backdrop-filter: blur(15px);
    max-width: 625px;
}
```

### **New CSS Explained**

| Property                | Explanation                       |
| ----------------------- | --------------------------------- |
| `flex-direction: row`   | Lays out elements side-by-side    |
| `padding`               | Space *inside* the card           |
| `border-radius`         | Rounds the corners                |
| `box-shadow`            | Adds a soft shadow                |
| `backdrop-filter: blur` | Blurs whatever is behind the card |

This creates the glass-like card effect.

---

# ⭐ 6. Build the Purple Side Bar

## Add this to your HTML:

```html
<div class="bar">
    <h1 class="title">Creative Tech ID</h1>
</div>
```

## And style it:

```css
.bar {
    background: var(--dark-primary);
    color: white;
    width: 60px;
    min-width: 60px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}
```

---

# ⭐ Style the Rotated Title

```css
.bar .title {
    transform: rotate(-90deg);
    transform-origin: center;
    white-space: nowrap;
    letter-spacing: 1px;
    text-align: center;
    text-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
    font-size: 30px;
    font-weight: 600;
    letter-spacing: 3.9px;
    text-transform: uppercase;
}
```

### **New CSS Explained**

| Property              | Meaning                         |
| --------------------- | ------------------------------- |
| `transform: rotate()` | Rotates the text                |
| `white-space: nowrap` | Prevents the text from wrapping |
| `letter-spacing`      | Spreads out letters             |
| `text-shadow`         | Adds a shadow behind text       |

---

# ⭐ 7. Style the Main Content Area

## Add the class to HTML:

```html
<div class="main-content">
```

## Add CSS:

```css
.main-content {
    flex: 1;
    padding-left: 16px;
    display: flex;
    flex-direction: column;
}
```

---

# ⭐ 8. Style the Top Section (Image + Info)

## Add class in HTML:

```html
<div class="top">
```

## Add CSS:

```css
.top {
    display: flex;
    flex-direction: row;
    align-items: center;
    border-bottom: 2px solid var(--dark-primary);
    padding-bottom: 10px;
}
```

---

# ⭐ Profile Image

Add class in HTML:

```html
<img src="./images/hands.png" class="profile-pic">
```

Add CSS:

```css
.profile-pic {
    border-radius: 15px;
    width: 185px;
    height: 168px;
}
```

---

# ⭐ Personal Info Area

HTML:

```html
<div class="info">
```

CSS:

```css
.info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-left: 5px;
    width: 100%;
}
```

---

# ⭐ Personal Info Divider

HTML:

```html
<div class="personal-info">
```

CSS:

```css
.personal-info {
    border-bottom: 2px solid var(--dark-primary);
    padding-bottom: 5px;
    margin-bottom: 8px;
}
```

---

# ⭐ Info Item (Label + Value)

HTML:

```html
<div class="info-item">
```

CSS:

```css
.info-item {
    display: flex;
    flex-direction: row;
}
```

---

# ⭐ Header Styling (All `<h2>` tags)

```css
h2 {
    color: var(--dark-primary);
    font-size: 18px;
    font-weight: 800;
    margin: 0;
    margin-right: 20px;
}
```

---

# ⭐ Likes & Dislikes Section

HTML:

```html
<div class="preferences">
```

CSS:

```css
.preferences {
    display: flex;
    flex-direction: row;
}
```

Width for each half:

```css
.preferences .likes,
.preferences .dislikes {
    width: 45%;
}
```

---

# ⭐ Lists Styling

```css
.answers {
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;
    margin: 0;
}
```

---

# ⭐ 9. Bottom Section Styling

HTML:

```html
<div class="bottom">
```

CSS:

```css
p {
    margin: 5px 0px;
}
```

---

# ⭐ Skills Area

HTML:

```html
<div class="skill-items">
```

CSS:

```css
.skill-items {
    display: flex;
    flex-direction: row;
    align-items: center;
}
```

---

# ⭐ Individual Skill Bubble

HTML:

```html
<div class="skill-item">Coding</div>
```

CSS:

```css
.skill-item {
    font-weight: 800;
    font-size: 16px;
    color: var(--dark-primary);
    background-color: var(--dark-primary-transparent);
    padding: 5px 15px;
    border: 2px solid var(--dark-primary);
    border-radius: 10px;
    margin-right: 6px;
}
```

---

# ⭐ Language Logos (HTML / CSS / JS)

Add classes in HTML:

```html
<a class="skill-item language html">...</a>
```

CSS:

```css
.language {
    padding: 5px 5px;
    background-color: transparent;
    display: flex;
    align-items: center;
}
```

Colored borders:

```css
.html {
    border: 2px solid #FC490B;
}

.css {
    border: 2px solid #2196F3;
}

.js {
    border: 2px solid #FFDF00;
}
```
