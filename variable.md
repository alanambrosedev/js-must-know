# 🧠 JavaScript Variables — Summary Notes

---

## 🔹 1. `var`, `let`, `const` Basics

```js
// var = old way (function-scoped, can re-declare, hoisted)
var name = "Alan";
var name = "John"; // allowed
console.log(name); // John

// let = modern way (block-scoped, cannot re-declare)
let age = 25;
// let age = 30; ❌ Error: Cannot re-declare
age = 26; // ✅ can reassign
console.log(age);

// const = fixed variable (block-scoped, cannot reassign)
const country = "India";
// country = "USA"; ❌ Error: Cannot reassign
console.log(country);
```

---

## 🔹 2. Block Scope vs Function Scope

```js
if (true) {
  const a = 10;
  let b = 20;
  var c = 30; // var ignores block and leaks out
}

console.log(c); // ✅ Works (var is function-scoped)
// console.log(a); ❌ Error (const is block-scoped)
// console.log(b); ❌ Error (let is block-scoped)
```

🧩 **Meaning:**

- `var` can be used outside the block
- `let` and `const` can’t — they live only inside `{}`

---

## 🔹 3. Hoisting & Temporal Dead Zone (TDZ)

```js
console.log(a); // undefined (var is hoisted but not initialized)
console.log(b); // ❌ Error (in TDZ)
console.log(c); // ❌ Error (in TDZ)

var a = 1;
let b = 2;
const c = 3;
```

🧩 **Meaning:**

- JavaScript moves all declarations to the top internally (hoisting).
- But only `var` gets `undefined` automatically.
- `let` and `const` are not usable before their line of declaration → **TDZ**.

---

## 🔹 4. Reassignment Rules

```js
let counter = 0;
counter++; // ✅ allowed
counter = counter + 1;
console.log(counter); // 2

const score = 10;
// score = 20; ❌ Error (cannot reassign const)
```

---

## 🔹 5. Mutating Objects and Arrays (Const Still Works)

```js
const user = { name: "Alan", age: 25 };
user.age = 26; // ✅ allowed (object value changed)
console.log(user);

// ❌ but reassigning whole object not allowed:
// user = { name: "John" }; // Error

const colors = ["red", "blue"];
colors.push("green"); // ✅ allowed (we changed content)
console.log(colors);
```

🧩 **Meaning:**
`const` freezes the variable **binding**, not the data inside it.

---

## 🔹 6. Why `var` is Problematic (Async Loops Example)

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 3 3 3 ❌ (same value printed each time)
```

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 0 1 2 ✅ (each loop keeps its own block scope)
```

🧩 **Meaning:**
`let` creates a new variable each loop → correct output.

---

## 🔹 7. Common Scope + Hoisting Bug

```js
function run() {
  console.log(x); // undefined (var hoisted)
  var x = 10;

  if (true) {
    let y = 20;
  }

  console.log(y); // ❌ Error (y is block-scoped)
}
run();
```

🧩 **Fix:**

```js
function run() {
  const x = 10;
  let y;
  if (true) {
    y = 20;
  }
  console.log(x, y); // ✅ Works fine
}
run();
```

---

## 🔹 8. Modern Best Practices Summary

✅ Use **`const`** → default for most variables
✅ Use **`let`** → when you need to change value later
❌ Avoid **`var`** → causes hoisting and scope confusion

---

## 🔹 9. Real Example (Refactoring Legacy Code)

Old code:

```js
var user = { name: "Alan" };
var age = 25;
var skills = ["JS", "Laravel"];
function update() {
  user.name = "Mentor";
  age = 26;
  skills.push("React");
}
```

Modern code:

```js
const user = { name: "Alan" }; // object doesn’t rebind
let age = 25; // value changes later
const skills = ["JS", "Laravel"]; // array same variable, new items ok

function update() {
  user.name = "Mentor"; // mutate allowed
  age = 26; // let allows change
  skills.push("React");
}
```

---

## 🧾 Final Recap

| Keyword   | Scope    | Reassign? | Redeclare? | Hoisted?       | Common Use                           |
| --------- | -------- | --------- | ---------- | -------------- | ------------------------------------ |
| **var**   | Function | ✅        | ✅         | ✅ (undefined) | Legacy / Avoid                       |
| **let**   | Block    | ✅        | ❌         | ❌ (TDZ)       | Loops, changing values               |
| **const** | Block    | ❌        | ❌         | ❌ (TDZ)       | Defaults, constants, arrays, objects |

---
