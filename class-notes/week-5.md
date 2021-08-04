# Week 5 - May 15th, 19th

### Saturday May 15th

#### Class Video Recording

{% embed url="https://www.youtube.com/watch?v=Yx5Ygn\_P\_u8&list=PLcnK74EfSdzZHjRRW7QfKzEGw3X5lR3tg&index=11" %}

Topics we covered

adding an event handler to an HTML element

writing a function to respond to the event

declaring and assigning values to variables

the window, document and console objects

document.getElementById

### Homework

I've created three small exercises to allow you to practice a bit of what we went over today. If you're having trouble, don't hesitate to connect with me on Slack and set up a time to review concepts.

#### Turning in Assignment

This assignment should be turned in via Canvas. You can submit it in whatever way you would prefer.

* check-in to github/netifly and submit the url
* paste in the contents of script1.js, script2.js, and script3.js as text content in the assignment in Canvas 
* upload the script files to Canvas.

I haven't used Canvas enough to know how all the options work for submitting assignments. I think I have set it up so you can submit a webURL, text, or upload files. 

f you're having trouble with submitting it, you could also just paste the text for the three script  files into Slack. They are short enough that it's easy for me to just review there.

#### Directions

Download a unzip the project directory from this github account

{% embed url="https://github.com/annechinn/jscript-hw-1" %}



The html page has three buttons on it. It also includes three separate script files. 

There is a separate button for each of three exercises. When you click on the button, it will call the appropriate function in the associated script file. So the first button calls the function "funcForExercise1", which is declared in script1.js. The same pattern for funcForExercise2 and funcForExercise3.

```javascript
<body>
    <div id="main-content">     
    </div>

    <div><button onclick="funcForExercise1()">click for exercise 1</button></div>
    <div><button onclick="funcForExercise2()">click for exercise 2</button></div>
    <div><button onclick="funcForExercise3(event)">click for exercise 3</button></div>

    <script src="script1.js"></script>
    <script src="script2.js"></script>
    <script src="script3.js"></script>
</body>
```

#### Exercise 1 

Step 1, 2, and 3 correspond to what each step in the code should look like when your code is complete.

#### Step 1

![](../.gitbook/assets/image%20%28404%29.png)

#### Step 2

![](../.gitbook/assets/image%20%28378%29.png)

#### Step 3

![](../.gitbook/assets/image%20%28373%29.png)

### Exercise 2

This is what the screen should look like when you click the button for exercise 2.

![](../.gitbook/assets/image%20%28362%29.png)

### Exercise 3

This is how the button should look after you click the button for exercise 3.

![](../.gitbook/assets/image%20%2828%29.png)

### Solutions

Look at these only after you've tried to do them on your own.

#### script1.js

```javascript
// you are writing a program that is going to prompt
// the user for their first and last name and then
// pass those two values to a function, which will
// alert the user with the full name.

function registerUser(firstName, lastName) {

  // you can concatenate strings together using the "+" character.

  let message = "Thanks " + firstName + " " + lastName + "!";
  alert(message);
}


function funcForExercise1()
{
  // step 1: prompt the user for their first name (already done)
  // documentation: https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt
  let firstName = prompt("What is your first name?");

  // step2: prompt the user to get their last name 
  // the prompt is provided, follow the example from step1 above
  let lastName = prompt("What is your last name?");

  // step 3: call the registerUser function above, passing in the 
  // firstName and lastName as arguments.
  registerUser(firstName, lastName);
}
```

#### script2.js

```javascript
function funcForExercise2() {

  let element = document.getElementById("main-content");

  // an element has the property "innerHTML" that you can assign a value to.
  // the value is a string representing valid HTML.

  element.innerHTML = "<h1>Look at this</h1>"

  // follow the example above, except this time get the element with the
  // id "exercise-2-div" and change its innerHTML to an image element
  // with the value of the src attribute to be the french-toast.jpg image
  // that's part of this project.

  element.innerHTML = "<img src='french-toast.jpg'>";
}
```

#### script3.js

