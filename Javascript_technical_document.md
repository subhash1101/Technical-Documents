# JavaScript Technical Document

---
---
# DIFFERENT DATA TYPES IN JAVASCRIPT

JavaScript has two types of data types:

### Primitive Types

* String
* Number
* Boolean
* Null
* Undefined
* BigInt
* Symbol

Example:

```js
let name = "Subhash";      // string
let age = 22;              // number
let isStudent = true;      // boolean
let x = null;              // null
let y;                     // undefined
let big = 123n;            // bigint
let sym = Symbol("id");    // symbol
```

### Non-Primitive Types

* Object
* Array

```js
let obj = {a:1};
let arr = [1,2,3];
```

---
---

# SCOPES IN JAVASCRIPT

Scope means where a variable can be accessed.

Types of scope

1. Global scope
2. Function scope
3. Block scope

Example:

```js
let a = 10; // global

function test(){
    let b = 20; // function scope
    if(true){
        let c = 30; // block scope
        console.log(c); // 30
    }
    console.log(b); // 20
}

test();
console.log(a); // 10
```

---
---

# let vs var vs const

### var

* function scoped
* hoisted
* can redeclare
* can update

### let

* block scoped
* cannot redeclare
* can update

### const

* block scoped
* cannot redeclare
* cannot update

Example:

```js
var a = 2; // allowed

let b = 1;
let b = 2; // error

const c = 3;
c = 4; // error
```

---
---

# WHY WE MUST NOT USE var

Problems with var:

1. No block scope
2. Can redeclare
3. Hoisting confusion

Example:

```js
if(true){
    var x = 10;
}
console.log(x); // 10 (bad)
```

With let:

```js
if(true){
    let x = 10;
}
console.log(x); // error
```

---
---

# WHY USING GLOBAL VARIABLES IS BAD

Problems:

* Memory stays forever
* Hard to debug
* Can be changed anywhere

Example:

```js
let total = 0;

function add(){
    total++;
}

add();
add();

console.log(total); // 2
```

Better:

```js
function add(total){
    return total + 1;
}

let t = 0;
t = add(t);
t = add(t);

console.log(t); // 2
```

---
---

# TRUTHY AND FALSY VALUES

### Falsy values:

* false
* 0
* ""
* null
* undefined
* NaN

**Everything else is truthy**

Example:

```js
if(0){
    console.log("yes");
}else{
    console.log("no"); // no
}
```

```js
if("hello"){
    console.log("yes"); // yes
}
```

---
---

# FUNCTION HOISTING

Functions declared with function keyword are hoisted.

```js
test();

function test(){
    console.log("hello"); // hello
}
```

Function expression not hoisted

```js
test(); // error

const test = function(){
    console.log("hi");
};
```

---
---

# FUNCTION WITHOUT RETURN

If no return ==> undefined

```js
function add(a,b){
    a+b;
}

let x = add(2,3);
console.log(x); // undefined
```

---
---

# DIFFERENT WAYS OF DECLARING FUNCTION

Function declaration

```js
function add(a,b){
    return a+b;
}
```

Function expression

```js
const add = function(a,b){
    return a+b;
};
```

Arrow function

```js
const add = (a,b) => a+b;
```

---
---

# PASS BY VALUE / PASS BY REFERENCE

### Primitive type ==> value

```js
let a = 10;

function change(x){
    x = 20;
}

change(a);
console.log(a); // 10
```

### Object type ==> reference

```js
let obj = {a:1};

function change(o){
    o.a = 5;
}

change(obj);
console.log(obj.a); // 5
```

---
---

# FOR LOOPS

### Normal for

```js
for(let i=0;i<3;i++){
    console.log(i);
}
// 0 1 2
```

### for..in (object keys)

```js
let obj = {a:1,b:2};

for(let k in obj){
    console.log(k);
}
// a b
```

### for..of (array values)

```js
let arr=[1,2,3];

for(let v of arr){
    console.log(v);
}
// 1 2 3
```

### forEach

```js
[1,2,3].forEach(x => console.log(x));
// 1 2 3
```

### while

```js
let i=0;
while(i<3){
    console.log(i);
    i++;
}
// 0 1 2
```

---
---

# ARRAY METHODS (mutable / immutable)

push (mutable)

```js
let a=[1,2];
a.push(3);
console.log(a); // [1,2,3]
```

pop (mutable)

```js
a.pop();
console.log(a); // [1,2]
```

concat (immutable)

```js
let b=a.concat([3]);
console.log(b); // [1,2,3]
```

slice (immutable)

```js
let c=[1,2,3,4].slice(1,3);
console.log(c); // [2,3]
```

splice (mutable)

```js
let d=[1,2,3];
d.splice(1,1);
console.log(d); // [1,3]
```

join (immutable)

```js
[1,2,3].join("-");
console.log([1,2,3].join("-")); // 1-2-3
```

flat (immutable)

```js
[1,[2,[3]]].flat(2);
console.log([1,[2,[3]]].flat(2)); // [1,2,3]
```

find

```js
[1,2,3].find(x=>x>1);
console.log([1,2,3].find(x=>x>1)); // 2
```

indexOf

```js
[1,2,3].indexOf(2);
console.log([1,2,3].indexOf(2)); // 1
```

includes

```js
[1,2,3].includes(3);
console.log([1,2,3].includes(3)); // true
```

findIndex

```js
[5,6,7].findIndex(x=>x==6);
console.log([5,6,7].findIndex(x=>x==6)); // 1
```

