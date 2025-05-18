# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS Event Assignment</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <button id="myButton">Click Me</button>
    <div id="hoverBox">Hover Over Me</div>
    
    <input type="text" id="nameField" placeholder="Enter name">
    <input type="email" id="email" placeholder="Enter email">
    <input type="password" id="password" placeholder="Enter password">
    <div id="feedback"></div>
    <button id="submitBtn">Submit</button>
    <button id="secret">Double Click or Long Press Me</button>
    
    <div id="tabs">
        <button class="tab" data-target="content1">Tab 1</button>
        <button class="tab" data-target="content2">Tab 2</button>
    </div>
    <div id="content1" class="content">Content for Tab 1</div>
    <div id="content2" class="content" style="display: none;">Content for Tab 2</div>
    <img id="slideshow" src="img1.jpg" alt="Slideshow">
    <script src="script.js"></script>
</body>
</html>

#hoverBox {
    width: 200px;
    height: 100px;
    background-color: white;
    border: 1px solid black;
    margin-top: 10px;
}
.tab {
    margin: 5px;
    padding: 8px;
    cursor: pointer;
    border: 1px solid gray;
}
.content {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid black;
}

document.getElementById("myButton").addEventListener("click", function() {
    this.textContent = "Clicked!";
    this.style.backgroundColor = "blue";
});
const box = document.getElementById("hoverBox");
box.addEventListener("mouseover", () => box.style.backgroundColor = "yellow");
box.addEventListener("mouseout", () => box.style.backgroundColor = "white");
document.addEventListener("keydown", function(event) {
    console.log(`You pressed: ${event.key}`);
});
const secretBtn = document.getElementById("secret");
secretBtn.addEventListener("dblclick", () => alert("Secret unlocked!"));
let pressTimer;
secretBtn.addEventListener("mousedown", () => {
    pressTimer = setTimeout(() => alert("Long press detected!"), 1000);
});
secretBtn.addEventListener("mouseup", () => clearTimeout(pressTimer));
document.getElementById("submitBtn").addEventListener("click", function() {
    const input = document.getElementById("nameField").value;
    if (!input) alert("Name is required!");
});
document.getElementById("email").addEventListener("input", function() {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    this.style.borderColor = emailPattern.test(this.value) ? "green" : "red";
});
document.getElementById("password").addEventListener("input", function() {
    const message = document.getElementById("feedback");
    this.value.length >= 8 
        ? message.textContent = "✔️ Strong password!" 
        : message.textContent = "❌ At least 8 characters required.";
});
document.querySelectorAll(".tab").forEach(tab => {
    tab.addEventListener("click", function() {
        document.querySelectorAll(".content").forEach(c => c.style.display = "none");
        document.getElementById(this.dataset.target).style.display = "block";
    });
});
let currentImage = 0;
const images = ["img1.jpg", "img2.jpg", "img3.jpg"];
const imgElement = document.getElementById("slideshow");
setInterval(() => {
    currentImage = (currentImage + 1) % images.length;
    imgElement.src = images[currentImage];
}, 3000);



