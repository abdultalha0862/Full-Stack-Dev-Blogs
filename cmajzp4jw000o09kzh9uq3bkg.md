---
title: "Learn CSS Basics: Master Display Properties, Shadows, Lists, and Overflow"
seoTitle: "CSS Basics: Display, Shadows, Lists, Overflow"
seoDescription: "Learn CSS basics with display properties, shadows, list styling, and managing overflow text to enhance your web design skills"
datePublished: Sun May 11 2025 18:30:49 GMT+0000 (Coordinated Universal Time)
cuid: cmajzp4jw000o09kzh9uq3bkg
slug: learn-css-basics-master-display-properties-shadows-lists-and-overflow
tags: css3, css, frontend, web-development, html, webdev, html5, frontend-development

---

## CSS Display Properties

The display properties in CSS are essential for organizing webpage content. The key display values include:

1. **display: inline;** – This value displays elements inline without inserting line breaks, allowing them to take only the necessary width..
    
2. **display: inline-block;** – This value combines the characteristics of inline and block elements, enabling them to sit next to each other while still allowing for padding and margins.
    
3. **display: flex;** – This value creates a flexible box layout suitable for responsive design, allowing for complex alignment and distribution of space among items.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740756076231/b6f69800-8580-4fd8-a824-7b217c3d188d.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Display Properties</title>
    <link rel="stylesheet" href="style.css">

</head>
<body>
    
    <ol class="ele">
        <li>HTML </li>
        <li>CSS </li>
        <li>JS </li>
        <li>Bootsrap </li>
        <li>Node</li>

    </ol>

    <div class="box box1">
        This is the div ele
    </div>

    <div class="box box2">
        This is the another div 
    </div>

    
</body>
</html>
```

```css
*{
    margin: 0px;
    padding: 0px;
}
.box{    
    border: 3px solid black;
    display: inline;
}
.ele{
    border: 2px solid black;
    display: inline-block;
}
.box1{
    /* display: none;
    visibility: hidden; */
    display: flex;
}

.box2{
    display: flex;
}
```

## CSS Shadow and Outlines

These shadow properties and Outlines are used when we want to include shadows on elements in the web page. These properties make the website stunning and look awesome.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740756088057/dda2af88-a76e-43ed-ac15-398a34b8f27b.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Shadow and Outlines</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="box">
        I am a div element
    </div>

    <p id="para">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quis laboriosam adipisci nemo, quasi sapiente porro, eveniet labore incidunt hic itaque rem repudiandae maxime, quas unde sint? Esse dolor quaerat repellat cum velit?
    </p>
</body>
</html>
```

```css
.box{
    padding: 30px;
    border: 2px solid blue;
    box-shadow: 5px 10px 5px salmon;
}
#para{
    text-shadow: 2px 4px 4px seagreen;
    outline: 5px solid blueviolet;
    border: 2px solid black;
    outline-offset: 25px;
}
```

## CSS Lists Styling

This concept is used to style lists. We have two types of lists: ordered lists and unordered lists. Each of these lists has a marker. To remove that marker, we use list styling concepts. This technique is mainly used in the navigation section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740756146101/604fbe27-8248-4cb7-8298-3877fca487be.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
			    nav ul li{
	    list-style:decimal;
	    background-color: aqua;
	    padding: 10px;
	    list-style-position: inside;
	    border: 2px solid yellowgreen;
}   
</style>
</head>
<body>
    <nav>
        <ul>
            <li>Home</li>
            <li>About</li>
            <li>Experience</li>
            <li>Projects</li>
            <li>Skills</li>
            <li>Extracurricular</li>
        </ul>
    </nav>
</body>
</html>
```

## CSS Overflow Property

This property helps us manage text that exceeds the defined block. We can control how the overflow text behaves using this property.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740756160805/67ea19b8-2fdd-4746-9992-966dab4cd00d.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS OverFlow Property</title>
    <style>
	    .box{
    height: 200px;
    width: 200px;
    border: 3px solid black;
    overflow: auto;
    text-overflow: clip;
}
    </style>
</head>
<body>
    <div class="box">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Est libero magni dolorum dignissimos alias, commodi error adipisci tenetur quibusdam hic officia optio ducimus unde quas eos, quis expedita quos aspernatur quam nihil cumque perspiciatis consectetur voluptatem voluptatum. Voluptatem laborum adipisci delectus. Suscipit dolore laborum recusandae.
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Recusandae maxime cupiditate voluptatum nulla, esse ipsum nostrum libero laborum explicabo. Commodi, veritatis? Veritatis temporibus molestiae minus et similique minima nam! Nisi.
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ipsam, magni pariatur repudiandae similique aut suscipit odio in fugiat explicabo molestias quod laudantium iusto minus, aspernatur optio voluptatem voluptatum. Consequatur, eveniet?
    </div>
</body>
</html>
```