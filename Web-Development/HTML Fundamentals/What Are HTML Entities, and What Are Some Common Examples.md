---
tags:
  - Web-Development
  - Resources
  - dev-tools
---


An HTML entity, or character reference, is a set of characters used to represent a reserved character in HTML. In this example, there is a paragraph element with an image element nested inside:

```html
<p>This is an <img /> element</p>
```

The text on the screen should say `This is an <img/> element`. However, the text currently says `This is an element.` This is happening because when the HTML parser sees the less than (`<`) symbol followed by an HTML tag name, it interprets that as an HTML element.

To fix this issue, you can use HTML entities. Here is an updated example using the correct HTML entities for the less than and greater than (`>`) symbols.

```html
<p>This is an &lt;img /&gt; element</p>
```

These types of character references are known as named character references. Named references start with an ampersand sign (`&`) and end with a semicolon (`;`). By using a named character reference, the HTML parser will not confuse this with an actual HTML element. Here is what the updated paragraph element looks like on the page: `This is an <img/> element`. Now, users will be able to see the entire image element syntax as you intended it.

Another type of character reference would be the decimal numeric reference. Here is an example of using the decimal numeric reference for the less than symbol:

```html
&#60;
```

This character reference starts with an ampersand sign and hash symbol (`#`), followed by one or more decimal digits, followed by a semicolon.

The last type of character reference would be the hexadecimal numeric reference. Here is an example of using the hexadecimal numeric reference for the less than symbol:

```html
&#x3C;
```

This character reference starts with an ampersand sign, hash symbol, and the letter `x`. Then it is followed by one or more ASCII hex digits and ends with a semicolon.

So what are some other examples of using HTML entities? Well, you often see them used for symbols like the copyright symbol (`©`), quotes (`"`), trademark symbol (`™`), and the ampersand sign.