# Week 13 - Saturday, July 10th

### Class Video

{% embed url="https://youtu.be/UBNQ7S8cIJw" %}



### Review

You should be able to explain why you are getting the results shown

```javascript
 let arr1 = [1,2,3,4];
 let arr2 = arr1.map(x=>x);
 console.log(arr1===arr2);
```

```javascript
 arr1 = [{x:1,y:1}, {x:2, y:2}];
 arr2 = arr1.map(x=>x);
 
 console.log(arr1===arr2);
 console.log(arr1[0]===arr2[0]);
```

```javascript
function f1(arr) {
   arr[0] = 2;
 }

 let arr1 = [1,2,3,4];
 f1(arr1);
 console.log(arr1);
```

```javascript
 function f2(str) {
   str+=" Chinn";
 }

 let name = "Anne";
 f2(name);
 console.log(name);
```

```javascript
 function f3(arr) {
  return [...arr];
 }

 arr1 = [{x:1,y:1}, {x:2, y:2}];
 arr2 = f3(arr1);
 console.log(arr1);
 console.log(arr2===arr1);
 console.log(arr1[0]===arr2[0])
```

```javascript
let obj1 = {x:1, y:1}
let obj2 = {x:1, y:1}
console.log(obj1===obj2);
```

```javascript
 let obj1 = {x:1, y:1}
 let obj2 = {...obj1}
 console.log(obj1===obj2);
```

```javascript
 let obj1 = {x:1, y:1}
 let obj2 = {...obj1, z:1}
 console.log(obj2);
```

### JavaScript Closure

> A **closure** is the combination of a function bundled together \(enclosed\) with references to its surrounding state \(the **lexical environment**\). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time. - MDN

```javascript
function multiplyBy(num) {
    return function(x) {
      return num*x;
    }
  }

  const double = multiplyBy(2);
  const triple = multiplyBy(3);

  console.log(double(2));
  console.log(triple(3));

  function reportError(section) {
    return function(message) {
      return `${section}: ${message}`
    }
  }

  const reportAppError = reportError('Application');
  const reportSystemError = reportError('System');

  console.log(reportAppError('app error'));
  console.log(reportSystemError('system error'));
```

### How/When Are Components Rendered?

React renders from the bottom up. In the example component hierarchy below, the BookCard elements will render before the BookGrid, which will render before the NYTBooks component.

The parent component is not done until all of it's children have rendered.  Once the entire component tree has been rendered, React has a snapshot of what the tree looks like at that point in time.

Think of it like a frame in an ongoing movie, It is a slice in time, in the evolving view of the live HTML document.

![](../.gitbook/assets/image%20%28342%29.png)

After the initial component hierarchy has been rendered, nothing will change until the state in a component changes. A state change will trigger the render function for the modified component, which will again build up a new render tree from the bottom up. React will then compare the previous version of the rendered tree for the component to the new one, and update the DOM with any changes.

### useEffect Hook

Each component can optionally call the useEffect hook. It is where you put your code that fetches external data, or reacts to changes in state.

The useEffect function takes two parameters:

* a function to run - such as a web API call to retrieve data
* an optional array to indicate what state variables should trigger the effect to run.

#### If you do not specify the optional trigger array, then the useEffect function will run every time the component is rendered.

We can use this setting to demonstrate when the components are being rendered.

There are three components: GrandParent, Parent, and Child. Each has state variable, named count, that can be triggered by clicking on a button, and will log to the console. Each component is also calling the useEffect hook,  but not specifying a trigger array, so it will always be called when the component is rendered.

![](../.gitbook/assets/image%20%28361%29.png)

![](../.gitbook/assets/image%20%28392%29.png)

When the code below first loads, you can see in the console log that the order in which the useEffect functions are called in the components is from the bottom up: from Child, Parent, to GrandParent.

But if you click on the Parent component, then only the Child, followed by the Parent component will be rendered. And if you click on the Child component, only the Child component will be rendered.

```javascript
function GrandParent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("GrandParent: useEffect");
  });

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Update GrandParent {count}</button>
      <Parent />
    </>
  );
}

function Parent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Parent: useEffect");
  });

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Update Parent {count}</button>
      <Child />
    </>
  );
}

function Child() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Child useEffect");
  });

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Update Child {count}</button>
    </>
  );
 
}

function Render() {
  return (
    <GrandParent/>
  )
}
```

#### Components are just Function Calls

You can see why this would be the case when you think of the components as nested function calls. It's like a call stack. A function can call another function and so on, and each function that makes a call to another function is waiting for the function to return its value and then it will continue and return its value all the way back up to the top-level function.

```javascript
function GrandParent() {
  return React.createElement(React.Fragment, null, 
      React.createElement("button", {onClick: () => setCount(count + 1)}, "Update GrandParent ", count), 
      React.createElement(Parent, null));
}

function Parent() {
  return React.createElement(React.Fragment, null, 
      React.createElement("button", {onClick: () => setCount(count + 1)}, "Update Parent ", count), 
      React.createElement(Child, null));
}

function Child() {
  return React.createElement(React.Fragment, null, 
    React.createElement("button", {onClick: () => setCount(count + 1)}, "Update Child ", count));
}

function Render() {
  return React.createElement(GrandParent, null);
}
```

#### If you specify an empty trigger array, then the useEffect function will run once AFTER the component is rendered.

Say, for example, that you need to load some data from the back-end when the component is first created, but you don't need to update that data. This is a case where you want your useEffect function to just run once.

