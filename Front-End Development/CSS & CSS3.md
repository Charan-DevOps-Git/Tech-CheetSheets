# Introduction

CSS (Cascading Style Sheets) is a style sheet language used for describing the presentation of a document written in HTML. CSS3 is the latest version, adding new features and capabilities for better styling and layout.

# Basic Syntax
```
selector {
    property: value;
}
```

# Selectors

- Universal Selector: *
- Type Selector: element
- Class Selector: .classname
- ID Selector: #idname
- Attribute Selector: [attribute=value]
- Pseudo-class Selector: :pseudo-class
- Pseudo-element Selector: ::pseudo-element
- Group Selector: selector1, selector2


# Box Model

- Content: The actual content of the box, where text and images appear.
- Padding: Clears an area around the content. Transparent.
- Border: A border surrounding the padding (if any) and content.
- Margin: Clears an area outside the border. Transparent.

```
div {
    width: 300px;
    padding: 20px;
    border: 5px solid gray;
    margin: 15px;
}
```

# Display & Positioning

- display: block, inline, inline-block, none, flex, grid
- position: static, relative, absolute, fixed, sticky
- float: left, right, none
- clear: left, right, both, none
- z-index: Stacking order of elements
```
.element {
    display: flex;
    position: relative;
    float: left;
    clear: both;
    z-index: 10;
}
```
# Flexbox
```
.container {
    display: flex;
    flex-direction: row; /* row, row-reverse, column, column-reverse */
    justify-content: center; /* flex-start, flex-end, center, space-between, space-around */
    align-items: center; /* flex-start, flex-end, center, baseline, stretch */
}
```
# Grid
```
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* Define columns */
    grid-template-rows: auto;
    gap: 10px; /* Space between grid items */
}

.item {
    grid-column: span 2; /* Span 2 columns */
    grid-row: 1 / 3; /* Row from 1 to 3 */
}
```
# Colors

- Named Colors: red, blue, green, etc.
- Hex Colors: #RRGGBB
- RGB Colors: rgb(255, 0, 0)
- RGBA Colors: rgba(255, 0, 0, 0.5)
- HSL Colors: hsl(0, 100%, 50%)
- HSLA Colors: hsla(0, 100%, 50%, 0.5)
```
.element {
    color: red;
    background-color: #00ff00;
    border-color: rgb(0, 0, 255);
}
```
# Text Styling

- font-family: Arial, Helvetica, sans-serif
- font-size: 16px, 1.5em, 120%
- font-weight: normal, bold, bolder, lighter, 100-900
- font-style: normal, italic, oblique
- text-align: left, right, center, justify
- text-decoration: none, underline, overline, line-through
- line-height: normal, 1.5, 150%
```
.text {
    font-family: Arial, sans-serif;
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    text-decoration: underline;
    line-height: 1.5;
}
```

# Backgrounds

- background-color: #ffffff
- background-image: url(image.png)
- background-repeat: repeat, no-repeat, repeat-x, repeat-y
- background-size: auto, cover, contain
- background-position: left top, center, right bottom
```
.background {
    background-color: #f0f0f0;
    background-image: url('image.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
}
```
# Borders and Shadows

- border: 1px solid #000
- border-radius: 5px, 50% (for circles)
- box-shadow: 2px 2px 5px #888888
```
.box {
    border: 2px solid #000;
    border-radius: 10px;
    box-shadow: 5px 5px 10px rgba(0,0,0,0.5);
}
```
# Transitions and Animations

- transition: property duration timing-function delay
- animation: name duration timing-function delay iteration-count direction
```
.transition {
    transition: all 0.3s ease;
}

@keyframes example {
    from {background-color: red;}
    to {background-color: yellow;}
}

.animation {
    animation: example 5s infinite;
}
```

# Media Queries
```
@media screen and (max-width: 600px) {
    .responsive {
        flex-direction: column;
    }
}
```

