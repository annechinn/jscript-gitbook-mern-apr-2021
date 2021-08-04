# Week 11 - Saturday, June 26th

### Class Video

{% embed url="https://www.youtube.com/watch?v=ps3gHhvnrWY" %}

### Update Main Branch

Here are the directions for how to incorporate updates on the main branch into another branch

{% hint style="danger" %}
* if you already started work in a new branch, add and commit the changes in your branch
  * git add .
  * git commit -m"\[message\]"
* switch to the main branch
  * git checkout main
* pull to update the main branch
  * git pull
* switch to your other branch
  * git checkout \[branch-name\]
* merge the main branch updates into your branch
  * git merge main
{% endhint %}

### Practice Problems

If you are finding these problems difficult, you can go to this site and focus on the problems that are in the "Very Easy" JavaScript category. If you sign-in, you can practice on the site, and you are allowed to unlock the answers.

{% embed url="https://edabit.com/challenges" %}



The solutions are in the next section below.

```javascript
// Problem: firstAndLast - array
// return a new array that contains the first and last
// elements from the input array

function firstAndLast(inputArray) {
}

// should return [1, 5]
console.log(firstAndLast([1, 2, 3, 4, 5]));
```

```javascript
// Problem: firstAndLast - object
// return a new object that contains two properties:
// first: hold the value of the first element in the input array
// last: hold the value of the last element in the input array.

function firstAndLast(inputArray) {
}

// should return {first: 1, last: 5}
console.log(firstAndLast([1, 2, 3, 4, 5]));
```

```javascript
// Problem: answer
// answer can be one of the following values: 
// "y", "Y", "yes", "Yes", "n", "N", "no", "No"
// the function should return "YES", if the input is a variant of "yes"
// the function should return "NO", if the input is a variant of "no"
// otherwise it should return "NEITHER"

function answer(input) {
}

// these should return "YES"
console.log(answer("yes")); 
console.log(answer("y"));
console.log(answer("YES"));
console.log(answer("Y"));

// these should return "NO"
console.log(answer("no")); 
console.log(answer("n"));
console.log(answer("NO"));
console.log(answer("N"));

// should return "NEITHER"
console.log(answer("XX"));
```

```javascript
// Problem: Q1
// input: an array of strings
// the function should return a string enumerating
// the choices in the input array.
// "You have three choices: strawberry, chocolate, vanilla"
// no local variables

function question(choices) {
  return ``;
}

console.log(question(['strawberry', 'chocolate', 'vanilla']));
```

```javascript
// Problem Q2
// input: an array of objects, with a property named 'flavor'
// the function should return a string enumerating
// the choices in the input array.
// "You have three choices: strawberry, chocolate, vanilla"
// no local variables

// Extra Challenge: have the choices contain the word "and" before
// the last element.
// "You have three choices: strawberry, chocolate, and vanilla"
// hint: the map function can accept a second parameter, which is 
// the current index. You can use that to determine whether you
// are processing the last element, and if so return the word
// "and " before the flavor.

function question(choices) {
  return ``;
}

console.log(question([{flavor: 'strawberry'}, {flavor: 'chocolate'}, {flavor: 'vanilla'}])); 
```

{% embed url="https://www.codewars.com/kata/56bc28ad5bdaeb48760009b0/train/javascript" %}

```javascript
// one solution

function removeChar(str){
  let result = "";
  for (let i=1;i<str.length-1;++i) {
    result+=str[i];
  }
  
  return result;
};

console.log(removeChar('eloquent') === 'loquen');
console.log(removeChar('country') === 'ountr');
console.log(removeChar('person') === 'erso');
console.log(removeChar('place') === 'lac');
console.log(removeChar('ooopsss') === 'oopss');
```

```javascript
// a better solution

function removeChar(str){
  return str.substring(1, str.length-1);
};

```

{% embed url="https://www.codewars.com/kata/5a00e05cc374cb34d100000d/train/javascript" %}

```javascript
const reverseSeq = n => {
  let results = [];
  for (let i=n;i>=1;--i) {
    results.push(i);
  }
  return results;
};

// should return [5, 4, 3, 2, 1]);
console.log(reverseSeq(5)); 

```

{% embed url="https://www.codewars.com/kata/563e320cee5dddcf77000158/train/javascript" %}

```javascript
// one solution

function getAverage(marks){
  let total = 0;
  marks.forEach(x=>total+=x);
  return Math.floor(total/marks.length);
}

console.log(getAverage([2,2,2,2])===2);
console.log(getAverage([1,2,3,4,5,])===3);
console.log(getAverage([1,1,1,1,1,1,1,2])===1);
```

```javascript
// solution, using Array.reduce

function geAverage(marks){
  let total = marks.reduce((acc,mark)=> acc+=mark, 0);
  return Math.floor(total/marks.length);
}
```

### Other Solutions

```javascript

// Problem: firstAndLast - array
// return a new array that contains the first and last
// elements from the input array

function firstAndLast(inputArray) {
    return [inputArray[0], inputArray[inputArray.length-1]]
}

// should return [1, 5]
console.log(firstAndLast([1, 2, 3, 4, 5]));

```

```javascript
// Problem: firstAndLast - object
// return a new object that contains two properties:
// first: hold the value of the first element in the input array
// last: hold the value of the last element in the input array.

function firstAndLast(inputArray) {
    return { 
      first: inputArray[0],
      last: inputArray[inputArray.length-1]
    }
}

// should return {first: 1, last: 5}
console.log(firstAndLast([1, 2, 3, 4, 5]));
```

