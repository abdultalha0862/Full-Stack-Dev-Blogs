---
title: "JavaScript Guide: Understanding Arrays, Factorials, and the DOM"
seoDescription: "Learn JavaScript arrays, factorial calculation, and DOM for efficient data management and interactive web application development"
datePublished: Sat May 10 2025 10:24:09 GMT+0000 (Coordinated Universal Time)
cuid: cmai2vf5t000k09l5e5vu6xxw
slug: javascript-guide-understanding-arrays-factorials-and-the-dom
tags: javascript, web-development, webdev

---

## Arrays

An array is a list of values arranged in a specific order. Each value is called an element, and it has a position in the array called its index. In JavaScript, arrays start counting from zero, so the first element is at index 0, the second element is at index 1, and so on.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arrays</title>
</head>
<body>
    <script src="./script.js"></script>
</body>
</html>
```

```jsx
let arr=[12,241,3512,426,565];
// console.log(arr);

// for(let i=0;i<arr.length;i++){
//     console.log(arr[i]);
// }

// console.log(typeof arr[2]);

// console.log(typeof arr);

// console.log(arr.join(" "));

// console.log(arr.length);

// console.log(arr.toString());

// console.log(arr.join(" "));

// arr.push(45);
// console.log(arr);

// let arr1=[1,2,4546,343];
// let arr2=["abc","ght","bjfhb"];

// console.log(arr1.concat(arr2));

```

```jsx
let arr=[45,34,12,56,34];

// arr.forEach((a,arr)=>{
//     console.log(a,arr);
    
// });

// for (const key in arr) {
//     if (Object.prototype.hasOwnProperty.call(arr, key)) {
//         console.log(arr[key]);       
        
//     }
// }

// for (const i of arr) {
//     console.log(i);
// }

let newArr=arr.map((e)=>{
    return e**2;
});

console.log(newArr);

```

## Excercise : Factorial of Number

```jsx
let num=6;
let fact=1;

for(let i=1;i<=num;i++){
    fact=fact*i;
    
}

console.log(fact);

```

## Document Object Model

The Document Object Model (DOM) links web pages to scripts or programming languages by showing how a document is structured in memory. It usually involves JavaScript, even though it can represent HTML, SVG, or XML documents as objects, which is not part of the main JavaScript language.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM</title>
</head>
<body>
    <script>
        document.title="You are excellent";
        
    </script>
</body>
</html>
```

### Methods

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM - Methods</title>

    <style>
        .box{
            height: 100px;
            width: 100px;
            border: 2px solid black;
            margin: 5px;
            padding: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box">Box 1 </div>
        <div class="box">Box 2</div>
        <div class="box">Box 3</div>
        <div class="box">Box 4</div>
        <div class="box">Box 5</div>
    </div>

    <script src="./script.js"></script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM</title>
    <style>
        .box{
            height: 100px;
            width: 100px;
            border: 2px solid black;
            margin: 2px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box">Jobs </div>
        <div class="box">Jobs </div>
        <div class="box">Jobs </div>
        <div id="black" class="box">Jobs </div>
        <div class="box">Jobs </div>
    </div>

    <script src="./script.js"></script>
</body>
</html>
```

```jsx
let boxes=document.getElementsByClassName("box");
console.log(boxes);

document.getElementsByClassName("box")[4].style.background="green";
document.getElementsByClassName("box")[0].style.color="red";
document.getElementById("black").style.background="aqua";
```

In conclusion, understanding JavaScript arrays, factorials, and the Document Object Model (DOM) is essential for web development. Arrays allow you to store and manipulate lists of data efficiently. Though a mathematical concept, factorials can be implemented in JavaScript to solve various computational problems. The DOM provides a structured representation of web documents, enabling dynamic interaction and manipulation through JavaScript. Mastery of these concepts enhances your ability to create interactive and responsive web applications.