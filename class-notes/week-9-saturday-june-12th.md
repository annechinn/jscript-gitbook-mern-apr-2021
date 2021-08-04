# Week 9 - Saturday June 12th

### Class Video

{% embed url="https://www.youtube.com/watch?v=uwjrO7iYiU8" %}



### Event Handler Setup

In the last class, we wrote some code to initialize the button with the id="lion-link". We now want to create similar code for all of the buttons. We code duplicate the code for each button, but it would be better to try to build the code so that there is as little duplication as possible. The code for initializing each button is essentially the same, so we just need a way to get all of the buttons to setup.

A technique developers use is to give elements an id value that has a pattern, so that you can parse the value and use it to provide information for you code.

For example, each button has the pattern of having the id attribute = \[animalTypeName\]-link. When we name it like this, we can then iterate through the animal types, extract the name and then use that to find the corresponding button that we want to set up.

We are going use the following technique to find all of the buttons.

* each buttons has an id that has the pattern: "{animalType}-link"
* loop through each of the animalType data elements and build up the button id for each animal type and get the DOM element for the button using the document.getElementById method.
* add an event handler for the button

```javascript
// button id pattern: `${animalType.name}-link`

function initAnimalType(animalType) {

    const id = `${animalType.name}-link`
    let button = document.getElementById(id);

    button.addEventListener("click", () => {

      
    });
}

function initAnimalTypes() {
  zoo.animalTypes.forEach((x) => initAnimalType(x));
}
```

```markup
 <div class="buttons">
    <button id="lion-link" class="btn btn-primary">Lions</button>
    <button id="bear-link" class="btn btn-primary">Bears</button>
    <button id="tiger-link" class="btn btn-primary">Tigers</button>
    <button id="penguin-link" class="btn btn-primary">Penguins</button>
    <button id="otter-link" class="btn btn-primary">Otters</button>
    <button id="frog-link" class="btn btn-primary">Frogs</button>
    <button id="snake-link" class="btn btn-primary">Snakes</button>
    <button id="giraffe-link" class="btn btn-primary">Giraffes</button>
    <button id="elephant-link" class="btn btn-primary">Elephants</button>
  </div>
```

```bash
  animalTypes: [
    {
      id: 1,
      name: 'lion',
      location: 'NE',
      caretakerId: 1, // Nigel
    },
    {
      id: 2,
      name: 'tiger',
      location: 'NW',
      caretakerId: 2, // Burl
    },
    
    // ....
  ],
```



#### Setting up the Event Handlers

```javascript
function initAnimalType(animalType) {

    const id = `${animalType.name}-link`
    let button = document.getElementById(id);

    let element = document.getElementById("main-content");

    button.addEventListener("click", () => {
    
        element.innerHTML = getHTMLForAnimalType(animalType);
      
    });
}

function initAnimalTypes() {
  zoo.animalTypes.forEach((x) => initAnimalType(x));
}
```

#### Generating the HTML

We'll start out with some very simple HTML. Just the name of the animal type. We can get that from the animalType.name property. We just build up a string to return.

```javascript
 // animalTypes: [
 //   {
 //     id: 1,
 //     name: 'lion',
 //     location: 'NE',
 //     caretakerId: 1, // Nigel
 //   }, 
 //   // ....
 // ],
 
 function getHTMLForAnimalType(animalType) { 
   return ` 
     <h1>${animalType.name}</h1>
     `;
 }
```

![](../.gitbook/assets/image%20%28230%29.png)

Next, we can expand the information we are displaying by adding the number of animals for the type.

We can use the Array.filter method to find all of the animals that match the animal type.

We use the relationship between these two objects to get the animals of the type

![](../.gitbook/assets/image%20%2849%29.png)

Then we can get the number of animals by getting the length of the array.

