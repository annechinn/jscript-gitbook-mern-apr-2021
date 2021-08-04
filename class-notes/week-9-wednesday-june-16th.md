# Week 9 - Wednesday, June 16th

### Class Video

{% embed url="https://www.youtube.com/watch?v=7TB7vZBikAY" %}



### Tables

Today we're going to learn about tables. They are used for storing tabular data. Basically the equivalent of a spreadsheet. 

Historically, before the div element and grid/flex were introduced, web developers often used tables to define the structure of their web pages. Now that these other techniques exists, it is a bad practice to use tables for this purpose. They should only be used to store tabular data.

{% embed url="https://learn.shayhowe.com/html-css/organizing-data-with-tables/" %}

{% embed url="https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics" %}

Here's an example of a table for our zoo exercise. It has four columns, and a row for each type of animal.

![](../.gitbook/assets/image%20%28412%29.png)

#### Table element

The table element is the top-level HTML element required to define a table. 

```markup
<table>
</table>
```

The table element has two child components.

#### Column headers

```markup
 <thead>
      <th>Type</th>
      <th>Location</th>
      <th>Number</th>
      <th>Residents</th>
  </thead>
```

#### Rows

```markup
 <tbody>
    <tr>
      <td>Lion</td>
      <td>NE</td>
      <td>4</td>
      <td>Dee, Zena, Faustino, Maxwell</td>
    </tr>
</tbody>
```

The thead and tbody elements are not required, but good practice, as the web browser uses them to enable scrolling of the table body independent of the header.

Here's a complete table element with one row of data.

```markup
  <table>
    <thead>
      <th>Type</th>
      <th>Location</th>
      <th>Number</th>
      <th>Residents</th>
    </thead>
    <tbody>
        <tr>
          <td>Lion</td>
          <td>NE</td>
          <td>4</td>
          <td>Dee, Zena, Faustino, Maxwell</td>
        </tr>
    </tbody>
  </table>

```

#### Dynamically building a summary table for our zoo data.

First, add a new button to the end of the list of buttons at the top of the page and give it an id="summary-link".

```markup
<button id="summary-link" class="btn btn-primary">Summary</button>
```

Next, create a function to initialize the summary button with a click event handler.

From within the click handler code, call a new function named showSummaryTable.

The showSummaryTable function should retrieve the div with the id="main-content" and the update the element's HTML with the new HTML content you are going to build for the summary table.

```javascript
function showSummaryTable() {
  let element = document.getElementById('main-content');
  element.innerHTML = getHTMLForSummaryTable();
}

function initSummaryButton() {
  let button = document.getElementById("summary-link");
  button.addEventListener("click", ()=> {
    showSummaryTable();
  });
}

initSummaryButton();
```

The next step is to build out the HTML for the summary table. The basic structure of the table is pretty straightforward. I've added some bootstrap styles to the table element to make the table look nice. If you remove them you can see the before/after to see what they add.

```javascript
function getHTMLForSummaryTable() {

  let rowsHTML = "";

  let html = `
    <table class="table table-striped">
      <thead>
        <th>Type</th>
        <th>Location</th>
        <th>Number</th>
        <th>Residents</th>
      </thead>
      <tbody>
        ${rowsHTML}
      </tbody>
    </table>
  `;

  return html;
}
```

The next step is to build the HTML for the rows. For each animal type, we will call a new function, named getHTMLForSummaryTableRow, that will build up the HTML for a single row in the table.

For the first step, we'll only build the content for the first three columns and leave the last column empty.

```javascript
function getHTMLForSummaryTableRow(animalType) {

  let animals = zoo.animals.filter(animal=>animal.typeId===animalType.id);
  
  return `
    <tr>
      <td>${animalType.name}</td>
      <td>${animalType.location}</td>
      <td>${animals.length}</td>
      <td></td>
    </tr>
    `;
}

function getHTMLForSummaryTable() {

  let rowsHTML = zoo.animalTypes
      .map(animalType =>getHTMLForSummaryTableRow(animalType))
      .join(" ");

  let html = `
    <table class="table table-striped">
      <thead>
        <th>Type</th>
        <th>Location</th>
        <th>Number</th>
        <th>Residents</th>
      </thead>
      <tbody>
        ${rowsHTML}
      </tbody>
    </table>
  `;

  return html;
}
```

