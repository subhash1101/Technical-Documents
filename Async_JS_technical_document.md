# Asynchronous JavaScript Technical Document

## How JavaScript Executes the Code

JavaScript is a single-threaded, synchronous language.

Single-threaded => One task at a time
Synchronous => Line by line execution

### JavaScript Execution Environment

JS engine uses:

* Call Stack
* Web APIs
* Callback Queue
* Event Loop

Flow:

```
Code => Call Stack => Web APIs => Callback Queue => Event Loop => Call Stack
```

---

## Difference Between Sync & Async

### Synchronous

* Executes line by line
* Blocks next line until current finishes

Example:

```js
console.log("1");
console.log("2");
console.log("3");
```

### Asynchronous

* Does not block execution
* Runs in background

Example:

```js
console.log("1");

setTimeout(() => {
  console.log("2");
}, 2000);

console.log("3");
```

Output:

```
1
3
2
```
---

## Ways to Make Code Async

JavaScript provides multiple ways:

### 1. setTimeout / setInterval

```js
setTimeout(() => {
  console.log("Hello");
}, 1000);
```

### 2. Callbacks

```js
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received");
  }, 1000);
}

fetchData((data) => {
  console.log(data);
});
```

### 3. Promises

```js
let p = new Promise((resolve, reject) => {
  resolve("Success");
});

p.then((res) => console.log(res));
```

### 4. Async / Await

```js
async function test() {
  let res = await Promise.resolve("Done");
  console.log(res);
}

test();
```
---

## What are Web Browser APIs

Web APIs are provided by the browser, not by JavaScript.

Examples:

* setTimeout
* DOM API
* fetch
* console

Example:

```js
setTimeout(() => {
  console.log("Hi");
}, 1000);
```
---

## What is Event Loop

Event Loop checks:

> Is call stack empty?

> If yes => take task from queue => push to stack



Example:

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

console.log("End");
```

Output:

```
Start
End
Timeout
```

The event loop waits for stack to be empty.

---

## What is Callback Hell

Callback hell = Nested callbacks

Bad code example:

```js
setTimeout(() => {
  console.log("1");

  setTimeout(() => {
    console.log("2");

    setTimeout(() => {
      console.log("3");
    }, 1000);

  }, 1000);

}, 1000);
```

This is called:

> Pyramid of Doom

Solution:

* Promises
* Async / Await

---

# PROMISES

## What is a Promise

Promise = Object representing future value

It may be:

* success
* failure
* pending

Example:

```js
let promise = new Promise((resolve, reject) => {
  resolve("Done");
});
```

---

## How to Create a Promise

Syntax:

```js
let p = new Promise((resolve, reject) => {

});
```

Example:

```js
let p = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("Success");
  } else {
    reject("Failed");
  }
});
```

---

## Promise States

Promise has 3 states:

### 1. Pending

Initial state

### 2. Fulfilled

Success

### 3. Rejected

Failure

Flow:

```
Pending => Fulfilled
Pending => Rejected
```

Never:

```
Fulfilled => Rejected
Rejected => Fulfilled
```

---

## How to Consume a Promise

We use:

* then()
* catch()
* finally()

Example:

```js
let p = new Promise((resolve, reject) => {
  resolve("Hello");
});

p.then((data) => {
  console.log(data);
});
```

With reject:

```js
let p = new Promise((resolve, reject) => {
  reject("Error");
});

p
  .then((data) => {
    console.log(data);
  })
  .catch((err) => {
    console.log(err);
  });
```

With finally:

```js
p
  .then(() => {})
  .catch(() => {})
  .finally(() => {
    console.log("Done");
  });
```
---

## Promise Chaining

Promise chaining means calling multiple `.then()` one after another.

Each `.then()` returns a new promise.

### Example

```js
let p = new Promise((resolve, reject) => {
  resolve(10);
});

p
  .then((num) => {
    console.log(num);
    return num * 2;
  })
  .then((num) => {
    console.log(num);
    return num * 3;
  })
  .then((num) => {
    console.log(num);
  });
```

Output

```
10
20
60
```
---

## Handling errors using .catch

`.catch()` handles any error in chain.

```js
p
  .then(() => {
    throw new Error("Fail");
  })
  .catch((err) => {
    console.log(err.message);
  });
```

Output

```
Fail
```

---

## finally block in promise chain

`finally()` runs always.

Success or failure.

```js
p
  .then(() => {
    console.log("Success");
  })
  .catch(() => {
    console.log("Error");
  })
  .finally(() => {
    console.log("Always runs");
  });
```

Output

```
Success
Always runs
```

---

## Error inside .then when there is .catch

Error goes to `.catch`.

```js
Promise.resolve()
  .then(() => {
    throw new Error("Boom");
  })
  .catch((err) => {
    console.log("Caught:", err.message);
  });
```

Output

```
Caught: Boom
```
---

## Error inside .then when there is NO .catch

Unhandled promise rejection.

```js
Promise.resolve()
  .then(() => {
    throw new Error("Boom");
  });
```

Output

```
Uncaught (in promise) Error: Boom
```

---

## 7. Why .catch must be at end of chain

Because errors travel forward.

Example:

```js
p
  .then(() => {})
  .then(() => {})
  .catch(() => {});
```

If catch in middle:

```js
p
  .then(() => {})
  .catch(() => {})
  .then(() => {}) // errors here not caught above
```
---

## Consuming multiple promises by chaining

Sequential execution.

```js
task1()
  .then((res1) => {
    return task2(res1);
  })
  .then((res2) => {
    return task3(res2);
  })
  .then((res3) => {
    console.log(res3);
  });
```

Runs one after another.

---

## 9. Consuming multiple promises using Promise.all

Runs parallel.

```js
Promise.all([
  promise1,
  promise2,
  promise3
])
.then((results) => {
  console.log(results);
})
.catch((err) => {
  console.log(err);
});
```

Output

```
[res1, res2, res3]
```
---

## Error handling in promises

Use:

* catch
* try/catch (async await)
* finally

Example

```js
fetchData()
  .then((data) => {
    return processData(data);
  })
  .catch((err) => {
    console.log("Error:", err);
  })
  .finally(() => {
    console.log("Done");
  });
```
---

## Promisify callback-based functions

Convert callback => promise

### Example with setTimeout

Callback version

```js
function wait(cb) {
  setTimeout(() => {
    cb("Done");
  }, 1000);
}
```

Promisified

```js
function wait() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Done");
    }, 1000);
  });
}
```

---

## Promise.resolve

Creates resolved promise.

```js
Promise.resolve(5)
  .then(console.log);
```

Output

```
5
```
---

## Promise.reject

Creates rejected promise.

```js
Promise.reject("Error")
  .catch(console.log);
```

Output

```
Error
```

---

## Promise.all

All must succeed.

```js
Promise.all([p1, p2, p3])
  .then(console.log)
  .catch(console.log);
```

---

## Promise.allSettled

Waits for all. Even if fail.

```js
Promise.allSettled([p1, p2, p3])
  .then(console.log);
```

Output

```
[
 {status: "fulfilled"},
 {status: "rejected"}
]
```
---

## Promise.any

Returns first success.

```js
Promise.any([p1, p2, p3])
  .then(console.log)
  .catch(console.log);
```

Fails only if all fail.

---

## Promise.race

Returns first finished.

```js
Promise.race([p1, p2, p3])
  .then(console.log)
  .catch(console.log);
```

First resolve OR reject.

---
