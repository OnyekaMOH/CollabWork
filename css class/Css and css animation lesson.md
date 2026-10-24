# CSS Fundamentals & CSS Animation
## The 10 Topics We'll Cover

**The learning path:** Setup → Selectors → Box Model → Colors, Units & Typography → Flexbox → Position & Transform → Transitions → Keyframe Animation → 🌙 Project: Moon Orbit → Accessibility & Debugging

---

## 0. Setup: How CSS Connects to HTML
CSS is the language that styles HTML. HTML says *what* is on the page; CSS says *how it looks*. You link a `.css` file to your HTML with a `<link>` tag in the `<head>`, then edit and refresh to see changes.

## 1. Selectors, Properties & Values
A CSS rule has three parts: a selector (what to style), a property (what to change) and a value (what to change it to). Select by element (`p`), class (`.moon`) or id (`#earth`). When rules clash, specificity and order decide the winner.

## 2. The Box Model
Every element is a rectangular box made of content, padding, border and margin. Set `box-sizing: border-box` so widths behave predictably. A square box with `border-radius: 50%` becomes a perfect circle.

## 3. Colors, Units & Typography
Colors can be written as names, hex, `rgb()` or `hsl()`, and gradients create depth. Use `px`, `rem`, `%` and `vh` for sizes. CSS variables (`--name`) let you store a value once and reuse it everywhere.

## 4. Layout with Flexbox (and Grid Centering)
`display: flex` turns a container into a layout system for its children. `justify-content` and `align-items` position items along the main and cross axes. `display: grid; place-items: center` is the one-line way to centre anything.

## 5. Position & Transform
`position: absolute` pins an element relative to its nearest positioned parent. `transform` moves, rotates and scales an element without disturbing the layout. Together they let you place a moon on the edge of a circle.

## 6. Transitions
A transition smooths the change between two states (like normal → hover). Define it with `transition: property duration timing-function`. It needs a trigger, and it is the simplest form of animation.

## 7. Keyframe Animation
`@keyframes` describes the steps of an animation and the `animation` property plays it. The browser fills in all the frames between your steps. Loops, delays, direction and pausing are all controlled with animation properties.

## 8. 🌙 Project: Build a Moon Orbit
Combine everything: a styled night sky, a glowing Earth, a dashed orbit ring and a moon that circles forever using one `@keyframes` rule. Includes step-by-step build, full code and extension challenges.

## 9. Accessibility, Performance & Debugging
Respect users who are sensitive to motion with `prefers-reduced-motion`. Animate `transform` and `opacity` for smooth performance, and use browser DevTools to inspect and fix your CSS.










# CSS Fundamentals & CSS Animation

## How the Modules Connect

```
HTML + CSS Setup
       │
       ▼
Selectors & Properties
       │
       ▼
   Box Model  ──► Colors, Units & Typography
       │
       ▼
Flexbox / Grid Centering
       │
       ▼
Position & Transform
       │
       ├──────────────► Transitions (A → B on hover)
       │                      │
       ▼                      ▼
@keyframes Animation ◄────────┘
       │
       ▼
🌙 PROJECT: Moon Orbit
       │
       ▼
Accessibility, Performance & Debugging
```

Each layer depends on the one above it. Master selectors before the box model, the box model before layout, and transforms before animation. The Moon Orbit project uses *every* module.

---

## Suggested Lesson Plan

| Session | Modules                      | Format                                         |
| ------- | ---------------------------- | ---------------------------------------------- |
| 1       | 0, 1, 2                      | Concept + live coding (build a styled card)    |
| 2       | 3, 4                         | Concept + exercises (style a profile page)     |
| 3       | 5, 6                         | Concept + exercises (hover effects, positioning) |
| 4       | 7                            | Concept + exercises (pulse, float, spin)       |
| 5       | 8, 9                         | Guided project: build the Moon Orbit together  |

---

# MODULE 0 — Setup: How CSS Connects to HTML

> Before writing any CSS, students need a working workflow: an HTML file, a CSS file, and a way to see changes instantly. Getting this right first prevents the most common "my CSS does nothing" frustrations.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Explain what CSS does and how it differs from HTML.
2. Link an external stylesheet to an HTML page with `<link>`.
3. Name the three ways to add CSS and explain why external stylesheets are preferred.
4. Open browser DevTools and inspect an element's styles.

---

## Section Breakdown

### 0.1 — What Is CSS?

**Plain-language definition:**
CSS (Cascading Style Sheets) is the language that controls the appearance of a web page: colors, fonts, spacing, layout and animation. HTML provides the structure and content; CSS makes it look good.

**Why it matters:**
Without CSS, every website would look like a plain black-and-white document. Separating structure (HTML) from style (CSS) means you can redesign an entire site by changing one file, without touching the content.

**Analogy:**
Think of a house. HTML is the building: walls, doors, windows and rooms. CSS is the interior design: paint colors, furniture placement, lighting. The same house can look completely different with a different designer.

**Common misconception:**
Beginners often think CSS is a programming language. It isn't. It has no loops or logic of its own. It is a *declarative* language: you describe what you want ("make this red") and the browser figures out how to draw it.

---

### 0.2 — Linking a Stylesheet

**Plain-language definition:**
An external stylesheet is a separate `.css` file connected to your HTML page using a `<link>` tag inside the `<head>`.

**Project structure:**

```
moon-orbit/
├── index.html
└── style.css
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My First CSS Page</title>

  <!-- Connect the stylesheet -->
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>Hello, CSS!</h1>
  <p>This page is about to look much better.</p>
</body>
</html>
```

**style.css:**

```css
h1 {
  color: tomato;
}
```

Open `index.html` in a browser. The heading should now be tomato red. 🎉

---

### 0.3 — Three Ways to Add CSS

| Method       | Where it lives                  | Example                                   | When to use                 |
| ------------ | ------------------------------- | ----------------------------------------- | --------------------------- |
| **Inline**   | Inside the HTML tag             | `<h1 style="color: red;">`                | Quick tests only            |
| **Internal** | In a `<style>` tag in the head  | `<style> h1 { color: red; } </style>`     | Single-page demos           |
| **External** | In a separate `.css` file       | `<link rel="stylesheet" href="style.css">` | ✅ Almost always            |

**Why external wins:**
One CSS file can style every page of a website. Change it once and every page updates. It also keeps your HTML clean and lets the browser cache the stylesheet.

---

### 0.4 — Your Best Friend: Browser DevTools

**Plain-language definition:**
DevTools is a set of inspection tools built into every browser. Right-click any element and choose **Inspect** (or press `F12`).

**What students should try:**
- Click an element in the **Elements** panel and see its CSS in the **Styles** pane.
- Untick a property to see what it does. Change a value and watch the page update live.
- Hover over an element in the panel to see its box highlighted on the page.

**Common beginner mistakes:**
- **Wrong file path:** `href="styles.css"` when the file is `style.css`. The page silently loads no styles.
- **Putting `<link>` in the `<body>`:** It belongs in the `<head>`.
- **Forgetting to save:** The browser can only show what is saved.
- **Seeing old styles:** The browser cached the old file. Do a hard refresh (`Ctrl+Shift+R` / `Cmd+Shift+R`).

---

## How Sub-sections Connect

`0.1` explains what CSS is → `0.2` shows how to connect it → `0.3` explains your options and why one is best → `0.4` gives you the tool to debug everything that follows.

---

## Key Terms Glossary

| Term             | Definition                                                                 |
| ---------------- | -------------------------------------------------------------------------- |
| **CSS**          | Cascading Style Sheets: the language that styles HTML                      |
| **Stylesheet**   | A file (or block) containing CSS rules                                     |
| **`<link>`**     | HTML tag that connects an external stylesheet to a page                    |
| **`<head>`**     | The part of an HTML page that holds metadata, including `<link>`           |
| **DevTools**     | Browser tools for inspecting and editing HTML/CSS live                     |
| **Hard refresh** | Reloading a page while ignoring cached files                               |

---

## Knowledge Check

1. In one sentence each, what is the job of HTML and the job of CSS?
2. Name the three ways to add CSS to a page. Which is best for real projects and why?
3. Your CSS file is saved and linked but nothing changes in the browser. List three things you would check.
4. Create `index.html` and `style.css`. Link them, then make the `<body>` background color `lightyellow`.
5. **Scenario:** A classmate puts `style="color:red"` on 40 different paragraphs. Explain the problem and how to fix it.

---

## Summary Recap

- HTML is structure; CSS is appearance.
- Link an external stylesheet with `<link rel="stylesheet" href="style.css">` inside `<head>`.
- External stylesheets are best: reusable, clean and cacheable.
- Use DevTools (`F12`) to inspect and experiment with styles live.
- If nothing changes, check the file path, the `<head>` placement, saving, and caching.

---
---

# MODULE 1 — Selectors, Properties & Values

> Every piece of CSS is the same simple pattern: *pick something, then change something about it*. Mastering this pattern unlocks everything else.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Identify the selector, property and value in any CSS rule.
2. Select elements by tag, class and id.
3. Use grouping, descendant selectors and the `:hover` pseudo-class.
4. Explain in simple terms how the cascade and specificity decide which rule wins.

---

## Section Breakdown