```javascript
// animalTypes: [
//   {
//     id: 1,
//     name: 'lion',
//     location: 'NE',
//     caretakerId: 1, // Nigel
//   }, 
//   // ....
// ],
// animals: [
//   {
//     name: "Zena",
//     sex: "female",
//     imageURL: "https://images.unsplash.com/photo-1571835782488...",
//     age: 12,
//     typeId: 1, // lion
//   },
//   // ... lions
//   {
//     name: "Shu",
//     sex: "female",
//     imageURL: "https://images.unsplash.com/photo-1562552476-8...",
//      age: 19,
//     typeId: 2, // tiger
//   }
//   // ...
// ];

function getHTMLForAnimalType(animalType) { 
  let animals = 
    zoo.animals.filter((x) => x.typeId === animalType.id);

  return ` 
    <h1>${animalType.name} - ${animals.length}</h1>
    `;
}
```

![](../.gitbook/assets/image%20%28422%29.png)

Next, we'll add the name of the caretaker for the animal type, as well as the location within the zoo where the animals of this type reside.

We're using a new method Array.find, to find the caretaker. Array.find searches through the array, and returns the array element that matches the criteria passed in through your function. If there isn't a match, it will return undefined.

{% embed url="https://www.digitalocean.com/community/tutorials/js-array-find-method" %}



```javascript
function getHTMLForAnimalType(animalType) { 
  let animals = 
    zoo.animals.filter((x) => x.typeId === animalType.id);
  
  let caretaker = 
    zoo.caretakers.find((x) => x.id === animalType.caretakerId);

  return ` 
    <h1>${animalType.name} - ${animals.length}</h1>
    <h3>Location: ${animalType.location}</h3>
    <h3>Caretaker: ${caretaker.firstName} ${caretaker.lastName}</h3>
    `;
 }
```

![](../.gitbook/assets/image%20%28111%29.png)

Next, we're going to add information about each of the animals for this type.

To organize the code, we're going to create a new function that generates the HTML for a specific animal. Then we'll call this for each animal of the given type and concatenate all of the HTML together before we update the page.

To start off, we'll name the function getHTMLForAnimal, and we'll just return the HTML to display the animal's name, age, and sex.

```javascript
function getHTMLForAnimal(animal) {
  return `
   <h3>${animal.name} - age: ${animal.age} sex: ${animal.sex}
   </h3>
  `;
}
```

Next, we'll modify our code that is generating the complete HTML to call this function for each animal of the selected type.

```javascript
// first way - concatenating string

let animalsHTML = "";

animals.forEach((x) => animalsHTML+=getHTMLForAnimal(x));
```

```javascript
// second way - using Array.map

let animalsHTML = animals.map(x=>getHTMLForAnimals(x)).join("");
```

{% embed url="https://www.digitalocean.com/community/tutorials/js-converting-arrays-to-strings" %}



```javascript
function getHTMLForAnimalType(animalType) { 
  let animals = zoo.animals.filter((x) => x.typeId === animalType.id);
  let caretaker = zoo.caretakers.find((x) => x.id === animalType.caretakerId);
  
  let animalsHTML = animals.map(x=>getHTMLForAnimals(x)).join("");

  return ` 
    <h1>${animalType.name} - ${animals.length}</h1>
    <h3>Location: ${animalType.location}</h3>
    <h3>Caretaker: ${caretaker.firstName} ${caretaker.lastName}</h3>

    <div>
      ${animalsHTML}
    </div>
    `;
}
```

* line 5 - we build the HTML for all of the individual animals of the type
* line 13 - we add that HTML to the overall HTML that is returned.

```javascript
function getHTMLForAnimalType(animalType) { 
    let animals = zoo.animals.filter((x) => x.typeId === animalType.id);
    let caretaker = zoo.caretakers.find((x) => x.id === animalType.caretakerId);
    let animalsHTML = "";
    
    animals.forEach((x) => animalsHTML+=getHTMLForAnimal(x));

    return ` 
      <h1>${animalType.name} - ${animals.length}</h1>
      <h3>Location: ${animalType.location}</h3>
      <h3>Caretaker: ${caretaker.firstName} ${caretaker.lastName}</h3>

      <div>
        ${animalsHTML}
      </div>
      `;
  }
```

