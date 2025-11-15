# 📘 Asynchronous JavaScript — Complete README

JavaScript is single-threaded, but real-world tasks like API calls, file reads, timers, and database calls take time.
To avoid blocking the UI, JavaScript uses **asynchronous programming**.

This guide covers the full progression:

1. **Callbacks**
2. **Callback Hell**
3. **Promises**
4. **then() / catch()**
5. **Promise APIs**

---

# 1️⃣ Callbacks

A **callback** is a function passed into another function to run _later_.

Common use: run code **after** an async task completes.

### Example:

```js
function loadData(callback) {
  setTimeout(() => {
    callback("Data loaded");
  }, 1000);
}

loadData((result) => {
  console.log(result);
});
```

Why callbacks?
✔ They allow you to wait for async operations.

---

# 2️⃣ Callback Hell

If you keep putting callbacks inside callbacks, code becomes messy:

```js
getUser((user) => {
  getPosts(user.id, (posts) => {
    getComments(posts[0].id, (comments) => {
      console.log("Finished");
    });
  });
});
```

Problems:

- Hard to read
- Hard to maintain
- Hard to handle errors
- Pyramid-shaped indentation

Solution → **Promises**

---

# 3️⃣ Promises

A Promise represents a value that will come **in the future**.

### States:

- **pending** → waiting
- **fulfilled** → success
- **rejected** → error

### Creating a Promise:

```js
const task = new Promise((resolve, reject) => {
  const ok = true;

  if (ok) {
    resolve("Operation successful");
  } else {
    reject("Something went wrong");
  }
});
```

---

# 4️⃣ then() and catch()

Promises replace the nested callback pattern with a cleaner flow.

### Using a Promise:

```js
task
  .then((result) => {
    console.log(result); // success
  })
  .catch((error) => {
    console.log(error); // failure
  });
```

### Chaining (Fix for callback hell):

```js
getUser()
  .then((user) => getPosts(user.id))
  .then((posts) => getComments(posts[0].id))
  .then((comments) => console.log("Done"))
  .catch((err) => console.log("Error:", err));
```

This is much more readable.

---

# 5️⃣ Promise APIs

Modern JavaScript provides several built-in utility functions for advanced async patterns.

---

### 🔹 **Promise.all()**

Runs tasks **in parallel** → waits until _every_ one finishes.

```js
Promise.all([task1(), task2(), task3()])
  .then((values) => console.log(values))
  .catch((err) => console.log("One failed:", err));
```

Fails if _any one_ promise fails.

---

### 🔹 **Promise.race()**

Returns result of **the first promise** that settles (resolve/reject).

```js
Promise.race([task1(), task2()]).then((value) =>
  console.log("Fastest:", value)
);
```

---

### 🔹 **Promise.allSettled()**

Waits for all promises — success or failure.

```js
Promise.allSettled([task1(), task2(), task3()]).then((results) =>
  console.log(results)
);
```

Useful when you want _all outcomes_.

---

### 🔹 **Promise.any()**

Returns the **first successful** promise.

```js
Promise.any([task1(), task2(), task3()])
  .then((value) => console.log("First success:", value))
  .catch(() => console.log("All promises failed"));
```

---

# ✅ Summary

| Concept       | Purpose                                       |
| ------------- | --------------------------------------------- |
| Callbacks     | Basic async handling                          |
| Callback Hell | Problem of nested callbacks                   |
| Promises      | Cleaner async model                           |
| then/catch    | Handle success/errors                         |
| Promise APIs  | Parallel, fastest, all results, first success |