### 1.1 — Anatomy of a CSS Rule

**Plain-language definition:**
A CSS rule tells the browser *which* elements to style and *how*. It has a selector, then curly braces containing one or more declarations. Each declaration is a property, a colon, a value and a semicolon.

```css
selector {
  property: value;
  property: value;
}
```

**Concrete example:**

```css
p {
  color: navy;
  font-size: 18px;
}
```

- `p` is the **selector** (every paragraph)
- `color` and `font-size` are **properties**
- `navy` and `18px` are **values**

**Analogy:**
A rule is like an instruction to a painter: "*In the kitchen* (selector), *paint the walls* (property) *light blue* (value)."

---

### 1.2 — Element, Class and ID Selectors

| Selector type | Syntax     | HTML it matches                 | Reusable?              |
| ------------- | ---------- | ------------------------------- | ---------------------- |
| **Element**   | `p`        | every `<p>`                     | n/a                    |
| **Class**     | `.moon`    | `<div class="moon">`            | ✅ Yes, many elements   |
| **ID**        | `#earth`   | `<div id="earth">`              | ❌ Only once per page   |

**Concrete example:**

```html
<h2>Planets</h2>
<p class="highlight">Earth</p>
<p>Mars</p>
<p class="highlight">Venus</p>
```

```css
.highlight {
  background-color: gold;
}
```

Only "Earth" and "Venus" turn gold, because only they have `class="highlight"`.

**Best practice:** Use **classes** for almost everything. They are flexible, reusable and keep specificity low.

---

### 1.3 — Grouping, Descendants and Hover

**Grouping:** apply the same style to several selectors with a comma.

```css
h1, h2, h3 {
  font-family: Arial, sans-serif;
}
```

**Descendant selector:** a space means "anywhere inside."

```css
.card p {
  color: gray;   /* only paragraphs inside .card */
}
```

**Pseudo-class:** a keyword that targets a *state*.

```css
.button:hover {
  background-color: orange;   /* when the mouse is over it */
}
```

---

### 1.4 — The Cascade and Specificity

**Plain-language definition:**
When two rules style the same property of the same element, the browser must choose one. It uses two tests:

1. **Specificity:** the more specific selector wins. `#id` beats `.class`, which beats `element`. Inline styles beat all three.
2. **Order:** if specificity is equal, the rule that comes **later** in the file wins.

**Concrete example:**

```css
p        { color: blue; }   /* least specific */
.intro   { color: green; }  /* beats p */
#special { color: red; }    /* beats .intro */
```

A `<p id="special" class="intro">` is **red**.

**Common beginner mistakes:**
- **Forgetting the dot:** `moon { }` targets a `<moon>` tag, not `class="moon"`. Write `.moon { }`.
- **Missing semicolon or brace:** One missing `;` can break the next line; one missing `}` can break everything below.
- **Typos in property names:** `colour` or `back-ground` are silently ignored.
- **Reaching for `!important`:** It forces a win but makes future changes painful. Fix the specificity instead.

---

## How Sub-sections Connect

`1.1` gives you the rule structure → `1.2` shows how to aim at elements → `1.3` shows more powerful ways to aim → `1.4` explains what happens when your aim overlaps.

---

## Key Terms Glossary

| Term             | Definition                                                         |
| ---------------- | ------------------------------------------------------------------ |
| **Selector**     | The part of a rule that picks which elements to style              |
| **Property**     | The aspect to change (e.g., `color`, `width`)                      |
| **Value**        | The setting for a property (e.g., `red`, `200px`)                  |
| **Declaration**  | One `property: value;` pair                                        |
| **Class**        | A reusable label (`class="x"`), selected with `.x`                 |
| **ID**           | A unique label (`id="x"`), selected with `#x`                      |
| **Pseudo-class** | A keyword targeting a state, such as `:hover`                      |
| **Cascade**      | The system that decides which conflicting rule wins                |
| **Specificity**  | How precisely a selector targets an element; higher wins           |

---

## Knowledge Check

1. Label the selector, property and value: `h1 { text-align: center; }`
2. What is the difference between `.box` and `#box`? Which should you usually use?
3. Why does this not work, and how do you fix it? `<div class="card">` with the CSS `card { color: red; }`
4. Write CSS that makes every `<li>` inside `.menu` green, and turns it bold on hover.
5. **Scenario:** You wrote `.title { color: blue; }` but the title stays red because of an earlier `#main-title { color: red; }`. Explain why and give two ways to fix it.

---

## Summary Recap

- A rule = selector + `{ property: value; }`.
- Use `.class` selectors for most styling; `#id` only for unique elements.
- Commas group selectors; spaces select descendants; `:hover` targets a state.
- The cascade picks a winner by specificity first, then by order.
- Avoid `!important`; typos and missing punctuation are the top causes of "broken" CSS.

---
---

# MODULE 2 — The Box Model

> Every single thing on a web page is a rectangle. Once students see the boxes, layout stops being mysterious.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Name the four layers of the box model and describe each.
2. Use `width`, `height`, `padding`, `border` and `margin`.
3. Explain why `box-sizing: border-box` is recommended.
4. Make a perfect circle using `border-radius`.

---

## Section Breakdown

### 2.1 — The Four Layers

**Plain-language definition:**
Every element is a box made of four layers, from the inside out:

```
┌──────────────────────────────┐
│           MARGIN             │  ← space outside the border
│  ┌────────────────────────┐  │
│  │        BORDER          │  │  ← the edge line
│  │  ┌──────────────────┐  │  │
│  │  │     PADDING      │  │  │  ← space inside the border
│  │  │  ┌────────────┐  │  │  │
│  │  │  │  CONTENT   │  │  │  │  ← text, image, etc.
│  │  │  └────────────┘  │  │  │
│  │  └──────────────────┘  │  │
│  └────────────────────────┘  │
└──────────────────────────────┘
```

**Why it matters:**
Spacing problems ("why is there a gap here?" or "why is this too wide?") are almost always box model questions.

**Analogy:**
A framed picture hanging in a gallery. The **picture** is the content, the **matting** around it is padding, the **frame** is the border, and the **empty wall space** between frames is the margin.

**Concrete example:**

```css
.card {
  width: 250px;
  padding: 20px;
  border: 2px solid black;
  margin: 30px;
  background-color: lightblue;
}
```

---

### 2.2 — `box-sizing: border-box`

**Plain-language definition:**
By default, `width: 250px` sets only the *content* width. Padding and border are added on top, so the box is actually wider than 250px. `box-sizing: border-box` changes this so that `width` includes padding and border.

**Why it matters:**
Without it, doing arithmetic to make elements fit becomes painful. With it, a 250px box is 250px.

**The standard reset (put this at the top of every stylesheet):**

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

| Setting                  | `width: 250px` + `padding: 20px` + `border: 2px` | Total width |
| ------------------------ | ------------------------------------------------ | ----------- |
| `content-box` (default)  | 250 + 40 + 4                                     | **294px**   |
| `border-box`             | stays inside 250                                 | **250px**   |

---

### 2.3 — Shorthand for Padding & Margin

```css
padding: 10px;                /* all four sides */
padding: 10px 20px;           /* top+bottom | left+right */
padding: 10px 20px 30px 40px; /* top | right | bottom | left (clockwise) */

margin: 0 auto;               /* no vertical margin, auto horizontal (centres a block) */
```

**Memory trick:** four values go clockwise like a clock, starting at **12 o'clock** (top).

---

### 2.4 — Circles with `border-radius`

**Plain-language definition:**
`border-radius` rounds the corners of a box. At `50%`, a square becomes a circle.

```css
.planet {
  width: 100px;
  height: 100px;          /* same as width = square */
  border-radius: 50%;     /* square → circle */
  background-color: steelblue;
}
```

> 🌙 **Project connection:** Earth, the Moon and the orbit ring in Module 8 are all just squares with `border-radius: 50%`.

**Common beginner mistakes:**
- **Forgetting `border-box`:** boxes end up wider than planned and overflow their containers.
- **Circle looks like an oval:** `width` and `height` are not equal.
- **Setting width on inline elements:** `<span>` ignores `width`/`height`. Use `display: block` or `inline-block`, or use a `<div>`.
- **Confusing margin and padding:** padding is *inside* the border (background colour fills it); margin is *outside* (always transparent).

---

## How Sub-sections Connect

`2.1` shows the layers → `2.2` fixes the biggest sizing surprise → `2.3` gives you quick spacing syntax → `2.4` uses the box to create circles, which you'll use for planets.

---

## Key Terms Glossary

| Term             | Definition                                                           |
| ---------------- | -------------------------------------------------------------------- |
| **Box model**    | The idea that every element is a box of content/padding/border/margin |
| **Content**      | The text or media inside the box                                     |
| **Padding**      | Space between content and border                                     |
| **Border**       | A line around the padding                                            |
| **Margin**       | Space outside the border, separating elements                        |
| **`border-box`** | Sizing mode where `width` includes padding and border                |
| **`border-radius`** | Rounds corners; `50%` on a square makes a circle                  |

---

## Knowledge Check

