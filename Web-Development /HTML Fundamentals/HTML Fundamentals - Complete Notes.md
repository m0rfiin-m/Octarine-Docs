
**HTML Fundamentals - Complete Notes**

### **1. What are Div Elements and When Should You Use Them**

The `div` is the Content Division Element:

```html
<div></div>
```

The `div` is flexible and can be anything you want. You can give it `height`, `width`, and background color using CSS.

**Basic use - grouping elements:**

```html
<div>
  <h1>I am a heading</h1>
  <p>I am a paragraph</p>
</div>
```

**Better alternative - semantic HTML:**

```html
<section>
  <h1>I am a heading</h1>
  <p>I am a paragraph</p>
</section>
```

The `section` element has semantic meaning. Browsers understand it better across all devices (desktop, mobile, etc.). The `div`doesn't have semantic meaning - it's like a "mysterious ghost" without inherent context.

---

### **2. What Are IDs and Classes, and When Should You Use Them**

**ID Attribute** - Unique identifier for elements:

```html
<h1 id="title">Movie Review Page</h1>
```

**CSS targeting with ID:**

```css
#title {
  color: red;
}
```

**ID Rules:**

- Must be unique (use only once per page)
- No spaces allowed (use `main-heading` not `main heading`)
- Only letters, digits, underscores, and dashes

**Class Attribute** - Can be reused and contain spaces:

```html
<div class="box"></div>
```

**Multiple classes:**

```html
<div class="box red-top"></div>
```

**CSS targeting with class:**

```css
.box {
  width: 200px;
  height: 200px;
  border: 2px solid black;
}
```

**When to use:**

- **Classes**: Apply styles to many elements
- **IDs**: Target one specific element

---

### **3. What Are HTML Entities, and What Are Some Common Examples**

HTML entities represent reserved characters in HTML.

**Problem:**

```html
<p>This is an <img /> element</p>
```

This displays as: `This is an element` (the tags disappear)

**Solution - Named character references:**

```html
<p>This is an &lt;img /&gt; element</p>
```

This displays correctly: `This is an <img/> element`

**Named references:**

- Start with `&` and end with `;`
- `&lt;` = less than `<`
- `&gt;` = greater than `>`

**Decimal numeric reference:**

```html
&#60;
```

Format: `&#` + decimal digits + `;`

**Hexadecimal numeric reference:**

```html
&#x3C;
```

Format: `&#x` + hex digits + `;`

**Common HTML entities:**

- `&copy;` = © (copyright)
- `&quot;` = " (quote)
- `&trade;` = ™ (trademark)
- `&amp;` = & (ampersand)

---

### **4. What Is the Role of the Script Element in HTML**

The `script` element embeds executable code (usually JavaScript) to add interactivity.

**Inline JavaScript:**

```html
<body>
  <script>
    alert("Welcome to freeCodeCamp");
  </script>
</body>
```

**Best practice - external JavaScript file:**

```html
<script src="path-to-javascript-file.js"></script>
```

**Why external files?**

- **Separation of concerns**: Keep JavaScript separate from HTML
- Better organization and maintainability
- The `src` attribute specifies the file location

---

### **5. What Are the Roles of the HTML Audio and Video Elements**

**Audio Element** - Supports mp3, wav, ogg formats:

**Basic (no controls visible):**

```html
<audio src="CrystalizeThatInnerChild.mp3"></audio>
```

**With controls:**

```html
<audio src="CrystalizeThatInnerChild.mp3" controls></audio>
```

**Loop attribute (continuous playback):**

```html
<audio
  src="https://cdn.freecodecamp.org/curriculum/js-music-player/can't-stay-down.mp3"
  loop
  controls
></audio>
```

**Muted attribute:**

```html
<audio
  src="https://cdn.freecodecamp.org/curriculum/js-music-player/can't-stay-down.mp3"
  loop
  controls
  muted
></audio>
```

**Multiple source formats (browser compatibility):**

```html
<audio controls>
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.wav" type="audio/wav" />
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

**Video Element** - Supports mp4, ogg, webm formats:

**Basic video:**

```html
<video
  src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
  loop
  controls
  muted
></video>
```

**With poster image (displays while loading):**

```html
<video
  src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
  loop
  controls
  muted
  poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
  width="620"
></video>
```

**Key attributes:**

- `controls` - Shows playback controls
- `loop` - Continuous replay
- `muted` - Starts muted
- `poster` - (Video only) Image shown while loading
- `width` - Set video width

---

### **6. What Are SVGs, and When Should You Use Them**

**Raster vs Vector:**

- **Raster (PNG/JPG)**: Pixel-based, becomes pixelated when scaled
- **Vector (SVG)**: Path/equation-based, scales perfectly without quality loss

**SVG = Scalable Vector Graphic**

- Stores data in XML
- Can be used directly in HTML
- Colors can be changed programmatically

**SVG smiley face example:**

```html
<svg width="100" height="100" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="45" stroke="black" stroke-width="4" fill="yellow" />
  <circle cx="35" cy="40" r="5" fill="black" />
  <circle cx="65" cy="40" r="5" fill="black" />
  <path d="M35 65 Q50 80 65 65" stroke="black" stroke-width="4" fill="transparent" />
</svg>
```

**SVG elements:**

- `svg` - Container for the entire drawing
- `circle` - Creates circular shapes
- `path` - Creates curved lines and complex shapes

**When to use SVGs:**

- **Icons** (social media, custom bullets)
- **Logos** (perfect scaling)
- **Responsive designs** (adapts to any size)
- Font Awesome uses SVGs for all their icons

**Pro tip:** Open SVG files in a text editor to see and edit the code directly.

---

### **7. What Are Common Ways to Optimize Media Assets**

**Three optimization factors:**

**1. Size/Resolution**

- Match image resolution to display size
- Example: If displaying at 640x480, serve 640x480, not 1920x1080
- Smaller resolution = smaller file size = faster load

**2. File Format**

- **Old formats**: PNG, JPG
- **Modern formats**: WEBP, AVIF (better compression, smaller files)
- Use modern formats unless you need to support old browsers

**3. Compression**

- Tools: pngcrush (local), online compression tools
- **Lossless**: Original data can be perfectly reconstructed
- **Lossy** (JPG): Compression degrades quality - be careful with re-compression

**Key principle:** Don't make users download unnecessary data

---

### **8. What Are the Different Types of Image Licenses**

**Default: All Rights Reserved**

- Images are intellectual property protected by copyright
- Creator owns all rights by default

**Three ways to legally use images:**

1. **Written permission** from copyright holder
2. **Purchase a license** from copyright holder
3. **Fair use** (limited and transformative use like commentary, review, parody)

**Permissive Licenses:**

- **Creative Commons**: Various restrictions (may require attribution, no commercial use, etc.)
- **BSD License**: Used by freeCodeCamp
- Always read the specific license terms

**Public Domain:**

- No copyright restrictions
- Free to use without limitations
- **Creative Commons 0 (CC0)**: Explicitly public domain

**Resources for free images:**

- Pixabay
- Unsplash
- Search engine license filters

**Always check license before using any image on your site**