---
title: "Ultimate CSS Guide: How to Style Web Pages Effectively"
seoTitle: "CSS Styling: Master Web Page Design"
seoDescription: "Learn how to effectively style web pages with CSS. Explore CSS types, selectors, box model, fonts, colors, specificity, and sizing units"
datePublished: Thu May 08 2025 14:24:55 GMT+0000 (Coordinated Universal Time)
cuid: cmafglc6a000109l4g8ue4l2t
slug: ultimate-css-guide-how-to-style-web-pages-effectively
tags: css3, css, web-development, webdev, full-stack, html5, css-animation, frontend-development

---

# What is CSS and Types of CSS

CSS stands for Cascading Style Sheets, and it is used to style websites. There are three different types of CSS:

1. **Inline CSS**: This method applies styles directly within an HTML element by using the `<style>` attribute in the tag of the element you want to style.
    
2. **Internal CSS**: This approach involves applying styles using a `<style>` tag located within the `<head>` section of the HTML document.
    
3. **External CSS**: In this method, all style attributes are written in an external stylesheet file. This approach is often the most preferable, as it helps keep the HTML clean and allows for easier maintenance of styles across multiple pages.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237511939/f4dcf75c-1fb5-4376-af8f-434e12d347bd.png align="center")
    

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Types of CSS</title>

    <!-- External CSS -->
    <link rel="stylesheet" href="styles.css">

    <!-- Internal CSS -->
    <style>
        h1 {
            color: green;
            text-align: center;
        }
        .internal-css {
            background-color: lightgray;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>

    <h1>CSS Types Example</h1>

    <!-- Inline CSS -->
    <p style="color: blue; font-size: 18px; font-weight: bold;">
        This paragraph uses Inline CSS.
    </p>

    <!-- Internal CSS -->
    <p class="internal-css">
        This paragraph is styled using Internal CSS.
    </p>

    <!-- External CSS -->
    <p class="external-css">
        This paragraph is styled using External CSS.
    </p>

</body>
</html>
```

```css
.external-css {
    color: red;
    font-size: 20px;
}
```

# CSS Selectors

CSS selectors are used to style the elements present on a web page. There are different types of selectors, which include:

1. Element Selector
    
2. Class Selector
    
3. ID Selector
    
4. Child Selector
    
5. Universal Selector
    
6. Pseudo Selector
    

Each of these selectors serves a specific purpose in targeting elements for styling.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237534691/4ebc39d7-fdb9-4e16-a66d-f4c60cbecf0e.png align="center")

## 1\. Element Selector

Element selectors are used to select specific elements in a document. The syntax for using these selectors is as follows:

```css
div{
            background-color: lightblue;
        }
```

## 2\. Class Selector

Class selectors are used to style similar groups of elements on a web page. The syntax for this selector is:

```css
/* Class Selector */
        .div1{
            background-color: lime;
            color: tomato;
        }
```

## 3\. ID Selector

The ID selector is used to style a specific element on a webpage. The syntax for this selector is

```css
/* ID Selector */
        #div2{
            background-color: rgb(155, 102, 106);
            color: black;
        }
```

## 4\. Child Selector

The Child selector is used when the descendant property is applied. The syntax for this is

```css
.div1 > p{
            background-color: rgb(255, 0, 0);
            color: orange;
        }
```

## 5\. Universal Selector

The universal selector is used to apply styling to the website. The syntax for this

```css
/* Universal Selector */
        *{
            border: 1px solid black;
        }
```

## 6\. Pseudo Selector

A pseudo-class in CSS applies additional rules to an element when it is in a specific state.

```css
a:link{
            color: red;
        }
        a:visited{
            color: green;
        }
        a:active{
            color: blue;
        }
        a:hover{
            color: yellow;
        }
```

The code for the selectors is

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Selectors</title>
    <style>

        /* Element Selector */
        div{
            background-color: lightblue;
        }

        /* Class Selector */
        .div1{
            background-color: lime;
            color: tomato;
        }

        /* ID Selector */
        #div2{
            background-color: rgb(155, 102, 106);
            color: black;
        }
        /* Child Selector */
        .div1 > p{
            background-color: rgb(255, 0, 0);
            color: orange;
        }

        /* Universal Selector */
        *{
            border: 1px solid black;
        }

        a:link{
            color: red;
        }
        a:visited{
            color: green;
        }
        a:active{
            color: blue;
        }
        a:hover{
            color: yellow;
        }
        .div1 > p {
            background-color: rgb(0, 8, 255);
            color: rgb(22, 15, 3);
        }
        

    </style>
</head> 
<body>
    <div class="div1">
        I am a div element
        <p>
            I am a paragraph inside a div element
            <p>
                I am a paragraph inside a paragraph
            </p>
        </p>

        <p>
            I am a 2nd paragraph inside a div element
        </p>

    </div>

    <div id="div2">
        I am a 2nd div element
    </div>

    <div class="div1">

        I am a 3rd div element
        <p>
            I am a paragraph inside a div element
        </p>
    </div>

    <div id="div2">
        I am a 4th div element
    </div>

    <a href="<https://www.google.co.in/>">google</a>

    <a href="<https://www.instagram.com/accounts/login/?hl=en>">instagram</a>
</body>
</html>
```

