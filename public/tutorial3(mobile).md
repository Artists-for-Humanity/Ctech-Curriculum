# 📱 **Part 3 — Making Your Creative Tech ID Card Mobile-Friendly**

In **Part 1**, you built the full HTML structure for your Creative Tech ID Card. 
In **Part 2**, you added CSS to style it and make it look like a real glassy ID card. 

In this tutorial, we’ll do one big thing:

> **Make your ID card look good on phones** using something called a **media query**.

You’ll learn:

* What “mobile-friendly” means
* What a **media query** is (in human words)
* How we used media queries to:

  * Re-arrange the layout on small screens
  * Resize images and text
  * Swap between a **desktop version** and a **mobile version** of your Likes/Dislikes section

---

## ⭐ 1. What Does “Mobile-Friendly” Mean?

Your webpage can be viewed on:

* A **big laptop screen**
* A **tablet**
* A **small phone**

If you design only for a big screen, on a phone things might:

* Look **squished**
* Be **too tiny** to read
* Go **off the edge** of the screen

A **mobile-friendly** page:

* **Rearranges** things on small screens
* **Resizes** text and images
* Stays **easy to read and use** on any device

That’s where **media queries** come in.

---

## ⭐ 2. What Is a Media Query?

A **media query** is like you giving a message to the browser:

> “Hey browser, **if** the screen is smaller than this size, use these **special styles** instead.”

In your `style.css`, a media query looks like this: 

```css
@media screen and (max-width: 750px) {
    .card {
        flex-direction: column-reverse;
        max-width: 350px;
        padding: 15px;
    }
}
```

Breakdown:

| Piece                | Meaning in plain English                                     |
| -------------------- | ------------------------------------------------------------ |
| `@media`             | “Start a media query” — special rules for certain situations |
| `screen`             | Apply these rules when viewing on a screen (not print)       |
| `(max-width: 750px)` | Only if the screen is **750 pixels wide or smaller**         |
| `{ ... }`            | Inside here are the **styles to use** on small screens       |

So this block says:

> “If the screen is small (like a phone), change how the `.card` looks.”

---

## ⭐ 3. Changing the Card Layout on Small Screens

On big screens, your `.card` is a **row**: purple bar on the left, content on the right. 

```css
.card {
    display: flex;
    flex-direction: row;
    /* other properties... */
}
```

Inside the media query, we change it:

```css
@media screen and (max-width: 750px) {
    .card {
        flex-direction: column-reverse;
        max-width: 350px;
        padding: 15px;
    }
}
```

What this does:

* `flex-direction: column-reverse;`
  → Instead of being side-by-side, the sections **stack vertically**, and the bar moves above the content.

* `max-width: 350px;`
  → The card gets **narrower**, better for a phone screen.

* `padding: 15px;`
  → Slightly smaller inner spacing so it doesn’t feel cramped.

This is our first example of **“on big screens, do X; on small screens, do Y.”**

---

## ⭐ 4. Making the Purple Bar Work on Phones

On desktop, the purple bar is **vertical** and skinny: 

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

The title inside is rotated:

```css
.bar .title {
    transform: rotate(-90deg);
    /* more styles... */
}
```

On a phone, that would look **weird**. So in the media query, we switch it to a **horizontal bar** with normal text: 

```css
@media screen and (max-width: 750px) {
    h1 {
        margin: 0px;
    }

    .bar {
        width: 100%;
        min-width: auto;
        padding: 8px 10px;
        border-radius: 16px;
        margin: 10px 0px;
    }
}
```

And for the title: 

```css
@media screen and (max-width: 750px) {
    .bar .title {
        transform: rotate(0deg);
        font-size: 25px;
    }
}
```

**Result on small screens:**

* The bar becomes a **top header** across the card
* The text is **straight**, bigger, and easier to read

---

## ⭐ 5. Adjusting the Main Content on Small Screens

The main content area is called `.main-content` in your HTML: 

```html
<div class="main-content">
    <!-- Top + bottom sections live in here -->
</div>
```

On desktop, it has left padding: 

```css
.main-content {
    flex: 1;
    padding-left: 16px;
    display: flex;
    flex-direction: column;
}
```

On small screens, that extra padding makes things feel squished, so we remove it in the media query: 

```css
@media screen and (max-width: 750px) {
    .main-content {
        padding-left: 0px;
    }
}
```

Tiny change, but it helps things fit better on a phone.

---

## ⭐ 6. Making the Profile Image and Personal Info Responsive

### 🖼 The Profile Image

Desktop: fixed width and height. 

```css
.profile-pic {
    border-radius: 15px;
    width: 185px;
    height: 168px;
}
```