1. List the four box model layers from inside to outside.
2. A `div` has `width: 200px; padding: 20px; border: 5px solid`. What is its total width with `content-box`? With `border-box`?
3. What does `margin: 10px 30px 20px 0;` mean for each side?
4. Write CSS for a 120px red circle.
5. **Scenario:** Your two 50%-wide columns wrap onto separate lines instead of sitting side by side, because each has `padding: 20px`. Explain why and fix it.

---

## Summary Recap

- Every element is a box: content → padding → border → margin.
- Always add `*, *::before, *::after { box-sizing: border-box; }`.
- Padding is inside the border; margin is outside.
- Shorthand values go clockwise: top, right, bottom, left.
- Equal `width` and `height` plus `border-radius: 50%` = a circle.

---
---

# MODULE 3 — Colors, Units & Typography

> Colors, sizes and text make a design feel intentional. This module also introduces CSS variables, which keep the Moon Orbit project easy to tweak.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Write colors using names, hex, `rgb()`/`rgba()` and `hsl()`.
2. Create `linear-gradient` and `radial-gradient` backgrounds and a `box-shadow` glow.
3. Choose between `px`, `rem`, `%`, `vw` and `vh`.
4. Declare and use CSS custom properties (variables).
5. Style text with `font-family`, `font-size`, `font-weight` and `line-height`.

---

## Section Breakdown

### 3.1 — Ways to Write a Color

| Format   | Example                      | Notes                                      |
| -------- | ---------------------------- | ------------------------------------------ |
| Name     | `tomato`                     | ~140 built-in names; fine for learning     |
| Hex      | `#ff6347`                    | Most common in design tools                |
| RGB      | `rgb(255, 99, 71)`           | Red, green, blue from 0–255                |
| RGBA     | `rgba(255, 255, 255, 0.3)`   | Adds **alpha** (transparency, 0 to 1)      |
| HSL      | `hsl(9, 100%, 64%)`          | Hue (0–360°), saturation, lightness. Easy to tweak |

```css
.sky {
  background-color: #0b1026;          /* deep night blue */
  color: rgba(255, 255, 255, 0.8);    /* slightly see-through white */
}
```

---

### 3.2 — Gradients and Glows

**Plain-language definition:**
A gradient is a smooth blend between colors, used as a background image. A `box-shadow` draws a soft shadow, or, with a light colour and no offset, a glow.

```css
/* Linear: straight line blend */
.banner {
  background: linear-gradient(to right, #ff7e5f, #feb47b);
}

/* Radial: blend outward from a point (perfect for spheres!) */
.planet {
  background: radial-gradient(circle at 30% 30%, #6fd0ff, #1b6ec2 60%, #0b3a75);
}

/* Glow: x-offset  y-offset  blur  color */
.planet {
  box-shadow: 0 0 30px rgba(80, 170, 255, 0.6);
}
```

**Why `radial-gradient` makes things look 3D:**
`circle at 30% 30%` puts the brightest point at the upper-left, as if a light source is shining from there. The darker edges make the flat circle read as a sphere.

---

### 3.3 — Units

| Unit   | Meaning                              | Best for                              |
| ------ | ------------------------------------ | ------------------------------------- |
| `px`   | Fixed pixels                         | Borders, small details, planet sizes  |
| `%`    | Percentage of the parent             | Fluid widths, `border-radius: 50%`    |
| `rem`  | Multiple of the root font size (16px default) | Font sizes and spacing         |
| `vw`/`vh` | 1% of viewport width / height     | Full-screen layouts (`100vh`)         |
| `s`/`ms` | Seconds / milliseconds             | Animation timing (Modules 6 & 7)      |

---

### 3.4 — CSS Variables (Custom Properties)

**Plain-language definition:**
A CSS variable stores a value once so you can reuse it. Declare it with two dashes, read it with `var()`. Declaring variables on `:root` makes them available everywhere.

**Why it matters:**
Change one number and the entire design updates. In the Moon Orbit project, you can resize the orbit or speed up the moon by editing a single line.

```css
:root {
  --orbit-size: 300px;
  --moon-size: 30px;
  --accent: #6fd0ff;
}

.moon {
  width: var(--moon-size);
  height: var(--moon-size);
}

.earth {
  box-shadow: 0 0 30px var(--accent);
}
```

**Analogy:**
Variables are like contacts in your phone. Instead of typing a long number every time, you save it under a name. If the number changes, update it in one place.

---

### 3.5 — Typography Basics

```css
body {
  font-family: "Segoe UI", Arial, sans-serif; /* fallbacks in order */
  font-size: 1rem;
  line-height: 1.6;       /* unitless: 1.6 × font size */
  color: #222;
}

h1 {
  font-size: 2.5rem;
  font-weight: 700;       /* 400 = normal, 700 = bold */
  text-align: center;
}
```

**Common beginner mistakes:**
- **Missing units:** `width: 100;` is invalid. Write `100px` (only `0` and `line-height` can be unitless).
- **Low contrast:** light grey text on white is unreadable for many people.
- **No fallback font:** always end `font-family` with a generic family like `sans-serif`.
- **Forgetting `var()`:** writing `width: --moon-size;` instead of `width: var(--moon-size);`.
- **Using spaces in variable names:** `--moon size` is invalid; use `--moon-size`.

---

## How Sub-sections Connect

`3.1` gives you colors → `3.2` turns flat colors into glowing spheres → `3.3` teaches sizing → `3.4` lets you store those colors and sizes in one place → `3.5` makes text readable.

---

## Key Terms Glossary

| Term                | Definition                                                            |
| ------------------- | --------------------------------------------------------------------- |
| **Hex color**       | A color written as `#rrggbb`                                          |
| **Alpha**           | Transparency level of a color (0 = invisible, 1 = solid)              |
| **Gradient**        | A smooth blend between two or more colors                             |
| **`box-shadow`**    | A shadow or glow drawn around an element's box                        |
| **`rem`**           | A unit relative to the root font size                                 |
| **Viewport**        | The visible area of the browser window                                |
| **Custom property** | A CSS variable declared with `--name` and read with `var(--name)`     |
| **`:root`**         | A selector matching the top of the document; the home for variables   |
| **Font stack**      | An ordered list of fonts to try, ending in a generic family           |

---

## Knowledge Check

1. Write the color orange three ways (name, hex, `rgb`).
2. What is the difference between `rgb(0,0,0)` and `rgba(0,0,0,0.5)`?
3. Write a `radial-gradient` that makes a gold sphere lit from the top-right.
4. Declare a `--size` variable of `80px` and use it for a square's width and height.
5. **Scenario:** Your design uses `#6fd0ff` in 14 places and the client wants a different blue. Describe how variables would have saved you time.

---

## Summary Recap

- Colors: names, hex, `rgb()`/`rgba()`, `hsl()`. Use alpha for transparency.
- `radial-gradient` + `box-shadow` turn flat circles into glowing spheres.
- Use `px` for fixed details, `rem` for text, `%`/`vh`/`vw` for fluid layouts.
- Variables: declare with `--name` in `:root`, use with `var(--name)`.
- Always include units and fallback fonts.

---
---

# MODULE 4 — Layout with Flexbox (and Grid Centering)

> Flexbox is the modern way to line things up. It also solves the most-asked CSS question of all time: "How do I centre this?"

---

## Learning Objectives

By the end of this section, you will be able to:

1. Turn a container into a flex container with `display: flex`.
2. Use `justify-content`, `align-items`, `gap` and `flex-direction`.
3. Centre an element horizontally and vertically.
4. Use the grid one-liner `place-items: center`.

---

## Section Breakdown

### 4.1 — What Is Flexbox?

**Plain-language definition:**
Flexbox is a layout system. You make a **parent** a flex container with `display: flex`, and its **direct children** become flex items that line up in a row (or column) and can be spaced and aligned with simple properties.

**Why it matters:**
Before Flexbox, centering and aligning elements required awkward hacks. Flexbox makes navigation bars, card rows and centred layouts easy.

**Analogy:**
A flex container is a shelf. The items on it can be pushed to the left, right or centre, spread out evenly, or stacked vertically, and you control it all from the shelf, not from each item.

**Concrete example:**

```html
<div class="row">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
</div>
```

```css
.row {
  display: flex;
  gap: 16px;           /* space between items */
}

.box {
  width: 80px;
  height: 80px;
  background: tomato;
}
```

---

### 4.2 — Main Axis vs. Cross Axis

```
flex-direction: row (default)

 main axis  ─────────────────►
 ┌───────┐ ┌───────┐ ┌───────┐   │
 │   1   │ │   2   │ │   3   │   │ cross axis
 └───────┘ └───────┘ └───────┘   ▼
```

| Property          | Controls…                          | Common values                                   |
| ----------------- | ---------------------------------- | ----------------------------------------------- |
| `flex-direction`  | Which way the main axis points     | `row`, `column`                                 |
| `justify-content` | Alignment along the **main** axis  | `flex-start`, `center`, `flex-end`, `space-between`, `space-around` |
| `align-items`     | Alignment along the **cross** axis | `stretch`, `flex-start`, `center`, `flex-end`   |
| `gap`             | Space between items                | `10px`, `1rem`                                  |
| `flex-wrap`       | Whether items wrap to a new line   | `nowrap`, `wrap`                                |

> **Memory trick:** `justify` = along the main axis, `align` = across it. When you switch to `flex-direction: column`, the axes swap too.

