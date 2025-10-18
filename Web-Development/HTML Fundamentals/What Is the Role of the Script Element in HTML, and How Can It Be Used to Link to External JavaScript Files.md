---
tags:
  - Web-Development
  - Resources
date: 2025-10-08
---

---

## 📋 Overview



---

## 🎯 Content

The `script` element is used to embed executable code. Most developers will use this to execute JavaScript code. JavaScript is used to add interactivity to your web pages. Common examples of using JavaScript include interactive games, image sliders, and dynamic forms that validate user input in real-time. Here is an example of using the `script` element in an HTML document:

```html
<body>
  <script>
    alert("Welcome to freeCodeCamp");
  </script>
</body>
```

In this example, we have an `alert` to display the message `Welcome to freeCodeCamp.` When the page first loads, the alert will pop up. Then the user can click on the OK button to dismiss the message.

While you can technically write all of your JavaScript code inside the `script` tags, it is considered best practice to link to an external JavaScript file instead. Here is an example of using the `script` element to link to an external JavaScript file:

```html
<script src="path-to-javascript-file.js"></script>
```

 The `src` attribute is used here to specify the location for that external JavaScript file. `src` stands for "source". The reason why it is not encouraged to place all of your JavaScript inside the HTML document is because of separation of concerns. Separation of concerns is a design principle where you separate your programs into distinct sections and have each section address a separate concern. In this case, we want to separate our JavaScript code from our HTML code.
---

## 🔗 Related

- [[HTML Build a Recipe Page]]

---




