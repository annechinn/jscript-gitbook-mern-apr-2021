# The DOM

Once your JavaScript function has been called in response to an event, the function will carry out whatever instructions it needs to do to generate the new HTML content it wants to update on the site. As an example, this could include communicating with the back-end server to retrieve the data for the comments section of an article page. And then it uses the DOM API to programmatically modify the in-memory representation of the live HTML page to insert a new section that contains a list of comments and new HTML elements to interact with those comments, such as buttons to add a new comment or reply to an existing one.

![](../.gitbook/assets/image%20%28222%29.png)

In the early days, when JavaScript was first introduced, developers had only one option. They worked directly with the DOM API that was published for each individual browser. Unfortunately, the APIs were not consistent across the different browsers and so it was a chore to build web sites that worked across all browsers.

#### jQuery

In 2006, a JavaScript library called jQuery was created and became hugely popular because it standardized the way to interact with the DOM across different browsers. It also had a very powerful query language to find elements in the DOM you wanted to manipulate. Web developers were still required to interact with the DOM directly, but jQuery made their job easier. But it was still a chore to work with the DOM directly, as it required programmers to modify the HTML with a programming API rather than specifying the modified HTML in a declarative way as we do when editing an HTML document.

### Application Libraries/Frameworks

The job of updating the content of a live HTML page got a whole lot easier with the release of the first front-end framework, AngularJS in 2010. Since then there has been huge growth in the number of front-end frameworks available, including the latest version of Angular, React and Vue.js. One of the biggest changes was that web developers rarely needed to interact with jQuery or the DOM API directly anymore because the libraries and framework provided a layer of abstraction and the task of manipulating the DOM fell to the framework rather than the web developer.

### JavaScript Front-end RoadMap

It is important for JavaScript front-end developers to understand what the DOM is and how to use the DOM API, but it is likely that you will be using an application framework, such as React, to build your web sites.