---

### 4.3 — Centering Anything

```css
.page {
  display: flex;
  justify-content: center;   /* horizontal centre */
  align-items: center;       /* vertical centre */
  min-height: 100vh;         /* the container must be tall enough! */
}
```

---

### 4.4 — The Grid One-Liner

**Plain-language definition:**
CSS Grid is a two-dimensional layout system. You don't need to learn it fully yet, but this shortcut centres children both ways with less code than Flexbox:

```css
.page {
  display: grid;
  place-items: center;
  min-height: 100vh;
}
```

> 🌙 **Project connection:** The Moon Orbit uses `display: grid; place-items: center;` to put the page's content in the middle of the screen *and* to put Earth in the middle of the orbit ring.

**Common beginner mistakes:**
- **Putting flex properties on the children:** `justify-content` belongs on the **container**.
- **Forgetting height:** vertical centering does nothing if the container is only as tall as its content. Add `min-height: 100vh`.
- **Confusing the axes** after switching to `flex-direction: column`.
- **Expecting grandchildren to move:** flex only controls *direct* children.

---

## How Sub-sections Connect

`4.1` introduces the idea → `4.2` explains the two axes that make every property make sense → `4.3` solves the classic centering problem → `4.4` offers a shorter way that you'll use in the project.

---

## Key Terms Glossary

| Term                | Definition                                                        |
| ------------------- | ----------------------------------------------------------------- |
| **Flex container**  | An element with `display: flex`                                   |
| **Flex item**       | A direct child of a flex container                                |
| **Main axis**       | The direction items flow (row = horizontal by default)            |
| **Cross axis**      | The axis perpendicular to the main axis                           |
| **`justify-content`** | Aligns items along the main axis                                |
| **`align-items`**   | Aligns items along the cross axis                                 |
| **`gap`**           | Space between flex or grid items                                  |
| **`place-items`**   | Grid shorthand for aligning items on both axes                    |
| **`vh`**            | 1% of the viewport height                                         |

---

## Knowledge Check

1. Which element gets `display: flex`: the parent or the children?
2. What is the difference between `justify-content` and `align-items`?
3. Write CSS that centres a single `.box` in the exact middle of the screen using Flexbox.
4. Rewrite your answer to question 3 using Grid.
5. **Scenario:** You wrote `display: flex; align-items: center;` but your content is still stuck at the top. What is the likely cause?

---

## Summary Recap

- `display: flex` on a parent lines up its direct children.
- `justify-content` works on the main axis; `align-items` on the cross axis.
- `gap` adds space between items without margin hacks.
- Centre anything with flex (`justify-content` + `align-items`) or grid (`place-items: center`).
- The container needs height (`min-height: 100vh`) for vertical centering to show.

---
---

# MODULE 5 — Position & Transform

> Position decides *where* an element sits. Transform decides how it moves, spins and scales. These two are the foundation of CSS animation.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Explain `position: static`, `relative` and `absolute`.
2. Use `top`, `left` and `inset` to place absolutely positioned elements.
3. Move, rotate and scale elements with `transform`.
4. Explain what `transform-origin` does.
5. Explain why animating with `transform` is better than animating `top`/`left`.

---

## Section Breakdown

### 5.1 — Position

**Plain-language definition:**
The `position` property controls how an element is placed on the page.

| Value      | Behaviour                                                                         |
| ---------- | --------------------------------------------------------------------------------- |
| `static`   | Default. Normal flow; `top`/`left` do nothing                                     |
| `relative` | Stays in the normal flow, but becomes the **anchor** for absolute children        |
| `absolute` | Removed from the flow. Placed relative to the nearest positioned ancestor         |

**Analogy:**
Imagine a corkboard (the `relative` parent) and sticky notes (the `absolute` children). Each note is pinned at a position measured *from the corkboard's edges*, not from the wall behind it. If the board isn't positioned, the note is measured from the whole wall (the page).

**Concrete example:**

```html
<div class="board">
  <div class="note"></div>
</div>
```

```css
.board {
  position: relative;      /* ← the anchor! */
  width: 300px;
  height: 300px;
  background: #eee;
}

.note {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 50px;
  height: 50px;
  background: gold;
}
```

**Handy shortcut:** `inset: 0;` is shorthand for `top: 0; right: 0; bottom: 0; left: 0;`. An absolute child with `inset: 0` fills its parent completely.

---

### 5.2 — Transform

**Plain-language definition:**
`transform` changes how an element is drawn (moved, rotated, scaled) *without* changing the space it takes up in the layout.

```css
.a { transform: translateX(50px); }        /* move right 50px */
.b { transform: translate(20px, -10px); }  /* move right 20, up 10 */
.c { transform: rotate(45deg); }           /* spin 45° clockwise */
.d { transform: scale(1.5); }              /* 150% size */
.e { transform: translate(-50%, -50%); }   /* move by half its OWN size */
```

**Key trick:** percentages inside `translate()` refer to the **element's own size**, not its parent. That makes `translate(-50%, -50%)` perfect for centring an element on a point.

**Multiple transforms** go in one declaration, applied **right to left**:

```css
.f { transform: translateX(100px) rotate(45deg); }
```

---

### 5.3 — `transform-origin`

**Plain-language definition:**
Every rotation and scale happens around a point called the origin. By default it is the element's centre (`50% 50%`). Change it with `transform-origin`.

```css
.door {
  transform-origin: left center;   /* hinge on the left edge */
  transform: rotate(-30deg);
}
```

**Analogy:**
Spin a pencil with your finger in the middle: it turns in place. Pin it at one end and spin it: the other end sweeps around in a big circle. That second one is an *orbit*, and it is the secret to the Moon Orbit project.

---

### 5.4 — Why Transform Beats `top`/`left` for Animation

Moving an element by changing `top` or `left` forces the browser to recalculate the layout for the whole page on every frame, which can cause stuttering. `transform` (and `opacity`) are handled by the graphics card and don't disturb the layout, so they are smooth.

**Rule of thumb:** *to move something, use `transform`; to place something, use `position`.*

**Common beginner mistakes:**
- **Forgetting `position: relative` on the parent:** the absolute child jumps to a corner of the whole page.
- **Using `rotate` without a unit:** `rotate(45)` is invalid; write `rotate(45deg)`.
- **Overwriting transforms:** a second `transform` declaration *replaces* the first. Combine them in one line.
- **Expecting transform to push neighbours:** it doesn't affect the layout, so other elements won't move out of the way.

---

## How Sub-sections Connect

`5.1` lets you place things → `5.2` lets you move and spin them → `5.3` lets you choose the pivot point → `5.4` explains why this is the right tool for animation, setting up Modules 6 and 7.

---

## Key Terms Glossary

| Term                   | Definition                                                              |
| ---------------------- | ----------------------------------------------------------------------- |
| **`position: relative`** | Keeps normal flow; becomes the reference for absolute children        |
| **`position: absolute`** | Removes from flow; positioned against the nearest positioned ancestor |
| **`inset`**            | Shorthand for `top`, `right`, `bottom`, `left`                          |
| **`transform`**        | Moves, rotates, scales or skews an element visually                     |
| **`translate()`**      | Moves an element along X and/or Y                                       |
| **`rotate()`**         | Turns an element by an angle in `deg`                                   |
| **`scale()`**          | Resizes an element visually by a multiplier                             |
| **`transform-origin`** | The pivot point for rotation and scaling                                |

---

## Knowledge Check

1. Why does an `absolute` child sometimes appear in the corner of the page instead of its parent?
2. What does `inset: 0` do?
3. Write CSS that places a 20px dot exactly in the centre of a 200px `relative` box, using `top`, `left` and `translate`.
4. What is the difference between `transform: translateX(50px)` and `left: 50px`? Which is better for animation?
5. **Scenario:** `transform: translateX(100px); transform: rotate(45deg);` only rotates the element. Why, and how do you fix it?

---

## Summary Recap

- `position: relative` on a parent + `position: absolute` on a child = precise placement.
- `inset: 0` makes an absolute child fill its parent.
- `transform` moves (`translate`), turns (`rotate`) and resizes (`scale`) without affecting layout.
- Percentages in `translate()` are relative to the element's own size.
- `transform-origin` sets the pivot point; a faraway pivot creates an orbit.
- Animate `transform` and `opacity` for smooth results.

---
---

# MODULE 6 — Transitions

> Transitions are the gentlest introduction to animation: "when this changes, take your time getting there."

---

## Learning Objectives

By the end of this section, you will be able to:

1. Explain what a CSS transition is and what triggers it.
2. Write a `transition` using property, duration, timing function and delay.
3. Build a hover effect that grows, glows or changes colour smoothly.
4. Explain where to place the `transition` declaration, and why.

---

## Section Breakdown

### 6.1 — What Is a Transition?

**Plain-language definition:**
A transition makes the browser animate smoothly between two values of a property instead of switching instantly. You define a starting state, an ending state, and *how long it takes* to travel between them.

**Why it matters:**
Instant changes feel abrupt and cheap. A 0.3-second transition makes buttons, menus and cards feel polished and alive, with only one line of CSS.

**Analogy:**
A light switch vs. a dimmer. A normal style change is a switch: instantly on or off. A transition is a dimmer: the light fades smoothly.