![](../.gitbook/assets/image%20%28326%29.png)

Last, we'll build the HTML content for the last column. It's a bit more complicated, because we want to build up a list of the animals \(name, age, sex\).

```javascript

function getHTMLForSummaryTableRow(animalType) {

  let animals = zoo.animals.filter(animal=>animal.typeId===animalType.id);

    let animalsOfTypeSummaryString = animals.map(animal=>{
      return `
        <strong>${animal.name}</strong> (${animal.sex}, ${animal.age})
      `;
    }).join(" ");

    return `
    <tr>
      <td>${animalType.name}</td>
      <td>${animalType.location}</td>
      <td>${animals.length}</td>
      <td>${animalsOfTypeSummaryString}</td>
    </tr>
    `;
}
```

### 

### Forms

An HTML form provides a way for websites to collect information from users and process requests. Forms can collect small amount of information, for example a login screen requests a user name and password, or large amounts of data, such as shipping and billing information.

Initially, there were very few form elements provided, but there currently is a wide selection for almost every need imaginable. Examples include text input, dropdowns, radio buttons, checkboxes, passwords and email addresses. The critical form element required with every form is the submit button.

In this lesson, we'll learn how to create a form, and define the elements within the form used to collect the information, and how to process the form.

We'll also briefly look at some styling that Bootstrap can provide to make  our job easier.

### Form Input Data

The form element is the container for building a form. One of the essential elements contained within the &lt;form&gt; element are &lt;input&gt; elements. The &lt;input&gt; element is used for text input, but has a type attribute to describe the type of data the element should contain.

HTML supports many different input data types for the &lt;input&gt; element. The web browser will present the appropriate UI control and validate based on the data type specified. The full list of data types supported by HTML5 can be[ found here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input).  The input type is a client-side attribute to assist in collecting the data and is not sent to with the form data sent to the server for processing. The only form data that is sent to the server is the names of the input fields and their associated values.

```markup
<form>
    <input name="firstName" type="text" />
    <input name="lastName" type="text" />
    <input type="submit" value="Submit"/>
</form>
```

### Form Styling

In the HTML code sample above, I omitted the elements that I added for the field labels and the CSS to make everything look nice. HTML forms need a lot of CSS to properly position and style their elements.  For example, here is what is displayed in the browser with just the minimal HTML from the code block above. There are just two &lt;input&gt; elements of type text, for the first and last name, and a single &lt;input&gt; element of type submit, which will be rendered as a button with default styling.

![](../.gitbook/assets/image%20%28122%29.png)

### Adding Input Field Labels

The &lt;label&gt; element is used to associate a label with a form input element. To associate the two, the label element must have the **for attribute** set to the value of the **id attribute** on the associated input element.

{% hint style="info" %}
The **id attribute** is necessary to associate a label, whereas the **name attribute** is necessary to indicate the field name to the POST request.
{% endhint %}

```markup
<label for="firstName">First Name:</label>
<input id="firstName" name="firstName" type="text" />
<label for="lastname">Last Name:</label>
<input id="lastName" name="lastName" type="text" />
```

![](../.gitbook/assets/image%20%2870%29.png)

### Adding Input Field Block Display

By default, the &lt;input&gt; and &lt;label&gt; elements are both inline elements, which is causing the entire form to be displayed on a single line. A common technique to get each input field to be in its own row is to wrap each with a &lt;div&gt; element \(which is a block element\) and add a margin on the bottom of each.

![](../.gitbook/assets/image%20%28103%29.png)

