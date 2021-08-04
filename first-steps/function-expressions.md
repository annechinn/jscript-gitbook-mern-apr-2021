# Function Expressions

### Defining a Function Expression

There is another option for how functions are defined. Instead of a function declaration, as we did in the previous section, you can declare a variable and initialize it with a function.

In the code sample below, the variable, sumNumbersInArray, is assigned a function as its value. 

```csharp
const sumNumbersInArray = function(array) {
    let sum = 0;
    for (let i=0; i<array.length; ++i) {
        sum+= array[i];
    }
    return sum;
}
```

Function expressions can completely replace the use of function declarations as a mechanism for defining functions. 

The use-case for this technique is when the function is the parameter or a return value of a function.

### Passing a Function Expression to another Function

In the next code sample, we are passing the filterFunc function to the filterElements function.

```csharp
let array =  [1, 2, 3, 4, 5];

const filterFunc = function(arrayElement) {
   return arrayElement > 3;
}


function filterElements(filterFunc) {
    let result = [];
    for (let i=0; i<array.length; ++i) {
        if (filterFunc(array[i])) {
            result.push(array[i]);
        }
    }

    return result;
}


console.log(filterElements(filterFunc));

```

But, we can also pass the function expression as an **anonymous function**, eliminating the need for the variable assignment. An anonymous function is just a function that doesn't have a name, as is the case when we are not assigning the function to a variable prior to passing it to the filterArrayElements function.

```csharp
let array =  [1, 2, 3, 4, 5];

// const filterFunc = function(arrayElement) {
//   return arrayElement > 3;
// }


function filterElements(filterFunc) {
    let result = [];
    for (let i=0; i<array.length; ++i) {
        if (filterFunc(array[i])) {
        result.push(array[i]);
        }
    }
    return result;
}

let sum = filterElements(function(arrayElement) {
   return arrayElement > 3;
});
```

And the next step is to use an arrow function to simplify it further.

```csharp
let array =  [1, 2, 3, 4, 5];

// const filterFunc = function(arrayElement) {
//   return arrayElement > 3;
// }


function filterElements(filterFunc) {
    let result = [];
    for (let i=0; i<array.length; ++i) {
        if (filterFunc(array[i])) {
        result.push(array[i]);
        }
    }
    return result;
}

// let sum = filterElements(function(arrayElement) {
//   return arrayElement > 3;
// });

let sum = filterElements(arrayElement => arrayElement > 3);
```

### Exercise

Create an html page named func-expr.html.  Add a script tag that includes an external script file named func-expr.js and add the following code to the file and then open the page with Live Server and then open Chrome Developer Tools console window to confirm that the expected output was displayed.

```javascript
function doThis(num1, num2, func) {
    func(num1, num2);
}

function add(num1, num2) {
    console.log(num1 + num2);
}

function multiply(num1, num2) {
    console.log(num1 * num2);
}

doThis(1, 2, add);
doThis(1, 2, multiply);

```

The code we're writing now is getting a little more involved, so it's a good time to introduce how to use the Chrome Developer Tools debugger. 

We have so far only used the Network, Elements, and Console tabs. When we want to debug our JavaScript code, we need to use the Sources tab. Once you click on that, you get a list of all of the source files relevant to the executing page.. If you click on the JavaScript file, it will load in the window on the right.

If you click on the left \(in the gutter\) of the source line you want to set a breakpoint at, the breakpoint will be indicated with a blue arrow. Since we have already loaded the page, this breakpoint will not be reached unless we refresh the page to cause it to be reloaded. So, let's go ahead and do that so we can step into the add function.

![](../.gitbook/assets/image%20%28251%29.png)

This is what the Sources screen looks like when the debugger is active and stopped at the breakpoint we set.

![](../.gitbook/assets/image%20%28355%29.png)

You can see that the parameters to the add function are being displayed by the debugger inline in the source code view, as well as on the right within the Scope section. 

Set a breakpoint at line 13, where the first doThis function is called, then refresh the page. This time, click the down arrow icon on the upper-right toolbar to step into the add function. And once you have done that click the big blue arrow on the same toolbar to have the code continue executing to completion.

We'll dive much deeper into how to use the debugger soon, but for now that is a good introduction. It is something that you will be using frequently to help debug your code.

### Challenge Exercise

See if you can modify the source code to use anonymous functions as the parameters to the doThis method.