**Concrete example:**

```css
.button {
  background-color: steelblue;
  transition: background-color 0.3s ease;   /* ← the dimmer */
}

.button:hover {
  background-color: orange;                 /* ← the destination */
}
```

---

### 6.2 — Transition Properties

```css
.card {
  transition-property: transform;
  transition-duration: 0.4s;
  transition-timing-function: ease-in-out;
  transition-delay: 0s;
}

/* Shorthand (same thing): property duration timing-function delay */
.card {
  transition: transform 0.4s ease-in-out 0s;
}
```

| Part              | Meaning                              | Example values                         |
| ----------------- | ------------------------------------ | -------------------------------------- |
| **property**      | Which property to animate            | `transform`, `opacity`, `background-color` |
| **duration**      | How long it takes                    | `0.3s`, `300ms`                        |
| **timing-function** | The speed curve                    | `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out` |
| **delay**         | Wait before starting                 | `0s`, `0.2s`                           |

**Timing functions explained:**

| Name         | Feel                                    |
| ------------ | --------------------------------------- |
| `linear`     | Constant speed (robotic, good for spinning) |
| `ease`       | Starts fast, ends slow (the default)    |
| `ease-in`    | Starts slowly, ends fast                |
| `ease-out`   | Starts fast, ends slowly (feels natural for things appearing) |
| `ease-in-out`| Slow at both ends                       |

---

### 6.3 — A Practical Hover Effect

```html
<div class="planet"></div>
```

```css
.planet {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #6fd0ff, #1b6ec2 60%, #0b3a75);
  box-shadow: 0 0 10px rgba(80, 170, 255, 0.4);
  transition: transform 0.3s ease-out, box-shadow 0.3s ease-out;
}

.planet:hover {
  transform: scale(1.15);
  box-shadow: 0 0 40px rgba(80, 170, 255, 0.9);
}
```

Hover over the planet: it grows and glows. Move away: it shrinks back smoothly. Separate multiple transitions with commas.

> 🌙 **Project connection:** In Module 8 you'll add this same hover effect to Earth.

---

### 6.4 — Limits of Transitions

A transition can only travel **between two states** and **needs a trigger** (like `:hover`, `:focus` or a class change). It cannot loop forever or run on page load by itself. For that you need `@keyframes` (Module 7).

**Common beginner mistakes:**
- **Putting `transition` only on `:hover`:** the element animates *in* but snaps back *out*. Put `transition` on the **base** rule so it works both ways.
- **Using `transition: all`:** it animates everything, including things you didn't intend, and wastes performance. Name the properties.
- **No duration:** `transition: transform ease;` has a default duration of `0s`, so nothing visibly happens.
- **Trying to transition `display`:** it can't be animated. Use `opacity` or `transform` instead.
- **Animating properties that can't be interpolated:** `width: auto` to `width: 200px` jumps. Use numbers on both sides.

---

## How Sub-sections Connect

`6.1` introduces the idea → `6.2` breaks down the syntax → `6.3` puts it into a real effect → `6.4` explains where transitions end, which is exactly where keyframe animation begins.

---

## Key Terms Glossary

| Term                | Definition                                                              |
| ------------------- | ----------------------------------------------------------------------- |
| **Transition**      | A smooth change between two states of a property                        |
| **Trigger**         | An event or state that starts a transition (`:hover`, `:focus`, class change) |
| **Duration**        | How long the transition lasts                                           |
| **Timing function** | The speed curve of the transition                                       |
| **Delay**           | How long to wait before the transition begins                           |
| **Interpolation**   | The browser calculating all the in-between values                       |

---

## Knowledge Check

1. What is the difference between a normal style change and a transition?
2. Where should the `transition` declaration go: on the base rule or on `:hover`? Why?
3. Write a button that smoothly changes from green to darkgreen in 0.5 seconds on hover.
4. Why is `transition: all 1s` considered a bad habit?
5. **Scenario:** You want a moon to circle the Earth forever as soon as the page loads. Can a transition do this? Why or why not?

---

## Summary Recap

- A transition animates smoothly between two states of a property.
- Shorthand: `transition: property duration timing-function delay;`.
- Put `transition` on the **base** rule so it plays in both directions.
- Name specific properties; prefer `transform` and `opacity`.
- Transitions need a trigger and can't loop, so for looping animation, use `@keyframes`.

---
---

# MODULE 7 — Keyframe Animation

> Keyframes let you choreograph a full animation: multiple steps, automatic looping and no trigger required. This is the module that makes the Moon Orbit move.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Write an `@keyframes` rule with `from`/`to` and with percentages.
2. Attach an animation to an element with the `animation` property.
3. Control duration, timing, delay, iteration count, direction and fill mode.
4. Pause and resume an animation with `animation-play-state`.
5. Build a pulse, a float and a spin animation.

---

## Section Breakdown

### 7.1 — What Is `@keyframes`?

**Plain-language definition:**
`@keyframes` defines a named animation: a list of *key moments* and what the element should look like at each one. The browser calculates all the frames in between automatically (this is called *tweening*).

**Why it matters:**
Keyframes unlock animations that loop, bounce, have many steps, and start automatically, none of which transitions can do.

**Analogy:**
A flipbook animator draws only the important poses (key frames), such as the start, the middle and the end, and an assistant draws all the in-between pictures. You are the animator; the browser is the assistant.

**Two steps are always needed:**

```css
/* STEP 1: Define the animation (the choreography) */
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

/* STEP 2: Attach it to an element (the performer) */
.loader {
  animation: spin 2s linear infinite;
}
```

---

### 7.2 — `from`/`to` vs. Percentages

For more than two steps, use percentages of the total duration.

```css
@keyframes pulse {
  0%   { transform: scale(1);   opacity: 1; }
  50%  { transform: scale(1.2); opacity: 0.6; }
  100% { transform: scale(1);   opacity: 1; }
}
```

Tip: end on the same state you started with (`0%` and `100%` match) for a seamless loop.

---

### 7.3 — The `animation` Properties

```css
.thing {
  animation-name: pulse;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 0s;
  animation-iteration-count: infinite;
  animation-direction: normal;
  animation-fill-mode: none;
  animation-play-state: running;
}

/* Shorthand: name duration timing-function delay iteration-count direction fill-mode */
.thing {
  animation: pulse 2s ease-in-out 0s infinite normal none;
}
```

| Property                    | What it does                                  | Common values                          |
| --------------------------- | --------------------------------------------- | -------------------------------------- |
| `animation-name`            | Which `@keyframes` to use                     | `pulse`, `spin`                        |
| `animation-duration`        | How long one cycle takes                      | `2s`, `500ms`                          |
| `animation-timing-function` | Speed curve                                   | `linear`, `ease-in-out`                |
| `animation-delay`           | Wait before starting (negative = start mid-way) | `0s`, `1s`, `-2s`                    |
| `animation-iteration-count` | How many times to play                        | `1`, `3`, `infinite`                   |
| `animation-direction`       | Which way it plays                            | `normal`, `reverse`, `alternate`       |
| `animation-fill-mode`       | Styles before/after playing                   | `none`, `forwards`, `both`             |
| `animation-play-state`      | Pause or resume                               | `running`, `paused`                    |

**Which timing function when?**
- **`linear`** for constant motion: spinning wheels, **orbits**, loading spinners.
- **`ease-in-out`** for natural back-and-forth motion: floating, pulsing, bouncing.

---

### 7.4 — Three Classic Animations

**1. Pulse (breathing glow)**

```css
@keyframes pulse {
  0%, 100% { box-shadow: 0 0 10px rgba(111, 208, 255, 0.4); }
  50%      { box-shadow: 0 0 35px rgba(111, 208, 255, 0.9); }
}
.glow { animation: pulse 3s ease-in-out infinite; }
```

**2. Float (gentle up-and-down)**

```css
@keyframes float {
  from { transform: translateY(0); }
  to   { transform: translateY(-20px); }
}
.balloon { animation: float 2s ease-in-out infinite alternate; }
```

`alternate` plays forward, then backward, so you only write half the motion.

**3. Spin (loader)**

```css
@keyframes spin {
  to { transform: rotate(360deg); }
}
.spinner { animation: spin 1s linear infinite; }
```

