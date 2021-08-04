# Node.js, npm

**Node.js** is a JavaScript runtime environment that runs on a web server and includes the JavaScript engine built by Google. Node.js allows developers to use JavaScript as the language for building the Web API. 

**npm**, or **Node Package Manager**, is also part of Node.js.

### Install Node.js

{% embed url="https://nodejs.org/en/download/" %}

#### Interactive Shell - REPL \(Read-Eval-Print-Loop\)

Node.js supplies an interactive shell that reads and evaluates code that you enter directly or load from a file.

To launch REPL, type **node** at the command line.

```bash
d:\dev>node
Welcome to Node.js v14.16.0.
Type ".help" for more information
```

You can now enter any JavaScript code at the command prompt and it will be executed.

#### Displaying Output

There isn't a user interface on the server. Your code can use the global console.log method to display results to the console.

```bash
d:\dev>node
Welcome to Node.js v14.16.0.
Type ".help" for more information
> console.log("Hello");
Hello
> 3 + 4
7
```

#### External Script Files

You can execute the code in a file by passing the filename to Node.js on the command line. 

In your test folder, create a file named script.js with the content below.

```javascript
// script.js
console.log("Hello");
```

Execute the script as follows.

```bash
d:\dev> node script.js
Hello
```

{% hint style="info" %}
Node.js does not have the window object that is available in a web browser because Node.js is running on the server.
{% endhint %}

### 

### Creating a Node Application

Create a new folder, cd into the folder and run the npm init command 

```bash
mkdir test-npm
cd test-npm
npm init
```

This will create a file named "packages.json" in the project root directory. This file is used by npm to track the modules it installs.

```javascript
{
  "name": "test-npm",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

#### Installing Packages - npm install \[package-name\]

```bash
$ npm install express
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN test-npm@1.0.0 No description
npm WARN test-npm@1.0.0 No repository field.

+ express@4.17.1
added 50 packages from 37 contributors and audited 50 packages in 3.242s
found 0 vulnerabilities
```

.Installing the express package, installed 50 packages that were dependencies of the express package. All packages are installed in a folder named "node\_modules". This folder is typically set up to be ignored by git commits because a project can have a huge number of modules and they can easily be installed from scratch from the packages.json file using the npm install command without a package specified.

![](../.gitbook/assets/image%20%28400%29.png)

After a modules has been added, the packages.json file is updated to include the new module in the "dependencies" section.

```bash
{
  "name": "test-npm",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

### Creating a Basic Web Server

In some web frameworks the web server handles the web requests and routes them to the web API handlers. In Node.js, you have to create the web server that responds to the initial incoming web requests and handle the routing to the request handlers in our code.

Create a file named "server.js" and add the following code to create a web server. require is how you include external modules in your code. It is different that the ES 6 Modules "import/export" functionality. We'll cover modules in a separate topic.

#### Server.js

```bash
const http = require('http');
const hostname = '127.0.0.1';
const port = 3000;
const server = http.createServer((req,res)=> {
  res.statusCode = 200;
  res.setHeader('Content-type', 'text/plain');
  res.end('Hello World!');
});

server.listen(port, hostname, ()=> {
  console.log(`Server started on port ${port}`)
})
```

#### Start the Service

```bash
anne@FIRENZE MINGW64 /d/skillspire/test-npm
$ node server
Server started on port 3000
```

#### Request in Browser

![](../.gitbook/assets/image%20%28235%29.png)

Now, let's load a HTML document, instead of just writing text to the response.

#### Server.js

```bash
const http = require('http');
const fs = require('fs');
const hostname = '127.0.0.1';
const port = 3000;

fs.readFile('index.html', (err, html) => {
  if (err) {
    throw err;
  }

  const server = http.createServer((req,res)=> {
    res.statusCode = 200;
    res.setHeader('Content-type', 'text/html');
    res.write(html);
    res.end();
  });

  server.listen(port, hostname, ()=> {
    console.log(`Server started on port ${port}`)
  })
});
```

#### Index.html

```bash
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <h1>Hello World!</h1>
  <img src="https://images.unsplash.com/photo-1564053489984-317bbd824340?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8ZWFydGh8ZW58MHx8MHx8&auto=format&fit=crop&w=400&q=60" alt="">
</body>
</html>
```

![](../.gitbook/assets/image%20%28453%29.png)

### Resources

{% embed url="https://www.youtube.com/watch?v=U8XF6AFGqlc" %}

There are other npm commands for updating modules to the latest version, removing modules, etc. Many of them are explained in further detail in the following tutorial.

{% embed url="https://www.digitalocean.com/community/tutorials/how-to-use-node-js-modules-with-npm-and-package-json" %}

{% embed url="https://www.youtube.com/watch?v=llPW0b1dQms" %}