```javascript
function funcForExercise3(event) {

  let element = event.target;

  // NOTE: the property name for the styles are the same as in
  // CSS, except that instead of a "-" between words, you
  // use camelCase, i.e. capitalizing the first letter in each word
  // so "background-color" in CSS is "backgroundColor" from JavaScript
  element.style.backgroundColor = "yellow";

  // following the same pattern, change the following styles
  // the color of the text to red
  // the border radius to 8px;
  // the font weight to 700;

  element.style.color = "red";
  element.style.borderRadius = "9px";
  element.style.fontWeight = "bold";
```

### 

### Wednesday May 19th

#### Class Video Recording

{% embed url="https://www.youtube.com/watch?v=zMQS\_BlbO40" %}

Topics we covered

### Variables

Primitive Data Types - string, number, boolean

Special types

**undefined** - the value of a variable which is uninitialized \(never been assigned a value\)

**null** - the value of a variable when the variable has been assigned the value null. 

A common situation in which a variable will be assigned the value null is when you call a function and the function returns null.

For example, in the code below, imagine I wrote a function that looks through the list of products and return the element that has the same name as the parameter passed in.

```javascript
function getProductByName(name) {

    for (let i=0; i<products.length; ++i) {
        if (products[i].name === name) {
            return products[i];
        }
    }
    
    // if we reach this point we have gone through the 
    // whole list and haven't found a product that matches
    // so we return null
    
    return null;
}

let product = getProductByName("French Bread");
if (product === null) {
    console.log("Didn't find it");
}
else {
    console.log("Found it");
}
```

### Arrays

We created an array containing four elements. Each element is a number.

The code below is just demonstrating how to access the element

```javascript
let arr = [1, 2, 3, 4];

console.log(arr[0]); // 1
console.log(arr[1]); // 2
console.log(arr[2]); // 3
console.log(arr[3]); // 4
```

This code is just demonstrating the use of a variable to access the elements in the array. The purpose of demonstrating this is so that you will better understand the use of a variable to access an array in the next example where we are using a for loop to access each element in the array.

```javascript
let i = 0;
console.log(arr[i]); // 1
i = i + 1; // i=1
console.log(arr[i]); // 2
i = i + 1; // i=2
console.log(arr[i]); // 3
i = i + 1; // i=3
console.log(arr[i]); // 4
```

An alternate way to increment the value store in a variable that is holding a numeric value is to use the "++" operator.

```javascript
let i = 0;
console.log(arr[i]); // 1
i++; // i=1
console.log(arr[i]); // 2
i++; // i=2
console.log(arr[i]); // 3
i++; // i=3
console.log(arr[i]); // 4
```

Now we're going to use the for loop to display the value of each element in the array to the console.

```javascript
let arr = [1, 2, 3, 4];

console.log(arr.length); // 4

// the loop will continue as long as the
// value of i<4
for (let i=0; i<arr.length ; i++) {
  console.log(arr[i]);
}
```

### Objects

An object with properties that have values that are primitive data types \(string, number, bool\)

```javascript
 let user {
    firstName: 'Sally',
    lastName: 'Smith',
    email: 'ss@company.com'
 }
 
 console.log(user.firstName);
```

We've added a property "address", that has a value that is an object.

```javascript
 let user {
    firstName: 'Sally',
    lastName: 'Smith',
    email: 'ss@company.com',
    address: {
      street: '120 5th Ave',
      city: 'Renton',
      zip: 98112
    }
 }
 
 console.log(user.address.zip);
```

We switched to working toward building a more complex object that represents a shopping cart that would track the user selecting products to purchase.

Here's the list of products.

```javascript
let products = [
  {
  name: 'Whole Grain Bread',
  category: 'bread',
  price: 5.99,
  onSale: true,
  discount: .79
},
{
  name: 'Potato Chips',
  category: 'chips',
  price: 3.99,
  onSale: false,
  discount: 0
}
,
{
  name: 'Roasted Nuts',
  category: 'nuts',
  price: 4.99,
  onSale: false,
  discount: 0
}
];
```

Then, we added the an object to represent the shopping cart. At first, we just added the property that will hold the products that the user selects. It's an empty array to start.

```javascript
let shoppingCart = {
  items: [],
}
```

Next, we added a function to the shopping cart object that would add an item to its list of items. The input data that it expects to receive is one of the products from the collection of products we stored in the products variable.

