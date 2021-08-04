# Main Content - adding showcase html

### Changing the Showcase content

I'm now going to demonstrate changing the content in the main section in a more significant way. I'm going to insert the show case HTML appropriate for the section.

This is what the showcase section looked like in our previous Article Grid. You can see that it is hard-coding the tech section. 

![](../.gitbook/assets/image%20%2848%29.png)

* the category-tech class
* the h1 "An Article About Technology"
* the background image

```javascript
.showcase {
  color: #fff;
  padding: 32px;
  height: 40vh;
  background: url("../images/robot.jpg") center/cover;
}
```

```javascript
<section class="showcase">
  <span class="category category-tech">Technology</span>
  <h1>An Article About Technology</h1>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
    recusandae consequatur similique doloribus. Corporis, et a ullam
  </p>
  <a href="" class="btn">Learn More</a>
</section>
```

Each of these can be modified with JavaScript.

In the previous version, we just created a string to insert in the element's innerHTML.

```javascript
element.innerHTML = `<h1>${sectionName} section</h1>`;
```

In this version, we're going to insert the HTML for the entire showcase section, but we're going to replace any references to tech with the section name that was clicked.

```javascript
<!----------------------- Showcase ------------------------>
<section class="showcase">
    <span class="category category-tech">Technology</span>
    <h1>An Article About Technology</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
    </p>
    <a href="" class="btn">Learn More</a>
</section>
```

The statement below would change the element's HTML to be the entire section, but it would be for the technology section. We need to modify the string so that it has the correct section.

```javascript
element.innerHTML = `
<section class="showcase">
    <span class="category category-tech">Technology</span>
    <h1>An Article About Technology</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
    </p>
    <a href="" class="btn">Learn More</a>
</section>
`
```

### Replace the background image

This one requires us to add a new style in the CSS file and use the same technique we used earlier to add a class to the section so that it will be targeted by the new style.

So, in addition to the showcase class, we're going to add a class based on the name of the section.

Let's walk through it manually first.  In the HTML file I have left in a commented-out section of HTML that is what we used for the showcase element in the previous version of the page.

We want to temporarily comment it in so we can see how we can change which image is used as the background image based on what link we click on the nav bar.

The only change you need to make is to add an additional class to the section. add "food".

```markup
<!----------------------- Showcase ------------------------>
<section class="showcase food">
    <span class="category category-tech">Technology</span>
    <h1>An Article About Technology</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
    </p>
    <a href="" class="btn">Learn More</a>
</section>
```

Add the following style

```css
.showcase.food {
  background: url("../images/french-toast.jpg") center/cover;
}
```

Notice that the two class selectors do not have a space between them. This is how you specify a selector when both classes are on the same element

These two changes cause the background for the section to be updated to use the food image instead of the tech image.

![](../.gitbook/assets/image%20%28436%29.png)

Now, we want to do it programmatically.  Remove the "food" class value on the showcase section so we can add that class programmatically through JavaScript.

First, we add the styles to change the background image based on the addition of the new class value on the show case element.

```css
.showcase.tech {
  background: url("../images/robot.jpg") center/cover;
}

.showcase.food {
  background: url("../images/french-toast.jpg") center/cover;
}

.showcase.tech {
  background: url("../images/skull.jpg") center/cover;
}

.showcase.arts {
  background: url("../images/break-dancer.jpg") center/cover;
}

.showcase.science {
  background: url("../images/blue-footed-bird.jpg") center/cover;
}
```

Next, we modify the HTML we are generating to add the new class value based on the section that has been clicked. We want to insert the lower-case section name that we created as the value for the class.

```markup
<section class="showcase ${sectionNameLC}">

<!-- would look like this -->
<section class="showcase tech">
```

```javascript
function updateMainContent(sectionId) {

  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);
  
  element = document.getElementById("main-content");
  
  element.innerHTML = 
  `<section class="showcase ${sectionName}">
     <span class="category category-tech">Technology</span>
     <h1>An Article About Technology</h1>
     <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
      </p>
      <a href="" class="btn">Learn More</a>
   </section>`;
}
```

