## 🧠 JavaScript Essentials – #3 Notes

_(Functions, Arrow Functions, Higher Order Functions, Arrays & Objects)_

---

### 1️⃣ **Functions**

```js
// Regular function
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Alan")); // Hello, Alan!
```

💡 **Notes:**

- Functions help reuse logic.
- You can pass data (parameters) and return results.

---

### 2️⃣ **Arrow Functions**

```js
// Shorter syntax, same result
const greet = (name) => `Hello, ${name}!`;

console.log(greet("Alan"));
```

💡 **Notes:**

- Arrow functions don’t have their own `this` keyword.
- Perfect for small, inline callbacks.

---

### 3️⃣ **Higher Order Functions (HOFs)**

```js
// Functions that take or return another function
const numbers = [1, 2, 3, 4, 5];

// map() → transforms each item
const doubled = numbers.map((num) => num * 2);

// filter() → filters based on a condition
const evens = numbers.filter((num) => num % 2 === 0);

// reduce() → reduces array to single value
const total = numbers.reduce((sum, num) => sum + num, 0);

console.log(doubled, evens, total);
```

💡 **Notes:**

- HOFs are used in modern JS to make code cleaner and declarative.

---

### 4️⃣ **Array Destructuring**

```js
const colors = ["red", "green", "blue"];

// Pull out values into variables
const [first, second] = colors;

console.log(first); // red
console.log(second); // green
```

💡 **Notes:**

- Destructuring makes it easy to unpack array items.

---

### 5️⃣ **Object Destructuring**

```js
const user = { name: "Alan", age: 25, skill: "Laravel" };

// Extract keys directly
const { name, age } = user;

console.log(name); // Alan
console.log(age); // 25
```

💡 **Notes:**

- Helps access object values cleanly.
- Variable names must match key names.

---

### 6️⃣ **Rest Operator (...)**

```js
// Rest collects remaining items
const [first, ...others] = [10, 20, 30, 40];
console.log(first); // 10
console.log(others); // [20, 30, 40]
```

💡 **Notes:**

- Used in function parameters or array/object destructuring.
- Gathers “the rest” of the data.

---

### 7️⃣ **Spread Operator (...)**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];

// Merge arrays
const merged = [...arr1, ...arr2];
console.log(merged); // [1, 2, 3, 4]

// Clone object
const user = { name: "Alan", age: 25 };
const updatedUser = { ...user, age: 26 };

console.log(updatedUser); // { name: 'Alan', age: 26 }
```

💡 **Notes:**

- Spread **expands** elements of an array/object.
- Commonly used for copying or merging.

---

### 📘 Quick Recap

| Topic                | Symbol / Example      | Meaning                        |
| -------------------- | --------------------- | ------------------------------ |
| Function             | `function greet(){}`  | Reusable block of code         |
| Arrow Function       | `const fn = () => {}` | Shorter function syntax        |
| HOF                  | `.map()`, `.filter()` | Takes/returns another function |
| Array Destructuring  | `[a, b] = arr`        | Extracts array values          |
| Object Destructuring | `{x, y} = obj`        | Extracts object properties     |
| Rest                 | `(...args)`           | Gathers remaining items        |
| Spread               | `[...]` or `{...obj}` | Expands elements               |