{% hint style="info" %}
It's important to realize that the useEffect function will run **AFTER** the component has rendered. So it will for a re-render of the component if the JSX for the component is dependent on the data. This means that you need to build your render function to handle the case where there is not data yet to include in the JSX output.
{% endhint %}



### useEffect - empty array of triggers - it will run once

If you want your effects to run more often, you can provide one or more dependencies for the effect. If one of the dependencies has changed since the last time, the effect will run again. Your dependencies can include state variables, or props passed into the component.

### useEffect - dependency will trigger useEffect

If you add a variable to the dependency array, and that variable changes, then the function you passed to useEffect will be called.

In the code below, the function will be called after the first render, and then it will only be called when the second button is clicked.

```javascript
function ThreeCounts() {
  const [count1, setCount1] = useState(0);
  const [count2, setCount2] = useState(0);
  const [count3, setCount3] = useState(0);

  useEffect(() => {
    console.log("count2 changed!");
  }, [count2]);

  return (
    <div>
      {count1} {count2} {count3}
      <br />
      <button onClick={() => setCount1(count1 + 1)}>Increment count1</button>
      <button onClick={() => setCount2(count2 + 1)}>Increment count2</button>
      <button onClick={() => setCount3(count3 + 1)}>Increment count3</button>
    </div>
  );
}
```

### NYT Book API Sample

In the NYTBooks component, we make the API call to retrieve the books in the useEffects function. We pass an empty array for the dependency triggers because we only need to retrieve the list once.

Because the book data may not be available the first time the render function gets called, we need to write code to handle that scenario and just return an empty element.

```javascript
function NYTBooks() {
  
  const [books, setBooks] = useState(null);

  useEffect(() => {
    
      (async () => {
        setBooks(await getBooks('hardcover-fiction'));
      })();

  }, []);


  if (books) {
    return (
      <>
      <BookGrid books={books.books}/>
      </>
      );
  }
  else {
    return (<></>);
  }
}
```

Now we're going to add some additional complexity to the component. We're going to allow the user to select which genre he wants to view.

So, we need to make two calls to the NYT Web API. The first, to retrieve the list of genres to populate our dropdown list. The second, to retrieve the list of books for the genre.

The second call now is dependent on change to the selected genre. So, every time the user selects a new genre, and we update the genre state variable, React will call the useEffect for retrieving the list of books.

```javascript
function BooksAPI() {
  const [books, setBooks] = useState(null);
  const [genreOptions, setGenreOptions] = useState([]);
  const [genre, setGenre] = useState('hardcover-fiction');

  useEffect(()=> {

    (async ()=>{

      const genres = await getGenres();
      setGenreOptions(genres.map(x=>({value: x.list_name_encoded, label:x.display_name})));
    
    })();

  }, []);

  useEffect(()=> {

    (async ()=>{
      
      setBooks(await getBooks(genre));
    })();

  }, [genre]);

  if (books) {
    return (
      <>
      <div class="select">
        <Select  options={genreOptions} onChange={(selectedOption)=>{
          setGenre(selectedOption.value);
        }}/>
      </div>
      <BookGrid books={books.books}/>
      </>
      );
  }
  else {
    return (<></>);
  }
}
```

![](../.gitbook/assets/image%20%28288%29.png)

### 

### Homework

You should do a git pull from the main branch prior to stating the homework.

The assignment is to build a component that works similarly to the NYT Books component that I  demoed in class, but create a component that gets a list of products from the fakeproductapi.com API.

Here's the code for the NYTBooks component. It is also in the repo at front-end/src/containers/NYTBooks.

```javascript
import React, {useState, useEffect} from 'react';

import './NYTBooks.css';
import {getBooks} from '../../api/nyt';
import BookGrid from '../../components/BookGrid/BookGrid';

function NYTBooks() {
  
  const [books, setBooks] = useState(null);

  useEffect(() => {
    
      (async () => {
        setBooks(await getBooks('hardcover-fiction'));
      })();

  }, []);


  if (books) {
    return (
      <>
      <BookGrid books={books.books}/>
      </>
      );
  }
  else {
    return (<></>);
  }
}

export default NYTBooks;
```

This function calls into the webAPI defined in the api/nyt.js file. There is an equivalent file in the api directory for retrieving the products through the fakeproductsapi.com, in fakeproducts.js. 

It would teach you more if you first tried to create the getProducts function in your component to retrieve the products. You should get used to looking through the documentation for a web API to figure out how to call their API.

{% embed url="https://fakestoreapi.com" %}

On their site, it shows the list of endpoints that you can call. So you call [https://fakestoreapi.com/products](https://fakestoreapi.com/products) to retrieve all of the products. To make a web API call, you need to use the axios module. Look in the api/fakeproducts.js file to see how the call is made after you've given a shot to building the equivalent function on your own.

![](../.gitbook/assets/image%20%28157%29.png)

Create your component in the practice/\[your-initial\] folder and include it in your top-level component so it will render when you click your initial on the nav bar.

For your component, you can create any child components in the same file.

#### Extra Challenge

Extend your component to have a drop-down list like the BooksAPI in my practice folder. I demoed this in class as well. The extension adds another useEffect call, so there are two:

* one to retrieve the list of product categories
* one to retrieve the list of products for the selected category.

As the BooksAPI demo showed, you have to make sure that the one to retrieve the list of products is triggered on a change to the selected product category.

