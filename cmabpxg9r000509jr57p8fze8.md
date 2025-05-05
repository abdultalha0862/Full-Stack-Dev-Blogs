---
title: "Beginner's Guide to Creating Web Pages with HTML"
seoTitle: "HTML Web Page Creation: A Beginner's Guide"
datePublished: Mon May 05 2025 23:35:12 GMT+0000 (Coordinated Universal Time)
cuid: cmabpxg9r000509jr57p8fze8
slug: beginners-guide-to-creating-web-pages-with-html
tags: web-development, html, full-stack, html5

---

## Introduction to HTML

HTML (HyperText Markup Language) is the standard language for creating web pages. It's the backbone of every website. HTML uses tags to structure content, telling the browser how to display text, images, links, and more. Let's start with a basic HTML structure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739283643906/12d527c9-f60b-47bd-a387-32101a121a70.png align="center")

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>First Website</title>
</head>
<body>
    This is the first Website
    
</body>
</html>
```

* `<!DOCTYPE html>`: This indicates the browser that this is an HTML5 document.
    
* `<html lang="en">`: This is the root element of the page. The `lang="en"` specifies the language as English.
    
* `<head>`: This section contains meta-information about the HTML document, such as the title, character set, and viewport settings.
    
    * `<meta charset="UTF-8">`: Specifies the character encoding for the document. UTF-8 supports a wide range of characters.
        
    * `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Configures the viewport for responsive design, ensuring the page looks good on different devices.
        
    * `<title>My First Website</title>`: Sets the title that appears in the browser tab.
        
* `<body>`: This section contains the content that will be visible to the user.
    
    * `<h1>Hello, World!</h1>`: A main heading.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739283519718/fc86e7fc-9751-4fe0-9831-81e37cf3ae0e.png align="center")
        

## Headings, Paragraphs, Link Tags

HTML provides six heading tags, ranging from `<h1>` to `<h6>`, which help structure and organize content on a webpage. It's essential to remember that:

* Heading tags serve a purpose beyond just styling text; they establish a hierarchical structure for the website.
    
* Using these tags correctly can improve Search Engine Optimization (SEO), increasing the chances of ranking higher on Google.
    
* They also enhance readability, navigation, and overall user experience.
    

To add body content, you can use the `<p>` tag to create paragraphs. Additionally, the `<a>` tag (anchor tag) enables you to create links to external websites, such as Google or Facebook, as well as internal links to different sections within your own webpage.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739283754622/a4a27423-1fe7-49fb-b48f-c632acf71dc3.png align="center")

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>First Website</title>
</head>
<body>
    <h1>This is the first heading using h1</h1>
    <h2>This is the second heading using h2</h2>
    <h3>This is the third heading using h3</h3>
    <h4>This is the fourth heading using h4</h4>
    <h5>This is the fifth heading using h5</h5>
    <h6>This is the sixth heading using h6</h6>

    <p>
        This is the paragraph which contains some inforamtion about Full stack. It consists of frotend and backend. Frontend is the part which is visible to the user and backend is the part which is not visible to the user.
        
    </p>

    <a href="<https://www.google.co.in/>">Open google</a>
    <a href="<https://www.facebook.com/login/>">facebook login</a>
    <a href="<https://www.linkedin.com/home/>">linkedin</a>
    
    
    
