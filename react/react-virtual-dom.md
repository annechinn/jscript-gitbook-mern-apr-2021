# React Virtual DOM

How does React update the DOM on every state change? How can we continually refresh the DOM without destroying our applications responsiveness and performance? 

With React you don’t manipulate the DOM directly. React uses a fast in-memory virtual DOM to record all your state changes, does a _diff_ to calculate the minimal number of changes needed to bring your UI up to the latest state, and executes them for you. 

So how does React know what has changed, and thus, what to update? Anytime React's setState function is called within a component to update the state, it is considered dirty and React will check to see what in the DOM needs to be updated.  To do this, React will call the component’s render\(\) method to determine how it should be rendered, compare that to what’s actually in the DOM at the time, and reconcile any differences for you.

![TechTalk\_BAnderson\_11052014\_Image7](https://techblog.constantcontact.com/wp-content/uploads/2014/11/TechTalk_BAnderson_11052014_Image7.png)

React’s diffing uses a fine-grained diffing algorithm to isolate and operate on only the minimal set of changes that need to happen. So instead of reloading an entire element, it will update only those specific attributes, nodes that require updating.

The big takeaway from how this works is that developers are able to express in a _declarative way_ what the UI should look like at any point in time, and React makes it so. This is a huge improvement in how web applications are written.

{% embed url="https://programmingwithmosh.com/react/react-virtual-dom-explained/" %}

