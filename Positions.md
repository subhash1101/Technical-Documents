# CSS Position Property

The position property in CSS is used to control how an element is positioned in a web page. It works together with the properties `top`, `right`, `bottom`, and `left` to place elements at specific locations.

## Types of Position in CSS

There are five main values of the position property:

1. static
2. relative
3. absolute
4. fixed
5. sticky

---

## 1. Static Position

`static` is the default position for all HTML elements. Elements are displayed according to the normal flow of the page.

### Example

```html
<style>
  .box {
    position: static;
    border: 2px solid black;
  }
</style>

<body>
  <div class="box">
    This is a static positioned element.
  </div>
</body>
````

---

## 2. Relative Position

When an element is set to `position: relative`, it remains in the normal document flow, but you can move it relative to its original position using `top`, `left`, `right`, or `bottom`.

### Example

```html
<style>
  .box {
    position: relative;
    top: 20px;
    left: 30px;
    border: 2px solid blue;
  }
</style>

<body>
  <div class="box">
    This element is moved 20px down and 30px right from its original position.
  </div>
</body>
```

---

## 3. Absolute Position

An element with `position: absolute` is positioned relative to its nearest positioned ancestor. If no positioned ancestor exists, it will be positioned relative to the `<body>`.

The element is removed from the normal document flow.

### Example

```html
<style>
  .container {
    position: relative;
    width: 300px;
    height: 200px;
    border: 2px solid black;
  }

  .box {
    position: absolute;
    top: 20px;
    right: 10px;
    background: lightblue;
  }
</style>

<body>
  <div class="container">
    <div class="box">
      Absolute positioned element
    </div>
  </div>
</body>
```

---

## 4. Fixed Position

An element with `position: fixed` is positioned relative to the browser viewport. It stays in the same place even when the page is scrolled.

### Example

```html
<style>
  .box {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: red;
    color: white;
    padding: 10px;
  }
</style>

<body>
  <div class="box">
    Fixed position element
  </div>
  <p>Scroll the page to see the element stay in place.</p>
</body>
```

---

## 5. Sticky Position

`position: sticky` behaves like `relative` until a certain scroll position is reached. After that, it behaves like `fixed`.

It is commonly used for sticky headers.

### Example

```html
<style>
  .section{
    margin-top:600px;
    height:1200px;
    background:green;
    padding:20px;
    margin-bottom:1000px
  }
  .sticky-box{
    position: sticky;
    top: 20px;
    background:#4dabf7;
    color:white;
    padding:10px;
  }

  .content{
    height:1500px;
  }
</style>

<body>
  <div class="fixed-header">
    I am FIXED 
  </div>
  <div class="section">
    <div class="sticky-box">
      I am STICKY 
    </div>
    <div class="content">
      see what happens when scrolled down
    </div>
  </div>
</body>
```
---
