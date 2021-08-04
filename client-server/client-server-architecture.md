# Client-server Architecture

### Overview

What is a web application? 

A web application is a website that is designed to look and feel like a downloadable app. There are different types of applications:

{% embed url="https://developer.mozilla.org/en-US/docs/Learn/Server-side/First\_steps/Client-Server\_overview" %}



#### Static Web Application

With a static web application,  HTML files reside on the server and are requested from the client, either as the top-level page, or through links within the site.

![](../.gitbook/assets/image%20%28332%29.png)

The content is static, meaning that it doesn't change, unless changes are made to the HTML files on the server. The web browser only makes HTTP GET requests to the server to return the HTML document.

The link below is to an example of a static website. 

{% embed url="https://www.berkshirehathaway.com/" %}

Advantages:

* **Cost-effective**: the files just need to reside on the server and the web server configured to return the files when requested.
* **Easy to update**: web developer needs basic HTML/CSS skills.
* **Suitable for small companies** with frequent content updates.

\*\*\*\*

**Dynamic Web Application**

A dynamic web application  allows the page content to be dynamically generated before being returned to the client. Active Server Pages and ASP.NET MVC are two of the early technologies from Microsoft for building dynamic web applications.

![](../.gitbook/assets/image%20%28276%29.png)



The HTML code contains special symbols to indicate where the code that requires server-side processing will insert dynamic content. 

![](../.gitbook/assets/image%20%288%29.png)

This type of site does not require JavaScript on the client to run. JavaScript can be added to add optional client-side interactivity, such as for animation effects, but it is not used to build the dynamic HTML content for the bulk of the page and its data. That is all happening on the server and that data is already built into the HTML page when it is returned to the client.



**Single Page Web Application \(SPA\)**

A single page application attempts to mimic a desktop experience in that there isn't the constant refreshing of the web site when new pages are requested from the server, as in a dynamic web application.

Most major web applications are now single page applications. For example, Gmail, Google Maps, Google Drive, Twitter, Facebook. They all feel like a real application, but on the web.

A single page application creates the illusion of a page change, but you are actually on the same page the entire time you are on the site. The URL is changing as you navigate around the site, even though no new page is being loaded from the server.

For example, when you visit Gmail in the browser, and click on the inbox, outbox, or some mail, the content changes, and the URL also changes, but you do not have the impression that the page is reloading, and it all transitions very smoothly. This is the core advantage of a single page application.

Here's the definition of a SPA from Wikipedia.

> **A single-page application is defined** **as ‘**_a web application or website that interacts with the web browser by dynamically rewriting the current web page with new data from the web server, instead of the default method of the browser loading entire new pages’_

In contrast to dynamic web applications, which required code on the server to dynamically build up the HTML page content, a single-page application requires JavaScript code on the client to build new HTML page content based on user requests that result in new data from the web server being requested.

![](../.gitbook/assets/image%20%28358%29.png)

The mechanism the client JavaScript code uses to communicate with the server is **AJAX**.   AJAX stands for Asynchronous JavaScript and XML.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX/Getting\_Started" %}

With the new architecture, the entire front end is loaded at once on the client-side. This enables the client to send and receive just the data it’s interested in and nothing more. It can send those requests asynchronously via AJAX.

Instead of receiving a full HTML page as a response, the client now gets a JSON representation of the data it requested. It then updates parts of the page that display the new data without having to reload the entire page. 

![](../.gitbook/assets/image%20%28353%29.png)

#### Application Shell

The term single-page might sound confusing at first. What it means is that it’s a shell that defines an overall layout of the application. This layout divides the application into multiple regions, for example header, footer, sidebar, and main content.

![](../.gitbook/assets/image%20%2845%29.png)

Whenever the user attempts to navigate from one part of the application to another, the application determines which region\(s\) needs to be refreshed. It will then swap the view that is currently being displayed in that region with a new view. During the initial load, the client side fetches all views in the application along with the shell. It has to do that because in an SPA architecture, the entire presentation layer is moved to the client side.

Of course the application doesn’t display all of those views at the same time. It will wait for the right conditions to be met before showing a particular view. This mechanism is what enables SPAs to present rich user interfaces without having to retrieve a new page from the server every time the user attempts to navigate to a different part of the application.

#### 

