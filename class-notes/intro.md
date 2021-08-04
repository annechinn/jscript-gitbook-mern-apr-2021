# Week 11 - Wednesday, June 30th

### Class Video

{% embed url="https://www.youtube.com/watch?v=mvuULNZPCEo" %}

### Pre-requisites to Using React

### Modules

#### Why We Need Them

Let's look at an example of why we need modules. We initially had this problem when we were practicing coding challenges. Everyone was naming their variables the same and there were name collisions.

```markup
<body>
  <script src="scripts/script1.js"></script> 
  <script src="scripts/script2.js"></script>
</body>
```

```javascript
// script1.js

const nums = [1,2,3,4,5];
let total = 0;
nums.forEach(x=>total+=x);
const average = Math.floor(total/nums.length);
```

```javascript
// script2.js

const nums = [1,2,3,4,5];
let total = 0;
nums.forEach(x=>total+=x);
const average = Math.floor(total/nums.length);
```

![](../.gitbook/assets/image%20%2857%29.png)

The way we solved it, was to use **IFFEs**, or immediately invoked function expressions. A function has a private scope. All of the variables declared within the function are only visible within the function. Before there were modules in JavaScript, developers used IIFEs to wrap the code within a file.

```javascript
(()=> {

  const nums = [1,2,3,4,5];
  let total = 0;
  nums.forEach(x=>total+=x);
  const average = Math.floor(total/nums.length);

})();
```

If you needed to expose some functionality from a file, then you would create another file, and create a global variable there, such as APP, and then assign those variables, functions that you wanted to "export" from your files to the APP object.

```javascript
// app.js

let APP = {};

(()=> {

  function otherPrivateStuff() {
    console.log("hello");
  }

  APP.getAverage = (marks) => {
    let total = 0;
    marks.forEach(x=>total+=x);
    return Math.floor(total/marks.length);
}

})();
```

```javascript
console.log(APP.getAverage([1,2,3,4,5]));
```

```javascript
// APP.otherPrivateStuff is undefined

console.log(APP.otherPriateStuff());
```

#### ES6 Modules

{% page-ref page="../other/modules.md" %}

### 

### Destructuring

{% page-ref page="../other/destructuring.md" %}



### What Is React?

React is a UI library for building user interface components. It was developed by Facebook in 2011 and is now an open-source project on GitHub. It is currently the most popular front-end framework/library for building web applications.

Here is the definition from the React.js website.

> React is a library for building composable user interfaces. It encourages the creation of reusable UI components which present data that changes over time. - React.js

{% embed url="https://reactjs.org/blog/2013/06/05/why-react.html" %}

### What React Does Really Well

Other front-end frameworks build web apps through composable components. What really sets React apart are two innovations:

#### State Management

React introduced a very simple conceptual model of how to envision binding a component's state to its view. 

Previously, the developer would be responsible for figuring out exactly what in the DOM needed to be updated, based on a change in state through a user event. 

With React, the developer just needs to declare the HTML markup that represents the fully rendered component, inserting state from the store, and React will figure out when and what needs to be updated in the DOM to reflect the changes. 

At first, this would appear problematic, as it would be extremely slow to update the DOM with the entire component's HTML on every little change in state. But React creates a Virtual DOM, which is its own representation of what needs to be changed in the UI, and it does a diff between its version and the real DOM and only updates what is different.

The ability to just visualize what the component's HTML should render, and  not work about what specifically needs to be updated in the DOM when the component's state changes, is a huge advance in simplifying the job web developers have to do.

React introduced a single way to manipulate a component’s state:  events update the state in the store. When the store state changes, the store will ask the component to re-render and React will only update the DOM with the minimal changes necessary.

