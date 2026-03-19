# AMA

## 1. What push method do

The `push()` method in JavaScript is used to add one or more elements to the end of an array.
```js
let arr = [1, 2, 3];
arr.push(4);

console.log(arr); // [1,2,3,4]
```

---

## 2. Diff b/w throw error and throw new error

* `throw` is used to throw any value.
* `throw new Error()` creates a proper error object with message and stack trace.

---

## 3. Diff b/w sync and async JS

### Sync
* Executes line by line
* Blocking

### Async
* Executes without blocking
* Non-blocking

```js
// Sync
console.log(1);
console.log(2);

// Async
setTimeout(() => console.log(1), 1000);
console.log(2);
```

---

## 4. Event bubbling

Event bubbling means event starts from child element and moves to parent.

```js
div => parent => body => html => document
```

---

## 5. Callback hell

Callback hell is when callbacks are nested inside callbacks many times.

```js
a(function(){
  b(function(){
    c(function());
  });
});
```

---

## 6. List in JS

JavaScript does not have list type, we use Array as list.

```js
let list = [1,2,3,4];
```

---

## 7. Closure in JS

Closure means a function remembers variables from its outer scope.

```js
function outer(){
  let x = 10;

  return function inner(){
    console.log(x);
  }
}

let a = outer();
a(); // 10
```

---

## 8. Diff b/w null & undefined

### null
* empty value
* type = object
### undefined
* variable declared but not assigned
* type = undefined

---

## 9. Mutable and immutable

Mutable => can change
Immutable => cannot change

Mutable:

```js
let arr = [1,2];
arr.push(3);
```

Immutable:

```js
let str = "hi";
str[0] = "H"; // not change
```

---

## 10. this keyword

`this` refers to current object.

```js
let obj = {
  name: "JS",
  show(){
    console.log(this.name);
  }
}
```

---

## 11. Split method in string in JS

`split()` converts string to array.

```js
let str = "a,b,c";
let arr = str.split(",");

console.log(arr); // ["a","b","c"]
```

---

## 12. Types of scope

1. Global scope => Accessed anywhere in code
2. Function scope => accsessed only in the function
3. Block scope => Accessed only in the block of the code


---

## 13. What happens when we add number and string

Number + String => String

```js
1 + "2" = "12"
```

---

## 14. Scope of var

`var` has function scope.

```js
function test(){
  var x = 10;
}
```

not block scoped.

---

## 15. Advantage of using catch block

Used to handle errors without stopping program.
```js
try {
  x();
} catch(e) {
  console.log("Error handled");
}
```
---

## 16. Hoisting

Hoisting means variables and functions move to top before execution.

```js
console.log(a);
var a = 5;
```

Internally:
```js
var a;
console.log(a);
a = 5;
```

---
