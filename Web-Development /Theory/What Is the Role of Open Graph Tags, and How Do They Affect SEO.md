
## 🎯 Content

The open graph protocol enables you to control how your website's content appears across various social media platforms, such as Facebook, LinkedIn, and many more. By setting these open graph properties, you can entice users to want to click and engage with your content. You can set these properties through a collection of `meta` elements inside your HTML `head` section.

The first important OG property to include would be the `title`. Here is an example of setting the OG `title` for the freeCodeCamp homepage:

```html
<meta content="freeCodeCamp.org" property="og:title" />
```

```html
<meta content="freeCodeCamp.org" property="og:title" />
```

For the `property` attribute, you will need to specify that it is `og:title`. The `content` attribute is where you will write the title you want displayed for social media sites.

The next important OG property would be the `type`. Here is an example of using the OG `type` for the freeCodeCamp homepage:

```html
<meta property="og:type" content="website" />
```

```html
<meta property="og:type" content="website" />
```

The `type` property is used to represent the type of content being shared on social media. Examples of this content include articles, websites, videos, or music.

The third important OG property would be the `image`. Here is an example of setting the OG `image` for the freeCodeCamp homepage:

```html
<meta
  content="https://cdn.freecodecamp.org/platform/universal/fcc_meta_1920X1080-indigo.png"
  property="og:image"
/>
```

```html
<meta
  content="https://cdn.freecodecamp.org/platform/universal/fcc_meta_1920X1080-indigo.png"
  property="og:image"
/>
```

In this example, the open graph image is pointing to the freeCodeCamp logo. All of these images should be high quality with good dimensions and ratios. Most social media platforms will include criteria for image requirements to help you ensure that your content displays well on their site. For example, the [developers.facebook.com](http://developers.facebook.com) documentation page states:

"use images that are at least 1200 by 630 pixels for the best display on high resolution devices. At the minimum, you should use images that are 600 by 315 pixels to display link page posts with larger images."

The fourth important OG property would be the `url`. Here is an example of setting the OG `url` for the freeCodeCamp homepage:

```html
<meta property="og:url" content="https://www.freecodecamp.org" />
```

```html
<meta property="og:url" content="https://www.freecodecamp.org" />
```

There are many more OG properties that you can set, like `description`, `audio`, `video` and `locale`. However, the open graph `url`, `image`, `type`, and `title` are the most important ones to include.

So how do these open graph properties affect Search Engine Optimization? When your content is shared on social media, well-crafted OG properties can enhance the appearance for your content in users' feeds. This can lead to higher click-through rates which could signal to search engines that your content is relevant and engaging.