# Article Summary - JavaScript

### Overview

This is an extra lab, where you can practice forking a repository and then cloning it to a local repo. The lab content focuses on dynamically updating the page based on data.

Below is a link to the GitHub repo in my account.

{% embed url="https://github.com/annechinn/article-summary-js" %}

### Forking a GitHub Repository

You fork a repository when you want to create a copy of someone else's repository in your own GitHub account. There are two use-cases for forking a GitHub repository.

* want to have a private copy of a repository from someone else's account.
* want to contribute to an open-source project.

Once you have forked the repository, it exists in your GitHub account, but does not yet exist on your local computer as a local repository. To do that you would just clone the repository.

For now we'll just use fork as a way to copy a repository from my GitHub account to start a private copy in your own GitHub account.

#### Fork the repo

Click the Fork button in the upper-right of the default page for the repo.

![](../.gitbook/assets/image%20%28439%29.png)

#### View the repo in your account

Now, go to your own GitHub home page and look for the new repo you just forked.

#### Clone the repo

Click the Code button and copy the GitHub URL for the repo.

![](../.gitbook/assets/image%20%28432%29.png)

From the command line, or from within VS Code, clone the repository. If you are doing it from the command line, you need to be in your skillspire directory, and then do the command "git clone \[copied-url\]".

The project has two folders: starter and final. You should work in the starter project, and only use final when you need some help to see the final solution.

#### What we're aiming for

We are going to write JavaScript code to change the color of the buttons and add an event handler that will update the main content of the page with information about the showcase article for the selected topic.

![](../.gitbook/assets/image%20%28406%29.png)

#### Setting up functions to process each topic

This exercise has three data files.

* topics - an array of topic objects that contain data about each topic.
* articles - an array of article objects that contain data about each article.
* authors - an array of author objects that contain data about each author.

There are links between the data files. For example, each topic object has a property called showcaseArticleId. The value is the id of the object in the articles array that is the showcase article for that topic. Similarly, each article object has an authorId that refers to the author object that is the author for the article and a topicId that refers to the topic for the article.

These relationship properties \(fields\) are how data is stored in a relational database. In a database, these objects are referred to as records, or rows in the database table for the type of object.

The image below shows the three database tables that correspond to the three data arrays in our project.

![](../.gitbook/assets/image%20%28430%29.png)

```javascript
const topicsData = [
    { 
      name: 'technology',
      color: '#009cff', 
      title: 'Technology',
      showcaseArticleId: 16
    }, 
    { 
      name: 'science',
      color: '#3bd142', 
      title: 'Science',
      showcaseArticleId: 20
    },
    { 
      name: 'food',
      color: '#d1483b', 
      title: 'Food',
      showcaseArticleId: 8
    },
    { 
      name: 'arts',
      color: '#a66bbe', 
      title: 'Arts' ,
      showcaseArticleId: 13
    },
    { 
      name: 'sports',
      color: '#f99500', 
      title: 'Sports',
      showcaseArticleId: 10
    }
];
```

```javascript
const authorsData = [
  {
    id: 1,
    firstName: 'Sally',
    lastName: 'Smith',
    imageURL: 'https://images.unsplash.com/photo-1579591919791-0e3737ae3808?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=658&q=80'
  },
  {
    id: 2,
    firstName: 'Joe',
    lastName: 'Jones',
    imageURL: 'https://images.unsplash.com/photo-1598198414976-ddb788ec80c1?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=626&q=80'
  }
]
```

```javascript
const articlesData = [
  {
      id: 1,
      title: 'Article 1',
      topicId: 2, // science
      abstract: `Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad.`,
      imageURL: 'https://images.pexels.com/photos/2599244/pexels-photo-2599244.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      body: `Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad. 
      `,
      authorId: 2, // Joe
  },
  {
      id: 2,
      title: 'Article 2',
      topicId: 2, // science
      abstract: `Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad.`,
      imageURL: 'https://images.pexels.com/photos/130621/pexels-photo-130621.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260',
      body: `Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
      impedit libero, beatae animi provident nesciunt molestias ipsam
      nemo ad. 
      `,
      authorId: 1
  },
  // ... articles
 }
```