```javascript
// Problem: Q1
// input: an array of strings
// the function should return a string enumerating
// the choices in the input array.
// "You have three choices: strawberry, chocolate, vanilla"
// no local variables

function question(choices) {
  return `You have ${choices.length} choices: ${choices.join(", ")}`;
}

console.log(question(['strawberry', 'chocolate', 'vanilla']));
```

```javascript
// Problem Q2
// input: an array of objects, with a property named 'flavor'
// the function should return a string enumerating
// the choices in the input array.
// "You have three choices: strawberry, chocolate, vanilla"
// no local variables

// Extra Challenge: have the choices contain the word "and" before
// the last element.
// "You have three choices: strawberry, chocolate, and vanilla"
// hint: the map function can accept a second parameter, which is 
// the current index. You can use that to determine whether you
// are processing the last element, and if so return the word
// "and " before the flavor.

function question(choices) {
  return `You have ${choices.length} choices: ${choices.map(x=>x.flavor).join(", ")}`;
}

console.log(question([{flavor: 'strawberry'}, {flavor: 'chocolate'}, {flavor: 'vanilla'}])); 
```

```javascript
// Problem: answer
// answer can be one of the following values: 
// "y", "Y", "yes", "Yes", "n", "N", "no", "No"
// the function should return "YES", if the input is a variant of "yes"
// the function should return "NO", if the input is a variant of "no"
// otherwise it should return "NEITHER"

function answer(input) {

  const lcInput = input.toLowerCase();
  if (lcInput === 'y' || lcInput === 'yes') return "YES";
  if (lcInput === 'n' || lcInput === 'no') return "NO";
  return "NEITHER"
}

// these should return "YES"
console.log(answer("yes")); 
console.log(answer("y"));
console.log(answer("YES"));
console.log(answer("Y"));

// these should return "NO"
console.log(answer("no")); 
console.log(answer("n"));
console.log(answer("NO"));
console.log(answer("N"));

// should return "NEITHER"
console.log(answer("XX"));
```

### Review Back-end

![](../.gitbook/assets/image%20%28415%29.png)

### Node.js

{% page-ref page="../client-server/node.js.md" %}

Node.js is a JavaScript runtime environment that runs on a web server and includes the JavaScript engine built by Google. 

#### http module - provides support for building a web servers

```javascript
const http = require('http');
const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req,res)=> {
  res.statusCode = 200;
  res.setHeader('Content-type', 'text/plain');
  res.end('Hello World!');
});

server.listen(port, hostname, ()=> {
  console.log(`Server started on port ${port}`)
})

```

#### Node Package Manager **\(npm\)** to manage external dependencies

```javascript
// packages.json
{
  "name": "back-end",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node server",
    "dev": "nodemon server"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "config": "^3.3.6",
    "cors": "^2.8.5",
    "dotenv": "^10.0.0",
    "express": "^4.17.1",
    "express-jwt": "^6.0.0",
    "jsonwebtoken": "^8.5.1",
    "mongo-seeding": "^3.7.0",
    "mongoose": "^5.12.14",
    "nodemon": "^2.0.7"
  }
}
```

#### Express.js

{% page-ref page="../client-server/express.md" %}

Express.js is a JavaScript library that simplifies the process of creating a web server and registering endpoints with the web server so that the requests from your JavaScript code on the client are routed to the correct code within the Web API. 

#### Basic Web Server

```javascript
const express = require('express');

const app = express();

app.get('/', (req, res)=> {
  res.send('Hello World!');

  // req: HTTP request:
  // URL parameters, query string, data in 
  // request body

  // res: HTTP response: what you send back to the client
  // JSON data, render a template, redirect, etc.
})

const port = 3000;
app.listen(port, ()=> {
  console.log(`Server started on port ${port}`)
});
```

#### Restful API

Conventions have been established for how to structure web APIs, especially for those that are public.

REST stands for **RE**presentational **S**tate **T**ransfer. It is an architectural model to organize interactions between independent systems. RESTful applications commonly use HTTP requests to post data \(create and/or update\), read data \(e.g., make queries\), and delete data.

| CRUD | HTTP Verb | URL | Description |
| :--- | :--- | :--- | :--- |
| Read | GET | /api/order | Returns all order |
| Read | GET | /api/order/3 | Returns order \#3 |
| Create | POST | /api/order | Creates new order |
| Update | PUT | /api/order/3 | Updates order \#3 |
| Delete | DELETE | /api/order/3 | Deletes order \#3 |

#### Express Routing - Code Organization

Express provides a mechanism to move the Express handlers for different MongoDB document collections to separate files.

```javascript
app.use('/api/users', require('./routes/api/users'));
app.use('/api/articles', require('./routes/api/articles'));
app.use('/api/topics', require('./routes/api/topics'));
```

![](../.gitbook/assets/image%20%28206%29.png)

{% page-ref page="../client-server/mongodb.md" %}

### SQL vs NonSQL Databases

#### SQL

![](../.gitbook/assets/image%20%28269%29.png)

NonSQL

![](../.gitbook/assets/image%20%28280%29.png)

![](../.gitbook/assets/image%20%28178%29.png)

### Mongoose

Mongoose is a Object Document Manager for Node.js, which is a library that allows you to define schemas for your MongoDB data and provides utilities for mapping the MongoDB data to JavaScript objects. 

### Homework

For this class, focus on increasing your basic JavaScript skills by reviewing all of the practice problems within this topic, as well as the ones from Week 10, Saturday. I have supplied all of the solutions to both my problems and the ones from code wars.

If these are not coming easily to you, you should be spending a couple of hours a day practicing them.

Also, walk through the code in my solution for the labs/article-summary and try to follow the sequence of steps all the way from the client through the server and back. 