```markup
<form>
    <div>
        <label for="firstName">First Name:</label>
        <input id="firstName" name="firstName" type="text" />
    </div>
    <div>
        <label for="lastname">Last Name:</label>
        <input id="lastName" name="lastName" type="text" />
    </div>
    <input type="submit" value="Submit"/>
    </form>
```

```css
form > div {
    margin-bottom:20px;
}
```

### Additional Input Types

Below are a few of the common input types that are available. As you can see, the browser has provided type-specific input controls to gather and validate the data. 

![](../.gitbook/assets/image%20%28381%29.png)

In some cases, the form data is sent directly to the web server for processing. When this is the desired behavior, there are two attributes on the form element that configure this.

### Form Submission

There are two ways of processing a form when the submission button is clicked. 

* send the form to the server to process
* process it on the client.

### Server-side Form Processing

#### form action and method attributes

The purpose of the **action** attribute is to specify the URL to which the form data will be sent when the user submits the form. The **method** attribute specifies how the data will be sent. This method value typically would be "POST", which indicates that the input data will be included in the request body. 

#### input name attribute

The **name** attribute is the form field name that will be used when the data is included in the request body.

```markup
<form action="https://formspree.io/f/xpzkzqpn" method="POST">
    <input name="firstName" type="text" />
    <input name="lastName" type="text" />
    <input type="submit" value="Submit"/>
</form>
```

![](../.gitbook/assets/image%20%28360%29.png)

You can see this output in the Chrome Developer Tools Network tab. 

![](../.gitbook/assets/image%20%28384%29.png)

First, we click on the Submit button and we can see that the form was submitted to the page below. 

![](../.gitbook/assets/image%20%28339%29.png)

If you scroll down in the Headers area, you can see the form data. The web server would have code waiting to respond to this submission and then it would unpack the form data from the request and process it.

![](../.gitbook/assets/image%20%28241%29.png)

### Client-side Processing

The other option is to register an event-handler on the submit button and process the code directly within the event handler on the client.  This is the process we're going to use for the remainder of this exercise as we build a new form to simulate purchasing tickets to the zoo.

### Styling

A big part of form development is the additional styling that is required to make the form look presentable, as the default styling by the web browser is pretty limited.  Additionally, validation of the data is necessary. This functionality is often a selling point of adopting a front-end framework, such as Bootstrap, which provides extensive support for forms.

For this exercise, we're going to use Bootstrap to help make our job of styling the form easier.

Building the Zoo Form

Our goal for this exercise is to create a form that allows a customer to purchase tickets.

![](../.gitbook/assets/image%20%28183%29.png)

After the data is entered and the Submit button is clicked, the form will be processed and the following table will be displayed.

![](../.gitbook/assets/image%20%2892%29.png)

In the previous example, I showed how a div is used to wrap each form element to get the separation between the different input fields. In Bootstrap there is a special CSS class used to style this. 

Each input element is surrounded by a div with the class="form-group". It includes space around the elements.

For our form we only have one type of input element. We're using the **select element**, which allows the form to present a dropdown list of values for the user to select from. This is what we are using to collect the number of tickets for the different categories.

```markup
<form id="form">
    <h1>Purchase Tickets</h1>							
                
    <div class="form-group">
      <label for="adults" class="control-label">Number of Adults</label>
      <select name="adults" required class="form-control">
        <option value="0" selected>0</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
      </select>
    </div>

    <div class="form-group">
      <label for="seniors" class="control-label">Number of Seniors</label>
      <select name="seniors" required class="form-control">
        <option value="0" selected>0</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
      </select>
    </div>

    <div class="form-group">
      <label for="children" class="control-label">Number of Children</label>
      <select name="children" required class="form-control">
        <option value="0" selected>0</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
      </select>
    </div>
    
    <div class="form-group">
      <button id="submit-btn"class="btn btn-primary">Submit</button>
    </div>     
        
</form>	 
```

### Processing the Form

The first step is to setup an event handler to respond to the click event on the submit button for the form.

