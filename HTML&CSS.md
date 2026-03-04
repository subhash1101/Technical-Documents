# CSS Box Model

## Parts of the Box Model

## 1. Content
The content is the actual text, image, or other data inside the element.
Example:

```html
<div class="box">Hello World</div>
```
---

## 2. Padding
Padding is the space between the content and the border. It creates space inside the box.
Example:

```css
.box {
  padding: 20px;
}
```

```css
padding: 10px 20px 30px 40px;
/* top right bottom left */
```

---

## 3. Border
Border goes around the padding and content.
Example:

```css
.box {
  border: 5px solid black;
}
```

---

## 4. Margin
Margin is the space outside the border.
Example:

```css
.box {
  margin: 30px;
}
```

```css
margin: 10px 20px 30px 40px;
/* top right bottom left */
```

---

## How Total Width and Height Are Calculated

Total Width =
content width + left padding + right padding + left border + right border

Example:

```
width: 200px
padding: 20px
border: 5px
```

Total width =
200 + 20 + 20 + 5 + 5 = 250px

---
---

# Inline vs Block Elements in HTML

# 1. Block Elements

A block element:

* Takes full width of the page and always starts on a new line
* Can contain other block and inline elements

## Common Block Elements

```html
<h1>This is a heading</h1>
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
```

* Here each `<p>` appears on a new line.

---

# 2. Inline Elements

An inline element:

* Does NOT start on a new line
* Only takes as much width as needed

## Common Inline Elements

```html
<p>This is a <span>simple</span> example.</p>
```

Here:

* `<span>` stays inside the paragraph.
* It does not move to a new line.
---

# Changing Display Type

You can change the behavior using CSS `display` property.

## Make Inline Element Act Like Block

```css
span {
  display: block;
}
```

## Make Block Element Act Like Inline

```css
div {
  display: inline;
}
```
---
---

# CSS Positioning: Relative and Absolute

# 1. position: relative

* You can move it using `top`, `right`, `bottom`, and `left`.
* The original space of the element is still reserved.

## Example

```css
.box {
  position: relative;
  top: 20px;
  left: 30px;
}
```

---

# 2. position: absolute

* It does NOT keep its original space.
* It is positioned relative to its nearest positioned element (relative, absolute, fixed).

---

## Example

```html
<div class="parent">
  <div class="child">Absolute Child</div>
</div>
```

```css
.parent {
  background-color: lightgray;
  position: relative;
}

.child {
  background-color: orange;
  position: absolute;
  top: 20px;
  right: 20px;
}
```

---
---

# Common CSS Structural Classes

Structural classes are CSS classes used to organize and structure a webpage layout. They help divide the page into sections like:

* Header
* Navigation
* Main content
* Sidebar
* Footer
* Row, Column

---

# 1. Header

The header is used for the top section of a website.

## Example

```html
<header class="header">
  <h1>My Website</h1>
</header>
```
---

# 2. Navigation

Navigation contains links to different pages.

## Example

```html
<div class="nav">
  <a href="#">Home</a>
  <a href="#">About</a>
</div>
```

---

# 3. Main Content

Main content is the primary section of the page.

## Example

```html
<div class="main">
  <h2>Main Content</h2>
  <p>This is the main area.</p>
</div>
```

---

# 4. Sidebar

A sidebar is used for extra information like:

* Links, Ads, Categories

## Example

```html
<div class="sidebar">
  <p>Sidebar content</p>
</div>
```
---

# 5. Footer

Footer is the bottom section of the webpage.


## Example

```html
<footer class="footer">
  <p>Copyright 2026</p>
</footer>
```
---
---

# Common CSS Styling Classes

Styling classes are used to change the appearance of elements.

They control:

* Colors, Text styles, Background, Spacing
* Borders, Shadows, Alignment

These classes help make websites look better and more organized.

---

# 1. Text Color Classes

Used to change text color.

## Example

```html
<p class="text-blue">This is blue text</p>
```

```css
.text-blue {
  color: blue;
}
```

---

# 2. Background Color Classes

Used to change background color.

## Example

```html
<div class="bg-dark">Dark Background</div>
```

```css
.bg-dark {
  background-color: black;
  color: white;
}
```

---

# 3. Text Alignment Classes

Used to align text.

## Example

```html
<p class="text-center">Center text</p>
```

```css
.text-center {
  text-align: center;
}
```

---

# 4. Font Size Classes

Used to control text size.

## Example

```html
<p class="small-text">Small text</p>
```

```css
.small-text {
  font-size: 12px;
}
```

---

# 5. Margin and Padding Classes

Used to control spacing.

## Example

```html
<div class="mar&pad">Box with spacing</div>
```

```css
.mar&pad {
  margin: 20px;
  padding: 10px;
}
```
---

# 6. Border Classes

Used to add borders.

## Example

```html
<div class="border-box">Bordered Box</div>
```

```css
.border-box {
  border: 2px solid black;
}
```
---
---

# CSS Specificity

CSS Specificity decides which CSS rule is applied when multiple rules target the same element.

Specificity is like a priority system.

# Specificity Order (Low to High)
---

# 1. Element Selector (Lowest)

Example:

```css
p {
  color: green;
}
```

This has the lowest priority.

---

# 2. Class Selector

Example:

```css
.text {
  color: blue;
}
```

Class selectors have higher priority than element selectors.

---

# 3. ID Selector

Example:

```css
#title {
  color: red;
}
```

ID selectors have higher priority than class selectors.

---

# 4. Inline Style

Inline styles are written inside HTML.

Example:

```html
<p style="color: purple;">Hello</p>
```

---

# 5. !important (Highest)

Example:

```css
p {
  color: green !important;
}
```

`!important` overrides almost everything.

---
---

# CSS Responsive Queries (Media Queries)

Responsive design means making a website look good on:

* Desktop
* Tablet
* Mobile

CSS Media Queries help us change styles based on screen size.

A media query is a CSS rule that applies styles only when certain conditions are true.


```css
@media (condition) {
  /* CSS rules here */
}
```
---

# Basic Example

```css
body {
  background-color: lightblue;
}
@media (max-width: 600px) {
  body {
    background-color: lightgreen;
  }
}
```

Explanation:

* If screen width is 600px or less
* Background becomes lightgreen
* Otherwise, it stays lightblue

---
---

# CSS Flexbox and CSS Grid


# CSS Flexbox

Flexbox is used to arrange items in:

* A row Or a column

## Important Flexbox Properties

### 1. flex-direction

Controls direction of items.

```css
flex-direction: row; 
```

---

### 2. justify-content

Aligns items horizontally (main axis).

```css
justify-content: center;
```

---

### 3. align-items

Aligns items vertically (cross axis).

```css
align-items: center;
```

---

### 4. flex

Controls item size.

```css
.box {
  flex: 1;
}
```

---
# CSS Grid

Grid is used to create layouts with:

* Multiple rows and Multiple columns


---

## Important Grid Properties

### 1. grid-template-columns

Defines number and size of columns.

```css
grid-template-columns: 200px 200px;
```

---

### 2. grid-template-rows

Defines row sizes.

```css
grid-template-rows: 100px 200px;
```

---

### 3. gap

Space between rows and columns.

```css
gap: 20px;
```

---

### 4. grid-column and grid-row

Used to make items span multiple columns.

```css
.box1 {
  grid-column: span 2;
}
```
