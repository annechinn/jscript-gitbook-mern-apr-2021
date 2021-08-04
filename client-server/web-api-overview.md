# Web API Overview

A Web API is just an programming API that work across the web, between a client and server. They rely on the HTTP protocol for their communication.

**REST** stands for **RE**presentational **S**tate **T**ransfer. It is an architectural model to organize interactions between independent systems. RESTful applications commonly use HTTP requests to post data \(create and/or update\), read data \(e.g., make queries\), and delete data. 

**HTTP** \(hypertext transfer protocol\) - allows to systems to communicate, even if they are not in the same place.

The protocol relies on the concept of a client and a server. The client generates a request as an URL in their browser. The server's job is to receive the request, process it accordingly, and then send back the response to the client. The client receives the response and renders it within the browser.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages" %}

The request contains, header, verb: GET, POST, PUT, DELETE, optional body section, can send data to the server for processing

The response contains header, status,  body.

### HTTP Verbs

Http requests used for web APIs are built on four verbs:

**GET** - GET requests are the most common and widely used methods in APIs and websites. Simply put, the GET method is used to retrieve data from a server at the specified resource. For example, say you have an API with a /users endpoint. Making a GET request to that endpoint should return a list of all available users.

**POST** - POST requests are used to send data to the API server to create or update a resource. The data sent to the server is stored in the request body of the HTTP request. The simplest example is a contact form on a website. When you fill out the inputs in a form and hit Send, that data is put in the body of the request and sent to the server and a new record is created.

**PUT** - Similar to POST, PUT requests are used to send data to the API to update or create a resource.

**DELETE** - The DELETE method is exactly as it sounds: delete the resource at the specified URL.

### HTTP Status Codes

All requests you make have their HTTP status codes. There are a lot of them and they are divided into 5 classes. The first number indicates which of them a code belongs to:

* **1xx** - informational
* **2xx** - success \(200 - OK\)
* **3xx** - redirection 
* **4xx** - client error \(403 - Forbidden, 404 - Not Found\)
* **5xx** - server error \(500 - Internal Server Error\)

### CRUD

The four HTTP verbs have been mapped to the acronym CRUD \(Create, Read, Update, and Delete\). The CRUD acronym identifies all of the major functions that are inherent to relational databases and the applications used to manage them,  such as Microsoft SQL Server, MySQL, and others.

**CREATE** - The create function allows users to create a new record in the database. In the SQL relational database application, the Create function is called INSERT.

**READ** - The read function is similar to a search function. It allows users to search and retrieve specific records in the table and read their values. Users may be able to find desired records using keywords, or by filtering the data based on customized criteria.

**UPDATE** - The update function is used to modify existing records that exist in the database. To fully change a record, users may have to modify information in multiple fields.

**DELETE** - The delete function allows users to remove records from a database that is no longer needed.

### Web APIs

The CRUD model works very well to simplify the building of web APIs that present a simple mapping of database tables to a web API. 

The model is based on performing the specific set of CRUD actions on a database resource. The naming conventions for resources in a RESTful API should be noun-based: "orders", "customers", "products", etc. The basic operations we perform on these resources are defined by the HTTP verbs: GET, POST, PUT, DELETE.

 It has resulted in a huge ecosystem of public web APIs that are easy to understand and web frameworks allow you to quickly create your RESTful APIs.

| CRUD | HTTP Verb | URL | Description |
| :--- | :--- | :--- | :--- |
| Read | GET | /api/order | Returns all order |
| Read | GET | /api/order/3 | Returns order \#3 |
| Create | POST | /api/order | Creates new order |
| Update | PUT | /api/order/3 | Updates order \#3 |
| Delete | DELETE | /api/order/3 | Deletes order \#3 |
|  |  |  |  |

### Beyond CRUD

But the CRUD model is not the only way to create a web API, and is sometimes criticized in the development community that advocates for "Design Driven Design". The complaint is that treating your web API as a shallow layer around your database tables does not allow you to represent the complexity of a large application that has complex operations, workflow involved.  To handle these cases, there is a need to extend the API to incorporate specific actions. Actions often include more complex data than a single object.

One approach is to use CRUD for the read, or query operations, and then create RPC-based APIs for the more complex actions. An RPC \(remote-procedure-call\) -based approach is more flexible, in that the web API can define a unique URL that typically includes the action, rather than the object, and more complex data can be supplied that would be more typical of how a local function would be called \(multiple parameters\).

For the purposes of our initial introduction to web APIs, we'll limit our use to CRUD.



### Resources

#### Install JSON View Chrome Extension

To make it easier to view the data returned from the API call, it is a good idea to install the Chrome Extension JSON View, which will format the data and make it easier to read.

To install a Chrome extension, go to More Tools=&gt;Extensions and search for JSON View and install the extension.

{% embed url="https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en" %}

{% embed url="https://www.postman.com/downloads/" %}

{% embed url="https://learning.postman.com/docs/sending-requests/requests/\#configuring-request-headers" %}



{% embed url="https://www.youtube.com/watch?v=s7wmiS2mSXY&t=129s" %}



{% embed url="https://www.youtube.com/watch?v=Q-BpqyOT3a8" %}