</body>
</html>
```

## Images, Lists, Tables Tags

**Image Tag:**

The `<img>` tag is used to add images to an HTML document. This tag includes several attributes:

* src: specifies the image source, which can be a local file or a URL.
    
* alt: provides alternative text to display if the image fails to load.
    
* height and width: allow you to specify the image dimensions.
    

**Table Tag:**

The `<table>` tag is used to create tables in HTML. To define a table, you'll use the following tags:

* &lt;table&gt;: defines the table.
    
* &lt;tr&gt;: defines a table row.
    
* &lt;td&gt;: defines a table data cell.
    

**Lists:**

HTML provides three types of lists:

1. Ordered List (&lt;ol&gt;)
    
2. Unordered List (&lt;ul&gt;)
    
3. Definition List (&lt;dl&gt;)
    

Code examples for these elements will be provided below.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h2>This is about placing image in html</h2>

    <img src="./download.jpeg" alt="image" height="400px" width="500px">

    <h2>Table formation </h2>

    <table border="3px">
        <tr>
            <td>S.NO</td>
            <td>Name</td>
            <td>Age</td>
            <td>Profession</td>
        </tr>
        <tr>
            <td>1</td>
            <td>John</td>
            <td>25</td>
            <td>Engineer</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Smith</td>
            <td>30</td>
            <td>Doctor</td>
        </tr>
        <tr>
            <td>3</td>
            <td>David</td>
            <td>35</td>
            <td>Teacher</td>
        </tr>

    </table>

    <h2>Creating Lists in HTML</h2>
    <ol>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
        <li>React</li>
        <li>Flask</li>
    </ol>
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
        <li>React</li>
        <li>Flask</li>
    </ul>
    <dl>
        <dt>HTML</dt>
        <dd>It is a markup language</dd>
        <dt>CSS</dt>
        <dd>It is a styling language</dd>
        <dt>JavaScript</dt>
        <dd>It is a scripting language</dd>
    </dl>
</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739284107674/a27d1e21-f69d-46f3-b60b-cd2536e66746.png align="center")

## Forms and Input Tags

The HTML `<form>` element is a powerful tool for collecting user information and sending it to a server for processing or handling it on the client-side. Forms are commonly used for various tasks, such as:

* Logging in or signing up
    
* Filling out contact forms
    
* Making payments
    
* Searching
    

A typical form consists of different input fields, including:

* Text boxes for entering text
    
* Radio buttons for selecting one option
    
* Checkboxes for selecting multiple options
    

These input fields enable users to provide information, which is then submitted to the server for processing or validation.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Forms</title>
</head>
<body>
    
    <form>
        
        <label for="First_Name">First_Name</label>
        <input type="text" name="First_Name" id="First_Name" placeholder="Enter your First Name">
        <br>
        <label for="Last_Name">Last_Name</label>
        <input type="text" id="Last_Name" name="Last_Name" placeholder="Enter your Last Name">
        <br>
        <label for="Email">Email</label>
        <input type="email" name="Email" id="Email" placeholder="Enter your Email">
        <br>
        <label for="Password">Password</label>
        <input type="password" name="Password" id="Password" placeholder="Enter your Password">

        <br>
        <label for="">Male</label>
        <input type="radio" name="gender" id="select_gender" value="Male">
        <br>
        <label for="">Female</label>
        <input type="radio" name="gender" id="select_gender" value="Female">

        <br>
        <br>
        <label for="area">Enter your comment</label>
        <textarea name="text" id="area"></textarea>

        <br>
        <select>
            <option value="apple">Apple</option>   
            <option value="banana">Banana</option>
            <option value="mango">Mango</option>  
        
        </select>
        
    </form>
</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739284166184/8c4bd663-f296-44b5-96c4-e128e44a702b.png align="center")

## Inline and Block Level Elements

In HTML, elements are categorized as either inline or block-level, which affects how they interact with surrounding content.

**Inline Elements:**

* Only occupy the space needed for their content
    
* Do not disrupt the flow of text around them
    
* Examples: &lt;span&gt;, &lt;a&gt;, &lt;img&gt;
    

**Block-Level Elements:**

* Occupy the full width of their container
    
* Push content below them to a new line, creating a stacking effect
    
* Examples: &lt;p&gt;, &lt;h1&gt;, &lt;div&gt;
    

Understanding the difference between inline and block-level elements is crucial for designing a webpage that effectively displays content and creates a clear layout.

### **Block Elements**

| Tag | Description |
| --- | --- |
| `<div>` | Generic block container |
| `<p>` | Paragraph |
| `<h1>` to `<h6>` | Headings (largest to smallest) |
| `<ul>` / `<ol>` | Unordered / Ordered lists |
| `<li>` | List item |
| `<table>` | Table |
| `<tr>` | Table row |
| `<td>` | Table data cell |
| `<th>` | Table header cell |
| `<form>` | Form container |
| `<section>` | Section of content |
| `<article>` | Independent content block |
| `<aside>` | Sidebar content |
| `<header>` | Header section |
| `<footer>` | Footer section |
| `<nav>` | Navigation links |
| `<main>` | Main content area |

### **Inline Elements**

| Tag | Description |
| --- | --- |
| `<span>` | Generic inline container |
| `<a>` | Hyperlink |
| `<b>` | Bold text |
| `<strong>` | Important (bold) text |
| `<i>` | Italic text |
| `<em>` | Emphasized (italic) text |
| `<u>` | Underlined text |
| `<small>` | Small text |
| `<mark>` | Highlighted text |
| `<code>` | Inline code snippet |
| `<br>` | Line break |
| `<img>` | Image |
| `<input>` | Form input field |
| `<label>` | Label for form input |
| `<button>` | Clickable button |

## Id and Classes in HTML

The `id` attribute in HTML assigns a unique name to a single element, ensuring that no two elements on the same page share the same id. This uniqueness makes it easy to target a specific element for styling.

In the other hand, the `class` attribute enables you to assign the same name to multiple elements. By using a class, you can apply consistent styles to a group of elements, keeping your code organized, clean, and easy to maintain – without duplicating styles.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ID & CLasses</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    
    <div id="firstdiv" class="divclass divclass1">
        This is the text
    </div>

    <div id="seconddiv" class="red">
        This is the text

    </div>
</body>
</html>
```

```css
.divclass{
    color: red;
}

.divclass1{
    background-color: green;
}
#seconddiv{
    color: blue;
}
```

## Audio , Video and IFrame Tags

The `<audio>` tag is an HTML element that enables you to embed audio files directly into a web page.The `<audio>` tag supports various attributes that enhance its functionality.

| Attribute | Description |
| --- | --- |
| `src` | Specifies the URL of the audio file. |
| `controls` | Adds audio controls like play, pause, and volume. |
| `autoplay` | Automatically plays the audio when the page loads. |
| `loop` | Repeats the audio file indefinitely. |
| `muted` | Mutes the audio by default. |
| `preload` | Specifies how the audio should be loaded when the page loads. Possible values: `auto`, `metadata`, `none`. |

