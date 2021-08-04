# Main Content - updating html to show section name

### Adding HTML Content

Next, we're going to update the main content area to indicate which section we're in by replacing the HTML content between the opening and closing tags for the div element.

An HTML element has a property, innerHTML, that can be used to change the HTML that is contained within the opening and closing tags.

So, we are going to replace the content within the div with the id value of "main-content" using JavaScript.

```markup
<!-- Before -->
<div id="main-content">
  Main Content
</div>

<!-- After-->
<div id="main-content">
  Tech Section
</div
```

![](../.gitbook/assets/image%20%28236%29.png)

To get the HTML element with the id "main-content", we can use the document.getElementById method. And we store the result in a new variable.

```javascript
function respondToClick(event) {
  event.preventDefault();
  let targetElement = event.target;
  targetElement.classList.add("active");
  
  // get the element with id="main-content"
  let mainElement = document.getElementById("main-content");
  // update the html content between its opening and closing
  // tags with the new html.
  mainElement.innerHTML = "<h1>Tech Section</h1>";
}
```

Refresh the page and click on the tech link.

We are now added "Tech Section" to the page, but we are putting in content that says "Tech", which will only work when we click on the Tech link. Since we're trying to use the same function to handle the click event for all the links, we want to change the content to have the correct word for the section we click on.

### Conditional Code - If Block

We're going to use an **if block** to figure out which anchor was clicked and create the correct string based on the section we're in.

```javascript
function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  let targetElement = event.target;
  targetElement.classList.add("active");
  
  // get the id of the element that was clicked
  // it will be one of: "tech-link", "food-link", etc.
  let targetId = targetElement.id;

  // get the object that represents the HTML
  // element with id="main-content"
  let mainElement = document.getElementById("main-content");

  // test to see what the id is on the element that was clicked
  // and set the new innerHTML value to the appropriate
  // string based on which one was clicked.
  
  if (targetId === "tech-link") {
    mainElement.innerHTML = "<h1>Tech Section</h1>";
  }
  else if (targetId === "sports-link") {
    mainElement.innerHTML = "<h1>Sports Section</h1>";
  }
  else if (targetId === "food-link") {
    mainElement.innerHTML = "<h1>Food Section</h1>";
  }
  else if (targetId === "arts-link") {
    mainElement.innerHTML = "<h1>Arts Section</h1>";
  }
  else if (targetId === "science-link") {
    mainElement.innerHTML = "<h1>Science Section</h1>";
  }
}
```

The **if keyword** indicates an if block. This is followed by a set of opening and closing parentheses which contains a condition to test.   And finally a block of code to execute if the condition is true. 

Here's an example.

```javascript
let users = [
  {
    id: 2,
    firstName: 'Sally',
    lastName: 'Smith'
 }, 
 {
    id: 1,
    firstName: 'Joe',
    lastName: 'Jones'
}];

function getUserById(id) {
  for (let i=0;i<users.length;++i) {
    let user = users[i];
    if (user.id === id) {
      return user;
    }
  }
}


```

The block of code can be a single statement, or a sequence of statements surrounded by curly braces.  

```javascript

function getUserById(id) {

  for (let i=0;i<users.length;++i) {
    let user = users[i];
    if (user.id === id) return user;
  }
}
```

It is best practice to use curly braces to define your block, unless there is only a single statement to be executed and it is very short and easily fits on one line, so that it increased the overall readability.

This is often something that a style-guide would include, such as this one provided by Google.

![](../.gitbook/assets/image%20%28365%29.png)

### Creating a Helper Function

There is still a lot of code that is repeated, or "redundant".  When we see code like this we try to "re-factor" the code \(re-organizing code without changing what it does\) so that it is more resilient to changes.  

For example, If we decide to change the h1 to an h2, in the current code, we would have to edit five separate lines of code. We need to figure out a way to build the string we are assigning to the innerHTML property.

```javascript
  let targetId = targetElement.id;

  if (targetId === "tech-link") {
    mainElement.innerHTML = "<h1>Tech Section</h1>";
  }
  else if (targetId === "sports-link") {
    mainElement.innerHTML = "<h1>Sports Section</h1>";
  }
  else if (targetId === "food-link") {
    mainElement.innerHTML = "<h1>Food Section</h1>";
  }
  else if (targetId === "arts-link") {
    mainElement.innerHTML = "<h1>Arts Section</h1>";
  }
  else if (targetId === "science-link") {
    mainElement.innerHTML = "<h1>Science Section</h1>";
  }
```

So we're going to re-factor the code for creating the innerHTML string into a new function that we will call from each of the cases.

The first step is to move all of the code that is testinng the targetId and updating the innerHTML to a separate function.

