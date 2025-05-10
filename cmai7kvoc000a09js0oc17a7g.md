---
title: "Ultimate Guide to CSS: Learn Positioning, Flexbox, and Grid Layouts"
seoTitle: "CSS Positioning, Flexbox & Grid Guide"
seoDescription: "Learn CSS positioning, flexbox, and grid layouts for responsive web designs. Enhance your modern web development skills today"
datePublished: Sat May 10 2025 12:35:56 GMT+0000 (Coordinated Universal Time)
cuid: cmai7kvoc000a09js0oc17a7g
slug: ultimate-guide-to-css-learn-positioning-flexbox-and-grid-layouts
tags: css3, css, frontend, web-development, html, webdev, html5, frontend-development

---

## CSS Position Property

There are different properties available in CSS for positioning elements: relative, absolute, fixed, and sticky.

### Relative Position

The relative position property is used to change the position of an element in relation to its normal position. With this property, you can move the element left, right, up, or down from where it would typically be located.

### Absolute Position

The absolute position property is used to align an element with its nearest positioned ancestor (an ancestor with a position value of anything other than "static"). If the element has no positioned ancestor, it will be positioned relative to the body element.

### Fixed Position

This property is applied when we want to fix an element in a specific position on the website. For example, if we want a banner to remain in view while scrolling through the page, we would use the fixed position property. The element will stay in the same position relative to the viewport, regardless of scrolling.

### Sticky Position

The sticky position property is used when we want an element, such as a navigation bar, to remain visible at the top of the page as we scroll down. This allows the element to "stick" to a specified position when the user scrolls past it.

### Note:

Additionally, properties like transform, filter, and perspective can also affect how an element is positioned.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744267179729/4ef1b7e5-9cd3-4089-8fd5-10c02a09dee3.png align="center")

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Postion Property</title>
    <style>
       

        *{
            margin: 0px;
            padding: 0px;
        }

        /*Exception:  Transform, filter,perpsective are can also make an element to be postionoed */

        .box{
            height: 200px;
            width: 75vw;
            border: 2px solid black;
            padding: 2px;
            margin: 3px;
        }

        .parent{
            height: 50vw;
            width: 90vw;
            border: 3px solid rebeccapurple;
            margin: 2px solid black;
            padding: 2px;
            /* position:absolute; */
        }

        .box1{
            background-color: aquamarine;
            /* position: relative; */
            /* position: absolute; */
            /* position: fixed; */
            position: sticky;
            top: 0px;
            left: 300px;           
            

        }
        .box2{
            background-color: blue;

        }
        .box3{
            background-color: beige;
        }

    </style>
</head>
<body>
    <div class="parent">
        <div class="box box1"></div>
        <div class="box box2"></div>
        <div class="box box3"></div>
    </div>
</body>
</html>
```

## CSS Variables

CSS variables, known as CSS custom properties, are defined by programmers and contain specific values that can be reused throughout a website

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Variables</title>
    <style>

        :root{
            --color:blue;
            --scolor:red;
            --ucolor:aqua;
        }
        
        .nav{
            background-color: beige;
        }

        .para{
            --scolor:rgb(139, 105, 204);
            background-color: var(--scolor);
        }
        div ul li{
            list-style: none;
        }
        div ul{
            display: flex;
            gap: 10px;
        }

        li:first-child{
            background-color: var(--ucolor);
        }
    </style>
</head>
<body>
    
    <div class="nav">
        <ul>
            <li>Home</li>
            <li>Projects</li>
            <li>Skills</li>
        </ul>
    </div>

    <div class="para">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates ducimus quasi porro deleniti, et voluptatem officiis pariatur, ipsa minus itaque est repellendus quae perspiciatis ab vitae maiores modi. Necessitatibus excepturi nihil inventore?
    </div>

    
</body>
</html>
```

## CSS Media **Queries**

Media queries in CSS allow you to apply styles based on device features like screen width, orientation, or color scheme. They're essential for making responsive designs that adapt to different screen sizes.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Media Quries</title>
    <style>
        body{
            background-color: aqua;
        }

        @media only screen and (max-width:500px)  {
            body{
                background-color: red;
            }          
            
        }
    </style>
</head>
<body>
    
</body>
</html>
```

## CSS Design Card Excercise

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Design Card</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="div-main">       
        <div class="img-class">
            <img src="<https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUPIfiGgUML8G3ZqsNLHfaCnZK3I5g4tJabQ&s>" alt="img">
        </div>
        <div>
            <span>Nature</span>
            <span>Life</span>

        </div>

        <div>
            <h2>Nature Lover</h2>
        </div>

        <div>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis maiores, dolores quas nihil minus, esse deleniti numquam quo, aperiam omnis fugit repellat ad!</p>
        </div>

        <div id="button">
            <button>Read More</button>
        </div>
    </div>
</body>
</html>
```

```css
body{
    background-color: darkgrey;
    padding: 100px 200px ;
}

.div-main{
    height: 480px;
    width: 280px;
    background-color: whitesmoke;
    border-radius: 5px;
}
.img-class img{
    padding: 4px;
    border-radius: 5px;
}
#button{
    text-align: center;
    border-radius: 5px
}
```