# CSS Variables (Custom Properties)

CSS variables allow you to store values in one place and reuse them throughout a document.
```
:root {
    --main-color: #3498db;
    --main-padding: 10px;
}

.element {
    color: var(--main-color);
    padding: var(--main-padding);
}
```

# Advanced Selectors

- Child Selector: parent > child
- Adjacent Sibling Selector: element + element
- General Sibling Selector: element ~ element
- Attribute Selector: [attribute^="value"] (starts with), [attribute$="value"] (ends with), [attribute*="value"] (contains)
```
div > p { /* Selects <p> elements that are direct children of <div> */ }
h1 + p { /* Selects <p> elements immediately following <h1> */ }
h1 ~ p { /* Selects all <p> elements that are siblings of <h1> */ }
a[href^="https"] { /* Selects <a> elements with href attribute starting with "https" */ }
```

# CSS Grid Advanced Layout
```
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    gap: 10px;
    grid-auto-flow: dense; /* Fill rows tightly */
}

.item-a {
    grid-column: 1 / span 2;
    grid-row: 1;
}
```

# CSS Transforms
- translate: translateX(100px), translateY(100px)
- rotate: rotate(45deg)
- scale: scale(1.5)
- skew: skewX(20deg), skewY(20deg)
- matrix: matrix(a, b, c, d, tx, ty)
```
.transform {
    transform: translateX(50px) rotate(45deg) scale(1.5);
}
```

# CSS Transitions
Smoothly animate property changes over a specified duration.
```
.transition {
    transition: all 0.3s ease-in-out;
}

.transition:hover {
    transform: scale(1.1);
}
```

# CSS Animations
Keyframe animations for complex sequences.
```
@keyframes slidein {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

.animation {
    animation: slidein 1s forwards;
}
```

# CSS Flexbox Advanced Features
- flex-grow: 1, 2, etc.
- flex-shrink: 0, 1, etc.
- flex-basis: auto, 100px, etc.
- align-self: auto, flex-start, flex-end, center, baseline, stretch
```
.container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.item {
    flex-grow: 1;
    flex-shrink: 0;
    flex-basis: 200px;
}
```

# CSS Clip Path
Clip part of an element to create interesting shapes.
```
.clip {
    clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
}
```

# CSS3 Filters
Apply graphical effects to elements.

- blur: blur(5px)
- brightness: brightness(1.2)
- contrast: contrast(200%)
- grayscale: grayscale(50%)
- hue-rotate: hue-rotate(90deg)
- invert: invert(100%)
- opacity: opacity(50%)
- saturate: saturate(200%)
- sepia: sepia(100%)
```
.filter {
    filter: blur(5px) brightness(1.2);
}
```

# CSS3 Columns
Creating multi-column layouts.
```
.columns {
    column-count: 3;
    column-gap: 20px;
}

.column-rule {
    column-rule: 1px solid #000;
}
```

# CSS3 Shapes
Define shapes for wrapping text around them.
```
.shape {
    shape-outside: circle(50%);
    float: left;
    width: 200px;
    height: 200px;
}
```

# CSS Object-Fit and Object-Position
Control how replaced elements like <img> or <video> are resized to fit their container.
```
img {
    object-fit: cover; /* fill, contain, cover, scale-down, none */
    object-position: center top; /* Align the image inside the container */
}
```

# CSS Writing Modes
Control text direction and block flow.
```
.writing-mode {
    writing-mode: vertical-rl; /* horizontal-tb, vertical-rl, vertical-lr */
}
```

# CSS Custom Fonts and Font Features
Include custom fonts and control typographic features.
```
@font-face {
    font-family: 'MyCustomFont';
    src: url('mycustomfont.woff2') format('woff2');
}

.custom-font {
    font-family: 'MyCustomFont', sans-serif;
    font-feature-settings: 'liga' on, 'dlig' on;
}
```
# Resources

[Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS)

