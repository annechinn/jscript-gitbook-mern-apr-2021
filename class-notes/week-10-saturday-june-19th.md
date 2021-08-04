# Week 10 - Saturday, June 19th

### Class Lecture

{% embed url="https://www.youtube.com/watch?v=KYi03bfpxxU" %}

### Topics

#### Switch Statement

{% embed url="https://www.w3schools.com/js/js\_switch.asp" %}

{% page-ref page="../control-flow/switch.md" %}

#### Client-Server

{% page-ref page="../client-server/client-server-architecture.md" %}

{% page-ref page="../client-server/web-api-overview.md" %}

{% page-ref page="../client-server/server-side-web-frameworks.md" %}

{% page-ref page="../client-server/node.js.md" %}

{% page-ref page="../client-server/express.md" %}

### Homework

Your assignment is to use the NY Times Books API to create a page that displays a responsive grid containing a card for each of the best selling books. 

You will continue working within the new-site-collab rehab. The code for this project should be modeled after the two other projects in this repo:

* zoo animals - in your folder within the labs/class-16 folder. it has code for creating a grid of cards using the Bootstrap card styles.
* news article grid - in the top-level, index.html is the starting file for this project. the scripts/scripts.js file contains code for creating a grid of cards \(not using Bootstrap\) as well as code for retrieving the article card data from the NY Time web API.

### Building from Scratch

 It's time for you to become more independent in your work. I want you to start this project from scratch, creating all of the files on your own. Before you start coding, you need to get your branches in order.

#### Clean up the current branch you are working on

* if you have a current branch that has modifications that are not committed, commit those changes.
  * **git add .**
  * **git commit -m"comment"**
  * **git push**
  * go to GitHub and create a pull request to merge your changes into the main branch.

### Get the latest sources from the main branch

* Move to the main branch, **git checkout main**.
* Get the latest code from the remote repo - **git pull**

#### Create a new branch

Name it the name of the issue that I have assigned you in the repo, such as "dw-nyt-books"

git checkout -b \[branch-name\] \(this will move you into the new branch\)

![](../.gitbook/assets/image%20%28328%29.png)

Now you are ready to begin coding.

#### Create a project folder

Within the labs/nyt-books folder, create a folder with your initials. So I would create a folder labs/nyt-books/ac.

#### Create your files for your project. 

You can organize and name the project files however you want. Just make sure they are correctly included in your HTML file.  In addition to your HTML file, you will need to create and include the following three files:

* stylesheet file
* data file
* script file

In addition, you will need to include a few external files to get the Bootstrap styles and the axios package that allows you to make remote calls to the NY Times web API.

#### Include the Bootstrap stylesheet CDNs

Include these two lines in your &lt;head&gt; section. There is an example of doing this in the tickets.html file.

```markup
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4" crossorigin="anonymous"></script>
```

#### Include axios CDN for getting NY Times Books API

Include this line in your &lt;head&gt; section. This external JavaScript library is used to retrieve the books data from the NY Times Books API. There is an example of doing this in the top-level index.html for the article grid.

```markup
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

#### Add the code to retrieve the books data from the NY Times Books API

Add this code to your data file.

```javascript
async function getBooks () {  
    const response = await axios.get(`https://api.nytimes.com/svc/books/v3/lists/current/hardcover-fiction.json?api-key=5Vd8O8baGS3WEG1eQVAaS2mG6K0VyHH8`)
    return response.data.results.books;
};
```

#### Add the code to show the books

In your script file, you will need to mark your function that calls the getBooks function with the "async" keyword.

```javascript
async function showBooks() {
    const books = await getBooks();
}

showBooks();
```

You now should have your basic project structure in place, and can begin coding the functionality to the showBooks function. Make sure it is working at this point with simple confirmations:

* add a style to add padding to the body element and add an &lt;h1&gt;Hello World&lt;/h1&gt; to the HTML document to confirm the stylesheet is being included correctly.
* in the showBooks function, write the books array to the console to confirm that the data file is being included correctly.

If things aren't working, use the Chrome Developer Tools to check for errors, and make sure all of your files are being loaded.



#### Populate and Style the Book Card Content

Review the script code in your zoo lab that creates the cards for the animals. Model your books cards after that HTML, but supply the relevant data from the book in your card. The following data returned from the API should be included:

* Book image
* Book rank - Book Title
* Book description
* Clicking on the book image or title should redirect to the Amazon page for the book.

![](../.gitbook/assets/image%20%2862%29.png)

#### The Final Product

Here's a sample of how the page might look. You're free to style it as you like, or add additional information from the data.

![](../.gitbook/assets/image%20%28179%29.png)

#### Make the Page Responsive

Look at the stylesheet for the article grid project \(css/styles.css\) if you need help figuring out how to do this.

![](../.gitbook/assets/image%20%2880%29.png)

#### Commit Your Branch

Do the ACP \(add, commit, push\) to your branch, and then create a pull request on GitHub to have the changes merged into the main branch.

#### Help Session

Here's a video session I did with Yakob clarifying some of the steps necessary to complete this HW. If you're having trouble, look at this first.

{% embed url="https://www.youtube.com/watch?v=VWtlRuWDKbU" %}



#### Coding Challenges

codewars.com is a site that has code challenges \(called katas\) of increasing difficulty. It's a good place to practice. Here are a few free ones to try at the entry level \(8\). The entry-level ones tend to be free. I don't think you need to sign up.

{% embed url="https://www.codewars.com/kata/51f9d93b4095e0a7200001b8/train/javascript" %}

```javascript
function howManyLightsabersDoYouOwn(name) {
  if (name==='Zach') return 18;
  else return 10;
}
```

{% embed url="https://www.codewars.com/kata/57eadb7ecd143f4c9c0000a3/train/javascript" %}

```javascript
function abbrevName(name){
  const parts = name.split(" ");
  return `${parts[0][0]}.${parts[1][0]}`;
}
```

{% embed url="https://www.codewars.com/kata/58649884a1659ed6cb000072/train/javascript" %}

```javascript
function updateLight(current) {
  switch (current) {
      case 'yellow':
        return 'red';
      case 'red':
        return 'green'
      case 'green':
        return 'yellow';
  }
}
```

{% embed url="https://www.codewars.com/kata/5865a28fa5f191d35f0000f8/train/javascript" %}

```javascript
function takeUmbrella(weather, chance) {
  if (weather==='rainy' || (weather==='cloudy' && chance>.2)) return true;
  if (weather==='sunny' && chance>.5) return true;
  return false;    
}
```

{% embed url="https://www.codewars.com/kata/545afd0761aa4c3055001386/train/javascript" %}

```javascript

function take(arr, n) {
  return arr.filter((x,i)=>i<n);
}
```

{% embed url="https://www.codewars.com/kata/55685cd7ad70877c23000102/train/javascript" %}

```javascript
function makeNegative(num) {
  return (num<0?num:-num);
}
```

{% embed url="https://www.codewars.com/kata/55a70521798b14d4750000a4/train/javascript" %}

```javascript
function greet(name){
  return `Hello, ${name} how are you doing today?`;
}
```

{% embed url="https://www.codewars.com/kata/5a00e05cc374cb34d100000d/train/javascript" %}

```javascript
const reverseSeq = n => {
  let results = [];
  for (let i=n;i>=1;--i) {
    results.push(i);
  }
  return results;
};
```