![](../.gitbook/assets/image%20%28393%29.png)

Finally, we'll clean up the styling to make it look better and add the animal's photo. 

We're going to use bootstrap, which is a front-end framework for styling HTML. It will allow us to create the cards for each animal really easily.

```bash
function getHTMLForAnimal(animal) {
    return `
      <div class="card">
        <img src="${animal.imageURL}" class="card-img-top">
        <div class="card-body">
          <h5 class="card-title">${animal.name}</h5>
          <p class="card-text">sex: ${animal.sex} age: ${animal.age}</p>
        </div>
      </div>
  `;
}
```

Next, we want to make the animals appear in a grid, rather than just running down the page in a single column. How can we do that? We need to wrap all of the animal elements with a container element so that we can set the style on the container to be a grid.

We'll add class='animals'' on the div that surrounds the animal content and then style that class to display as a grid.

```bash
function getHTMLForAnimalType(animalType) { 
    // ... 
    return ` 
      // ....
      <div class="animals">
        ${animalsHTML}
      </div>
      `;
  }
```

```bash
.animals {
  margin-top:20px;
  display:grid;
  grid-template-columns: 1fr 1fr;
  grid-gap:16px;
}
```

![](../.gitbook/assets/image%20%28133%29.png)

### Homework

#### Add a Home button which shows the showcase animal when clicked

You're going to add a button at the beginning of the list of buttons at the top of the page with the label "Home". When clicked, it should call the showHome function.

* Add the Home button. Give it an id="home-link"
* Create a function, named showHome.
* The showHome function should perform the exact same statements that are in the initLionButton function \(from Wedneday's HW\). The only change is that the call to document.getElementById with the "lion-link" should be changed to "home-link".
* call the function showHome from your script so that it runs when the script is loaded and the default content is the showcase animal.

![](../.gitbook/assets/image%20%28232%29.png)

#### Add prompt to select animals to show

When the user clicks on an animal type button, you are going to bring up a window.prompt message box that is going to ask the user which animal he wants to see, giving a list of the animal names.

{% hint style="info" %}
Use the Array.map, followed by the Array.join\(" "\) function to construct the list of names as a string.
{% endhint %}

The default value for the prompt should be "all".

![](../.gitbook/assets/image%20%28389%29.png)

Conditionally processing the return value from window.prompt.

If the user clicked the Cancel button, then window.prompt will return null. In this case, don't do anything. Just exit the function.

If "all" is returned from window.prompt, then do what we did during class, show all the animals.

![](../.gitbook/assets/image%20%28168%29.png)

If one of the animal names is returned, only show that specific animal.

![](../.gitbook/assets/image%20%28115%29.png)

![](../.gitbook/assets/image%20%2869%29.png)

If the user entered an invalid name, call window.alert, informing them that it is invalid and show all the animals.

![](../.gitbook/assets/image%20%28447%29.png)

![](../.gitbook/assets/image%20%2818%29.png)

![](../.gitbook/assets/image%20%2850%29.png)

#### Code Challenge

```javascript
data = [
  {
    name: 'Butters',
    age: 3,
    type: 'dog'
  },
  {
    name: 'Lizzy',
    age: 6,
    type: 'dog'
  },
  {
    name: 'Red',
    age: 1,
    type: 'cat'
  },
  {
    name: 'Joey',
    age: 3,
    type: 'dog'
  }
];

// sum all of the dogs ages in dog years.
//  select only the dogs
//  translate each age into dog years (multiply them by seven)
//  sum the ages
  
function getAges(data) {
    let sum = 0;
    // use for loop
    return sum;
}

console.log(getAges(data)); // returns 84;
```

