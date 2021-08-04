# Storing Data - Variables

When we need to store data in a computer program for later use, we use variables. A variable is a “named storage” for data. Think of it as a box, with a label on the outside, saying what's in the box.

![https://stevenpcurtis.medium.com/what-is-a-variable-3447ac1331b9](../.gitbook/assets/image%20%28143%29.png)

### The Let Keyword

To create a variable in JavaScript, use the **let** keyword, followed by the name of the variable.

The variable can contain any type of data. The name should be a meaningful label \(describes the purpose of the variable\) for the data that is stored in the variable. 

Other naming restrictions:

* no spaces in the name
* cannot start with a number, or special character

{% hint style="info" %}
The convention for naming variables in JavaScript is to use camelCase, meaning that the first character in each word in the variable is upper-case.
{% endhint %}

```javascript
let name = "Sally";
let age = 42 + 21;
let oldEnoughToVote = true;
```

### Variables Hold Values For Later Use

Imagine that we need to collect some personal information from a user to register them for a new program. We need to first ask the user for several pieces of information, and then once it has all been received, we can then go off and register the user. We do the equivalent of writing down the answers on our notepad, and then, once we're done interacting with the user, we take those values stored in the variables and use them to register the user.

```javascript
function registerNewUser(fn, ln, email) {
  /* sends data to the backend to register user */
}


let firstName = prompt("What is your first name?");
let lastName = prompt("What is your last name?");
let email = prompt("What is your email?");

registerNewUser(firstName, lastName, email);
```

### Variable Declaration

**Let keyword** - The way you declare a variable in JavaScript is with the let keyword, followed by the name of the variable. 

```javascript
let firstName;
```

#### Uninitialized Variables - Undefined Value

At this point the statement just says that you need a variable where you can store some data. You haven't put any data in the variable yet. You're just planning ahead. 

 If we were to display the value of the variable to the console, it would return a value of **undefined**.

```javascript
let firstName;
console.log(firstName); // undefined
```

The **undefined** value is a special primitive type in the JavaScript language that is used specifically for this purpose. It indicates that the variable has not yet been assigned a value.

{% hint style="info" %}
This is an aspect of the JavaScript language that is different than many other languages. For example, the C\# language will always provide a default value for every datatype. A numeric variable would be initialized with the value 0. A boolean variable would be initialized with the value false.
{% endhint %}

#### **Empty Variables - Null Value**

```javascript
let element = document.getElementById("tech-link");
```

**Null**: A variable can be assigned the null value, which is a another special primitive type in the JavaScript language that is used specifically to indicate that the value of the variable is empty.

It is different than the undefined value, because it is a value that the programmer explicitly assigns to a variable to indicate that the variable is currently empty. 

In the example above, the call to get the HTML element with the id="tech-link" will result in a null value being returned, if the element doesn't exist.

### Variable Initialization

You can assign an initial value to a variable as part of the declaration. This is called initializing the variable. The initial value can be a literal value, such as a string, or it can be the value returned from a function, such as the value returned from the JavaScript prompt function. 

```javascript
// initialized with a literal value
let firstName = "Sally";

// initialized with the value returned from a function
let firstName = prompt("What is your first name?");
```

### Variable Assignment

You can also first declare the variables, and assign them a value at a later time. In this case we skipped the initialization step. They had the value of undefined until they were assigned a value.

{% hint style="info" %}
The best practice is do declare your variables near where they will be used, and if possible assign them an initial value.
{% endhint %}

```javascript
let firstName;
let lastName;
let email;

firstName = prompt("What is your first name?");
lastName = prompt("What is your last name?");
email = prompt("What is your email?");
```

### 

### The Const keyword

When you know the value of the variable you are declaring should not change after it has been initialized,  you should use the const keyword instead of let. This is helpful so that you don't mistakenly overwrite the variable value. 

{% hint style="info" %}
If you don't need to re-assign the value of a variable, use const, otherwise use let.
{% endhint %}

```javascript
const tipRate = .15;
tipRate = .20; // error raised, can't re-assign a constant
```

### Dynamic Typing

The value stored in a JavaScript variable is always of a certain type, such as a string or a number, or an object. JavaScript doesn't require you to specify what type of data is going to be stored in your variable. The JavaScript engine can figure it out when your script is running.  

This is not the case for all languages. If the language requires you to indicate the type of data the variable will contain, then it is called a **statically typed** language. Languages that don't require it, such as JavaScript, are called **dynamically typed** languages. 

```javascript
// C# is a statically typed language
// the code must specify the type of the data
// that the variable will contain.
// int is the datatype of the variable total.

int total = 0;

// JavaScript is a dynamically typed language
// the code does not need to specify the datatype
// of the varialble.
// The JavaScript engine will figure out that 
// the datatype of the variable total is a 
// number when it executes the code.

let total = 0;
```

### Loosely Typed

In addition to being dynamically typed, JavaScript is also a loosely typed language. That means that you are able to store different types of data in the same variable. 

{% hint style="info" %}
While this is supported in the language, it is not a good practice, as it can make your code less understandable. Best practice is to create a unique variable for each separate data element you need to store and give it a meaningful name to indicate what the purpose of the data is.
{% endhint %}

```javascript
let x = 23;
x = "Hello";
x = { firstName: 'Sally', lastName: 'Smith' }
```

### Resources

{% embed url="https://www.youtube.com/watch?v=sjyJBL5fkp8" %}

{% embed url="https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75" %}

{% embed url="https://wesbos.com/let-vs-const" %}