![](https://miro.medium.com/max/700/1*lNLcKqywLkrHadcA-zhgBA.png)

#### JSX

React also introduced a language that allows the component's view to be rendered in a declarative way \(with markup instead of an API\) and insert JavaScript expressions within the markup to pull state from the store and add dynamic content.

In other frameworks, such as Angular, you have to modify the component's view in a template HTML file, and use special syntax, such as ng-repeat, to insert dynamic content. In React, you just need to know JavaScript and all of the functions, such as Array.map, filter, that you are familiar with.

### What React Doesn't Do

React is called a "library" vs. a "framework" because it is very focused in what it does. It handles rendering the HTML for a UI component based on changes in the state of the component.

It doesn't have any support for the following:

| Technology | Sample Third-party Option |
| :--- | :--- |
| fetching data through http | axios, fetch |
| routing | react-router |
| styling | styled-component |
| modules | ES6 modules |

In contrast, Angular is a "framework", because it has a very large suite of functionality that you get when you use it.  Angular enforces a structure to how applications are built, and for large applications, this can help with the complexity.

{% embed url="https://daveceddia.com/what-react-does/" %}

### Main React Concepts

We'll be breaking down learning React into four main concepts. Today we'll focus on how you define components.

* Components
* State Management
* Fetching Data
* Routing

### Creating and Running React Applications

#### Test App

If you just want to try out React in a small test environment, the cloud-based apps, such as [stackblitz.com](http://stackblitz.com) are an easy way to do so. Just go to the site and select the React w/JavaScript option.

![](../.gitbook/assets/image%20%28275%29.png)

#### Local App

When you want to create a React app to run on your local computer, you use a program called  **create-react-app**. It can be launched through npm, without having to download the package with the following command.

```css
npx create-react-app [app-name]
```

Running this command will create a folder with the name \[app-name\] in the current directory and populate it with a starter React application. It will download all of the packages needed to launch a react app.

React applications are different than the applications we have been building so far. For those, we just launch the index.html file in the browser. 

For a React application, there is a bunch of pre-processing that has to happen prior to the application being able to run.  

For example,

* ES6 JavaScript is converted to JavaScript that will run in all browsers
* Static files are bundled up for efficient delivery. 
* Process stylesheet pre-processors, such as SASS.

These tasks are all coordinated by something called webPack through a module called react-scripts.  You can take a look at the file in node\_modules/react-scripts/config/webpack.config.js. 

One of he downsides of all of the file bundling, is that the source code is no longer in separate files, and so it is much more difficult to find your code int he bundled file. 

There is a way to override some of the webPack configuration, and I have set up our project to create source maps, which are mappings between the bundled file, and an individual file, so that we can work with individual files when we are in the Chrome Developer Tools. 

You will need to enable source maps within the Chrome Developer Settings. To bring up the settings, click on the gear icon in the upper right of the Inspect window.

![](../.gitbook/assets/image%20%28309%29.png)

Then, make sure the "Enable JavaScript source maps" is checked.

![](../.gitbook/assets/image%20%28395%29.png)

Just like the back-end Node.js application, the front-end React application must also be launched in a special way to get the process started.

To start a React application you run the following command in the project directory. 

```css
npm start
```

#### Added front-end React application to news-site-collab repo

I have created a react app within the news-site-collab repo. I removed a few files that aren't necessary for our purposes, and added a few folders for organizing the project. Similar to the back-end project, the front-end also has a packages.json, that is a registry for the packages included in the project, and a node\_modules folder to hold all of the packages the app requires. All of our code for the React components we build will go in the src folder. The assets folder will contain all assets, such as images and videos.

![](../.gitbook/assets/image%20%28167%29.png)

### 

### Component-based Development

A core concept in React is component-based development. Component-based development is an important abstraction that is central to software development. Dividing sections of the UI into components, is similar to how functions breakdown the source code into manageable chunks. Both result in the following benefits:

* isolated - easier to understand, modify, test
* reusable - minimize repetition
* composable - build larger things out of smaller things.

In a React application, you build individual components that form the building blocks of your site. Every React site has a root component, called the App component, and the App component is made up of a hierarchy of  other components.

![](../.gitbook/assets/image%20%28128%29.png)

![](../.gitbook/assets/image%20%28109%29.png)

### Dynamic Composition

The components can change, based on the users' interaction with the site. For example, if the user clicks on the NavBar, and chooses a different section, then an entire portion of the component tree can be switched out.

Let's say there was a link on the NavBar for NYT Books. When the user clicks on that link, the NYTBooks component tree would replace the Home component tree in the overall component hierarchy.

![](../.gitbook/assets/image%20%28442%29.png)

![](../.gitbook/assets/image%20%28329%29.png)

### First React App

Let's start exploring React with a simple example in [stackblitz.com](http://stackblitz.com). Create a React/JavaScript application.

There are three critical files to understand:

#### Index.html

Just like we have been doing in our dynamic HTML projects, there must be an element in the HTML document where the rendered content will be inserted.

```markup
<div id="root"></div>
```

#### Index.js

This script is the entry point into initiating the React rendering process. 

The ReactDOM render method renders the React element tree returned from the React App component \(the root component of the component hierarchy\) into the DOM in the supplied container.

```javascript
import React from "react";
import ReactDOM from "react-dom";

import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

#### App.js

Every React component maps directly to a function with the same name.  The function must return the HTML markup for the component.

React supports a special language called JSX \(JavaScript XML\), which allows the component function to express its return value in a **declarative** manner \(looks like the HTML markup you want to render on the screen\). 

It also allows the insertion of JavaScript expressions into the markup, similarly to how a JavaScript expression can be inserted into a JavaScript string literal. A slight difference: you don't use the $ before the braces surrounding the expression.

```javascript
import React from "react";
import "./style.css";

export default function App() {
  return (
    <div>
      <h1>Hello World!</h1>
      <p>Today is {new Date().toDateString()}</p>
    </div>
  );
}
```

Behind the scenes, a compilation step takes place, that translates the JSX to JavaScript calls into the React API to create a hierarchy of React elements. They look very similar to the DOM API.

```javascript
function App() {
  return React.createElement("div", null, 
            React.createElement("h1", null, "Hello World!"), 
            React.createElement("p", null, "Today is ", 
                              new Date().toDateString())
          );
}
```

#### 

### Nested React Components

As we saw earlier, a web page is made up of components laid out in a nested “tree” structure. Just like HTML elements can contain other elements, React components can contain other React components \(and native elements like div and button\). But these nested React components are functions.

Let's add a nested component, named Greeting, to our App component.

```javascript
function Greeting(props) {
  return (
    <h1>Hello World!</h1>
  )
}
export default function App() {
  return (
    <div>
      <Greeting/>
      <p>Today is {new Date().toDateString()}</p>
    </div>
  );
}
```

The JSX code returned from the App function contains an embedded React component. During the translation from JSX to React API calls, the Greeting component will also be translated to React API calls.

```javascript
function Greeting(props) {
  return React.createElement("h1", null, "Hello World!");
}

function App() {
  return React.createElement("div", null, 
                React.createElement(Greeting, null), 
                React.createElement("p", null, "Today is ", 
                        new Date().toDateString()));
}
```

One thing to notice is the Greeting **function declaration** is passed to the React createElement function. It will be invoked at a later time by React, when it needs to render the HTML for the component.

### Component Parameters - Props

Just like regular functions, React component functions can accept data through a single object parameter conventionally called "props". The prop data object is created and passed to the function by React \(similar to how the web browser passes an event object to event handlers\). 

It is an object that contains a property for each attribute name/value pair on the component.

For example, we can extend our Greeting component to accept two properties, name and occupation.

```javascript
function Greeting(props) {
  return (
    <>
    <h1>Hello World! My name is {props.name}.</h1>
    <p>I am a {props.occupation}</p>
    </>
  )
}

export default function App() {
  return (
    <div>
      <Greeting name="Anne" occupation="software developer"/>
      <p>Today is {new Date().toDateString()}</p>
    </div>
  );
}
```

{% hint style="info" %}
React component functions must return a single React element. The "&lt;&gt;" and "&lt;/&gt;' elements at the beginning and end of the JSX is a construct that forces a single element to be returned. It is a common pattern to always place these surrounding the JSX you return.
{% endhint %}

The can access the individual properties as property values of the props object. Another technique is to use **ES6 object destructuring** to create individual parameters for each property you want to use.

Object destructuring allows you to pull out multiple object properties into local variables in a single instruction.

```javascript
const {name, occupation} = props;
```

In the context of a React component function, you can use destructuring as follows:

```javascript
function Greeting({name, occupation}) {
  return (
    <>
    <h1>Hello World! My name is {name}.</h1>
    <p>I am a {occupation}</p>
    </>
  )
}
```

### 

### Migrating our News Site to React

Earlier in the course, we completed a lab \(labs/news-homepage\) that built a static site for an online newspaper home page. This version didn't include any JavaScript, and the articles were all hard-coded, i.e. each one was manually entered in the HTML markup.

We had a single index.html file, and a corresponding style.css file.

We're going to go through the process of migrating this page into our React application with multiple components that represent the different sections of the page.

This diagram outlines the initial React components that we will create.

![](../.gitbook/assets/image%20%28374%29.png)

#### Add the initial HTML/CSS to the App component

To start off, I've added all of the HTML from index.html into the App.js file and all of the CSS from styles.css into the App.css file. Our job is to incrementally move the code from these files into component files.

#### Exporting/Importing components

Each React component file will export the component function as the default export for the file. For example, the App component file is exporting the App function at the bottom of the file.

```javascript
function App() {
  return (
    <>
    <main>
     ...
    </main>
    </>  
  );
}

export default App;
```

The App component file can then be imported with an import statement.

```javascript
// index.js

import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

#### Importing Image Paths

In a React application, there is a process that prepares the code to run. For example, the JSX code needs to be translated to JavaScript by the Babel compiler. There are also steps that package up all of the static resources into a single bundle for more efficient delivery. This is done by something called [WebPack](https://webpack.js.org/). One of the ramifications of this, is that local image paths are not the same as the deployed image paths, so the mechanism by which you refer to the src for a local image file is different.

You must use an import statement to retrieve the image path and use that value in your img elements. 

```javascript
// import the image path
import logo from './assets/logo.png';

// used later in an img element
<img src={logo} class="logo" alt="logo" />
```

#### Importing Stylesheets

You use the import statement to include stylesheets in your file.

{% embed url="https://create-react-app.dev/docs/adding-images-fonts-and-files/" %}

```css
import './App.css';
```

#### Converting class to className

class is a reserved word in JavaScript, so React requires that you use the term className wherever you used the term class.

#### Project Directory Structure

Developers working on React projects tend to organize their project structure following some standard conventions. The convention that I have chosen for this project is this one.

{% embed url="https://daveceddia.com/react-project-structure/" %}

There will be two folders dividing presentation components \(components\) from container components \(container components\). 

**Containers/Stateful Components** are the components which have a direct subscription to the state of the app, likely a store. These components have access to the values in the state and can trigger changes to the state.

**Presentational/Stateless Components** are the components who have an indirect access/subscription to the state of the app. They are used only to display information passed through props and cannot trigger any change to the state directly.

In our site, the ShowcaseArticle and ArticleCard components are presentation components, whereas the Header, NavBar, Home, Footer and  ArticleGrid are container components.

For each component we will create a folder named the same as the component, and it will contain the component file, as well as the CSS file.

![](../.gitbook/assets/image%20%28207%29.png)

For each component, move the code from the App.js file into the component JavaScript file, and the code from the App.css into the component CSS file. Then replace the code in App.js with the  component element and add an import statement to include the component module.

When the process is complete, the App.js file will look like the following:

#### App.js

```javascript
import React from 'react';
import './App.css';

import Header from './containers/Header/Header';
import Footer from './containers/Footer/Footer';
import Home from './components/Home/Home'

function App() {
    return (
        <main>
             <Header/>
             <Home/>
             <Footer/>
        </main>
    );
}

export default App;
```

#### App.css

```javascript
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");

html {
  --primary-color: #c72727;
  --light-color: #f3f3f3;
  --dark-color: #333;
  --link-color: #333;
}

body {
  font-family: "Poppins", sans-serif;
  background-color: var(--light-color);
}

a {
  color: var(--link-color);
  text-decoration: none;
}
```

And here are a few examples of the components pulled out of the App component.

#### Header.js

```javascript
import React from 'react';
import './Header.css';
import logo from '../../assets/logo.png';

import NavBar from '../NavBar/NavBar';

function Header() {
  return (
    <header>
       <a href="index.html">
        <img src={logo} class="logo" alt="logo" />
      </a>
      <NavBar/>
    </header>
    );
}

export default Header;
```

#### Header.css

```css
main header {
  background-color: #fff;
  padding: 18px;
  display: flex;
}

/* this style centers the logo image within the anchor */
main header > a {
  display: flex;
  justify-content: center;
  align-items: center;
}

header .logo {
  width: 180px;
}
```

#### ArticleGrid.js

```javascript
import React from 'react';
import './ArticleGrid.css';
import ArticleCard from '../../components/ArticleCard/ArticleCard';

function ArticleGrid() {
  return (
    <section class="articles">
        <ArticleCard
          topic="science"
          imageURL="https://images.pexels.com/photos/130621/pexels-photo-130621.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>

        <ArticleCard
          topic="food"
          imageURL="https://images.pexels.com/photos/6529912/pexels-photo-6529912.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>

        <ArticleCard
          topic="sports"
          imageURL="https://images.pexels.com/photos/863988/pexels-photo-863988.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=50"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>

        <ArticleCard
          topic="arts"
          imageURL="https://images.pexels.com/photos/256189/pexels-photo-256189.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>
    
        <ArticleCard
          topic="sports"
          imageURL="https://images.unsplash.com/photo-1551524559-8af4e6624178?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8c25vd2JvYXJkZXJ8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>
       
       <ArticleCard
          topic="science"
          imageURL="https://images.unsplash.com/photo-1453847668862-487637052f8a?ixid=MnwxMjA3fDB8MHxzZWFyY2h8Mnx8c2NpZW5jZSUyMHNrdWxsfGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
          title="Lorem ipsum dolor sit amet."
          abstract="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
          impedit libero, beatae animi provident nesciunt molestias ipsam nemo
          ad."/>
      </section>
    );
}

export default ArticleGrid;
```

#### ArticleGrid.css

```css
.articles {
  display: grid;
  grid-template-columns: 1fr;  
}

@media screen and (min-width: 600px) {
  .articles {
    display: grid;
    grid-gap: 16px;
    grid-template-columns: 1fr 1fr 1fr;
  }
}
```

### 

### React State Management - Data-binding

The connection between the component's logic \(variables\) and the data that is displayed on the screen is called data-binding. 

![](../.gitbook/assets/image%20%28166%29.png)

When you "bind" a variable in your component's logic to an element in the view, you are telling the framework to watch the variable for changes. If changes are detected, the framework takes care of updating the view accordingly.

When React was first introduced, and provided automatic one-way data-binding, from a central store of state, it was a groundbreaking advance. With vanilla JavaScript, or even libraries like jQuery, it is up to the developer to update the view and the DOM acts as the central state of the application.

What prompted Facebook to design React was the problems they were having integrating their chat feature into their app. There were multiple different components within the site that exposed aspects of the chat feature, all needing to be kept in sync when things changed in any of the components and some changes were coming in asynchronously from the back-end as data from other users needed to update the current state/view. There was no way to guarantee the state of the UI at any point in time.

DOM race conditions were one of the most common bugs in early web applications. As the complexity of a web application grows, the process of updating the DOM becomes increasingly difficult to manage, as the various event handlers are all independently modifying the DOM. This leads to bugs and unpredictable behavior.

![Unidirectionaldataflow-2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603797044830/sPUPllSHX.png?auto=compress)

### React - Unidirectional Data-binding

React was designed to support one-way data-binding, flowing from the component to the view.

React's architecture enforces a single source of state for each component, or a collection of related components. To have React manage state within your component, you must use special functions \(hooks\) for telling React which variables you want it to manage, and for initializing and updating them.

Once the state variables are being managed by React,  the web developer doesn't need to be concerned with whether a state change should trigger an update to the UI. 

The web developer just needs to build the declarative JSX that incorporates the current state into the HTML. 

React is responsible for calling the component's render function when a state change occurs. Whenever we tell a React component to change its state, the component will automatically re-render itself. 

![](../.gitbook/assets/image%20%28147%29.png)

### How to Have React Manage State

Let's start with a simple example. Our page sets the background color to the value of a state variable.

React has what are called "hooks" that are special functions that you call to setup the state that you want React to manage. The **useState** function returns an array. The first element is the variable that will be managed, and the second is a function that you must use to update the value of the variable. 

In the example below, array destructuring is used to extract out the two values in the array into independent variables.

{% hint style="info" %}
Note, the style attributes takes an object, which contains any of the properties you would normally set in your CSS file. So, the inner {} is the object, while the outer brace is the JavaScript evaluate syntax.
{% endhint %}

```javascript
export default function App() {
  const [color, setColor] = useState('lightgrey');

  return (
    <div>
      <h1 style={{color:color}}>Hello World!</h1>
     </div>
  );
}
```

![](../.gitbook/assets/image%20%28159%29.png)

If you change the initial value passed to the **useState** function, you will immediately see that change reflected in the view. That is React reacting to the state change and re-rendering the view.

```javascript
export default function App() {
  const [color, setColor] = useState('orange');

  return (
    <div>
      <h1 style={{color:color}}>Hello World!</h1>
     </div>
  );
}
```

![](../.gitbook/assets/image%20%28136%29.png)

#### Updating State From UI Events

Your code will need to respond to user interactions. Any interactions that result in updates to the UI need to use the React function that was returned from **useState** to update the value of the variable managed by React.

In this example, we have added an input field on the page to allow the user to type in a new color and an **onChange** event handler to respond to the user typing in the new value.  The onChange event handler calls the **setColor** function to update the value of the color variable managed by React. 

This will automatically trigger React to detect the change and can the render function to update the view.

```javascript
export default function App() {
  const [color, setColor] = useState('orange');

  return (
    <div>
      <h1 style={{color:color}}>Hello World!</h1>

      <input type='text' onChange={(event)=> {
        setColor(event.target.value);
      }}/>
     </div>
  );
}
```

![](../.gitbook/assets/image%20%28451%29.png)

### 

### Homework

Before starting on the process of componentizing the new-site-collab content, I want you to read through this tutorial and do the exercises that are included. Go through it until you reach the section titled "**Fetch Data with React**". We'll cover that in the next class.

{% embed url="https://daveceddia.com/react-getting-started-tutorial/" %}

Next, I want you to to try to go through the steps that I did during class to split up the new-site-collab App.js/App.css content into separate modules.

Create a new branch to work on this. When you are done, push your branch to GitHub. We won't be merging these changes into the main branch, but I will take a look at the code in your branch.

