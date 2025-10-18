First, you need to understand how images work. Common image formats like PNG and JPG are classified as raster formats. This essentially means that they are pixel-based, with the data tracking the color value in each pixel.

A large downside of raster based images is that they do not upscale well. If you've ever tried to make a PNG larger, you may have seen that it becomes pixelated, or blurry.

An SVG is a different kind of image. SVG stands for a scalable vector graphic. A vector graphic tracks data based on paths and equations to plot points, lines, and curves. What this really means is that a vector graphic, like an SVG, can be scaled to any size without impacting the quality.

SVGs specifically have the added benefit of storing data in XML. This means you can use them directly in your code as raw HTML with the `svg` element. It also means you can programmatically change the color of the image.

```html
<svg width="100" height="100" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="45" stroke="black" stroke-width="4" fill="yellow" />
  <circle cx="35" cy="40" r="5" fill="black" />
  <circle cx="65" cy="40" r="5" fill="black" />
  <path d="M35 65 Q50 80 65 65" stroke="black" stroke-width="4" fill="transparent" />
</svg>
```

This SVG code draws a smiley face by combining a few basic elements:

- The `svg` element is the container for the whole drawing. It sets up the space where all the shapes appear. Everything you want to draw with SVG, such as circles, lines, or paths, goes inside the `svg` element.
- The `circle` element is used to make the face and the eyes. One large circle forms the yellow face, and two smaller circles make the eyes.
- The `path` element is used to draw the smile. It creates a curved line for the mouth.
- Each SVG element has attributes that control its appearance and position within the drawing area.

So when would you want to use an SVG? A great use case is for icons. If you want to create custom bullet points, or add icons to your links to represent social media platforms, using SVGs is the best approach. One of the most popular icon libraries, Font Awesome, uses SVG images for their icons. SVGs are also great for webpage logos, because they scale perfectly. They allow you to adapt your layout to any responsive design you need. Next time you have an SVG locally, try opening it with a text editor and playing with the code.