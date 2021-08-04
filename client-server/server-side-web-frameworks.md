# Server-side Web Frameworks

Server-side Web Frameworks provide utilities to simplify many of the tasks associated with building responses to requests from the client.

* Map incoming requests \(URLS\) to specific handler functions.
* Access data from the request.
  * query string parameters
  * post data
  * headers
  * cookies
  * authentication/authorization
* Provide an abstraction layer for database access - Object-Relational Mapper \(ORM\)
* Templating services, just as ASP.NET MVC \(for dynamic web apps\)

#### Popular Web Frameworks

* Django \(Python\)
* Flask \(Python\)
* **Express \(Node.js/JavaScript\) - MERN STACK \(React on client\)**
* Ruby on Rails \(Ruby\)
* Laravel \(PHP\)
* ASP.NET \(C\#, VB, etc. - CLR Languages\)
* Spring Boot \(Java\)

### MERN Stack - Web Application Framework

![](../.gitbook/assets/image%20%28195%29.png)

### Node.js - JavaScript Runtime Environment

Node.js is a JavaScript runtime environment that runs on a web server and includes the JavaScript engine built by Google. Prior to Node.js, JavaScript could only run within a web browser. Was mostly used for UI enhancements.

Node.js allows developers to build their server-side web API using JavaScript.

#### JavaScript runtime on the client

![](../.gitbook/assets/image%20%2873%29.png)

#### JavaScript runtime on the server

![](../.gitbook/assets/image%20%28284%29.png)

### Express.js - Library for Routing Web Requests to Handler

Express.js is a JavaScript library that simplifies the process of registering endpoints with the web server so that the requests from your JavaScript code on the client are routed to the correct code within the Web API. 

### MongoDB - Not only SQL Database

MongoDB is a database provider that is used when implementing your Web API using the MERN Stack. Your JavaScript code will use the MongoDB API to store and retrieve data from the database. 

There is an additional technology that MongoDB provides for hosting a database in the cloud, called Atlas. We will be using Atlas to host the database for our sample websites developed in this course.

### Mongoose - Provides Structure/Schema for MongoDB Data

MongoDB does not enforce a schema \(structure\) on the data stored in their database collections. Think of it like the JavaScript array. While it is more typical to store elements of the same type in the array, JavaScript allows you to store different types of data in the same array. The same is true of a MongoDB database. It is up to the developer to determine how to use the data in the array, or database.

Schemas are typically used to ensure the data you are using in your application is structured as you expect and in most cases, web application developers use them with their database data. 

Mongoose is a Object Document Manager for Node.js, which is a library that allows you to define schemas for your MongoDB data, and makes sure your queries are working with the correct data based on those schemas. 

> Mongoose provides a straight-forward, schema-based solution to model your application data. It includes built-in type casting, validation, query building, business logic hooks and more, out of the box.  - From the Mongoose documentation.

### Resources

{% embed url="https://developer.mozilla.org/en-US/docs/Learn/Server-side/First\_steps/Web\_frameworks" %}

