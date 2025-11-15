# 📘 Async/Await & Try/Catch — Notes

## ## 8. Async / Await

### **What is async/await?**

Async/await is a cleaner and easier way to work with Promises.
It makes asynchronous code look like normal step-by-step code.

---

## **async keyword**

- Used before a function.
- That function automatically returns a Promise.
- Inside this function, you can use `await`.

Example:

```js
async function getValue() {
  return 10; // becomes Promise.resolve(10)
}
```

---

## **await keyword**

- Pauses the code until a Promise completes.
- Can only be used inside an async function.
- Removes the need for `.then()` chains.

Example:

```js
function waitOneSec() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Done"), 1000);
  });
}

async function run() {
  console.log("Start");
  const msg = await waitOneSec(); // waits here
  console.log(msg);
  console.log("End");
}
```

---

## **Why async/await?**

- Easy to read
- Easy to write
- Looks like normal synchronous code
- No “.then().then().then()” chains
- Better for complex async logic

---

# ## 9. Try / Catch

### **What is try/catch?**

Used to safely handle errors in your code, especially inside async functions.

- **try** → Code that may fail
- **catch** → Runs when an error happens

---

## Example with fetch

```js
async function getUser() {
  try {
    const res = await fetch("https://api.com/user"); // waits
    const data = await res.json(); // waits
    console.log(data);
  } catch (err) {
    console.log("Error fetching user"); // handles errors
  }
}
```

---

# ⭐ Combined Flow (Easy to Remember)

1. Add `async` to function
2. Use `await` to pause until Promise finishes
3. Use `try` for the main code
4. Use `catch` to catch errors

---

# 🧠 One-Line Summary

**async/await makes promise-based code simple, and try/catch makes error handling clean.**
