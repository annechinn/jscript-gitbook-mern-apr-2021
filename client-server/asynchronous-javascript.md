# Asynchronous JavaScript

### What does Asynchronous Mean?

When you don't know when the task will return so you can continue on instead of waiting for the task to return. For example, when you make a call to a web API, this is an asynchronous task.

This topic is going to follow the video below closely. He does a great job of explaining the topic.

{% embed url="https://www.youtube.com/watch?v=PoRJizFvM7s" %}

### Using setTimeout

setTimeout is a JavaScript function that executes a function in the future, based on the number of ms specified.

The following code is calling setTimeout five times, and each call will wait 1, 2, 3, 4, and 5 seconds before it runs the statement.

```javascript
for (let i=0;i<=5;++i) {
  setTimeout(()=> {
    console.log(`i: ${i}`);
  }, i*1000);
}
```

We're going to use setTimeout to show how callbacks can be used to sequence code.

We have created two function. 

getAnimals - prints out the names of the animals in the array after 1 second.

createAnimal - adds an animal to the array after 2 seconds.

When this code is run, the animals are logged to the console before the new one is added.

```javascript
const animals = [
  {
    name: "Zena",
    age: 12,
  },
  {
    name: "Maxwell",
    age: 15,
  }
];

function getAnimals() {
  setTimeout(()=> {
    console.log(animals.map(x=>x.name).join(", "));
  }, 1000);
}

function createAnimal(animal) {
  setTimeout(()=> {
    animals.push(animal);
  }, 2000);
}

createAnimal({
  name: "Boo",
  age: 12,
});

getAnimals();

```

The old way to sequence these functions would be to use a callback, or to pass the function that is displaying the animals to the function that is updating the animals so that the display function wouldn't be called until after the update function.

In this version, the new animal is added, and then the callback function is called, ensuring that the animal is added before the animals are displayed.

```javascript
function getAnimals() {
  setTimeout(()=> {
    console.log(animals.map(x=>x.name).join(", "));
  }, 1000);
}

// add a callback parameter, that is the function to display
// the animals to be called after the new animal is created.

function createAnimal(animal, callback) {
  setTimeout(()=> {
    animals.push(animal);
    callback();
  }, 2000);
}

// pass the getAnimals function to the createAnimal function.
createAnimal({
  name: "Boo",
  age: 12,
}, getAnimals);
```

### ES6 - Promises

Typically you will only be a consumer of promises, i.e. you will call functions that return a promise, but we'll show here how to create a Promise so that you understand how it works and the expected return values.

```javascript
 const animals = [
  {
    name: "Zena",
    age: 12,
  },
  {
    name: "Maxwell",
    age: 15,
  }
];

function getAnimals() {
  setTimeout(()=> {
    console.log(animals.map(x=>x.name).join(", "));
  }, 1000);
}

function createAnimal(animal) {
  return new Promise((resolve, reject)=> {
    setTimeout(()=> {
      animals.push(animal);
      
      const status = true;
      if (status) resolve();
      else reject("Failed");
      
    }, 2000);
  });
}


createAnimal({name: "Boo", age: 12,})
  .then(getAnimals)
  .catch(err=>console.log(err));
```

```javascript
function getBooks () {
    
    const url = "https://api.nytimes.com/svc/books/v3/lists/current/hardcover-fiction.json?api-key=5Vd8O8baGS3WEG1eQVAaS2mG6K0VyHH8";
    return axios.get(url).then((response)=> {
        const books = response.data.results.books;
        return books;
    })
};
```

### ES7 - async/await

ES7 introduced a very convenient way to execute code that returns a promise. There are two new keywords in the JavaScript language.

* **async** - used to identify a function as asynchronous. This is necessary if you are going to use the associated "await" keyword.
* **await** - used to tell the code to wait for the asynchronous call to return before proceeding.

```javascript
async function showBooks() {
  let element = document.getElementById("book-grid");
  let books = await getBooks();
  element.innerHTML = books
            .map(x=>getHTMLForBookSummary(x))
            .join("");
}
```

{% embed url="https://www.digitalocean.com/community/tutorials/understanding-javascript-promises" %}