Mobile: we let it **shrink** with the screen: 

```css
@media screen and (max-width: 750px) {
    .profile-pic {
        width: 50%;
        height: auto;
    }
}
```

* `width: 50%;` → image takes up half the card’s width
* `height: auto;` → height adjusts automatically so it doesn’t stretch

### 📋 The Info Items

Each line like **Name:** and **Birthday:** is wrapped in `.info-item` HTML: 

On desktop they’re side-by-side:

```css
.info-item {
    display: flex;
    flex-direction: row;
}
```

On mobile they stack:

```css
@media screen and (max-width: 750px) {
    .info-item {
        flex-direction: column;
        font-size: 14px;
    }

    .info-item h2 {
        padding: 10px 0px;
    }

    h2 {
        font-size: 14px;
        margin-right: 10px;
    }
}
```

This makes your labels and answers easier to read when there isn’t much horizontal space.

---

## ⭐ 7. Desktop vs Mobile Likes/Dislikes

This is the most interesting part: your HTML actually has **two versions** of the Likes/Dislikes section: one for **desktop**, one for **mobile**. 

### 🖥 Desktop Version (detailed lists)

Inside your `.top` section:

```html
<div class="preferences desktop">
    <div class="likes">
        <h2>Likes:</h2>
        <ul class="answers">
            <li>Coding</li>
            <li>Music</li>
            <li>Art</li>
        </ul>
    </div>
    <div class="dislikes">
        <h2>Dislikes:</h2>
        <ul class="answers">
            <li>Spam Emails</li>
            <li>Slow Internet</li>
        </ul>
    </div>
</div>
```

### 📱 Mobile Version (shorter text)

Below the top section, you added a simpler, mobile-friendly version:

```html
<div class="preferences mobile">
    <div class="likes">
        <h2>Likes:</h2>
        <div class="answers">
            <div>Coding, Art, Music</div>
        </div>
    </div>
    <div class="dislikes">
        <h2>Dislikes:</h2>
        <div class="answers">
            <div>Coding, Art, Music</div>
        </div>
    </div>
</div>
```

You don’t want **both** to show at the same time, so CSS + media queries control which one is visible.

### 🎚 Hiding/Showing with Media Queries

In your base CSS (desktop), you hide the mobile version: 

```css
.preferences {
    display: flex;
    flex-direction: row;
}

.preferences.mobile {
    display: none;
}
```

And give each half a width:

```css
.preferences .likes,
.preferences .dislikes {
    width: 45%;
}
```

Then in your media query for small screens, you **swap** them: 

```css
@media screen and (max-width: 750px) {
    .preferences.desktop {
        display: none;
    }

    .preferences.mobile {
        display: block;
        border-bottom: 2px solid var(--dark-primary);
        padding: 10px 0px;
    }

    .preferences .likes,
    .preferences .dislikes {
        display: flex;
        flex-direction: row;
        align-items: end;
        width: 100%;
        font-size: 14px;
    }
}
```

So in words:

* **Big screen:**

  * `.preferences.desktop` → **shown**
  * `.preferences.mobile` → **hidden**

* **Small screen:**

  * `.preferences.desktop` → **hidden**
  * `.preferences.mobile` → **shown**

This lets you design **two different layouts** for the same information and pick which one fits the device best.

---

## ⭐ 8. Making Text and Skills Easier to Read on Mobile

A few more tweaks in the media query make text comfortable on phones:

### Paragraph text: 

```css
p {
    margin: 5px 0px;
}

@media screen and (max-width: 750px) {
    p {
        font-size: 14px;
    }
}
```

### Skill items:

```css
.skill-item {
    font-weight: 800;
    font-size: 16px;
    /* more styles... */
}

@media screen and (max-width: 750px) {
    .skill-item {
        font-size: 14px;
    }
}
```

These small changes make sure your card is **readable without zooming** on a phone.

---

## ⭐ 9. Big Picture: What You Did in Part 3

Using **media queries**, your page now:

* Shows a **horizontal bar** on mobile instead of a vertical one
* Stacks card content **top-to-bottom** on small screens
* Resizes the **profile picture** so it fits nicely
* Swaps between **desktop** and **mobile** Likes/Dislikes sections
* Shrinks text so it stays **comfortable and readable**

You’ve now:

1. Built the structure (**Part 1 — HTML**) 
2. Styled it to look like a real card (**Part 2 — CSS**) 
3. Made it **mobile-friendly** (**Part 3 — media queries + responsive tweaks**) using your `index.html` and `style.css`.  

You just built a **responsive ID card** like real websites use. 🎉
