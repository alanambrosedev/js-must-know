## 🧩 #6 Event Listeners & Timers in JavaScript

🎯 What You’ll Learn _
Attaching and handling user events (`click`, `blur`, `change`, `focus`) _ Using
**setTimeout()** and **setInterval()** \* Understanding **Event Bubbling** and
**Event Capturing** --- ### 📘 1. Basic Event Listeners Event listeners allow
JavaScript to “listen” for user interactions. #### Example: onClick ```html
<button id="btn">Click Me</button>

<script>
  const btn = document.getElementById("btn");

  btn.addEventListener("click", () => {
    alert("Button Clicked!");
  });
</script>

`#### Example: onFocus & onBlur`html
<input id="nameInput" placeholder="Type your name" />

<script>
  const input = document.getElementById("nameInput");

  input.addEventListener("focus", () => {
    input.style.border = "2px solid blue";
  });

  input.addEventListener("blur", () => {
    input.style.border = "1px solid gray";
  });
</script>

`#### Example: onChange`html
<select id="language">

  <option value="">Select Language</option>
  <option value="js">JavaScript</option>
  <option value="php">PHP</option>
</select>

<script>
  const select = document.getElementById("language");

  select.addEventListener("change", () => {
    console.log("You selected:", select.value);
  });
</script>

````--- ### ⏱️ 2. setTimeout() and setInterval() #### setTimeout() Runs the code
**once** after a delay. ```js setTimeout(() => { console.log("This runs after 2
seconds"); }, 2000); ``` #### setInterval() Runs the code **repeatedly** after a
given time interval. ```js let count = 0; const interval = setInterval(() => {
count++; console.log("Count:", count); if (count === 5) clearInterval(interval);
}, 1000); ``` --- ### 🌀 3. Event Bubbling & Capturing **Bubbling:** The event
starts at the deepest element and bubbles **upward**. **Capturing:** The event
is captured **from top (root)** down to the target. #### Example: ```html
<div id="parent" style="padding: 20px; background: lightgray">
  Parent
  <button id="child" style="margin-top: 10px">Child Button</button>
</div>

<script>
  document.getElementById("parent").addEventListener("click", () => {
    console.log("Parent Clicked (Bubbling)");
  });

  document.getElementById("child").addEventListener("click", () => {
    console.log("Child Clicked");
  });

  // Capturing phase
  document.getElementById("parent").addEventListener(
    "click",
    () => {
      console.log("Parent Capturing");
    },
    true
  ); // <- 'true' enables capturing
</script>
``` 🧠 **Flow:** * Capturing → `Parent Capturing` * Target → `Child Clicked` *
Bubbling → `Parent Clicked (Bubbling)` --- ### ✅ Summary | Concept |
Description | | ------------------- | ------------------------------- | |
**onClick** | Fires when user clicks | | **onBlur** | When element loses focus |
| **onFocus** | When element gains focus | | **onChange** | When input/select
value changes | | **setTimeout()** | Runs code once after delay | |
**setInterval()** | Repeats code at interval | | **Event Bubbling** | Event
flows upward | | **Event Capturing** | Event flows downward |
````
