## 🧠 Conditional (Ternary) Operator in JavaScript

### 🔹 What It Is

The **conditional (ternary) operator** lets you write a quick `if...else` statement in a single line.
It’s called _ternary_ because it has **three parts**.

---

### 🔹 Syntax

```js
condition ? expressionIfTrue : expressionIfFalse;
```

---

### 🔹 Basic Example

```js
let age = 18;
let message = age >= 18 ? "You can vote." : "You're too young.";
console.log(message); // "You can vote."
```

✅ **Same as:**

```js
if (age >= 18) {
  message = "You can vote.";
} else {
  message = "You're too young.";
}
```

---

### 🔹 Nested (Chained) Ternaries

Use when you have more than two possible outcomes:

```js
let score = 75;
let result =
  score >= 90
    ? "Excellent"
    : score >= 70
    ? "Good"
    : score >= 50
    ? "Pass"
    : "Fail";

console.log(result); // "Good"
```

🧩 JavaScript checks conditions **from left to right** and stops when it finds one that’s true.

---

### 🔹 When to Use

#### ✅ Use **ternary** when:

- The condition and outcomes are short.
- It improves readability in one line.

**Examples:**

```js
let access = age >= 18 ? "Allowed" : "Denied";
let displayName = isLoggedIn ? userName : "Guest";
```

#### 🚫 Use **if...else** when:

- You have **multiple or nested** conditions.
- You need **clarity** or **debugging** ease.

**Example (better as if...else):**

```js
if (score > 90) grade = "A";
else if (score > 80) grade = "B";
else if (score > 70) grade = "C";
else grade = "F";
```

---

### 🔹 Summary Table

| Situation                         | Best Choice   | Example                            |
| --------------------------------- | ------------- | ---------------------------------- |
| Simple true/false check           | **Ternary**   | `isOnline ? "Active" : "Offline"`  |
| Two short outcomes                | **Ternary**   | `num % 2 === 0 ? "Even" : "Odd"`   |
| Multiple branches (3+)            | **if...else** | grading system, range checks       |
| Complex logic needing explanation | **if...else** | input validation, nested decisions |