```javascript
function processForm() {
  // todo
}

function setupFormEventHandler() {
  
  // when user clicks "Submit" on form
  let submitBtn = document.getElementById("submit-btn");
  submitBtn.addEventListener("click", (event)=> {
    processForm(event);
  });
}

setupFormEventHandler();
```

Next, we need to collect the data from the form elements. After getting the form element from the DOM, there are properties on the form object for accessing the elements.

A short aside. We have not yet introduced an alternate way you can access object properties. So far, we have learned the dot notation.

```javascript
let user = {
    firstName: 'Sally',
    lastName: 'Smith'
}
console.log(user.firstName);
```

It is also possible to access object properties using bracket notation.

```javascript
let user = {
    firstName: 'Sally',
    lastName: 'Smith'
}
console.log(user['firstName']);
```

Bracket notation is useful when you want to dynamically access a property of an object. That is, you do not know the name of the property until runtime. We'll learn about some use-cases for this later. For now we just need to know about this syntax because we are using it to access the form elements.

The code below is getting the values input by the user for each of the select elements. The values are returned as strings, so we need to use the JavaScript parseInt function to convert the string to a number so that we can add them.

```javascript
function processForm() {
  event.preventDefault();
  
  let form = document.getElementById("form");

  let numAdults = parseInt(form.elements["adults"].value);
  let numSeniors = parseInt(form.elements["seniors"].value);
  let numChildren = parseInt(form.elements["children"].value);
}
```

Next, we want to do some processing of the data.

We want to calculate the total cost for the tickets. I've added some new data to the zoo data for the prices.  We'll use this in our calculations and then, as a first step, just print out the total to the screen.

```javascript
zoo = {
  prices: { 
    adult: 49.99, 
    senior: 24.99, 
    child: 20.99 
  },
  // other data
}
```

```javascript
function processForm(event) {
  event.preventDefault();
  
  let form = document.getElementById("form");

  let numAdults = parseInt(form.elements["adults"].value);
  let numSeniors = parseInt(form.elements["seniors"].value);
  let numChildren = parseInt(form.elements["children"].value);
  let numTickets = numAdults + numSeniors + numChildren;

  let adultTotal = zoo.prices.adult * numAdults;
  let seniorTotal = zoo.prices.senior * numSeniors;
  let childTotal = zoo.prices.child * numChildren;
  let totalCost = (adultTotal + seniorTotal + childTotal);
  
  let div = document.getElementById('ticket-total');
  div.innerHTML = `
    <h1>Total: ${totalCost.toFixed(2)}</h1>
  
}
```

![](../.gitbook/assets/image%20%28391%29.png)

The next step is to build a table to contain more detail.

```javascript
  div.innerHTML = `
  <table class='table table-striped'>
    <thead>
      <th>Type</th>
      <th>Number</th>
      <th>Cost</th>
      <th>Total</th>
    </thead>
    <tbody>
    <tr>
      <td>Adult</td>
      <td>${numAdults}</td>
      <td>${zoo.prices.adult}</td>
      <td>${adultTotal}</td>
    </tr>
    <tr>
      <td>Senior</td>
      <td>${numSeniors}</td>
      <td>${zoo.prices.senior}</td>
      <td>${seniorTotal}</td>
    </tr>
    <tr>
      <td>Child</td>
      <td>${numChildren}</td>
      <td>${zoo.prices.child}</td>
      <td>${childTotal}</td>
    </tr>
    <tr>
      <td>Total</td>
      <td>${numTickets}</td>
      <td></td>
      <td>${totalCost}</td>
    </tr>
    </tbody>
  </table>
`;
```

### Homework

Add one additional field on the form that collects a coupon code, which will be used to calculate a discount on the total price. If the coupon code is added, then the total price will include a 10% discount.

![](../.gitbook/assets/image%20%28160%29.png)

```javascript
<div class="form-group">
  <label for="coupon" class="control-label">Coupon Code</label>
  <input type="text" name="coupon" class="form-control">
