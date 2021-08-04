# Modules

### ES6 Modules - used in front-end

#### Named Exports

Named exports are useful to export several values. During the import, it is mandatory to use the same name of the corresponding object.

For example, I created a file containing the functions to retrieve the data from the back-end webAPI. It's useful to export these as an object so that the importer can import the specific functions they need.

```javascript
import axios from 'axios';

const PORT=5000;
const SERVER_URL_ROOT = `http://localhost:${PORT}/api`;

async function getTopics() {
  const response = await axios.get(`${SERVER_URL_ROOT}/topics`);
  return response.data;
}

async function getTopic(topicId) {
  const response = await axios.get(`${SERVER_URL_ROOT}/topics/${topicId}`);
  return response.data;
}

async function getArticle(articleId) {
  const response = await axios.get(`${SERVER_URL_ROOT}/articles/${articleId}`);
  return response.data;
}

async function getArticles() {
  const response = await axios.get(`${SERVER_URL_ROOT}/articles/`);
  return response.data;
}

async function getArticlesForTopic(topicId) {
  const response = await axios.get(`${SERVER_URL_ROOT}/articles/topic/${topicId}`);
  return response.data;
}

export {
  getArticles,
  getArticlesForTopic,
  getArticle,
  getTopics,
  getTopic
}
```

```javascript
import {
    getArticlesForTopic, 
    getArticle, 
    getTopic
} from '../../api/back-end';
```

#### Default Exports

But a default export can be imported with any name:

```javascript
// export feature declared earlier as default
export { myFunction as default };

// export individual features as default
export default function () { ... }
export default class { .. }

// each export overwrites the previous one
```

The React component functions are exported as the default export.

```javascript
function Header() {
  return (
    <header>
       <a href="index.html">
        <img src={logo} class="logo" alt="logo" />
      </a>
      <NavBar/>
    </header>
    );
}

export default Header;
```

A default export is imported with whatever name you specify.

```javascript
import Header from './containers/Header/Header';
```

### 

### CommonJS Modules - Node.js



### Resources

{% embed url="https://flaviocopes.com/commonjs/" %}

{% embed url="https://www.digitalocean.com/community/tutorials/how-to-create-a-node-js-module" %}

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export" %}

{% embed url="https://www.jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/" %}

{% embed url="https://ui.dev/javascript-modules-iifes-commonjs-esmodules/" %}