## CSS Box Model

The CSS Box Model is a key concept in web design that describes how elements are displayed and spaced. Each HTML element is treated as a box with four layers:

1. **Content**: The area where text, images, or media are displayed, defined by width and height.
    
2. **Padding**: The transparent space between the content and border, adjustable with shorthand or individual properties.
    
3. **Border**: The line surrounding the padding and content, styled with properties like border-width, border-style, and border-color.
    
4. **Margin**: The outer layer that creates space between the element's border and adjacent elements, also set using shorthand or individual suborder width, border style, and border color properties.
    

Understanding this model is essential for effective layout and spacing in web design.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237570618/895a0698-67ce-48ed-8719-2526d55bb283.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Box Model</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .div{
            display: inline-block;
        }

        .div1{
            background-color: aqua;
        }
        .div2{
            background-color: blueviolet;
        }

        .div1{
            color: rgb(255, 0, 64);
            padding: 15px;
            border: 3px solid black;
            margin: 20px;
            width: 400px;
            height: 200px;
            text-align: center;

        }
        .div2{
            color: rgb(3, 3, 35);
            padding: 20px;
            border: 3px solid black;
            margin: 30px;
            width: 400px;
            height: 200px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="div div1">I am a div Block</div>
    <div class="div div2">I am a another div block</div>

</body>
</html>
```

## CSS Fonts and Colors

CSS provides a large variates of colors and fonts that we can use in our website. We can take the other fonts from the internet and we can represent the colors in different forms.

### Fonts:

We can take many differernt forms of text in our website it has so many properties for text.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Fonts and Colors</title>
    <style>
        @import url('<https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap>');
        h1{
            font-family: 'Poppins', sans-serif;
            color: red;
            text-align: center;
        }
        p{
            font-family: Georgia, 'Times New Roman', Times, serif;
            font-style: italic;
            font-size: larger;
            color: blue;
            font-weight: 200px;
        }
        p{
            text-transform: lowercase;
            /* text-align: center; */
            text-decoration: underline;
            text-decoration-color: silver;
            text-decoration-thickness: 5px;
            text-indent: 20px;
        }
        .para{
            height: 500px;
            width: 200px;
            text-align: center;
            border: 2px solid black;
            text-overflow: ellipsis;
            overflow: hidden;
        }

    </style>
</head>
<body>
    <h1>
        Fonts and Colors
    </h1>
    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse!
    </p>

    <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse!
    </p>

    <p class="para">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse! Lorem ipsum dolor sit amet consectetur adipisicing elit. Magnam corrupti ad labore debitis animi ipsum maiores tenetur vitae quia quisquam facere ex illum, dolor ab at non pariatur! Aliquid, esse!

    </p>
</body>
</html>
```

### Colors:

Colors can be represent in the following forms. they are

1. Color name
    
2. Hex Code
    
3. RGB
    
4. RGBA
    
5. HSL
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237594172/55b33925-89e1-45a7-8850-de5efba66558.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Colors</title>
    <style>
        h1{
            text-align: center;
        }
        #id1{
            color: aqua;
        }
        #id2{
            color: #871e1e;
        }
        #id3{
            color: rgb(255, 100, 20);
        }
        #id4{
            color: rgba(255, 50, 109, 0.5);
        }
        #id5{
            color: hsl(0, 100%, 50%);
        }

    </style>
</head>
<body>
    <h1>
        Colors
    </h1>
    <ol>
        <li id="id1">color</li>
        <li id="id2">Hex Code</li>
        <li id="id3">RGB</li>
        <li id="id4">RGBA</li>
        <li id="id5">HSL</li>
    </ol>
</body>
</html>
```

## CSS Specificity and Cascade

This concept applies when there are multiple properties assigned to a specific element. These types of conflicts can be resolved using the cascade algorithm.

This algorithm has four stages:

1. **Position and Order**: This refers to the sequence in which the properties are written.
    
2. **Specificity**: This considers the strength of the match of the CSS rules.
    
3. **Origin**: This relates to the order in which the CSS is applied, including built-in styles from the browser.
    
4. **Importance**: When we declare a property with the `!important` tag, it takes precedence as the most important property for that element.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237623769/1e16d9df-05fb-4590-a235-2a59bbc07d25.png align="center")

The order of specificity is as follows:

Inline styles &gt; ID Selector &gt; Class or Attribute Selector &gt; Element Selector &gt; Universal Selector.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Specificty and Cascade</title>
    <style>
        h1{
            color: red;
        }
        .x1{
            color: blue;
        }
        .x2{
            color: green;
        }
        .x3{
            color: yellow;
        }
    </style>
</head>
<body>
    
    <h1 class="x1 x2 x3">
        This is the heading Tag
    </h1>

    
</body>
</html>
```