```javascript
function updateMainContent(targetId) {
 // get the object that represents the HTML
  // element with id="main-content"
  let mainElement = document.getElementById("main-content");

  // test to see what the id is on the element that was clicked
  // and set the new innerHTML value to the appropriate
  // string based on which one was clicked.
  
  if (targetId === "tech-link") {
    mainElement.innerHTML = "<h1>Tech Section</h1>";
  }
  else if (targetId === "sports-link") {
    mainElement.innerHTML = "<h1>Sports Section</h1>";
  }
  else if (targetId === "food-link") {
    mainElement.innerHTML = "<h1>Food Section</h1>";
  }
  else if (targetId === "arts-link") {
    mainElement.innerHTML = "<h1>Arts Section</h1>";
  }
  else if (targetId === "science-link") {
    mainElement.innerHTML = "<h1>Science Section</h1>";
  }
}

function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  let targetElement = event.target;
  targetElement.classList.add("active");
  
  // get the id of the element that was clicked
  // it will be one of: "tech-link", "food-link", etc.
  let targetId = targetElement.id;

  updateMainContent(targetId);
}
```

### Extract the section name out of the anchor id

In our function, we receive the string representing the id of the anchor tag. It is "tech-link", or "food-link", etc. We need to extract the part of the string to the left of the "-" character.

The String object has a method for doing this. It's the String.split method. The split method splits the string in to multiple strings for each sub-string that is separated by the specified delimiter.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/split" %}

Paste the following in the Chrome Dev Tools Console.

```javascript
let str = "my-test-string";
let result = str.split("-"); 
console.log(result); // ["my", "test", "string"]
console.log(result[0]); // "my"
```

The value assigned to the result variable will be an array containing three strings: \["my", "test", "string"\]

Now we have a way to get the word that represents what section was clicked.  It is a common technique used in web programming to pass data through attribute values. The only way you can get data relevant to a specific HTML element is to store it as an attribute on the element.

Next, we're going to use the String.split method technique above to change the code inside the updateMainContent function to extract the first part of the id and use that string to build the string to put in the innerHTML.

```javascript
function updateMainContent(targetId) {

  // targetId = "tech-link", "food-link", etc
  // we need to extract out the part of the string
  // before the "-" character.
  
  // String.split breaks the string into separate string
  // divided by the delimiter specified and puts them into
  // an array.
  // ["tech", "link"]
  // we then extract the first element in the array
  
  // let splitResult = targetId.split("-");
  // let sectionName = splitResult[0];
  let sectionName = targetId.split("-")[0];

  element = document.getElementById("main-content");
  element.innerHTML = "<h1>" + sectionName + "Section</h1>";
}
```

### String Template Literals

Notice on the last line in the code above that we are using the "+" sign to concatenate strings together to build the entire string that we are setting for the inner HTML value.

```javascript
element.innerHTML = "<h1>" + sectionName + " Section</h1>";
```

There is also another technique, called a template literal, which allows you to build a string from literal strings and variable values.

You use back-ticks, instead of quotes, to surround to string, and then wrap each variable with ${}. The value of the variable will then be evaluated by the JavaScript engine and inserted into the final string.

```javascript
  element.innerHTML = `<h1>${sectionName} Section</h1>`
```

Here's what our code should look like after the re-factoring.

```javascript
function updateMainContent(targetId) {
  let sectionName = targetId.split("-")[0];

  element = document.getElementById("main-content");
  element.innerHTML = `<h1>${sectionName} Section</h1>`;
}

function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  let targetElement = event.target;
  targetElement.classList.add("active");

  let targetId = targetElement.id;
   updateMainContent(targetId);
}
```

### Capitalize the Section Name

You'll notice that the section name is no longer capitalized because it isn't in the anchor element id. So I've created a function named capitalize that will return a capitalized version of the string passed in.

It's suprising that there isn't a built-in method on the JavaScript String object to capitalize a word, but there isn't, so you have to build that function yourself.

```javascript
function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1);
}
```

Try this in the StackBlitz to see how the String.slice method works.

```css
let str = "test";
let strUC = str.toUpperCase();
console.log(strUC);
console.log(str.slice(0));
console.log(str.slice(1));
console.log(str.slice(2));

let firstCharUC = str[0].toUpperCase();
let restOfString = str.slice(1);
console.log(firstCharUC);
console.log(restOfString);
strUC = firstCharUC + restOfString;

console.log(strUC);
```

I've changed the code to now store both a lowercase and capitalized version of the section name and am using the capitalized value in the HTML that we are assigning to the element's innerHTML.

```javascript
function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1);
}

function updateMainContent(targetId) {
  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);

  element = document.getElementById("main-content");
  element.innerHTML = `<h1>${sectionName} Section</h1>`;
}

function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  let targetElement = event.target;
  targetElement.classList.add("active");

  let targetId = targetElement.id;

   updateMainContent(targetId);
}
```



