# Statements/Functions

### Statements

```javascript
alert('Hello World!');
```

The code above is a JavaScript statement. A statement is an instruction that performs an action.  While JavaScript does not require a semi-colon at the end of a statement, and allows multiple statements to be on a single line, it is best practice to follow these rules:

* write each statement on a single line
* end each statement with a semi-colon

```javascript
alert('Hello World!');
alert('Hello again!');
```

### Global Statements vs Functions

The statements above are global statements, meaning that they are at the top-level of the script and as the file is processed, they will be executed immediately. 

In contrast to global statements, the vast majority of statements will be organized into reusable units of code that can be executed at a later time in response to events, such as a user clicking a button. These separate blocks of code are known as functions. 

There can be both functions and global statements in a script file. 

```javascript
function doSomething() {
    /* code to do something */
}

function doSomethingElse() {
/* code to do something else */
}

alert("Hello");
```

A function is just a reusable chunk of code that does something.  Functions help organize our code and make it easier understand. You can create your own functions and use functions created by team members or third-party libraries. The JavaScript runtime environment also supplies a large number of built-in functions.

The alert function is an example of a function provided by the JavaScript runtime environment. Its purpose is to display a text message on the screen. There's a lot going on inside the alert function, but we don't need to worry about that. We can just call the function and expect that it will do what the documentation says it will do. 

The functions provided by the JavaScript runtime environment are always available to use in your scripts. Functions provided by third-party libraries, require you to download their scripts and import them into your project, just like you do with your own script files.



### Calling Functions

When the code below is first processed, it will see the two functions, and store them away until it encounters a statement that invokes the function.

```javascript
function doSomething() {
    /* code to do something */
}

function doSomethingElse() {
/* code to do something else */
}
```

At some later point, such as when a user clicks a button,  the JavaScript Engine will execute a call to the function.

```markup
<button onClick="doSomething()">Click to do something</button>
```

### 

### Functions With and Without Return Values

Some functions just execute a sequence of statements and they are done. The code that called them waits for the function to complete, and then continues on with the next statement.

Other functions perform some work that results in some data that needs to be returned to the caller. The calling function can receive the value returned by the function and  store it in a variable to use in its own code. 

```javascript
function calculateTotalWithTip(amount, rate) {
    let total = amount + (amount * rate);
    return total;
}

let total = calculateTotalWithTip(10.50, .15);
console.log(total);
```

### Practice

Create a function named add, that accepts two numbers as parameters. The function should return the sum of the two numbers. 

Call the function and log the returned value to the console.