forEach

```js
[1,2].forEach(x=>console.log(x)); // 1 2
```

sort (mutable)

```js
[3,1,2].sort();
console.log([3,1,2].sort()); // [1,2,3]
```

Chaining

```js
[1,2,3,4]
.filter(x=>x>1)
.map(x=>x*2)
.reduce((a,b)=>a+b,0);

console.log(
[1,2,3,4].filter(x=>x>1).map(x=>x*2).reduce((a,b)=>a+b,0)
); // 18
```

---
---

# STRING METHODS (immutable)


```js
let s="hello";

s.toUpperCase();
console.log(s.toUpperCase()); // HELLO

s.slice(1,4);
console.log(s.slice(1,4)); // ell

s.includes("he");
console.log(s.includes("he")); // true

s.split("");
console.log(s.split("")); // [h,e,l,l,o]

s.replace("h","y");
console.log(s.replace("h","y")); // yello

s.trim();
console.log(" hi ".trim()); // hi
```

---
---

# OBJECT METHODS

### keys

```js
Object.keys({a:1,b:2});
console.log(Object.keys({a:1,b:2})); // [a,b]
```

### values

```js
Object.values({a:1,b:2});
console.log(Object.values({a:1,b:2})); // [1,2]
```

### entries

```js
Object.entries({a:1});
console.log(Object.entries({a:1})); // [[a,1]]
```

### assign (mutable target)

```js
let a={x:1};
Object.assign(a,{y:2});
console.log(a); // {x:1,y:2}
```

### freeze

```js
let o={a:1};
Object.freeze(o);
o.a=2;
console.log(o.a); // 1
```

---
---
# forEach vs map vs filter vs reduce

---

Use forEach ==> when you only want to loop

```js
[1,2,3].forEach(x => console.log(x)); // 1 2 3
```

Use map ==> when you want new array

```js
let a = [1,2,3].map(x => x*2);  // [2,4,6]
```

Use filter ==> when you want some elements

```js
let a = [1,2,3,4].filter(x => x>2);  // [3,4]
```

Use reduce ==> when you want single value

```js
let a = [1,2,3].reduce((s,x)=>s+x,0);  // 6
```

---
---

# Mutable vs Immutable methods

Mutable ==> changes original

push, pop, splice, sort, reverse

```js
let a=[1,2];
a.push(3);
console.log(a); // [1,2,3]
```

Immutable ==> returns new

map, filter, slice, concat

```js
let a=[1,2];
let b=a.concat([3]);
console.log(a); // [1,2]
console.log(b); // [1,2,3]
```

---
---

# Error Handling (try catch)

try is used to check if it gives an error or not

catch is used to catch the error if it arises

```js
try {
    let x = y;
} catch(e) {
    console.log("error"); // error
}
```

---
---
# Throwing Errors

```js
function test(x){
    if(x<0){
        throw new Error("negative");
    }
}

try{
    test(-1);
}catch(e){
    console.log(e.message); // negative
}
```
---
---

# throw new Error vs throw "error"

---

Better

```js
throw new Error("bad");
```

Bad

```js
throw "bad";
```

Reason

Error object has stack trace

---

# Reading stack trace

---

Example

```js
function a(){
    b();
}

function b(){
    c();
}

function c(){
    throw new Error("boom");
}

a();
```

Stack trace shows

c ==> b ==> a

---
---

# Spread operator

```js
let a=[1,2];
let b=[...a,3];
console.log(b); // [1,2,3]
```

Object

```js
let a={x:1};
let b={...a,y:2};
console.log(b); // {x:1,y:2}
```

---
---

# Template literals

```js
let name="Sam";
console.log(`Hello ${name}`); // Hello Sam
```

---
---

# Destructuring

Array

```js
let [a,b]=[1,2];
console.log(a); // 1
```

Object

```js
let {x,y}={x:5,y:6};
console.log(x); // 5
```

---
---

# Closures

Function remembers scope

```js
function outer(){
    let x=10;
    return function(){
        console.log(x);
    }
}

let f=outer();
f(); // 10
```

---
---

# Arrow vs Regular function

Arrow has no this

```js
const a = () => 5;
```

Regular

```js
function a(){
    return 5;
}
```

---
---

# value === undefined vs !value

```js
if(!value)
```

Because 0 "" false also false

```js
if(value===undefined)
```
---
---

# Chaining methods

```js
let x=[1,2,3,4]
.filter(x=>x>1)
.map(x=>x*2)
.reduce((a,b)=>a+b,0);

console.log(x); // 18
```

---

# null vs undefined

---

undefined ==> not assigned

null ==> assigned empty

```js
let a;
let b=null;

console.log(a); // undefined
console.log(b); // null
```

---
---

# require / module.exports

file1.js

```js
function add(a,b){
    return a+b;
}

module.exports = add;
```

file2.js

```js
const add = require("./file1");

console.log(add(2,3)); // 5
```

---
---

# console methods

---

```js
console.log("hi"); // hi
console.error("err"); // err
console.info("info"); // info
console.warn("warn"); // warn
console.table([1,2]); // table
```

---
---

# Passing functions to functions

```js
function run(fn){
    fn();
}

run(()=>console.log("hi")); // hi
```

---
---

# Debugging strategies

1. console.log
2. read error
3. read stack trace
4. check undefined
5. run small code
6. use try catch

Example

```js
let a;
console.log(a.x); // error
```

Read error ==> undefined

Fix

```js
if(a) console.log(a.x);
```

---
