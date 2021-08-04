# Main Content - removing active class

### Removing the active class before updating the new section

If you look at the current version of the site, when we click on a new section, the last section that was clicked still has the red color. That's because we add the active class value to each element as it is clicked, but we never remove it.

![](../.gitbook/assets/image%20%2882%29.png)

We need to build a function that will remove the active class value from all of the anchors before we add it to the new active one. To do this we're going to use an array.

We've created an array to hold each of the section names.

```javascript
let sections = ["tech", "sports", "arts", "food", "science"];
```

### For Loop

The for loop is one way to iterate through each of the elements in an array.

Below is the overall structure of a for loop.

There are three parts to the test condition, separated by semi-colons.

```javascript
for (initialization; condition; post-expression) {
    // statements
}
```

Try the following in StackBlitz.

```javascript
let array = [1,2,3,4,5];

for (let i=0; i<array.length; ++i) {
    console.log(array[i]);
}
```

**Initialization**: The initialization expression is where you perform any initialization before the first iteration begins. Typically, a for loop has a variable that is counting the iterations and it would be initialized here. If you define the variable with the let keyword, the variable will only be accessible within the scope of the loop.

**Condition**: The condition is an expression that is evaluated once before every iteration. The statement inside the loop is executed only when the condition evaluates to true. The loop is terminated if the condition evaluates to false. 

**Post-expression**: The for loop statement evaluates the post-expression after each loop iteration. Typically, you update the counter variable in the post-expression.

#### Iterating through the sections

For each element in the sections array we do the following:

* get the section string out of the array
* use the section to build the value of the id attribute for the section
* get the anchor element by its id
* remove the active class value from the class attribute.

```javascript
let sections = ["tech", "sports", "arts", "food", "science"];

function removeActiveClassFromAllSections() {

  for (let i=0;i<sections.length; ++i) {
 
    // get the section string out of the array
    let section = sections[i];
    
    //  build the value of the id attribute for the section
    // "tech-link", "food-link", etc
    let sectionId = `${section}-link`;
    
    // get the anchor element with the sectionId
    let element = document.getElementById(sectionId);
    
    // remove the active value from the class attribute
    element.classList.remove("active");
  }
}
```

```javascript
function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1)
}

let sections = ["tech", "sports", "arts", "food", "science"];

function removeActiveClassFromAllSections() {

  for (let i=0;i<sections.length; ++i) {
 
    // get the section string out of the array
    let section = sections[i];
    
    //  build the value of the id attribute for the section
    // "tech-link", "food-link", etc
    let sectionId = `${section}-link`;
    
    // get the anchor element with the sectionId
    let element = document.getElementById(sectionId);
    
    // remove the active value from the class attribute
    element.classList.remove("active");
  }
}

function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1);
}

function updateMainContent(targetId) {
  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);

  element = document.getElementById("main-content");
  element.innerHTML = `<h1>${sectionNameCap} Section</h1>`;
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