```javascript
 let shoppingCart = {
  items: [],
  
  addItem: function(item) {
    this.items.push(item);
  }
 }

// Add two products to the shopping cart
shoppingCart.addItem(products[0]);
shoppingCart.addItem(products[1]);

console.log(shoppingCart.items);
```

Last, we worked on writing a method on the shopping cart object that would use a for loop to go through the elements in the items array and add up the price of each and return the total amount for all of the items.

```javascript
 let shoppingCart = {
  items: [],
  
  addItem: function(item) {
    this.items.push(item);
  }
  
  getTotalCost: function() {
    let sum = 0;

    for (let i=0; i<this.items.length;++i) {
      let item = this.items[i];
      // console.log("i: ", i);
      // console.log("sum before: ", sum);
      // console.log("price: ", item.price);
      sum = sum + item.price;
      console.log("sum after: ", sum);
    }

    return sum;
  }
  
 }
 
shoppingCart.addItem(products[0]);
shoppingCart.addItem(products[1]);
console.log(shoppingCart.items);
console.log(shoppingCart.getTotalCost());

```

Here's the complete solution to the shopping cart example.

#### index.html

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">

</head>
<body>
  <script src="script.js"></script>
</body>
</html>
```

#### script.js

```javascript
let products = [
  {
  name: 'Whole Grain Bread',
  category: 'bread',
  price: 5.99,
  onSale: true,
  discount: .79
  },
  {
    name: 'Potato Chips',
    category: 'chips',
    price: 3.99,
    onSale: false,
    discount: 0
  },
  {
    name: 'Roasted Nuts',
    category: 'nuts',
    price: 4.99,
    onSale: false,
    discount: 0
  }
];

let shoppingCart = {
  items: [],
  
  addItem: function(item) {
    this.items.push(item);
  }
  
  getTotalCost: function() {
    let sum = 0;

    for (let i=0; i<this.items.length;++i) {
      let item = this.items[i];
      // console.log("i: ", i);
      // console.log("sum before: ", sum);
      // console.log("price: ", item.price);
      sum = sum + item.price;
      console.log("sum after: ", sum);
    }

    return sum;
  }
  
 }
 
shoppingCart.addItem(products[0]);
shoppingCart.addItem(products[1]);
console.log(shoppingCart.items);
console.log(shoppingCart.getTotalCost());
```

Functions

Walked through exercise to update the main content section of the article grid page

{% page-ref page="../article-grid-js-updates/main-content-updating-html.md" %}

```javascript
function capitalize(str) {
  return `${str[0].toUpperCase()}${str.slice(1)}`;
}

function updateMainContent(targetId) {

  // targetId: "tech-link"
  let sectionName = targetId.split("-")[0]; // "tech";
  let capSectionName = capitalize(sectionName); // "Tech";
  console.log(capSectionName);
  let mainContentElement = document.getElementById("main-content");
  mainContentElement.innerHTML = `<h1> ${capSectionName} Content</h1>`;
}

function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  console.log(event);

  let targetElement = event.target;
  targetElement.classList.add("active");

  let targetId = targetElement.id; // "tech-link", "food-link", etc..

  updateMainContent(targetId);
}

```

### HW

You do not need to turn anything in, but try to see if you can set up a project to run practice some JavaScript code.

To practice these on your own, create an new project folder, load it in VS Code and create two files: index.html and script.js. Then include the script.js file in your index.html using the script element. Once this is in place, you can just start adding the code for the exercises in your script.js file. 

As you work on each exercise, you can comment out the code for the previous exercise so it doesn't get called while your working on the next one. An alternative is to create a function for each exercise, and only add a statement to call the one you are currently working on.

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">

</head>
<body>
  <script src="script.js"></script>
</body>
</html>
```

#### Exercise 1

```javascript
let arr = [1, 2, 3, 4];

// write a for loop that goes through each of the elements
// sums up the total and pass the total to console.log
```

#### Exercise 2

```javascript
// create an array that contains two user objects. 
// each user object has just two properties: firstName and lastName
```

#### Exercise 3

```javascript
let firstName = "Sally";
let lastName = "Smith";

// create a new variable that is assigned the value 
// "Hi, my name is " + firstName + " " + lastName
// but use a string literal to do it instead of the "+" operator
```