(If you leave out `from`, the browser uses the element's current style as the start.)

---

### 7.5 — Pausing on Hover

```css
.spinner:hover {
  animation-play-state: paused;
}
```

The animation freezes exactly where it is and resumes from that point, with no jump.

**Common beginner mistakes:**
- **Name mismatch:** `animation: spinn 2s` when the keyframes are named `spin`. Nothing happens.
- **Forgetting the duration:** `animation: spin infinite;` has a default duration of `0s`, so it never visibly runs.
- **Mixing up the two times in the shorthand:** the **first** time value is the duration; the **second** is the delay.
- **Forgetting `infinite`:** the animation plays once and stops.
- **Using `ease` for orbits and spinners:** the speed-up/slow-down makes each rotation feel jerky. Use `linear`.
- **Overriding a base transform:** if an element is centred with `transform: translate(-50%, -50%)` and you animate `transform`, the keyframes *replace* the centring. Centre with another method (like grid or `top/left` + margin), or include `translate(-50%, -50%)` inside every keyframe.
- **Animating `top`/`left`/`width`:** causes layout recalculations and jank. Prefer `transform`.

---

## How Sub-sections Connect

`7.1` introduces the two-step pattern → `7.2` extends it to multi-step animations → `7.3` gives you full control → `7.4` shows three reusable examples → `7.5` adds interactivity. Next, you'll combine a spinning animation, a pivot point and absolute positioning to build an orbit.

---

## Key Terms Glossary

| Term                          | Definition                                                         |
| ----------------------------- | ------------------------------------------------------------------ |
| **`@keyframes`**              | An at-rule that defines the steps of a named animation             |
| **Keyframe**                  | A moment in the animation with specific styles (`from`, `50%`, `to`) |
| **Tweening**                  | The browser generating the in-between frames                       |
| **`animation`**               | Shorthand that attaches a keyframe animation to an element         |
| **`infinite`**                | Loops the animation forever                                        |
| **`alternate`**               | Plays forwards then backwards on alternate cycles                  |
| **Fill mode**                 | Whether styles from the first/last keyframe persist outside the animation |
| **`animation-play-state`**    | Pauses (`paused`) or resumes (`running`) an animation              |

---

## Knowledge Check

1. What two things must you write to make an element animate?
2. What is the difference between a transition and a keyframe animation? Give one thing keyframes can do that transitions can't.
3. Why use `linear` instead of `ease` for a spinning loader?
4. Write a keyframe animation named `fade-in` that goes from invisible to fully visible in 1.5 seconds and plays once.
5. **Scenario:** You wrote `animation: bounce infinite;` and nothing moves. Name two possible causes.

---

## Summary Recap

- Animation = `@keyframes` (what happens) + `animation` property (play it).
- Use `from`/`to` for simple animations and percentages for multi-step ones.
- Shorthand order: name, duration, timing-function, delay, iteration-count, direction, fill-mode.
- Use `linear infinite` for continuous rotation and `ease-in-out infinite alternate` for floating or pulsing.
- `animation-play-state: paused` freezes an animation, which is handy for hover.
- Animate `transform` and `opacity`; watch for keyframes overriding existing transforms.

---
---

# MODULE 8 — 🌙 Project: Build a Moon Orbit

> Time to combine everything. In this guided project, students build a glowing Earth with a moon that circles it forever, using only HTML and CSS: no JavaScript, no images.

---

## Learning Objectives

By the end of this project, you will be able to:

1. Plan a CSS illustration by breaking it into simple shapes.
2. Build circles, gradients and glows using the box model and colour tools.
3. Centre elements with grid and position a child on the edge of a circle.
4. Create an orbit by animating the rotation of a parent container.
5. Polish the result with variables, a hover pause and a glow pulse.
6. Customise and extend the project independently.

---

## Section Breakdown

### 8.1 — The Plan: How Does an Orbit Work?

**Plain-language definition:**
We can't make an element "orbit" directly in CSS. Instead, we use a clever trick: put the moon at the edge of an invisible arm that is pinned to Earth's centre, then **rotate the arm**. The moon is carried around in a circle.

**Analogy:**
Imagine a child sitting at the end of a spinning merry-go-round. The child doesn't move on their own. The *platform* rotates, and the child goes along for the ride. Here: the platform is `.moon-track`, the child is `.moon`.

**The three characters:**

```
┌───────────────── .orbit (the ring, fixed) ────────────────┐
│                                                            │
│            ┌─── .moon-track (invisible arm, ROTATES) ───┐  │
│            │                                            │  │
│            │         🌍 .earth (centre)                 │  │
│     🌙 ◄───┤                                            │  │
│  .moon     │                                            │  │
│ (on the    └────────────────────────────────────────────┘  │
│  left edge)                                                │
└────────────────────────────────────────────────────────────┘
```

**Which earlier modules do we use?**

| Skill                                  | Module |
| -------------------------------------- | ------ |
| Circles with `border-radius: 50%`      | 2      |
| Gradients, glow, CSS variables         | 3      |
| Grid centering                         | 4      |
| `position: absolute`, `translate`      | 5      |
| Hover effect                           | 6      |
| `@keyframes` + `animation`             | 7      |

---

### 8.2 — Step 1: The HTML

Keep the HTML tiny. Each element is one shape.

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Moon Orbit</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="orbit">
    <div class="earth"></div>

    <div class="moon-track">
      <div class="moon"></div>
    </div>
  </div>

</body>
</html>
```

---

### 8.3 — Step 2: Reset, Variables and the Night Sky

```css
/* style.css */

*,
*::before,
*::after {
  box-sizing: border-box;
}

:root {
  --orbit-size: 300px;
  --earth-size: 90px;
  --moon-size: 30px;
  --orbit-time: 10s;
}

body {
  margin: 0;
  min-height: 100vh;
  display: grid;
  place-items: center;          /* centre the orbit on the screen */
  background-color: #0b1026;    /* deep night blue */
}
```

**Checkpoint:** you should see a dark blue page. Nothing else yet.

---

### 8.4 — Step 3: The Orbit Ring

```css
.orbit {
  position: relative;                      /* anchor for absolute children */
  width: var(--orbit-size);
  height: var(--orbit-size);
  border: 1px dashed rgba(255, 255, 255, 0.3);
  border-radius: 50%;                      /* square → circle */
  display: grid;
  place-items: center;                     /* Earth sits in the exact centre */
}
```

**Checkpoint:** a faint dashed circle in the middle of the screen.

**Why `position: relative`?** The `.moon-track` will be absolutely positioned, and we want it measured from *this* circle, not from the whole page (Module 5).

---

### 8.5 — Step 4: Earth

```css
.earth {
  width: var(--earth-size);
  height: var(--earth-size);
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #6fd0ff, #1b6ec2 60%, #0b3a75);
  box-shadow: 0 0 30px rgba(80, 170, 255, 0.5);
}
```

**Checkpoint:** a glowing blue sphere in the middle of the ring.

---

### 8.6 — Step 5: The Moon Track and the Moon

This is the key step. Read it slowly.

```css
.moon-track {
  position: absolute;
  inset: 0;                 /* same size as .orbit, so its centre = Earth's centre */
}

.moon {
  position: absolute;
  top: 50%;                 /* halfway down… */
  left: 0;                  /* …on the left edge of the track */
  width: var(--moon-size);
  height: var(--moon-size);
  transform: translate(-50%, -50%);   /* centre the moon ON that edge point */
  border-radius: 50%;
  background: radial-gradient(circle at 35% 30%, #f5f5f0, #b9b9b4 70%, #8a8a86);
}
```

**What's happening:**
1. `.moon-track` fills the ring (`inset: 0`), so its **centre is Earth's centre**.
2. `.moon` is placed at `top: 50%; left: 0`: the middle of the track's left edge, which is exactly on the orbit line.
3. `translate(-50%, -50%)` shifts the moon back by half its own size so its *centre* (not its top-left corner) sits on the line.

**Checkpoint:** a grey moon sits on the left of the dashed ring. It isn't moving yet.

---

### 8.7 — Step 6: Make It Orbit! 🚀

```css
.moon-track {
  position: absolute;
  inset: 0;
  animation: orbit var(--orbit-time) linear infinite;
}

@keyframes orbit {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
```

**Why this works:**
- `rotate()` spins an element around its centre, and the track's centre is Earth's centre (Module 5.3).
- The moon is pinned to the track's edge, so as the track turns, the moon sweeps around a circle with a radius of half the track.
- `linear` keeps the speed constant. `infinite` repeats forever.

🎉 **Checkpoint:** the moon circles Earth every 10 seconds.

> **Fun fact:** the real Moon is *tidally locked*, so the same face always points at Earth. Because our moon rotates together with its track, it does exactly the same, and its face always points toward Earth too.

---

### 8.8 — Step 7: Polish

**Stars in the sky** (several tiny radial gradients tiled across the page):

```css
body {
  background-color: #0b1026;
  background-image:
    radial-gradient(1px 1px at 20px 30px,  #fff, transparent),
    radial-gradient(1.5px 1.5px at 90px 70px, #fff, transparent),
    radial-gradient(1px 1px at 130px 20px, #fff, transparent),
    radial-gradient(1px 1px at 60px 120px, #fff, transparent);
  background-size: 160px 160px;
}
```

**Moon craters** (using a pseudo-element, so no extra HTML):

```css
.moon::before {
  content: "";
  position: absolute;
  top: 6px;
  left: 14px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.15);
  box-shadow: -8px 12px 0 -1px rgba(0, 0, 0, 0.12);   /* a second crater */
}
```

**Earth hover effect** (Module 6):

```css
.earth {
  transition: transform 0.3s ease-out, box-shadow 0.3s ease-out;
}

.earth:hover {
  transform: scale(1.1);
  box-shadow: 0 0 50px rgba(80, 170, 255, 0.9);
}
```

**Pause the orbit on hover** (Module 7.5):

```css
.orbit:hover .moon-track {
  animation-play-state: paused;
}
```

**Earth glow pulse** (Module 7.4):

```css
@keyframes earth-glow {
  0%, 100% { box-shadow: 0 0 25px rgba(80, 170, 255, 0.4); }
  50%      { box-shadow: 0 0 45px rgba(80, 170, 255, 0.8); }
}

.earth {
  animation: earth-glow 4s ease-in-out infinite;
}
```

> ⚠️ **Heads-up:** `.earth:hover` also sets `box-shadow`, but the running `animation` takes priority over normal styles, so the hover glow will not show while the pulse runs. Students will notice this. It makes a great discussion about the cascade (Module 1.4). To keep both, remove the `box-shadow` from `.earth:hover` and keep only the `scale`.

---

### 8.9 — The Complete Code

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Moon Orbit</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="orbit">
    <div class="earth"></div>

    <div class="moon-track">
      <div class="moon"></div>
    </div>
  </div>

</body>
</html>
```

**style.css**

```css
/* ============================================
   MOON ORBIT: pure HTML & CSS
   ============================================ */

/* ---------- 1. Reset ---------- */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* ---------- 2. Variables (edit these to customise!) ---------- */
:root {
  --orbit-size: 300px;
  --earth-size: 90px;
  --moon-size: 30px;
  --orbit-time: 10s;
}

/* ---------- 3. Night sky ---------- */
body {
  margin: 0;
  min-height: 100vh;
  display: grid;
  place-items: center;
  background-color: #0b1026;
  background-image:
    radial-gradient(1px 1px at 20px 30px,     #fff, transparent),
    radial-gradient(1.5px 1.5px at 90px 70px, #fff, transparent),
    radial-gradient(1px 1px at 130px 20px,    #fff, transparent),
    radial-gradient(1px 1px at 60px 120px,    #fff, transparent);
  background-size: 160px 160px;
}

/* ---------- 4. The orbit ring ---------- */
.orbit {
  position: relative;
  width: var(--orbit-size);
  height: var(--orbit-size);
  border: 1px dashed rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  display: grid;
  place-items: center;
}

/* ---------- 5. Earth ---------- */
.earth {
  width: var(--earth-size);
  height: var(--earth-size);
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #6fd0ff, #1b6ec2 60%, #0b3a75);
  box-shadow: 0 0 30px rgba(80, 170, 255, 0.5);
  transition: transform 0.3s ease-out;
  animation: earth-glow 4s ease-in-out infinite;
}

.earth:hover {
  transform: scale(1.1);
}

/* ---------- 6. The rotating arm and the moon ---------- */
.moon-track {
  position: absolute;
  inset: 0;
  animation: orbit var(--orbit-time) linear infinite;
}

.moon {
  position: absolute;
  top: 50%;
  left: 0;
  width: var(--moon-size);
  height: var(--moon-size);
  transform: translate(-50%, -50%);
  border-radius: 50%;
  background: radial-gradient(circle at 35% 30%, #f5f5f0, #b9b9b4 70%, #8a8a86);
}

.moon::before {
  content: "";
  position: absolute;
  top: 6px;
  left: 14px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.15);
  box-shadow: -8px 12px 0 -1px rgba(0, 0, 0, 0.12);
}

/* ---------- 7. Interaction ---------- */
.orbit:hover .moon-track {
  animation-play-state: paused;
}

/* ---------- 8. Animations ---------- */
@keyframes orbit {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

@keyframes earth-glow {
  0%, 100% { box-shadow: 0 0 25px rgba(80, 170, 255, 0.4); }
  50%      { box-shadow: 0 0 45px rgba(80, 170, 255, 0.8); }
}

/* ---------- 9. Accessibility: respect reduced-motion settings ---------- */
@media (prefers-reduced-motion: reduce) {
  .moon-track,
  .earth {
    animation: none;
  }
}
```

---

### 8.10 — Alternative Technique: Orbit Without a Track

**Plain-language definition:**
You can also orbit a single element, with no `.moon-track`, by chaining transforms inside the keyframes: *rotate → move outward → rotate back*.

```css
.moon {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 30px;
  height: 30px;
  margin: -15px 0 0 -15px;            /* centre on the middle of .orbit */
  border-radius: 50%;
  background: #ccc;
  animation: orbit-b 10s linear infinite;
}

@keyframes orbit-b {
  from { transform: rotate(0deg)   translateX(150px) rotate(0deg); }
  to   { transform: rotate(360deg) translateX(150px) rotate(-360deg); }
}
```

**How it reads (right to left, remember Module 5.2):** first the final `rotate` keeps the moon's face upright, then `translateX(150px)` pushes it out to the orbit's radius, then the first `rotate` swings it around the centre.

**Trade-offs:**

| Technique              | Pros                                      | Cons                                          |
| ---------------------- | ----------------------------------------- | --------------------------------------------- |
| **A: Rotating track**  | Easy to understand; moon is tidally locked | Needs an extra HTML element                   |
| **B: Chained transforms** | No extra element; moon stays upright   | The radius is hard-coded; harder to read      |

---

### 8.11 — Troubleshooting Table

| Symptom                                          | Likely cause                                              | Fix                                                                |
| ------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------------ |
| Nothing is styled                                | `<link>` path wrong or missing                            | Check `href="style.css"` and the file name                         |
| The orbit ring is an oval                         | `width` ≠ `height`                                        | Use the same variable for both                                     |
| The moon is in the page corner                   | `.orbit` is missing `position: relative`                  | Add it to `.orbit`                                                 |
| The moon orbits a point that isn't Earth         | `.moon-track` isn't `inset: 0`, or the ring isn't centred | Set `position: absolute; inset: 0;`                                |
| The moon is off the ring line                    | Missing `translate(-50%, -50%)` on `.moon`                | Add the transform to centre the moon                               |
| The moon doesn't move                            | Keyframe name mismatch, or missing duration               | Check `animation: orbit var(--orbit-time) linear infinite`         |
| The moon speeds up and slows down                | `ease` timing function                                    | Use `linear`                                                       |
| Variables don't work                             | `var()` missing, or variable name typo                    | Write `var(--moon-size)`, check spelling                           |
| The moon moves, but Earth moves too              | Animation applied to `.orbit` instead of `.moon-track`    | Animate only `.moon-track`                                         |

---

### 8.12 — Extension Challenges

**🟢 Easy**
1. Change `--orbit-time` to `4s`, then `30s`. How does the feel change?
2. Change the sizes with variables to make a giant moon and a tiny Earth.
3. Recolour Earth to look like Mars (red/orange gradient).

**🟡 Medium**
4. Add a second moon with a different size, a different speed and a different starting position. *(Hint: you'll need a second track. Use a negative `animation-delay` such as `-5s` to start it halfway round, and a different `--orbit-size` or inset to give it a smaller ring.)*
5. Add a **sun** in a corner that slowly rotates and pulses.
6. Add `animation-direction: reverse` so the moon orbits the opposite way.

**🔴 Hard**
7. Give the scene a 3D tilt by adding `transform: rotateX(65deg);` to `.orbit`. What happens to the planets? *(Hint: they flatten into ovals. Can you counter-rotate them?)*
8. Create a **solar system**: a sun, three planets at different radii and speeds, each with its own track.
9. Make the orbit responsive using `min(80vw, 400px)` for `--orbit-size`.

---

## How Sub-sections Connect

`8.1` plans the illustration → `8.2`–`8.6` build the static scene one shape at a time (checking each step) → `8.7` adds the single rotation that creates the orbit → `8.8` polishes using hover, pseudo-elements and extra animation → `8.9` gives the finished code → `8.10` shows an alternative technique → `8.11` helps debug → `8.12` pushes students to create on their own.

---

## Key Terms Glossary

| Term                  | Definition                                                                      |
| --------------------- | ------------------------------------------------------------------------------- |
| **Orbit**             | A circular path an object travels around a central point                        |
| **Track (arm)**       | An invisible element, centred on the pivot, that rotates to carry its child     |
| **Pivot**             | The point an element rotates around (default: its centre)                       |
| **Tidal locking**     | When an orbiting body always shows the same face to what it circles             |
| **Pseudo-element**    | A CSS-generated element (`::before`/`::after`) that needs no HTML               |
| **`content: ""`**     | Required to make a pseudo-element appear                                        |
| **Negative delay**    | `animation-delay: -5s` starts the animation as if it's already 5 seconds in     |
| **Radial gradient**   | A colour blend radiating from a point; used to fake a 3D sphere                 |

---

## Knowledge Check

1. In your own words, explain how rotating an *invisible* element makes the moon orbit Earth.
2. Why must `.orbit` have `position: relative`?
3. What does `translate(-50%, -50%)` do to the moon, and what would you see without it?
4. Change the project so the moon takes 20 seconds per orbit and moves anticlockwise. Which two things do you edit?
5. **Scenario:** A student animates `.orbit` instead of `.moon-track`. The whole ring, Earth *and* moon spin in place. Why, and how do they fix it?
6. **Build it:** Add a second moon that starts on the opposite side of the orbit and moves at the same speed.

---

## Summary Recap

- An orbit = a child pinned to the edge of an invisible parent that rotates around its centre.
- `border-radius: 50%` makes circles; `radial-gradient` + `box-shadow` makes them look like glowing spheres.
- `display: grid; place-items: center;` centres the scene and Earth.
- `position: relative` (parent) + `position: absolute` (child) + `translate(-50%, -50%)` places the moon exactly on the ring.
- `@keyframes` rotating `0deg → 360deg` with `linear infinite` creates a seamless, endless orbit.
- Variables let you resize and re-time the whole scene by changing one line.
- `animation-play-state: paused` and `transition` add polish and interactivity.

---
---

# MODULE 9 — Accessibility, Performance & Debugging

> Great animation isn't just pretty; it's comfortable to use, smooth on every device and easy to fix when it breaks.

---

## Learning Objectives

By the end of this section, you will be able to:

1. Explain why motion can be a problem for some users.
2. Use `@media (prefers-reduced-motion: reduce)` to turn off or tone down animations.
3. Name the properties that animate smoothly and the ones to avoid.
4. Use DevTools to inspect, pause and debug animations.

---

## Section Breakdown

### 9.1 — Respecting Reduced-Motion Preferences

**Plain-language definition:**
Some people feel dizzy, nauseated or distracted by moving content. Operating systems have a setting ("Reduce motion") that browsers pass on to your CSS through a media query.

**Why it matters:**
It is a simple way to make your site more inclusive. Always provide it when you use looping or large animations.

```css
@media (prefers-reduced-motion: reduce) {
  .moon-track,
  .earth {
    animation: none;
  }
}
```

**Analogy:**
Think of a restaurant that asks "any allergies?" before cooking. The media query is the browser telling your CSS about the guest's needs so you can adjust the recipe.

**Try it:** turn on "Reduce motion" in your operating system settings (or emulate it in Chrome DevTools: *Rendering* tab → *Emulate CSS media feature prefers-reduced-motion*) and reload the Moon Orbit. The moon should stay still.

---

### 9.2 — Animating for Performance

| ✅ Smooth (cheap)            | ⚠️ Avoid animating (expensive)                |
| ---------------------------- | --------------------------------------------- |
| `transform`                  | `width`, `height`                             |
| `opacity`                    | `top`, `left`, `right`, `bottom`              |
|                              | `margin`, `padding`                           |
|                              | `font-size`                                   |

**Why:** `transform` and `opacity` are handled by the graphics processor without recalculating the page layout. Animating the others forces the browser to re-layout and repaint on every frame.

**Other tips:**
- Keep animations short and purposeful: motion should help, not distract.
- Don't animate dozens of big, glowing (`box-shadow`) elements at once; shadows are costly.
- Avoid the `will-change` property unless you have measured a problem; overusing it wastes memory.

---

### 9.3 — Debugging with DevTools

**Inspecting an element:**
Right-click → **Inspect**. In the **Styles** pane, look for rules with a ~~strikethrough~~, which means they were overridden or invalid, and for yellow warning icons that flag mistakes.

**Debugging animations (Chrome/Edge):**
1. Open DevTools → three-dot menu → **More tools** → **Animations**.
2. Reload the page. Animations appear as timelines that you can slow down (25%, 10%) or replay.
3. Click an animated element to see its keyframes and edit values live.

**Debugging checklist:**
1. Is the CSS file linked and saved? Hard refresh.
2. Does the class in HTML exactly match the selector in CSS?
3. Are there any strikethrough declarations in the Styles pane?
4. Does the `@keyframes` name match the `animation` name exactly?
5. Does the animation have a duration?
6. Is another `transform` overriding the one in your keyframes?
7. Does the parent have `position: relative` when the child is absolute?

**Common beginner mistakes:**
- **Skipping reduced-motion support** on large or looping animations.
- **Animating layout properties** like `left`/`width` instead of `transform`.
- **Guessing instead of inspecting:** DevTools shows exactly what the browser applied.
- **Changing many things at once:** change one thing, refresh, check. It makes the bug obvious.

---

## How Sub-sections Connect

`9.1` makes your animations considerate → `9.2` makes them smooth → `9.3` gives you the tools to fix anything that goes wrong. Together they separate a *working* animation from a *professional* one.

---

## Key Terms Glossary

| Term                         | Definition                                                         |
| ---------------------------- | ------------------------------------------------------------------ |
| **Media query**              | A CSS rule that applies only when a condition is true              |
| **`prefers-reduced-motion`** | A media feature indicating the user wants less motion              |
| **Layout / reflow**          | The browser recalculating element sizes and positions              |
| **Repaint**                  | The browser redrawing pixels on screen                             |
| **GPU acceleration**         | Offloading drawing work to the graphics processor for smooth motion |
| **Animations panel**         | A DevTools tool for slowing, replaying and editing animations      |

---

## Knowledge Check

1. Why should you support `prefers-reduced-motion`?
2. Name two CSS properties that are cheap to animate and two that are expensive.
3. Add a reduced-motion media query to a `.spinner` that spins forever.
4. Name three things to check when a keyframe animation does nothing.
5. **Scenario:** A teammate animates a menu by changing `left` from `-300px` to `0`, and it stutters on phones. What would you recommend and why?

---

## Summary Recap

- Wrap animation in a `prefers-reduced-motion` media query so motion-sensitive users stay comfortable.
- Animate `transform` and `opacity` for smooth, efficient motion.
- Avoid animating `width`, `height`, `top`, `left`, `margin` and `padding`.
- Use DevTools (Elements, Styles and Animations panels) to debug.
- Change one thing at a time and always inspect before guessing.

---
---

# MASTER GLOSSARY: Full Module Reference

| Term                      | Definition                                                              |
| ------------------------- | ----------------------------------------------------------------------- |
| **CSS**                   | Cascading Style Sheets: the language that styles HTML                   |
| **Selector**              | Picks which elements a rule applies to                                  |
| **Property / Value**      | The thing to change / what to change it to                              |
| **Class (`.x`)**          | A reusable label; the most common selector                              |
| **ID (`#x`)**             | A unique label; use sparingly                                           |
| **Pseudo-class**          | A state selector such as `:hover`                                       |
| **Pseudo-element**        | Generated content such as `::before`                                    |
| **Cascade**               | The rules for choosing between conflicting declarations                 |
| **Specificity**           | How precisely a selector targets; higher wins                           |
| **Box model**             | Content → padding → border → margin                                     |
| **`box-sizing: border-box`** | Width includes padding and border                                    |
| **`border-radius`**       | Rounds corners; `50%` = circle                                          |
| **Hex / RGB / HSL**       | Ways to write colours                                                   |
| **Alpha**                 | Colour transparency                                                     |
| **Gradient**              | A smooth colour blend                                                   |
| **`box-shadow`**          | Shadow or glow around a box                                             |
| **Custom property**       | CSS variable: `--name` / `var(--name)`                                  |
| **`rem` / `vh` / `vw`**   | Relative sizing units                                                   |
| **Flexbox**               | One-dimensional layout system (`display: flex`)                         |
| **Grid centering**        | `display: grid; place-items: center;`                                   |
| **Main / cross axis**     | The two directions in a flex layout                                     |
| **`position`**            | `static`, `relative`, `absolute`                                        |
| **`inset`**               | Shorthand for `top`/`right`/`bottom`/`left`                             |
| **`transform`**           | `translate`, `rotate`, `scale`: visual movement without layout changes |
| **`transform-origin`**    | The pivot point of a transform                                          |
| **Transition**            | Smooth change between two states                                        |
| **Timing function**       | Speed curve: `linear`, `ease`, `ease-in-out`…                           |
| **`@keyframes`**          | Defines the steps of a named animation                                  |
| **`animation`**           | Attaches keyframes to an element                                        |
| **`infinite`**            | Repeat forever                                                          |
| **`alternate`**           | Play forwards then backwards                                            |
| **`animation-play-state`**| Pause or resume an animation                                            |
| **Orbit (CSS)**           | A child pinned to a rotating parent, or chained rotate/translate        |
| **Tweening**              | Browser-generated in-between frames                                     |
| **Media query**           | Conditional CSS (`@media`)                                              |
| **`prefers-reduced-motion`** | User setting to limit motion                                         |
| **DevTools**              | Browser inspection and debugging tools                                  |

---

## Final Knowledge Check

1. Explain the difference between a **class** and an **id** selector, and which to prefer.
2. Why does `box-sizing: border-box` make layout easier?
3. What are the two steps needed to make a keyframe animation run?
4. Explain, using the terms *pivot*, *track* and *rotate*, how the Moon Orbit works.
5. Why use `transform` rather than `left` when animating movement?
6. **Capstone:** Using what you've learned, design and build your **own** looping CSS animation scene (a bouncing ball, a spinning fan, a pulsing heart, a solar system…). It must include:
   - at least one `@keyframes` animation,
   - at least one `transition` on hover,
   - CSS variables,
   - a `prefers-reduced-motion` rule.

---

## Final Summary Recap

- CSS styles HTML. Link one external stylesheet and use classes to target elements.
- Everything is a box; use `border-box`, and `border-radius: 50%` for circles.
- Use colours, gradients, shadows and variables to give things depth and flexibility.
- Centre and arrange with Flexbox or `place-items: center`.
- Place with `position`, move with `transform`.
- Transitions smooth a change between two states; keyframes choreograph looping, multi-step motion.
- An orbit is a rotating, invisible arm with the moon pinned to its edge.
- Animate `transform` and `opacity`, respect `prefers-reduced-motion`, and debug with DevTools.