---
title: "Master JavaScript: A Complete Guide from OOP to Node.js Backend"
seoDescription: "Master JavaScript including OOP, advanced concepts, Node.js, NPM, and module systems for efficient app development"
datePublished: Sat May 24 2025 14:05:41 GMT+0000 (Coordinated Universal Time)
cuid: cmb2ay8fx000209jsedycc72k
slug: master-javascript-a-complete-guide-from-oop-to-nodejs-backend
tags: js, javascript, web-development, webdev

---

## Object Oriented Programming

Object-oriented programming (OOP) is a way of writing code that groups related data and actions into reusable objects. JavaScript supports this approach with OOP features.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Object Oriented Programming</title>
</head>
<body>
    <script src="./script.js"></script>
</body>
</html>
```

```jsx
// let obj={
//     a:"King",
//     b:"Name"
// }

// console.log(obj);

// let animal={
//     eats:true
// };

// let rabbit={
//     jumps:true
// };

// console.log(animal);

// console.log(rabbit);

class Animal{
    constructor(name1,name2){
        this.name1=name1;
        this.name2=name2;
        console.log("Constrictor is being Created"+name1+" "+name2);
        
    }

    eats(){
        console.log("He is eating");
        
    }
    jumps(){
        console.log("He is Jumping");
        
    }

}

let a=new Animal("Abdul","Talha");
console.log(a);

a.eats();
a.jumps();

class Tiger extends Animal{
    attack(){
        console.log("Tiger is Attacking");        
    }
}

let tiger=new Tiger();

console.log(tiger);

tiger instanceof Tiger

```

## Advanced Concepts in JS

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advaced JS</title>
</head>
<body>
    <script src="./script.js"></script>
</body>
</html>
```

```jsx
async function sleep() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(85);
        }, 1000);
    });
}

// let a = await sleep();
// let b = await sleep();

(async function main() {
    // let a = await sleep();
    // console.log(a);

    // let b = await sleep();
    // console.log(b);

    // let [x,y]=[2,4];
    // console.log(x,y);

    // let [x,y, ...rest]=[1,2,3,4,5,56];
    // console.log(x,y,rest);

    let arr=[1,2,4,5,6,77,8];

    

})();
```

## Backend,npm and Node Js

Node.js lets you create the backend of web applications using JavaScript. It performs tasks such as storing data, responding to user actions, and connecting to databases. Because it operates on an event-driven system, Node.js is fast and can handle many users at the same time.

NPM is a tool that comes with Node.js. It helps you install and manage packages (libraries or tools) that add features to your app. For example, you can use it to install packages for sending emails, handling files, or connecting to databases. Using NPM makes development faster and easier.

[JavaScript-learnings/Backend Node js and NPM at main · abdultalha0862/JavaScript-learnings](https://github.com/abdultalha0862/JavaScript-learnings/tree/main/Backend%20Node%20js%20and%20NPM)

[https://github.com/abdultalha0862/JavaScript-learnings/tree/main/Backend Node js and NPM](https://github.com/abdultalha0862/JavaScript-learnings/tree/main/Backend%20Node%20js%20and%20NPM)

## CommonJs and EcmaScript Modules

JavaScript has two main ways to handle modules: ECMAScript Modules (ESM) and CommonJS (CJS).

* ESM is the newer standard for JavaScript modules. It uses “import” and “export” statements, allowing for better analysis and optimization. You can find it in most web browsers and in modern Node.js.
    
* CommonJS is the older method used in Node.js. It relies on “require()” and “module.exports,” and it works synchronously. This method is not suitable for browsers unless you use a bundler.
    

# Challenges and Solutions

**Challenge**: I wrote a function in Node.js that was supposed to run immediately, but it didn't produce any output. The function was defined, but it didn’t execute, so I saw nothing in the console.

**Solution**: After checking the syntax, I realised I forgot to add parentheses. Once I wrapped the function with parentheses and included `()`It executed correctly, and I got the output I wanted.

# Conclusion

In conclusion, to master JavaScript, you need to understand its main ideas, like object-oriented programming, advanced features, and backend development with Node.js. Using tools like NPM and knowing about module systems such as CommonJS and ECMAScript Modules helps developers create efficient and scalable applications. Facing challenges like debugging and optimising code is part of the learning process and improves problem-solving skills. With regular practice and exploration, developers can unlock the full potential of JavaScript to build dynamic and strong web applications.