# Arrow/Anonymous Functions

In ES6, there is a new syntax for creating function expressions. It is a short-hand notation.

```csharp
// start with a standard function expression

const add = function(num1, num2) {
    return num1 + num2;
}

// convert to an arrow function

// 1. remove the "function" keyword
// 2. place an arrow after the parameters

const add  = (num1, num2) => {
    return num1 + num2;
}
```

So far, it's not that big of an improvement, and it does taking some getting used to the new syntax. The real advantage of the new syntax becomes clearer as you add some optional simplifications.

#### Body block curly braces are not required if there is a single statement.

Notice that the return keyword is not used when the body braces have been removed.

```csharp
// option 1
const add = (num1, num2) => {
    return num1 + num2;
}

// option 2 - remove body block braces, return keyword
const add = (num1, num2) => num1 + num2;


```

#### Parentheses are not required for a single parameter

```csharp
// option 1
const showMessage = (message) {
    alert(message);
}

// remove body block braces, return statement
const showMessage = (message) => alert(message);

// remove parameter parens

const showMessage = message => alert(message);

```

#### Summarizing Rules for Arrow Functions

* Function body block bracing is required if there is more than one statement in the function body. They can be removed if there is only a single statement;
* Parentheses surrounding the function parameters are optional if there is a single parameter.

Combining arrow functions with anonymous functions is where their usage really shines as you'll see below.

### Anonymous Functions

In the section on function expressions we demonstrated how a function can be passed as an argument to another function. In that case we first defined the function and assigned it to a variable, and then passed the variable to the function.

It is also possible, and more common, to define the function inline, using arrow functions, as I'll demonstrate below. The functions in this case are called anonymous, because they do not have a name and exist only as long as they are used in the context of the function call.

This is how we did it in the previous example. We defined a function expression, assigned it to the variable, and then passed the variable to the doSomething function.

```csharp
function doSomething(doThis) {
    doThis();
}

const sayHello = function() {
    alert("Hello");
}

doSomething(sayHello);
```

Here, we are passing in an anonymous function expression without having to bother with pre-defining it.

```csharp
function doSomething(doThis) {
    doThis();
}

doSomething(()=>alert("Hello"));
```

Anonymous functions are an extremely important concept to understand in JavaScript.  As an example of their typical usage, the JavaScript Array object has many methods that accept a function to apply to each of the elements in an array.

```csharp
// the filter method will return a new array
// containing the elements that return true
// when the passed-in function is called with the
// number as a parameter

const numArray = [1,2,3,4,5];
const result = numArray.filter((num)=>num<3);
console.log(result); // [1,2];
```

```csharp
// map applies the function to each element
// and returns an array with the new values.
const numArray = [1,2,3,4,5];
const result = numArray.map((num)=>num*2);
console.log(result); // [2,4,6,8,10];
```

#### Multi-line Complex Anonymous Functions

We discussed the rule earlier that the body braces and the return statement weren't required if the body contained a single statement only. The anonymous function can get a bit more complex as there is more involved in the body. Here is an example of how JavaScript typically looks when anonymous functions are used.

The anonymous function is the parameter to the someFunction, and it accepts two parameters. It also has the body braces and a more complex statement than the simple case we saw above when adding two numbers.

```csharp
someFunction((a1, a2) => {
  if (a1.equals(a2)) {
    doSomething(a1);
  } else {
    doSomethingElse(a2.propertyName);
  }
});
```

Sometimes it helps to pull out the anonymous function and pass it in as a variable to simplify it when you are first getting used to this format.

```csharp
const myFunc = (a1, a2) => {
  if (a1.equals(a2)) {
    doSomething(a1);
  } else {
    doSomethingElse(a2.propertyName);
  }
}

someFunction(myFunc);
```

Or, even convert it back a function expression without the arrow function notation.

```csharp
const myFunc = function(a1, a2) {
  if (a1.equals(a2)) {
    doSomething(a1);
  } else {
    doSomethingElse(a2.propertyName);
  }
}

someFunction(myFunc);
```

We're going to spend a lot of time working with anonymous arrow functions, as that is the way most JavaScript code is written and will be a skill you need to master.

