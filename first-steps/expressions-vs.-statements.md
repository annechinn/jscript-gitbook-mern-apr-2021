# Expressions vs. Statements

**Expression** -  a snippet of code that evaluates to a value.

**Statement** - a snippet of code that performs an action.

### Expressions

#### Primary Expression - a single value

Primary expressions refer to stand alone expressions such as literal values, certain keywords and variable values.

```javascript
let total = 0;

'hello world'; // A string literal
23;            // A numeric literal
true;          // Boolean value true
total;         // Value of variable total
this;          // A keyword that evaluates to the current object
add(1,2);      // A function call result
```

#### Arithmetic Expression - an arithmetic operation that evaluates to a numeric value

```javascript
// 10 + 3 is evaluated by the JS Engine to return the value 13

> 10 + 3;
13


// 10 * 3 is evaluated by the JS Engine to return the value 30
// which is then passed as the argument to the console.log method

console.log(10*3); // 30

```

#### String Expressions - evaluate to a string

```javascript
// the line is evaluated to return 'Hello World'
> 'Hello' + ' ' + 'World'
'Hello World'
```

#### Logical Expressions - evaluate to true of false \(boolean values\)

```javascript
> 10 > 5
true

> let num1 = 10;
> let num2 = 20;
> num1 + num2   // num1 > num2 evaluates to false
false

```

#### Left-hand Side Expressions - anything that can be assigned a value

Any variable that can be assigned a value can be evaluated as an expression

```javascript
let sum = 0;

// JS Engine evaluates the value of sum and returns 0
>sum
0

> let user = { firstName: 'Sally', lastName: 'Smith' }

// JS Engine evaluates the value of user.name and returns 'Sally'
> user.name
'Sally'

> let arr = ['apples', 'oranges', 'grapes'];
// JS Engine evaluates the value of arr[0]  and returns 'apples'
> arr[0]
'apples'


```

#### Assignment Expression

The value of an assignment expression is the value of the right-side operand. As a side effect, the = operator assigns the value on the right side to the value on the left side.

```javascript
// JS Engine evaluates the assignment are return the new value

> arr[0] = 'cherries'
'cherries'
```

The result of a function call can be used in an assignment expression.

```javascript
> let answer;

> function add(num1, num2) {
    return num1 + num2;
}

// JavaScript Engine evaluates the call to add and returns the result
> add(1, 2)
3

> answer = add(1, 2);
3
```

### Statements

A statement is an instruction to perform a specific action. There are two types of statements.

#### Declarative

Includes statements for creating a variable or a function.

```javascript
let total = 0;

function add(num1, num2) {
    return num1 + num2;
}
```

#### Expression Statements

Wherever you can use a statement, you can write an expression.

```javascript
let total = 0; // statement

// this is an assignment expression and also a statement
total = total + 1;
```

The reverse is not allowed. You cannot use a statement in place of an expression.

```javascript
let total = let sum; // not allowed

console.log (let total);
```

#### Conditional Statements

Conditional statements execute statements based on the value of an expression. Examples of conditional statements includes the if/else and switch statements.

```javascript
let age = prompt("How old are you?");
if (age >= 18) {
    /* execute statements */
}

let counter = 0;
while (counter < 10) {
    /* execute statements */
    counter = counter - 1;
}
```

