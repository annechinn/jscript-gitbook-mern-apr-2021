# Week 12 - Saturday, July 3rd

### Class Video

{% embed url="https://www.youtube.com/watch?v=JTFytl0dJd0" %}

### React Router

We reviewed how to use react-router-dom to set up links and route paths \(URLS\) to particular components.

{% embed url="https://reactrouter.com/web/guides/quick-start" %}

### React State Management

We created components for each news section and learned to use useState to store the articles returned from the back-end web API for retrieving articles.

We also learned how useEffect is used to call asynchronous functions.

We reviewed the code within the ArtsSection component that renders a grid of cells that change their background color and box shadow styles when the user's mouse moves over and away from a cell.

This exercises demonstrated how to modify state data when it is an array so that React will detect that a change in the data has occurred.

React just compares the state variable before and after the call to set the state has been called. For an array or an object, if you change an array element, or change an object property, React will not detect a change because it is just using the equality === operator to check and the array or object has changed. You must create a new array/object and repopulate it with the old data, plus any changes, for React to detect a change in state.

{% embed url="https://dev.to/andyrewlee/cheat-sheet-for-updating-objects-and-arrays-in-react-state-48np" %}

### Homework

Before you start, make sure you have done a pull from the main branch, as I have pushed changes you will need to do this assignment. Create a new branch to work on this assignment.  I think some of you may have branches that are not committed. If you want some help getting your repo in shape, just let me know.

I want you each to follow the example I created for adding a link on the NavBar to a component that you can use to practice building some small components.

In front-end/src/practice, I created a folder named "ac", and within that folder I created another folder named "ACPage". The ACPage folder is for a top-level component that I have linked to the NavBar item "AC". So when I click on the "AC" link on the NavBar, the ACPage component will be rendered. 

To do this, you will need to make modifications in NavBar.js and App.js.

In the ACPage component, I can then add any components that I want to build and test out. 

So your first step, is to duplicate that structure for your own component, so that we each have a link on the NavBar that is linked to a component in the practice folder. 

For example, the first component that I want you to build is a component called PriceCheck. So you will create a new component in your folder, and then include that component as a child of your top-level component.  You can continue to include additional components as children of your top-level component so that they will always be displayed when you click on your initials on the NavBar.

#### PriceCheck component

I want you to build a component that simulates a checkout screen on an e-commerce site. The example below, from amazon, shows the item that I have in my cart and a dropdown list under the item with the quantity I want to purchase. When I change the quantity, then the subtotal over on the right updates to say how many items and the total price. 

![](../.gitbook/assets/image%20%28372%29.png)

For your control, you will display the image, and below the image a price \(sorry, I forgot that in my demo below, but you should include it\), and a dropdown that allows you to select a quantity between 1 and 3. 

To the right, you will display the Subtotal display, like the one on amazon. It should have the same format: 

**Subtotal \(num items\) cost.**

Use this URL for the img src. [https://m.media-amazon.com/images/I/71ijdc+5X+L.\_AC\_AA220\_.jpg](https://m.media-amazon.com/images/I/71ijdc+5X+L._AC_AA220_.jpg). 

![](../.gitbook/assets/image%20%287%29.png)

You can create a const variable to hold the price with a value of 32.99.

You will need to create a React state variable to store the quantity, and then pull that in your render function to build the Subtotal display.

Here is my example:

![](../.gitbook/assets/image%20%28279%29.png)

There is a component that I installed for the select, called react-select. I've shown enough below for you to be able to use it.

```javascript
// import the select component
import Select from "react-select";

// set up values to display in the select dropdown
 const options = [
    { value: "1", label: "1"},
    { value: "2", label: "2"},
    { value: "3", label: "3"},
  ];
  
  // in your render function, use the component
  // as follows:
  
  <Select options={options} onChange={(event)=> {
            ... add your code here
        }} />
```

Create a new branch for your work and push it to the github repo when you are done.

