# Build Site

```javascript
let sections = ["tech", "sports", "arts", "food", "science"];

function capitalize (string) {
  return string[0].toUpperCase() + string.slice(1)
}

function buildNavLinkHTML(sectionName) {
  return `<li><a href="">${capitalize(sectionName)}</a></li>`;
}

function buildNavLinksHTML() {
  let html = '';
  for (let i=0;i<sections.length; ++i) {
    html+= buildNavLinkHTML(sections[i]);
  }
  return html;
}

console.log(buildNavLinksHTML());
```

Add id to link

```javascript
function buildNavLinkHTML(sectionName) {
  return `<li id=${sectionName}><a href="">${capitalize(sectionName)}</a></li>`;
}
```

Build Nav Links

```javascript
function addNavBar() {
  let linksHTML = sections
                    .map(x=>buildNavLinkHTML(x))
                    .join("");

  element = document.getElementById("nav-bar");
  element.innerHTML =
  `<nav class="nav-container">
  <a href="index.html">
    <img src="images/logo.png" class="logo" />
  </a>
  <ul>
    ${linksHTML}
    <li><a href="">Account</a></li>
 </ul>
</nav>
  `
}
```

Build Article HTML

```javascript
function buildArticleHTML(article) {
  return `
  <article>
        <img src="${article.imageURL}" alt="" />
        <span class="category category-${article.topic}">${capitalize(article.topic)}</span>
        <h3><a href="">${article.title}</a></h3>
        <p>
          ${article.abstract}
        </p>
      </article>
  `
}
```

Build Articles HTML

```javascript
function addArticleGrid(sectionName) {
  element = document.getElementById("article-grid");
 
  let articlesHTML = articles
    .filter(x=>x.topic ===sectionName)
    .map(x=>buildArticleHTML(x))
    .join("");

  element.innerHTML = articlesHTML;
}
```

Add Showcase Article

```javascript
function addShowCaseArticle(sectionName) {
  element = document.getElementById("showcase");
 
  // for now, just get the first article in the section
  let article = articles
    .filter(x=>x.topic ===sectionName)[0];

  let capSectionName = capitalize(sectionName);
  let showCaseHTML =
    `<section style="background:url(${article.imageURL}) center/cover" class="showcase ${sectionName}">
        <span class="category category-${sectionName}">${capSectionName}</span>
        <h1>${article.title}</h1>
        <p>
         ${article.abstract}
        </p>
        <a href="" class="btn">Learn More</a>
    </section>`;

    element.innerHTML = showCaseHTML;
}
```



