## 🧩 JavaScript: Logical Operators & Optional Chaining

### 🧠 What You’ll Learn

- How `&&` (AND) and `||` (OR) behave with real values (not just booleans)
- How **optional chaining (`?.`)** safely accesses nested data
- How to combine them for cleaner, error-free code

---

### ⚙️ Logical Operators Overview

| Operator | Meaning           | Returns                                   | Example        | Result                                    |     |     |          |           |
| -------- | ----------------- | ----------------------------------------- | -------------- | ----------------------------------------- | --- | --- | -------- | --------- |
| `&&`     | AND               | First **falsy** value, or last truthy one | `"Hi" && "JS"` | `"JS"`                                    |     |     |          |           |
| `        |                   | `                                         | OR             | First **truthy** value, or last falsy one | `0  |     | "Guest"` | `"Guest"` |
| `?.`     | Optional chaining | `undefined` if chain breaks               | `user?.name`   | `undefined`                               |     |     |          |           |

---

### 🔍 Why Use Optional Chaining

If you try to access a nested property that doesn’t exist:

```js
console.log(user.address.city);
// ❌ TypeError: Cannot read properties of undefined
```

✅ With optional chaining:

```js
console.log(user?.address?.city);
// ✅ Returns undefined safely
```

---

### 💡 Example 1 — Safe Access + Fallback

```js
const user = {
  profile: { name: "Alan" },
};

const displayName = user?.profile?.name || "Guest";
console.log(displayName); // "Alan"
```

Explanation:

- `user?.profile?.name` safely checks each level.
- If `name` is missing, `"Guest"` becomes the fallback.

---

### 💡 Example 2 — Conditional Display with AND

```js
const greeting = user?.profile?.name && `Hello, ${user.profile.name}!`;
console.log(greeting); // "Hello, Alan!"
```

Explanation:

- `&&` ensures the right side runs only if the left is truthy.
- No name → expression stops early.

---

### 💡 Example 3 — Missing Nested Property

```js
const user2 = { name: "Alan" };

const city = user2?.address?.city || "Unknown";
const message = user2?.address?.city && `Lives in ${user2.address.city}`;

console.log(city); // "Unknown"
console.log(message); // undefined
```

Explanation:

- `address` doesn’t exist, so `user2?.address?.city` → `undefined`.
- `||` returns `"Unknown"`.
- `&&` short-circuits → `undefined`.

---

### 🚀 Combine All in One Example

```js
const user = {
  profile: { name: "Alan" },
  settings: { theme: "dark" },
};

// Safe access and defaults
const name = user?.profile?.name || "Guest";
const theme = user?.settings?.theme || "light";
const location = user?.address?.city || "Unknown";

// Conditional rendering
const welcomeMsg = user?.profile?.name && `Welcome back, ${name}!`;

console.log(name); // "Alan"
console.log(theme); // "dark"
console.log(location); // "Unknown"
console.log(welcomeMsg); // "Welcome back, Alan!"
```

---

### 🧭 Quick Summary

| Operator | Use When                                                     | Example                         |                                       |           |     |          |
| -------- | ------------------------------------------------------------ | ------------------------------- | ------------------------------------- | --------- | --- | -------- |
| `&&`     | You only want the next part to run **if previous is truthy** | `isLoggedIn && showDashboard()` |                                       |           |     |          |
| `        |                                                              | `                               | You want a **default/fallback value** | `username |     | "Guest"` |
| `?.`     | You’re not sure an object/property exists                    | `user?.settings?.theme`         |                                       |           |     |          |