In our first version of our article grid site, we hard-coded all of the article data in the initial HTML. It was not loaded from a database. But that is not how web pages are typically built. 

The way they are typically built, is JavaScript code retrieves the data from the web server for a particular section of the site and then builds up the HTML dynamically \(programmatically\) and updates the in-memory version of the HTML page.

We're going to start to use this technique to learn how to work with data and build the HTML to update the page for our article grid site. We're going to be using the array methods for finding and filtering the data and string methods for building the HTML to update the page.

#### Build functions to create iterative through topic buttons

First, create some functions to iterate through each of the topic buttons at the top of the page. Once this basic functionality is in place, we can add code to perform specific tasks for each topic button.

The initTopics function uses the topicsData to iterate through each of the topics, and then builds up the id for the topic so we can use that to call document.getElementById to retrieve the button from the DOM.

```bash
function initTopic(topicData) {
  let button = document.getElementById(`${topicData.name}-link`);
}

function initTopics() {
  topicsData.forEach(x=>initTopic(x));
}

initTopics();
```

Next, just to practice working with styles through the DOM, and retrieve data from our topics data, we're going to change the background color of the buttons to have the value that is specified in the color property of the topic.

```javascript
function initTopic(topicData) {
 
  // set button color to topic color
  let button = document.getElementById(`${topicData.name}-link`);
  button.style.backgroundColor = topicData.color;

}
```

![](../.gitbook/assets/image%20%28387%29.png)

Next, add an event handler to each button so that we can respond to the event by calling a function that will build the HTML for the topic that is clicked and and update the main area of the page with the new content.

Register the event in JavaScript by calling the  addEventListener method on the DOM element and passing an anonymous arrow function for the event handler.

Now, when any of the buttons are clicked the showTopic function will be called with the specific topic data for the selected topic.

```bash
function initTopic(topicData) {
 
  // set button color to topic color
  let button = document.getElementById(`${topicData.name}-link`);
  button.style.backgroundColor = topicData.color;

  // register click event handler
  button.addEventListener("click", ()=>{
    showTopic(topicData);
  });
}
```

#### Show Topic - Building the HTML to Update The Page

The showTopic function is going to do two things:

* update the color of the text for the main-content element to be the color of the topic. For example, the tech topic will have blue text.
* call a function to build the HTML for the main-content element and update the element with the new content.

```javascript
function showTopic(topicData) {
  let element = document.getElementById("main-content");
  element.style.color = topicData.color;
  element.innerHTML = getHTMLForShowcaseArticleSummary(topicData);
}
```

#### Build HTML Text

The function getHTMLForShowcaseArticleSummary generates the HTML. It uses the Array.find method to find the article that is the showcase article for the topic. It then calls another function to build the HTML for the article.

```bash
function getHTMLForShowcaseArticleSummary(topicData) {
  let showcaseArticle = 
      articlesData.find(x=>x.id===topicData.showcaseArticleId);

  return getHTMLForArticleSummary(showcaseArticle);
}
```

```bash
function getHTMLForArticleSummary(articleData) {
  let author = authorsData.find(x=>x.id===articleData.authorId);

  return `
    <div class="article">
      <h2>${articleData.title}</h2>
      <div class="profile">Written by ${author.firstName} ${author.lastName}</div>
      <p>${articleData.abstract}</p>
      <img src='${articleData.imageURL}'>
    </div>
  `;
}
```

### Stretch Exercise

Get your project working with the above code sample, then make the following modifications.

#### Display all article summaries

Currently, the showTopic function is building the HTML for the showcase article. Your task is to create a new function, named getHTMLForTopicSummary, that builds the HTML to display all of the article summaries one after another. Then replace the call to getHTMLForShowcaseArticleSummary with this one.

This is very similar to how the zoo exercise built the HTML for all of the animals for a given type.

```bash
function getHTMLForTopicSummary(topicData) {
  // TODO: build the HTML to show all of the article
  // summaries for the topic instead of just the
  // showcase article
}

function showTopic(topicData) {
  let element = document.getElementById("main-content");
  element.style.color = topicData.color;
  
  // call getHTMLForTopicSummary instead
  // of getHTMLForShowcaseArticleSummary
  element.innerHTML = getHTMLForTopicSummary(topicData);
}
```



