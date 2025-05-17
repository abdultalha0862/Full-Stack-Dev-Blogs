---
title: "JavaScript Essentials: Understanding Events, Asynchronous Functions, and Error Handling"
seoDescription: "Learn JavaScript events, asynchronous functions (callbacks, promises, async/await), and error handling for better code management and execution"
datePublished: Sat May 17 2025 16:24:28 GMT+0000 (Coordinated Universal Time)
cuid: cmasftr4w001409jsflnm0kmc
slug: javascript-essentials-understanding-events-asynchronous-functions-and-error-handling
tags: js, javascript, web-development, webdev

---

## Events, Events Bubbling

JavaScript events are actions that happen in the browser. Users can trigger them through different interactions, or the browser can trigger them itself.

Event bubbling in JavaScript happens when an event on a child element spreads upward through its parent elements in the DOM. This allows parent elements to react to events that occur on their child elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Events</title>
    <style>
        .child{
            background-color: aliceblue;
            border: 2px solid black;
            margin: 3px;
            padding: 14px;
        }

        .childContainer{
            background-color: rgb(104, 171, 54);
            border: 2px solid black;
            margin: 3px;
            padding: 14px;
        }

        .container{
            background-color: rgb(55, 103, 145);
            border: 2px solid black;
            margin: 3px;
            padding: 14px;
        }
    </style>
</head>
<body>
    <!-- <div class="container">
        <div  class="box">
            Hey I am a content
        </div>
        <button id="btn">Click Here</button> -->

        <div class="container">
            <div class="childContainer">
                <div class="child">
                    I am a child
                </div>
            </div>
        </div>

        <button id="btn">Click Here</button>
        <script src="./script.js"></script>
    </div>
</body>
</html>
```

```jsx
let button=document.getElementById("btn");

// console.log(button);

// button.addEventListener("click",()=>{
//     alert("Button is Clicked");
// })

// button.addEventListener("dblclick",()=>{
//     document.querySelector(".box").innerHTML="You are Awesome";
// })

// button.addEventListener("click",(e)=>{
//     console.log(e);
// })

document.querySelector(".child").addEventListener("click",(e)=>{
    // e.stopPropagation();
    alert("Child was Clicked");
})

document.querySelector(".childContainer").addEventListener("click",(e)=>{
    // e.stopPropagation();
    alert("Child Container was clicked");
})

document.querySelector(".container").addEventListener("click",(e)=>{
    // e.stopPropagation();
    alert("Conatainer was clicked");
})

// setInterval(()=>{
//     document.querySelector(".child").style.background="red"
// },2000)

// setTimeout(()=>{
//     document.querySelector(".child").style.background="red"
// },2000)
```

## Callbacks and Promises

**Callbacks:**

A callback function is a function that is passed as an argument to another function and is executed at a later time.

This allows one function to invoke another function after a certain operation has been completed. Essentially, a function can accept another function as a parameter, enabling this delayed execution.

**Promise:**

The promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

```xml
	<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Callbacks and Promises</title>
</head>
<body>
    <script src="./promises.js"></script>
</body>
</html>
```

```jsx
// console.log("You are Awesome");
// console.log("Again You are Awesome");

// setTimeout(()=>{
//     console.log("You are inside set Timeout Function");    
// },3000)

// setTimeout(()=>{
//     console.log("You are inside set timeout Function 2");
    
// },1000)

const callback=(arg)=>{
    console.log(arg);
    
}

const loadScript=(src,callback)=>{
    let sc=document.createElement("script");
    sc.src=src;
    sc.onload=callback("King");
    document.head.append(sc);
}

loadScript("<https://www.bloomberg.com/quote/FB:US>",callback)
```

```jsx
let prmo1=new Promise((resolve,reject)=>{
    let a=Math.random();
    if(a<0.4){
        reject("No Random Number is found");
    }
    else{
        setTimeout(()=>{
            console.log("This is done");
            resolve("King");

            
        },3000)
    }
})

prmo1.then((a)=>{
    console.log("Print");
    
})

prmo1.catch((a)=>{
    console.log("Not Found");    
})
```

## Async and Await

Async and Await in JavaScript helps you work with asynchronous tasks more easily by using promises. This feature makes your asynchronous code look and feel like it's running in a straightforward, step-by-step way. It improves readability and simplifies the management of complex asynchronous processes.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Async and Await</title>
</head>
<body>
    <script src="./script.js"></script>
</body>
</html>
```

```jsx
async function getData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(455);
        }, 10);
    });
}

async function main() {
    console.log("Sub Task 1");
    let data=await getData();

    console.log(data);
    
        
}

// data.then((a)=>{
//     console.log("Task 1");

//     console.log("Task 2");

//     console.log("Task 3");  
// })
```

## Exception handling

In JavaScript, handling errors helps you manage problems that happen while your code runs. You can use tools like try, catch, throw, and finally to take care of errors and keep your program from crashing. This allows you to give clear error messages, fix your code more easily, and keep everything running smoothly.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exception Handling</title>
</head>
<body>
    <script src="./script.js"></script>
</body>
</html>
```

```jsx
let a=prompt("Enter first Num");
let b=prompt("Enter Second Num");

// if(isNaN(a)|| isNaN(b)){
//     throw new Error("Not a Valid Num")
// }
let sum=parseInt(a)+parseInt(b);
console.log(sum);

function main(){
    let c=1;
    try{
        console.log(sum*c);
        return true;
        
    }
    catch{
        console.log("Error Occured");
        return false;
        
    }
    
    finally{
        console.log("Code is Working Fine");
    }
}

main();

```

# Challenges Faced

**Challenge:**

I had a problem where clicking a child element did not highlight the parent and grandparent containers. There were no error messages or visual feedback.

**Solution:**

After troubleshooting, I realized I forgot to add a dot before my class name in the `querySelectorAll` call. I changed `document.querySelectorAll('my-container')` to `document.querySelectorAll('.my-container')`, and the parent containers highlighted as expected. This experience taught me to always double-check selectors for mistakes!

# Resources Used:

1. [**Code with Harry tutoria**](https://www.youtube.com/playlist?list=PLu0W_9lII9agq5TrH9XLIKQvv0iaF2X3w)[**l:** Watched tutorials from hi](https://www.youtube.com/playlist?list=PLu0W_9lII9agq5TrH9XLIKQvv0iaF2X3w)s channel, and the link is given below.