## More on CSS Selectors

There are some widely used selctor while designning the website

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Selectors</title>
    <style>
        /* .box:first-child{
            color: aqua;
        } */
/* 
        .boxes::first-line{
            background-color: rgb(140, 226, 226);
        } */
        .boxes *{
            background-color: bisque;
            border: 2px solid rgb(112, 32, 32);
        }

        .box:nth-child(odd){
            background-color: rgb(111, 255, 0);
        }

        .box:nth-last-child(odd){
            background-color: rgb(124, 95, 95);
        }

        .box::before{
            content: "You are Awesome";
        }

        .boxes::after{
            content: "You are amazing";
            background-color: blanchedalmond;
            color: tomato;
        }
        ::selection{
            color: aqua;
        }
    </style>
</head>
<body>
    <div class="boxes">
        <div class="box">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Delectus quia sit, nihil ut dolores quas magnam quis dicta natus deleniti similique doloribus nulla, commodi dolorum quo nesciunt iusto recusandae tempora maxime, voluptatem non temporibus. Dolorum hic a labore ad dicta, temporibus, maiores iste magnam aliquam tenetur quas libero sit ea fuga consequuntur sequi accusantium quasi porro eligendi, sunt optio. Adipisci doloribus dolores, asperiores laborum quam fugiat nulla quis ipsa repellendus cum temporibus quod consequuntur porro. Pariatur, recusandae ipsa dolore eveniet nulla quo, exercitationem distinctio iste vitae ducimus expedita excepturi itaque.</div>
        <div class="box">hey I am box 2</div>
        <div class="box">Hey I am box 3</div>

        <div class="box">hey I am box 2</div>
        <div class="box">Hey I am box 3</div>
    </div>
</body>
</html>
```

## CSS Flexbox

CSS Flexbox is a one‑dimensional layout system that arranges items in a row or column within a container. It uses properties like **flex-direction**, **justify-content**, and **align-items** to control how items are spaced and aligned. Each child (flex item) can also be individually adjusted with properties like **flex**, **order**, and **align-self**. This makes building responsive and dynamic layouts straightforward.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS FlexBox</title>
    <style>
        .container{
            border: 3px solid rgb(255, 0, 0);
            display: flex;
            height: 70vh;
            align-items:center;
            justify-content: center;
            flex-direction: row;
            flex-wrap: wrap;
            gap: 20px 50px;
            flex-flow: row wrap;
        }
        .item{
            height: 100px;
            width: 100px;
            border: 2px solid black;
            background-color: aqua;
            margin: 3px;
            
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        
        
    

    </div>
</body>
</html>
```

## CSS Grid

The Grid Layout Module provides a system for creating layouts based on rows and columns. This module enables developers to build complex web designs easily. It simplifies the process of designing responsive layout structures without relying on floats or positioning. Additionally, the CSS grid properties are compatible with all modern browsers.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Grid</title>
    <style>
        .container{
            border: 2px solid black;
            display: grid;
            grid-template-columns: 150px 200px 130px 150px;
            grid-template-rows: 100px 200px;
        }

        .item{
            height: 100px;
            width: 100px;
            border: 2px solid rgb(255, 0, 0);
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
        <div class="item">6 </div>
        <div class="item">7</div>
        <div class="item">8</div>
        <div class="item">9</div>
        <div class="item">10</div>
    </div>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Grid</title>
    <style>
        .container{
            border: 2px solid black;
            display: grid;
            grid-template-areas: "nav nav nav"
                                "side article article"
                                "footer footer footer"
            ;
            
        }

        .item{
            height: 100px;            
            border: 2px solid rgb(255, 0, 0);
        }
        .item-1{
            grid-area: nav;
            background-color: aqua;
        }
        .item-2{
            grid-area: side;
            background-color: bisque;
        }
        .item-3{
            grid-area: article;
            background-color: burlywood;
        }
        .item-4{
            grid-area: footer;
            background-color: coral;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item item-1">1</div>
        <div class="item item-2">2</div>
        <div class="item item-3">3</div>
        <div class="item item-4">4</div>
        
        
    </div>
</body>
</html>
```

# **Challenges and Solutions**

1. **Challenge:** Learning how to use Media Queries.  
    **Solution:** I struggled to use media queries correctly for different screen sizes. I visited W3Schools and read about using `min-width`, `max-width`, and how to combine rules. This helped me make my website look good on all devices. The examples made everything clearer for me.
    
2. **Challenge:** Understanding the difference between absolute and relative positioning in CSS.  
    **Solution:** I was confused about how elements move when using `position: absolute` and `position: relative`. I used W3Schools to learn the differences. I practiced with examples and found that `absolute` positioning moves the element based on its nearest positioned parent, while `relative` positioning moves the element from its original spot in the layout.
    

# **Resources Used**

* [W3Schools – Media Queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp): Helped me learn to make websites responsive.
    
* [W3Schools – CSS Position Property](https://www.w3schools.com/css/css_positioning.asp): Helped me understand how to position elements using CSS.