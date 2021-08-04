# React vs. Angular

Both Angular and React share the concept of breaking the  UI into components to render what is displayed on the screen.  

### Data-binding

The connection between the component's logic and the data that is displayed on the screen is called data-binding.

React was designed for one-way data-binding only, flowing from the component to the view.  This means in React, by default there is no way that a view can change the component’s logic. Only the component’s logic can affect the view.

![](../.gitbook/assets/image%20%28166%29.png)

#### Component to View Data-binding

Here is an example of component to view binding in React. The state within the component is being modified and the view is being automatically updated by React. The view is bound to the data and any changes in the data are immediately reflected in the UI.

This is because React requires that all state be stored in an object that they control and modifications to the state must go through 

![https://soshace.com/understanding-data-binding-in-react-and-angular/](https://soshace-12d3e.kxcdn.com/wp-content/uploads/rcl-uploads/articles/2020/07/2065010.gif)



#### View to Component

React does not allow the view to change or update the component’s logic **directly** but, we can **add event handlers** to the view elements and change the component’s data. 

```javascript
function someComponent() {
  let [inputValue,setInputValue] = useState('');
  let changeValue = (e) => setInputValue(e.target.value);
   
   return (
     <div>
       <input type=”text” onChange={changeValue} />
       <p>Input Value: {inputValue}</p>
     </div>
   );
}
```

Similar to the previous example of component to view, we have bound the value of the input element to the state variable called inputValue. To implement the connection between the view and component, we have attached the onChange event to the input element. This event listens for any changes made to the input element by the user, inside the view. Then, the event calls the function _**changeValue\( \)**_, which sets the _**inputValue**_ variable to the new updated value. To see the change inside the component, we have displayed the value of _**inputValue**_ inside the paragraph element. We can see in the following example, any change made inside the view, reflects in the component:

![Example of View to Component binding in React](https://soshace-12d3e.kxcdn.com/wp-content/uploads/rcl-uploads/articles/2020/07/6710824.gif)

  


#### Angular

Angular followed a design modelled after the template mechanism used to build HTML dynamically on the server, such as with ASP.Net Active Server Pages. The template has sections where dynamic content will be added programmatically. 

![](../.gitbook/assets/image%20%28212%29.png)

In Angular, the HTML template file contains special Angular directives, interspersed throughout the HTML markup, that are used to programmatically modify the HTML that will be rendered. 

```markup
// html inside component's HTML file
<ul id="products">
        <li *ngFor="let product in products">
                {{product.name}}
        </li>
</ul>
```

#### React

In contrast, each component in a React application is contained within a single JavaScript function, rather than an HTML template and an associated JavaScript file. And there are no special directives to programmatically modify the HTML markup. You can use plain JavaScript.  React developed a special declarative language called JavaScript XML \(JSX\) that allows the HTML markup to be visualized and JavaScript can be used to modify the JSX content.

In the sample below, you can see that the dynamic content is using the JavaScript Array.map method.

```javascript
<ul id="products">
        {products.map((product, index) => (
            <li key="index">
                {{product.name}}
          </li>
</ul>
```

### Resources

{% embed url="https://soshace.com/understanding-data-binding-in-react-and-angular/" %}



