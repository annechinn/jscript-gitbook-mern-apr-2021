# Week 10 - Wednesday, June 24th

### Class Video

{% embed url="https://www.youtube.com/watch?v=7lMEj5TA5Ro" %}



{% embed url="https://www.youtube.com/watch?v=2vgAaQAds8Q" %}



### Algorithm Practice Problem - Reversing an Array

**Reverse an array using a new array.** Start from the end and push each element into a new array.

```javascript
function reverseArray(array) {
  let result = [];
  for (let i=array.length-1;i>=0;i--) {
    result.push(array[i]);
  }

  return result;
}

const array = [1,2,3,4];
console.log(reverseArray(array)); // [4, 3, 2, 1]
```

**Reverse "in-place".**  Move inward from both ends and swap the start/end elements until they meet in the middle.

```javascript
function reverseArray(array) {
 let start = 0;
 let end = array.length-1;
 while (start<=end) {
 
   // swap start and end elements
   const temp = array[start];
   array[start] = array[end];
   array[end]=temp;
   
   // move indices inward by one
   start++;
   end--;
 }
 return array;
}

const array = [1,2,3,4];
console.log(reverseArray(array));
```

There's a great visual in the article below showing the swapping process.

{% embed url="https://afteracademy.com/blog/reverse-an-array" %}



### New JavaScript Concepts

{% page-ref page="../client-server/asynchronous-javascript.md" %}

### Project Management w/GitKraken Boards

Install VS Code Extension

![](../.gitbook/assets/image%20%2819%29.png)

### Code Review/Bug Fixing Opportunities

I've created two new labs that are small games. They are useful to review the code and see if you can understand what is going on. I have also created a few bugs in the code that can be fixed if you have time.

### Commit Work/PR - linked Issue

Make sure all of your work on the nyt-books branch is committed and then create a PR that links to the issue you were assigned. The issue should automatically move to the Done column.

### Back-end Continued - Database

{% page-ref page="../client-server/mongodb.md" %}

### Homework

{% hint style="danger" %}
You need to get the changes I pushed to the main branch to get a few fixes I added for this assignment.

* if you already started work in a new branch, add and commit the changes in your branch
  * git add .
  * git commit -m"\[message\]"
* switch to the main branch
  * git checkout main
* pull to update the main branch
  * git pull
* switch to your other branch
  * git checkout \[branch-name\]
* merge the main branch updates into your branch
  * git merge main
{% endhint %}



We're going to do another lab similar to the last one. Again, you'll try to start from scratch and use some of the previous labs as models for how to proceed.

We're also going to start using GitKraken for managing the GitHub issues. 

#### Commit Changes for In-Progress Issues

It's important to keep your branches organized, and remove any that you are done working on. Before you start working on this assignment, make sure that you have finished the last assignment and committed it to the GitHub repo and merged it back into the main branch through a Pull Request \(PR\).

#### Prepare for Work in New Branch

Before starting a new branch, remember to **go to your main branch and do a pull** to make sure you have all of the latest sources.

From within GitKraken, **move the Issue for today's assignment to the In-Progress column** to indicate that you have started working on it. Just drag it from the Issues column to the In-progress column.

#### Create a New Branch

You can either create the branch from the command line, or use the VS Code Extension that allows you to start a branch from an Issue assigned to you. If you create it on your own, then name it the title of the Issue. For example, 'ac-article-summary-lab'.

#### Project Setup

Create a new folder with your initials in the labs/article-summary folder in the news-site-collab repo. You will again create your own files for the html, css, and script.

In your html file, you'll need to include the three data files \(articles.js, authors.js, and topics.js\) in the labs/article-summary/data folder.

You can use bootstrap, or create your own styles for what you display for the article. If you use bootstrap, then it will look like a card vs what I displayed in the screenshots below. Either is fine.

To use bootstrap, copy the link elements from you last homework where you included the bootstrap stylesheets in your index.html and include them in your current index.html file.

```javascript
 <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">
 <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4" crossorigin="anonymous"></script>

```

#### Button Setup

When the page first comes up, there should be a series of buttons: one for each topic that is contained within the static data file data/topics.js. They should be initialize in a similar way to how the buttons at the top of the zoo lab were.

There is one additional requirement when initializing the buttons. You should set the background color of the button to the topic color \(specified in the topic data element\).

![](../.gitbook/assets/image%20%28173%29.png)

#### Event Handler

In the event handler you set up for the button click, you need to build up the HTML dynamically to display a summary of an article \(which article is explained below\).

#### Article Summary

Your going to need to navigate around the three different data files to build the HTML. Your event handler will be given the topic data element when the button is clicked. 

From the topic element, you can get the topic.showcaseArticleId, and use that id to look up the article from the articles array in data/articles.js file using the find method.

From the article element, you can get the article.authorId, and use that id to look up the author from the authors array in the data/authors.js file. using the find method.

Try to change the  color of the text for the article summary so that it matches the color of the topic.

![](../.gitbook/assets/image%20%28198%29.png)

![](../.gitbook/assets/image%20%2853%29.png)

![](../.gitbook/assets/image%20%28257%29.png)

#### Merging Your Work into the Main Branch

Create a PR to merge the changes into the main branch. When you create the PR, **link the Issue that you are working on to the PR**. That way, it will be automatically moved to the Done column in the GitKraken project board.

### Extra Challenge

I have checked in my solution for this assignment. It in labs/article-summary/ac. In my solution, I am using the web API from the back-end. Study my code, and then change your code to call your back-end instead of loading the data from the static data files.

You will need to run the following:

* cd back-end
* node seeder - reseed the database \(i made some changes, so you need to do this even if you already ran this recently\)
* npm run dev - start the web server

