# CSS Complete Guide (Zero to Advance) — मराठी

---

## भाग 1: CSS म्हणजे काय?

CSS (Cascading Style Sheets) HTML ला **style/सजावट** देतं — रंग, size, spacing, layout वगैरे.

**CSS लिहायचे 3 मार्ग:**

```html
<!-- 1. Inline CSS -->
<p style="color:red;">Text</p>

<!-- 2. Internal CSS -->
<head>
<style>
  p { color: red; }
</style>
</head>

<!-- 3. External CSS (best practice) -->
<head>
<link rel="stylesheet" href="style.css">
</head>
```

```css
/* style.css फाईल मध्ये */
p {
  color: red;
}
```

---

## भाग 2: Basic Syntax

```css
selector {
  property: value;
}
```

```css
p {
  color: blue;
  font-size: 16px;
}
```

---

## भाग 3: Selectors

```css
/* Element selector */
p { color: red; }

/* Class selector (.) - reusable */
.highlight { background: yellow; }

/* ID selector (#) - unique */
#header { font-size: 24px; }

/* Universal selector */
* { margin: 0; padding: 0; }

/* Group selector */
h1, h2, p { color: navy; }

/* Descendant selector (space) */
div p { color: green; }

/* Child selector (>) - direct child only */
div > p { color: orange; }

/* Adjacent sibling selector (+) */
h1 + p { color: purple; }

/* General sibling selector (~) */
h1 ~ p { color: gray; }

/* Attribute selector */
input[type="text"] { border: 1px solid gray; }

/* Pseudo-class */
a:hover { color: red; }
a:visited { color: purple; }
a:active { color: green; }
li:first-child { font-weight: bold; }
li:last-child { color: gray; }
li:nth-child(2) { color: blue; }
li:nth-child(odd) { background: #eee; }
input:focus { border-color: blue; }
input:disabled { background: #ccc; }

/* Pseudo-element */
p::first-letter { font-size: 30px; }
p::first-line { font-weight: bold; }
p::before { content: "★ "; }
p::after { content: " ★"; }
::selection { background: yellow; }
```

---

## भाग 4: Colors

```css
p {
  color: red;                    /* named color */
  color: #ff0000;                /* hex */
  color: rgb(255, 0, 0);         /* rgb */
  color: rgba(255, 0, 0, 0.5);   /* transparency सकट */
  color: hsl(0, 100%, 50%);      /* hue, saturation, lightness */
  background-color: lightblue;
}
```

---

## भाग 5: Text व Fonts

```css
p {
  font-family: Arial, sans-serif;
  font-size: 18px;
  font-weight: bold;      /* normal, bold, 100-900 */
  font-style: italic;
  text-align: center;      /* left, right, center, justify */
  text-decoration: underline;
  text-transform: uppercase; /* lowercase, capitalize */
  line-height: 1.5;
  letter-spacing: 2px;
  word-spacing: 5px;
  white-space: nowrap;
  text-shadow: 2px 2px 4px gray;
}

/* Custom fonts import */
@import url('https://fonts.googleapis.com/css2?family=Roboto');
```

---

## भाग 6: Box Model (सर्वात महत्त्वाचं!)

```css
div {
  width: 200px;
  height: 100px;
  padding: 20px;       /* content ते border मधली जागा */
  border: 2px solid black;
  margin: 10px;         /* border बाहेरची जागा */
}
```

Box Model order (आतून बाहेर): **Content → Padding → Border → Margin**

```css
/* वेगवेगळ्या बाजू */
margin-top: 10px;
margin-right: 5px;
margin-bottom: 10px;
margin-left: 5px;

/* shorthand */
margin: 10px 5px;              /* top-bottom left-right */
margin: 10px 5px 15px 20px;    /* top right bottom left */

/* box-sizing - width/height मध्ये padding/border धरायचं की नाही */
* {
  box-sizing: border-box;
}
```

---

## भाग 7: Display व Positioning

```css
div {
  display: block;         /* full width, नवीन line */
  display: inline;        /* गरजेपुरती जागा */
  display: inline-block;  /* दोन्हीचं मिश्रण */
  display: none;           /* पूर्ण गायब */
}

.box {
  position: static;      /* default */
  position: relative;    /* स्वतःच्या जागेपासून shift */
  position: absolute;    /* nearest positioned parent च्या relative to */
  position: fixed;        /* screen वर fixed, scroll झालं तरी */
  position: sticky;       /* scroll पर्यंत relative, मग fixed */
  top: 10px;
  left: 20px;
  right: 0;
  bottom: 0;
}
```

---

## भाग 8: Flexbox (Modern Layout)