</div>
```

The processForm function will need to be modified in the following ways:

* get the value from the coupon form element
* check to see if the coupon was entered, and if it matches the word "ZOOPASS", then apply a 10% discount to the totalCost.
* Add an additional row in the table, just below the last row that give the total. This row has the following HTML.

```javascript
<tr>
    <td>Discount</td>
    <td></td>
    <td></td>
    <td>${discount}</td>
</tr>
```

The output should look like this:

![](../.gitbook/assets/image%20%28132%29.png)

To get the numbers to only show two decimal places to the right, you can use the Number.toFixed method.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number/toFixed" %}

### Challenge Exercise - Bootstrap Carousel

I added some code to the ticket page/script to show a carousel of the lions \(picked just the lions because the image dimensions are all the same, which is needed for the carousel\).

![](../.gitbook/assets/image%20%28283%29.png)

```markup
<!-- add this above the form div -->

<div class="row">
    <div class="col-md-4">

      <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-inner">
          <!-- plug in the items here -->
          <div id="carousel-content"></div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div>
    </div>  
  </div>  
```

```javascript
// add this to the bottom of your tickets.js file

function getHTMLForCauroselItem(item, index) {
  return `
    <div class='carousel-item ${index===0?"active":""}'>
      <img src="${item.imageURL}" class="d-block w-100" alt="...">
      <div class="carousel-caption d-none d-md-block">
        <h5>${item.name}</h5>
        <p>${item.description}</p>
      </div>
    </div>
  `;
}

function setupFormCaurosel() {

  let div = document.getElementById('carousel-content'); 
  let html = food.map((x,index)=> {
      return getHTMLForCauroselItem(x, index);
    }).join("");
    div.innerHTML = html;
}

setupFormCaurosel();
```

You can click on the next/prev links to slide through the food items.

The challenge is for you to create a new data file and use that data to display in the carousel.

Create a new file, named carousel-data.js, in your local project directory \(same directory as scripts.js\) and then include that in the tickets.html after the line that is including tickets.js.

Next, build some data for something you want to display. You can just create a variable that holds an array of objects, with each object containing the properties you'll use in your carousel item HTML.

Use unsplash.com to get the images. Pick a set of images that are all approximately the same dimensions so they will look nice in the carousel.



{% embed url="https://unsplash.com/" %}



For example, I created an array of food items, I'd create some data like the following. You can create any properties you want.

```javascript
let food = [
  {
    name: 'Burger',
    imageURL: 'https://images.unsplash.com/photo-1499028344343-cd173ffc68a9?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MjJ8fGZvb2R8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
    description: 'A delicious buger for lunch'
  },
  {
    name: 'Curry',
    imageURL: 'https://images.unsplash.com/photo-1455619452474-d2be8b1e70cd?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MjR8fGZvb2R8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60',
    description: 'A delicious curry for lunch'

  },
  // ....

];
```

{% hint style="info" %}
Note: I had to get a later version of the bootstrap stylesheet to get the carousel to work. Replace the bootstrap link at the top of tickets.html with these two lines.
{% endhint %}

```javascript
 
 <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4" crossorigin="anonymous"></script>

```

### Preparation for Next Class

I'd like you to watch the following three videos introducing Rest API and Node.js. 

#### REST API

{% embed url="https://www.youtube.com/watch?v=7YcW25PHnAA" %}

{% embed url="https://www.youtube.com/watch?v=Q-BpqyOT3a8" %}

### Node.js

{% embed url="https://youtu.be/U8XF6AFGqlc" %}



### 

### 

### General Resources

{% embed url="https://learn.shayhowe.com/html-css/building-forms/" %}

{% embed url="https://getbootstrap.com/docs/4.0/components/forms/" %}



{% embed url="https://getbootstrap.com/docs/4.0/content/tables/" %}

{% embed url="https://getbootstrap.com/docs/5.0/layout/grid/" %}



