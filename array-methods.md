## 🧩 JavaScript Array Methods — `map()`, `filter()`, `reduce()`, `sort()`

### 🧠 Overview

These methods help you **transform, filter, combine, and order** data in arrays without mutating the original array (except `sort()`, which does mutate).

---

### 1️⃣ `map()`

Transforms every element and returns a **new array** of the same length.

```js
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);

console.log(doubled); // [2, 4, 6, 8]
```

✅ Doesn’t change the original array
✅ Always returns a new one

---

### 2️⃣ `filter()`

Keeps only elements that match a condition.

```js
const numbers = [1, 2, 3, 4, 5];
const even = numbers.filter(num => num % 2 === 0);

console.log(even); // [2, 4]
```

✅ Returns a new array
✅ Can return fewer (or zero) elements

---

### 3️⃣ `reduce()`

Combines all array elements into **one value** (number, string, object, or array).

#### Example: Sum of numbers

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);

console.log(sum); // 10
```

#### Example: Count items

```js
const fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];

const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});

console.log(count); // { apple: 3, banana: 2, orange: 1 }
```

#### Example: Flatten nested arrays

```js
const nested = [[1, 2], [3, 4], [5, 6]];

const flat = nested.reduce((acc, curr) => acc.concat(curr), []);

console.log(flat); // [1, 2, 3, 4, 5, 6]
```

✅ Very flexible — can calculate, build, or transform any kind of data

---

### 4️⃣ `sort()`

Sorts array elements **in place**.
By default, it sorts as strings (lexicographically).

```js
const nums = [5, 10, 1, 25];
console.log(nums.sort()); 
// [1, 10, 25, 5] ❌ (string sort)
```

#### ✅ Numeric Sort

```js
const ascending = nums.sort((a, b) => a - b);
console.log(ascending); // [1, 5, 10, 25]

const descending = nums.sort((a, b) => b - a);
console.log(descending); // [25, 10, 5, 1]
```

✅ Use a compare function for correct numeric sorting
⚠️ `sort()` **changes** the original array

---

### 🧭 Quick Summary

| Method     | Returns    | Mutates Original | Use For             |
| ---------- | ---------- | ---------------- | ------------------- |
| `map()`    | New array  | ❌ No             | Transforming values |
| `filter()` | New array  | ❌ No             | Selecting elements  |
| `reduce()` | Any value  | ❌ No             | Combining values    |
| `sort()`   | Same array | ✅ Yes            | Ordering values     |
