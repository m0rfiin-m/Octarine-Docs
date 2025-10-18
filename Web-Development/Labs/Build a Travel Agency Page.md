
Instructions to build

 1. You should have a `DOCTYPE` declaration.
 2. You should have an `html` element with `lang` set to `en`.
 3. You should have a `head` element containing a `meta` void element with `charset` set to `utf-8` and a `title` with the text `Travel Agency Page`.
 4. You should have a `meta` tag in your `head` element that contains a short description of your website for SEO.
 5. You should have an `h1` element to present your travel destinations.
 6. You should have a paragraph below the `h1` element introducing the travel opportunities.
 7. You should have an `h2` element with the text `Packages`.
 8. You should have a `p` element introducing briefly the various packages.
 9. You should have an unordered list element with two list items. The two list items should have the text `Group Travels`and `Private Tours`, respectively. The text of each list item should be enclosed by an anchor element.
10. You should have an `h2` element with the text `Top Itineraries`.
11. You should have at least three `figure` elements, each containing an anchor element and a `figcaption` element.
12. The three anchor elements should have an `img` element with an appropriate `alt` attribute and a `src` attribute set to a valid image as their content. You can use `https://cdn.freecodecamp.org/curriculum/labs/colosseo.jpg`, `https://cdn.freecodecamp.org/curriculum/labs/alps.jpg`, and `https://cdn.freecodecamp.org/curriculum/labs/sea.jpg` if you would like.
13. All your five anchor elements should have an `href` attribute with the value of `https://www.freecodecamp.org/learn` and a `target` attribute with the value of `_blank`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="description" content="Discover amazing travel destinations with our curated group tours and private travel packages across Europe and beyond.">
    <title>Travel Agency Page</title>
</head>
<body>
    <h1>Explore Unforgettable Destinations</h1>
    <p>Welcome to your gateway for extraordinary travel experiences. Whether you're seeking adventure, culture, or relaxation, we offer carefully crafted journeys to the world's most captivating locations.</p>
    
    <h2>Packages</h2>
    <p>Choose the travel style that fits your needs. We offer flexible options for both group adventures and personalized private tours.</p>
    
    <ul>
        <li><a href="https://www.freecodecamp.org/learn" target="_blank">Group Travels</a></li>
        <li><a href="https://www.freecodecamp.org/learn" target="_blank">Private Tours</a></li>
    </ul>
    
    <h2>Top Itineraries</h2>
    
    <figure>
        <a href="https://www.freecodecamp.org/learn" target="_blank">
            <img src="https://cdn.freecodecamp.org/curriculum/labs/colosseo.jpg" alt="The ancient Colosseum in Rome with tourists walking around the historic amphitheater">
        </a>
        <figcaption>Historic Rome - Explore ancient wonders and Renaissance art</figcaption>
    </figure>
    
    <figure>
        <a href="https://www.freecodecamp.org/learn" target="_blank">
            <img src="https://cdn.freecodecamp.org/curriculum/labs/alps.jpg" alt="Snow-capped Alpine mountains with green valleys and traditional chalets">
        </a>
        <figcaption>Swiss Alps Adventure - Mountain peaks and scenic villages</figcaption>
    </figure>
    
    <figure>
        <a href="https://www.freecodecamp.org/learn" target="_blank">
            <img src="https://cdn.freecodecamp.org/curriculum/labs/sea.jpg" alt="Crystal clear turquoise Mediterranean waters along a coastal beach">
        </a>
        <figcaption>Mediterranean Coast - Sun, sea, and stunning shorelines</figcaption>
    </figure>
</body>
</html>
```