# Scope

Scope is a policy that manages the accessibility of variables.

### Global Scope

Variables defined outside of a function are in the global scope. Variables inside the Global scope can be accessed and altered in any other scope.

```csharp
let globalVar = "Global Hello";

function sayHello() {
    alert(globalVar);
    
    globalVar = "I'd rather say Hi";
    alert(globalVar);
}
```

#### Web Browser Global Scope

In the context of the JavaScript runtime within the web browser, any variables declared in your script code that is not contained within a function is in the global scope.

The window and document objects, supplied by the JavaScript runtime are also in the global scope.

#### Global Variables Can Collide

If there are two global variables with the same name, there is a name collision. In this case the JavaScript engine will process the scripts in order and the most recent declaration and modifications will be used.

{% hint style="info" %}
Global variables should be avoided if possible.
{% endhint %}

```csharp
// script1.js

let globalVar = "Script 1 Global Hello";
```

```csharp
// script2.js

let globalVar = "Script 2 Global Hello";
```

```csharp
<script src="script1.js"></script>
<script src="script2.js"></script>
```

### Function Scope

Variables declared with the let or const keyword inside a function are only visible within the function only.

```csharp
function sayHello() {
    let message = "Hello!";
    alert(message);
}

alert(message); // message is not defined
```

Functions can access global variables

```csharp
let message = "Hello";

function sayHello() {
    alert(message);
}
```

But a variable with the same name within the function will be used in place of the global variable.

```csharp
let message = "Hello from outside";

function sayHello() {
    let message = "Hello from inside";
    alert(message); // Hello from inside
}
```

### Code Block Scope

Variables declared with the let or const keyword inside a code are only visible within the code block only. The scope of a code block is equivalent to the scope of a function.

```csharp
if (true) {
    let message = "Hello!";
    alert(message);
}

alert(message); // message is not defined
```

### Lexical Scope

Lexical Scope has to do with scope in situations where there are nested code blocks and the accessibility of a variable outside of a code block to the code within a nested code block.

The engine determines the nesting of scopes just by looking at the JavaScript source code, without executing it.

The inner function scope can access variables from the outer function scope.

```csharp
function f1() {
    const outerScope = "outer scope";
    
    if (true) {
        const innerScope = "inner scope";
        console.log(outerScope);  // "outer scope";
        console.log(innerScope);  // "inner scope";
    }
    
    console.log(outerScope);  // "outer scope"
    console.log(innerScope);  // Reference Error: not defined
}
```

### Scope Summary

* Scopes are created by code blocks.
* A let or const variable is scoped within a code block, function, or module.
* A let or const variable defined within a code block is only visible within the code block.
* Lexical Scope can be determined by looking at the code. If a variable is within the current code block, or your code is referencing a variable that is visible to your nested code block,  it is within your scope.