The `<video>` tag is used to embed video files directly into a web page. This tag allows you to add video content to your website, enhancing user engagement. The `<video>` tag includes several attributes that can be used to customize its behavior.

| Attribute | Description |
| --- | --- |
| `src` | Specifies the URL of the video file. |
| `controls` | Adds video controls like play, pause, volume, and fullscreen. |
| `autoplay` | Automatically plays the video when the page loads. |
| `loop` | Repeats the video indefinitely. |
| `muted` | Mutes the video by default. |
| `preload` | Specifies how the video should be loaded when the page loads. Possible values: `auto`, `metadata`, `none`. |
| `poster` | Specifies an image to display before the video starts playing. |
| `width` | Defines the width of the video player in pixels. |
| `height` | Defines the height of the video player in pixels. |
| `playsinline` | Ensures the video plays inline on mobile devices instead of fullscreen. |

The `<iframe>` tag is used to embed external content, such as YouTube videos, maps, or other web pages, directly into an HTML document. This allows you to seamlessly integrate third-party content into your website

| Attribute | Description |
| --- | --- |
| `src` | Specifies the URL of the page to embed. |
| `width` | Defines the width of the iframe in pixels or percentage. |
| `height` | Defines the height of the iframe in pixels or percentage. |
| `title` | Provides a text description for accessibility. |
| `name` | Assigns a name to the iframe, which can be used for targeting links. |
| `allow` | Specifies permissions like fullscreen, microphone, camera, etc. |
| `sandbox` | Enables a set of restrictions for security purposes. Possible values: `allow-scripts`, `allow-same-origin`, `allow-forms`, etc. |
| `loading` | Controls loading behavior (`lazy` or `eager`). |
| `referrerpolicy` | Specifies how the referrer information should be sent. Values: `no-referrer`, `origin`, `unsafe-url`, etc. |
| `allowfullscreen` | Enables fullscreen mode for the embedded content. |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Audio and Video</title>
</head>
<body>
    
    <h1>Audio and Video Tags</h1>

    <audio src="./file_example_MP3_700KB.mp3" controls autoplay muted>Audio File </audio>

    <h1>Video Tags</h1>
    <video src="./file_example_MP4_480_1_5MG.mp4" controls height="500" width="500" muted autoplay title="Video" >Video</video>

    <iframe src="<https://www.youtube.com/embed/rmBIZT0lRwQ?si=U7HgvRzO0y6mo5u3>" frameborder="1" width="500" height="500" title="StandUp"></iframe>

</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739284218174/05b482b0-a4d9-455a-857a-e1dea3eeb82b.png align="center")

## Semantic Tags

Semantic tags are essential for organizing website content, providing clear meaning and context. These tags will enhance both accessibility and readability.

This structured approach helps search engines index the content more effectively, ultimately improving the website’s search engine optimization (SEO) and increasing its visibility in search results on Google.

1. **&lt;header&gt;**: Represents the introductory content or a group of navigational links. Typically contains the site logo, title, and navigation.
    
2. **&lt;nav&gt;**: Defines a set of navigation links. It's used to group links that are relevant to the overall website navigation.
    
3. **&lt;main&gt;**: Represents the main content of the document. There should be only one main element per page.
    
4. **&lt;article&gt;**: Used to represent a self-contained composition in a document that is intended to be independently distributable or reusable.
    
5. **&lt;section&gt;**: Represents a thematic grouping of content, typically with a heading. It can be used to organize different sections of a webpage.
    
6. **&lt;aside&gt;**: Defines content that is tangentially related to the content around it. Often used for sidebars or pull quotes.
    
7. **&lt;footer&gt;**: Represents the footer for its nearest sectioning content or sectioning root element. It typically contains information about the author, copyright, or links to related documents.
    
8. **&lt;figure&gt;**: Used to encapsulate images, charts, or diagrams along with a caption, providing a self-contained reference.
    
9. **&lt;figcaption&gt;**: Represents a caption or legend for the content of the &lt;figure&gt; element.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739284247245/bb368dfb-9773-40c2-becd-b2de6baa8857.png align="center")
    

# Challenges and Solutions

1. **Challenge:** Figuring out how to effectively use colspan and rowspan attributes in tables to merge cells correctly.
    
    **Solution:** I practiced creating various tables, experimenting with different colspan and rowspan configurations until I achieved the desired layout.
    
2. **Challenge** : Implementing multimedia elements, particularly ensuring proper file paths for video and audio sources.
    
    **Solution :** For multimedia elements, I double-checked my file paths and consulted tutorials that detailed the usage of the `<video>` and `<audio>` tags, which clarified any misunderstandings.
    

# Resources Used

1. [Mozilla Developer Network (MDN) Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML): A comprehensive resource for HTML documentation and examples.
    
2. [YouTube Tutorial](https://www.youtube.com/watch?v=tVzUXW6siu0&list=PLu0W_9lII9agq5TrH9XLIKQvv0iaF2X3w): I used Code With Harry's resources to better understand HTML.