### Change the category-{section} class value

```markup
<!-- before -->
<span class="category category-tech">Technology</span>

<!-- after -->
<span class="category category-${sectionName}">Technology</span>
```

**Create the category-{sectionNameLC}.**

```javascript
function updateMainContent(sectionId) {

  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);
  
  element = document.getElementById("main-content");
  
  element.innerHTML = 
  `<section class="showcase ${sectionName}">
     <span class="category category-${sectionName}">Technology</span>
     <h1>An Article About Technology</h1>
     <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
      </p>
      <a href="" class="btn">Learn More</a>
   </section>`;
}
```

### Replace the word Technology with the section name

```javascript
function updateMainContent(sectionId) {

  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);
  
  element = document.getElementById("main-content");
  
  element.innerHTML = 
  `<section class="showcase ${sectionName}">
     <span class="category category-${sectionName}">${sectionNameCap}</span>
     <h1>An Article About ${sectionNameCap}</h1>
     <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
      </p>
      <a href="" class="btn">Learn More</a>
   </section>`;
}
```

### Solution So Far

```javascript
function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1)
}

function getSectionNameLC(sectionId) {
  let splitResult = sectionId.split("-");
  let sectionNameLC = splitResult[0];
  return sectionNameLC.toLowerCase();
}

function updateMainContent(sectionId) {

  let sectionName = targetId.split("-")[0];
  let sectionNameCap = capitalize(sectionName);
  
  element = document.getElementById("main-content");
  
  element.innerHTML = 
  `<section class="showcase ${sectionName}">
     <span class="category category-${sectionName}">${sectionNameCap}</span>
     <h1>An Article About ${sectionNameCap}</h1>
     <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
      recusandae consequatur similique doloribus. Corporis, et a ullam
      </p>
      <a href="" class="btn">Learn More</a>
   </section>`;
}

function respondToClick(event) {  
  // prevent page from refreshing
  event.preventDefault();

  let targetElement = event.target;
  targetElement.classList.add("active");

  let targetId = targetElement.id;

  updateMainContent(targetId);
}

```

We added these styles

```css
.showcase.tech {
  background: url("../images/robot.jpg") center/cover;
}

.showcase.food {
  background: url("../images/french-toast.jpg") center/cover;
}

.showcase.tech {
  background: url("../images/skull.jpg") center/cover;
}

.showcase.arts {
  background: url("../images/break-dancer.jpg") center/cover;
}

.showcase.science {
  background: url("../images/blue-footed-bird.jpg") center/cover;
}
```

```markup
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="css/styles.css" />
    <title>News Site</title>
  </head>
  <body>
    <main>

      <!----------------------- NavBar ------------------------>
      <nav class="nav-container">
        <a href="index.html">
          <img src="images/logo.png" class="logo" />
        </a>
        <ul>
          <li><a id="tech-link" onclick="respondToClick(event);" href="">Tech</a></li>
          <li><a id="science-link" onclick="respondToClick(event);" href="">Science</a></li>
          <li><a id="food-link" onclick="respondToClick(event);" href="">Food</a></li>
          <li><a id="arts-link" onclick="respondToClick(event);" href="">Arts</a></li>
          <li><a id="sports-link" onclick="respondToClick(event);" href="">Sports</a></li>
          <li><a href="">Account</a></li>
        </ul>
      </nav>

      <!-- <section class="showcase">
        <span class="category category-tech">Technology</span>
        <h1>An Article About Technology</h1>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
          recusandae consequatur similique doloribus. Corporis, et a ullam
        </p>
        <a href="" class="btn">Learn More</a>
      </section> -->
      
      <!-------------------- Main Content --------------------->
      <div id="main-content">
        Main Content
      </div>

      <!----------------------- Footer ------------------------>
      <footer class="footer-container">
        <div>
          <img src="images/logo_light.png" alt="NewsGrid" />
        </div>
        <div>
          <h3>This is the Footer</h3>
        </div>
        <div>
          <h3>Connect with Us</h3>
        </div>
      </footer>
    </main>

    <script src="script.js"></script>
  </body>
</html>

```

