# Babel

## What is Babel <a id="446f"></a>

* JavaScript transpiler
* Initially, the main focus of babel is to convert ECMAScript 2015+ \(ES6+\) code into a backwards compatible version of JavaScript that can be run by older JavaScript engines
* Nowadays, Babel is used to convert \(transpile\) JSX syntax , Typescript , Code Compression, and any syntaxs in proposal stage. For example, arrow function, which are specified in ES6 are converted into regular function declarations



When you use JSX, the compiler transforms it into React function calls that the browser can understand. **The old JSX transform** turned JSX into `React.createElement(...)` calls.

For example, let’s say your source code looks like this:

```javascript
import React from 'react';

function App() {
  return <h1>Hello World</h1>;
}
```

Under the hood, the old JSX transform turns it into regular JavaScript:

```javascript
import React from 'react';

function App() {
  return React.createElement('h1', null, 'Hello world');
}
```

