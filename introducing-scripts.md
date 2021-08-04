# JavaScript in the Browser

### Project Setup

Create a new project folder named scripts-intro. Open the folder in VS Code and create an index.html file and add the following in the body element.

### &lt;script&gt; element with embedded JavaScript code

JavaScript scripts can be included directly within the HTML document using the &lt;script&gt; element and placing the JavaScript code between the opening and closing tags.

```markup
<body>
  <script>
    console.log("Hello");
  </script>
</body>
```

### &lt;script&gt; element with external JavaScript code

But the preferred method is to load the script from an external file, by specifying the location of the file with the src attribute.

```javascript
/* script.js */

console.log("Hello");
```

```markup
<html lang="en">
<head>
</head>
<body>
  <!-- all other html first -->
  <script src="script.js"></script>
</body>
</html>

```

### script placement

The &lt;script&gt; element causes the web browser to stop processing the HTML and process the script element before continuing to process the HTML document.

It is legal for a script element to be placed anywhere in the document, including the head element. But a script could run into a problem if it is located in the document before an element that the script references.

For example, if a script element is inside the head element, and it set the background color of the body element, an error would occur because the body element has not been generated yet.

For that reason, it is best practice to position any script elements at the very end of the body element.  
    

### JavaScript Statement

The code below is a JavaScript statement. 

```javascript
console.log("Hello");
```

A statement is an instruction that performs an action.  

### JavaScript built-in objects

Objects represent things in real life and are also used in computer programs to model data. Objects have properties \(characteristics of the object, such as a person having a first name and last name\) and methods. A method is an action that can be invoked to complete a task.

The JavaScript runtime environment within the web browser provides several objects you will use frequently.

#### console object

The console object is available to JavaScript code and provides methods for logging content to the console.

```javascript
console.log("Hello");
```

![](.gitbook/assets/image%20%28370%29.png)

![](.gitbook/assets/image%20%28323%29.png)

### Exercise

Add a script element to your html document and first add an embedded script to call the console.log method with some text;

Now, move your script code to an external script.js file.

#### 

#### document object

If you open Chrome Dev Tools/Console and type document you will get an object that represents the HTML document. 

![](.gitbook/assets/image%20%28312%29.png)

The  document object is available to JavaScript code and is the entry into the DOM, which is the API that allows us to manipulate the HTML elements in the document.

### object properties

The statement below is setting the value of the backgroundColor property on the body element. Each dot in the statement is accessing an object contained within the parent object.

```javascript
document.body.style.backgroundColor = "red";
```

After the statement has been executed, the HTML document will be modified to have added the background-color to the body element.

![](.gitbook/assets/image%20%28108%29.png)

### window object

When JavaScript code is executed within a browser, the window object is the global object and represents the browser window. 

The document and console object are actually not a global objects, but  properties of the window object. But, all properties of the global window object can be accessed directly.

![](.gitbook/assets/image%20%28371%29.png)

```markup
/* this */
window.alert("Hello");

/* is the same as this */
alert("Hello");
```

### window.alert method

The statement is calling the alert method on the window object in order to display a message window to the user.

```markup
<body>
    <script>
        window.alert("Hello");
    </script>
</body>
```

![](.gitbook/assets/image%20%28171%29.png)

**alert\(message\)** - shows a message to the user and waits for the user to click Ok.

![](.gitbook/assets/image%20%28266%29.png)

### window.prompt method

**prompt\(message, default value\)** - shows a modal dialog with a message and a input field for the user to enter a value and waits for the user to click Ok or Cancel. The second parameter is optional, and will be used as the default value if it is supplied. The function will return the value the user entered.

The script below is calling the prompt method on the window object to ask the user what color to change the background color to.

The prompt method returns a value entered by the user. In order to store the return value we need to create a variable to hold the return value.

The **let keyword** is how you define a variable to hold a value. 

The **= symbol** is how you assign a value to a variable.

```javascript
let color = window.prompt("What color should I set the background to?", "yellow");
```

![](.gitbook/assets/image%20%28193%29.png)

![](.gitbook/assets/image%20%28247%29.png)

Use the value stored in the color variable to set the value of the body element's background color;

```javascript
let color = window.prompt("What color should I set the background to?", "yellow");
document.body.style.backgroundColor = color;
```

### Concatenating Strings

Modify the above script to use the window.alert method to display the value of the background color after it has been changed.

The "+" character can be used to concatenate strings to form a larger string.

```javascript
let color = window.prompt("What color should I set the background to?", "yellow");
document.body.style.backgroundColor = color;
window.alert("The color is: " + color);
```

![](.gitbook/assets/image%20%28191%29.png)

Modify the script above to display the color before and after the change.

```javascript
let colorBefore = document.body.style.backgroundColor;
let color = window.prompt("What color should I set the background to?", colorBefore);
document.body.style.backgroundColor = color;
window.alert("The color has been changed from " + colorBefore + " to " + color);
```

### window.confirm method

![](.gitbook/assets/image%20%28114%29.png)

**confirm\(message\)** - shows a modal dialog with a message and waits for the user to click Ok or Cancel. The function will return true if the user clicks Ok, and false if the user clicks Cancel.

In the script below, on line 3, we've added a call to the window.confirm method to ask whether the user wants to change the background color. But we're not doing anything with the return value. But we're not using the answer to decide whether to change the color.

```javascript
let colorBefore = document.body.style.backgroundColor;
let answer = window.confirm("Do you want to change the background color?");
let color = window.prompt("What color should I set the background to?", colorBefore);
document.body.style.backgroundColor = color;
window.alert("The color is: " + color);
```

### Conditional Statements

Here, we are testing the answer to see if it is true, and if it is, then we prompt to ask for a color to change.

```markup
<body>
  <script>
    let answer = window.confirm("Do you want to change the background color?");
    if (answer === true) {
      let color = window.prompt("What color should I set the background to?", colorBefore);
      document.body.style.backgroundColor = color;
      window.alert("The color is: " + color);
    }
  </script>
</body>
```

