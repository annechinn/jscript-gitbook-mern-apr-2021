# JavaScript on the Server

### JavaScript on the Server

There are two main types of requests a server gets from a client and they are each handled by separate entities. As a web developer, we write code to build a Web API.

**Web Server** - The job of a web server is to  respond to **file requests**, such as an HTML Page, an image, or a PDF document. A web server is a separate application that is not the responsibility of the developers building a web site. IIS \(Internet Information Services\) is a web server provided by Microsoft. A web server is responsible for hosting a web site and responding to requests for web documents. 

**Web API** - The job of the Web API is to respond to **data requests**. A back-end developer will build a set of endpoints \(the URL the client uses to communicate\) that your JavaScript code can call to send and retrieve data for the site.  There are many web sites that publish a public Web API that can be used by any web application. For example, Google Maps, Twitter,  and the NY Times are just a few companies that have a public API. 

Below is an example of calling the NY Times public Web API. It allows you to retrieve information about top stories.

Data returned from a Web API call is returned in a format called JSON \(JavaScript Object Notation\). It will be very familiar to you as you become familiar with JavaScript, as it is the same format that JavaScript uses for objects.

{% embed url="https://api.nytimes.com/svc/topstories/v2/arts.json?api-key=5Vd8O8baGS3WEG1eQVAaS2mG6K0VyHH8" %}

#### Implementation of Web API

When building the Web API, a development team will decide on the set of technologies to use. There are lots of choices. As an example, outside of our MERN Stack, Microsoft has a set of technologies that are often used together to build a Web API, including .NET Core, Entity Framework Core, and SQL Server.

 For our purposes, since this is a MERN Stack course, we'll focus on how a Web API is built using the technologies in the MERN Stack.



