---
tags:
  - Web-Development
  - Resources
date: 2025-10-08
---


The `id` attribute adds a unique identifier to an HTML element. In this example, there is an `h1` element with an `id` of `title`:

```html
<h1 id="title">Movie Review Page</h1>
```

You can reference the `id` name of `title` within your JavaScript or CSS. Here's a CSS example referencing the `id` of `title` to change the text `color` to `red`:

```css
#title {
  color: red;
}
```

The hash symbol (`#`) in front of `title`, tells the computer you want to target an `id` with that value. `id` names should not be used more than once, and they should always be unique. Another thing to note about `id` values, is that they cannot have spaces in them. Here is an example of applying the words `main` and `heading` to an `id` attribute value:

```html
<h1 id="main heading">Main heading</h1>
```

Browsers will see this space as part of the `id` which will lead to unwanted issues when it comes to styling and scripting. `id` attribute values should only contain letters, digits, underscores, and dashes.

In contrast to the `id` attribute, the `class` attribute value does not need to be unique and can contain spaces. Here is an example of applying a class called `box` to a `div` element:

```html
<div class="box"></div>
```

If you wanted to add multiple class names to an element, you can do so by separating the names by a space. Here is an updated example applying multiple classes to a `div` element:

```html
<div class="box red-top"></div>
```

To apply a set of styles to that `box` class, you can reference that class inside your CSS. Here is an example of setting `width`, `height`, and `border` properties to the element with the `class` name of `box`:

```css
.box {
  width: 200px;
  height: 200px;
  border: 2px solid black;
}
```

The dot symbol (`.`) in front of `box`, tells the computer you want to target a `class` with that value. When the code runs, it will search through all of your HTML document to find all elements with that class name and apply those styles.

So, to recap, when should you use an `id` versus a `class`? Classes are best used when you want to apply a set of styles to many elements. If you want to target a specific element, it is best to use `id` because those values need to be unique.


[[HTML Build a Recipe Page]]