## CSS Sizing Units

There are different size units available in CSS that can be used according to our requirements for making the website responsive. The major units are:

1. **px** (pixels)
    
2. **vw, vh** (viewport width and viewport height)
    
3. **rem, em** (root em and em)
    
4. **vmin, vmax** (minimum and maximum of viewport dimensions)
    

These are the most commonly utilized units in CSS.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740237647996/0f95a0d2-5876-4670-8625-43c48ee19c4f.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .div1{
            border: 2px solid black;
            width: 500px;
            height: 500px;
            background-color: aqua;
        }
        .div2{
            border: 2px solid black;
            width: 100vw;
            height: 100vh;
            background-color: aqua;
        }

        .container{
            border: 2px solid black;
            width: 100vw;
            height: 100vh;
            font-size: 1.25rem;
            background-color: beige;
        }
    </style>
</head>
<body>
    <!-- <div class="div1">
        This is the div element Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt enim laborum culpa, quas commodi maiores facilis mollitia a voluptas ipsum consectetur alias praesentium quam corrupti. Temporibus sed saepe sit, officiis iusto minus!
        <br>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic voluptatum incidunt mollitia velit voluptatibus architecto molestiae cupiditate vitae. Recusandae saepe, cum consectetur corporis quod nostrum exercitationem molestias, in magnam ab, distinctio est?
        <br>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Obcaecati unde eveniet commodi enim totam. Sed nulla dolorem sequi possimus ea beatae expedita! Est repellat numquam quaerat hic expedita dignissimos dicta incidunt dolores, ipsa minima, vitae deserunt ab dolore quasi fugiat nobis. Cum ratione eaque nulla.
        <br>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eius error eaque praesentium dignissimos accusamus inventore, numquam exercitationem at totam ipsa odio quia ipsum nihil quam suscipit laboriosam. Vitae fuga ipsam modi maxime nulla, labore, asperiores earum voluptatibus quibusdam, deleniti commodi doloribus tempora molestias! Nam pariatur velit optio enim asperiores itaque aspernatur dolor repellat? Ducimus quos, odio dignissimos illo modi ab, totam officiis consequatur rem obcaecati aut dicta architecto illum. Molestias, necessitatibus? Temporibus placeat consectetur corrupti? Quia illo asperiores eaque accusamus fugiat. Cum reprehenderit laborum molestias quibusdam. Ducimus nostrum aut, veniam quos delectus repellat aliquam ex! Dolore libero cum repellendus!
    </div>

    <br>
    <br> -->

    <!-- <div class="div2">
        This is the div element Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt enim laborum culpa, quas commodi maiores facilis mollitia a voluptas ipsum consectetur alias praesentium quam corrupti. Temporibus sed saepe sit, officiis iusto minus!
        <br>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic voluptatum incidunt mollitia velit voluptatibus architecto molestiae cupiditate vitae. Recusandae saepe, cum consectetur corporis quod nostrum exercitationem molestias, in magnam ab, distinctio est?
        <br>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Obcaecati unde eveniet commodi enim totam. Sed nulla dolorem sequi possimus ea beatae expedita! Est repellat numquam quaerat hic expedita dignissimos dicta incidunt dolores, ipsa minima, vitae deserunt ab dolore quasi fugiat nobis. Cum ratione eaque nulla.
        <br>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eius error eaque praesentium dignissimos accusamus inventore, numquam exercitationem at totam ipsa odio quia ipsum nihil quam suscipit laboriosam. Vitae fuga ipsam modi maxime nulla, labore, asperiores earum voluptatibus quibusdam, deleniti commodi doloribus tempora molestias! Nam pariatur velit optio enim asperiores itaque aspernatur dolor repellat? Ducimus quos, odio dignissimos illo modi ab, totam officiis consequatur rem obcaecati aut dicta architecto illum. Molestias, necessitatibus? Temporibus placeat consectetur corrupti? Quia illo asperiores eaque accusamus fugiat. Cum reprehenderit laborum molestias quibusdam. Ducimus nostrum aut, veniam quos delectus repellat aliquam ex! Dolore libero cum repellendus!
        <br>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellendus obcaecati expedita minus! Minima, fugit veniam? Impedit magni tenetur quae quia vitae corporis natus quibusdam quos fuga saepe? Illum laborum quo molestiae quaerat eaque laboriosam necessitatibus commodi dolore autem beatae, deserunt delectus obcaecati cupiditate ut dolorem, eum facilis nobis voluptatem quis ad ullam ipsum, in impedit. Corporis.
        <br>
        quas aliquam dolorem ratione repellat exercitationem illum commodi porro! Voluptatibus neque illo doloremque ducimus perferendis niunt magni at fuga eaque? Rem itaque quos tenetur nostrum minima, consequatur perspiciatis! Excepturi debitis aliquid delectus nostrum, velit porro repellendus labore sit nam repudiandae ducimus quaerat earum dolorem voluptates sapiente fugit? Alias sit, delectus dolorem veniam impedit perspiciatis magni ab perferendis consequuntur odit dolorum minima similique ratione explicabo minus, quidem, labore distinctio eligendi non debitis? Quam assumenda sunt itaque? Eaque quo aliquid porro eius modi, ullam nobis, cupiditate est architecto accusantium consectetur nostrum at, velit sunt dolore natus laboriosam 
    </div> -->

    <div class="container">
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Voluptate accusantium sapiente animi labore eius, quod eligendi, aliquam vitae iure aliquid, cum suscipit. Laborum perferendis minima laudantium assumenda fugiat veritatis dolor eligendi corporis.
        <br>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Alias consequuntur repudiandae temporibus maiores, quas quaerat deleniti numquam tempore rem id suscipit fugiat, explicabo iste sed officiis magnam et. Harum ratione modi eius beatae vero sit, corrupti fugiat error veniam placeat odit quo exercitationem laboriosam ut, minima soluta, quam earum. Eveniet, temporibus ab sequi eaque mollitia ipsam similique autem quidem providen
        t nulla aspernatur quis blanditiis non totam. Ducimus voluptatem distinctio laboriosam tenetur eligendi expedita harum, mollitia tempore in beatae maxime architecto neque provident! Dolorem modi nesciunt quisquam deleniti accusantium. Unde aliquam similique non dolorem mollitia doloremque culpa? Iste rerum ab aut, eius repudiandae fuga exercitationem, corporis quaerat illo, numquam ipsum architecto harum esse consequuntur dolor sed 
        reiciendis dolorum hic quo. Nam quasi officiis exercitationem dolorum placeat libero. Sapiente eligendi earum recusandae esse nostrum. Cumque nemo aut totam doloribus, eaque eligendi! Repudiandae magni quos voluptas facilis voluptatibus delectus officiis architecto corporis veritatis nam mollitia iure accusantium voluptatem iste, libero obcaecati nobis, odio illum suscipit ratione est animi et nihil optio. Fugit, hic modi dignissimos dolore velit illum, quos eum debitis corporis fuga quod unde laudantium voluptatum doloremque reiciendis dicta! Delectus cumque eaque illo necessitatibus deserunt, et tempora rerum itaque? Similique quos iusto, alias temporibus error accusantium est. Ab totam aut veritatis aspernatur eaque laudantium nostrum iure nemo qui, quia, cum cupiditate illo doloribus iusto molestias unde id dolorem officiis assumenda voluptate. Obcaecati velit vitae quam reiciendis eius ipsam quia perferendis aperiam voluptate, quibusdam quo neque cumque adipisci culpa ipsa atque mollitia ratione repellat suscipit officia quasi consequatur tempore incidunt tempora? Consequuntur praesentium, sint dolorum reprehenderit facilis enim! Vel delectus quisquam optio laboriosam. Facere quia eum, sequi culpa distinctio accusamus ut perferendis perspiciatis quae laboriosam, dolorum at vitae possimus soluta, error aut. Fugiat sed accusantium quia itaque molestiae voluptatibus commodi nesciunt earum facilis, modi nulla distinctio pariatur quas iure reprehenderit ut iste animi rerum architecto quidem beatae quo illo quis aperiam? Perferendis eum adipisci eligendi tempore.
    </div>
</body>
</html>
```

# Challenges and Solutions

1. **Challenge:** Understanding selectors, particularly pseudo-class and class selectors.
    
    **Solution:** By referring to the MDN docs and experimenting with different elements, I grasped the concept of these selectors.
    
2. **Challenge**: Understanding the box model in CSS; I initially struggled with the concept.
    
    **Solution:** I referred to the article on the CSS box model, and the [link](https://www.codewithharry.com/tutorial/css-box-model/) is provided below.
    

# Resources Used

1. [Mozilla Developer Network (MDN) Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML): A comprehensive resource for HTML documentation and examples.
    
2. [YouTube Tutorial](https://www.youtube.com/watch?v=tVzUXW6siu0&list=PLu0W_9lII9agq5TrH9XLIKQvv0iaF2X3w): I used Code With Harry's resources to better understand HTML.