```css
.container {
  display: flex;
  flex-direction: row;         /* row, column, row-reverse, column-reverse */
  justify-content: center;     /* main axis वर alignment */
  align-items: center;         /* cross axis वर alignment */
  align-content: center;
  flex-wrap: wrap;
  gap: 10px;
}

.item {
  flex: 1;              /* space equally share */
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: 100px;
  align-self: flex-end;  /* individual item साठी override */
  order: 2;               /* visual order बदलायला */
}
```

`justify-content` values: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`

---

## भाग 9: Grid Layout

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;   /* 3 equal columns */
  grid-template-rows: 100px 200px;
  gap: 15px;
  grid-template-areas:
    "header header header"
    "sidebar content content"
    "footer footer footer";
}

.item {
  grid-column: 1 / 3;    /* column 1 पासून 3 पर्यंत span */
  grid-row: 1 / 2;
  grid-area: header;      /* named area वापरायला */
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
```

---

## भाग 10: Background व Borders

```css
div {
  background-color: lightgray;
  background-image: url('bg.jpg');
  background-size: cover;       /* contain, cover, 100px 100px */
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;

  border: 2px solid black;
  border-radius: 10px;           /* गोल कोपरे */
  border-top-left-radius: 20px;
  box-shadow: 2px 2px 10px gray;
  box-shadow: inset 0 0 5px red; /* आतल्या बाजूने shadow */
}

/* Gradient background */
div {
  background: linear-gradient(to right, red, blue);
  background: radial-gradient(circle, red, blue);
}
```

---

## भाग 11: Units

```css
width: 200px;      /* fixed pixels */
width: 50%;        /* parent च्या relative */
font-size: 2em;    /* parent font size च्या relative */
font-size: 2rem;   /* root(html) font size च्या relative */
width: 100vw;      /* viewport width चा 100% */
height: 100vh;     /* viewport height चा 100% */
width: 50ch;       /* character width च्या relative */
```

---

## भाग 12: Responsive Design (Media Queries)

```css
/* Mobile साठी */
@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
  .container {
    flex-direction: column;
  }
}

/* Tablet साठी */
@media (min-width: 601px) and (max-width: 1024px) {
  .container {
    grid-template-columns: 1fr 1fr;
  }
}

/* Print साठी */
@media print {
  nav { display: none; }
}
```

---

## भाग 13: Transitions व Animations

```css
button {
  background: blue;
  transition: background 0.3s ease;
  transition: all 0.5s ease-in-out;
}
button:hover {
  background: red;
}

/* Keyframe animation */
@keyframes slide {
  from { transform: translateX(0); }
  to { transform: translateX(100px); }
}

@keyframes bounce {
  0% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
  100% { transform: translateY(0); }
}

.box {
  animation: slide 2s infinite alternate;
  animation: bounce 1s ease-in-out infinite;
}
```

---

## भाग 14: Transform

```css
.box {
  transform: rotate(45deg);
  transform: scale(1.5);
  transform: translate(20px, 10px);
  transform: translateX(20px);
  transform: skew(10deg);
  transform: rotate(45deg) scale(1.2);   /* combine करता येतं */
  transform-origin: center;
}
```

---

## भाग 15: Advanced Concepts

```css
/* CSS Variables (Custom Properties) */
:root {
  --main-color: #3498db;
  --spacing: 16px;
}
div {
  color: var(--main-color);
  padding: var(--spacing);
}

/* Z-index (layering, कोण वर कोण खाली) */
.popup {
  position: fixed;
  z-index: 999;
}

/* Overflow */
div {
  overflow: hidden;    /* scroll, auto, visible */
  overflow-x: scroll;
  overflow-y: hidden;
}

/* Object-fit (images साठी) */
img {
  object-fit: cover;   /* contain, fill, none */
}

/* Filter effects */
img {
  filter: blur(5px);
  filter: grayscale(100%);
  filter: brightness(1.5);
}

/* Cursor styles */
button {
  cursor: pointer;      /* not-allowed, grab वगैरे */
}

/* CSS Counters */
ol {
  counter-reset: section;
}
li::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";
}

/* clip-path (shapes cut करायला) */
.box {
  clip-path: circle(50%);
}

/* Aspect ratio */
.video {
  aspect-ratio: 16 / 9;
}
```

---

## भाग 16: CSS Combinators Summary

| Combinator | अर्थ | Example |
|---|---|---|
| (space) | Descendant | `div p` |
| `>` | Direct child | `div > p` |
| `+` | Immediate sibling | `h1 + p` |
| `~` | General sibling | `h1 ~ p` |
