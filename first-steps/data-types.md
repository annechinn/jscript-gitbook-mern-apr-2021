---
description: Defining data structures to hold data.
---

# Primitive Data Types

What kind of values can we assign to variables?

There are two categories of values. The first category is primitive data types.

### Primitive Data Types - Value Types \(String, Number, Boolean, Undefined, Null\)

A primitive data type is one that is a fundamental unit of data provided by the programming language. It cannot be broken down any further. As you'll see later, they can be used to build more complex data types, called objects.

### Number

In JavaScript there is a single data type for representing all numeric data. A number is used to  represent integers as well as floating point numbers. In order to store such a wide range of numbers, JavaScript uses 64 bits of storage in memory to store a number.

In other, lower-level languages, such as C/C++, there is a much larger range of data types to represent numbers. You must specify what type you are using, such as an int, double, unsigned int, etc. This allows the programmer to be more precise in specifying the amount of memory the variable will require and not waste extra space. 

Higher-level languages, like JavaScript, prioritize ease-of-use over performance, and this is one example of that.

```javascript
let age = 25;
let temp = 98.6;
```

You can do the expected arithmetic operations with numbers.

```javascript
let age = 25;
let ageNextYear = age + 1;

const tipRate = .15;
let total = 10.50 + (10.50*tipRate);
```

### String

A string represent a sequence of characters. Strings must be enclosed in quotes. There are three different ways to quote a string:

You can surround the string with double quotes

```javascript
let message = "Hey, how are you?";
```

Or single quotes

```javascript
let message = 'Hey, how are you?';
```

Or back-ticks, which allows you to substitute the value of a variable or an expression into the string.

```javascript
let baseAmount = 10.00;
let tipRate = .15;
let tip = `You should tip ${baseAmount*tipRate} dollars`;
```

If you need to embed a quotation mark inside a string you need to escape it using the back-slash symbol.

```javascript
let message2 = 'What\'s up?';
```

You can concatenate string with the "+" operator

```javascript
let name = "Anne";
let message = "Hey, how are you, " + name;
```

A value of a different type will be converted to a string when it is concatenated with another string.

```javascript
console.log("Hello, " + "how are you?"); 
```

### Boolean

The boolean datatype describe data that has only two values: true or false.

```javascript
let ready = false;
```

A boolean can result when an expression is evaluated. The expression on the right of the assignment operator will evaluate to false, and the value false will be assigned to the variable on the left of the assignment operator.

```javascript
let age = 14;
let oldEnoughToVote = (age >= 18);
```

### Undefined and Null

JavaScript has two special primitive types that each support a single value only, which is the name of the type. Unlike the number datatype, which can represent any numeric value, the undefined datatype holds the single value of undefined, and the null datatype holds the single value null. 

We discussed these two types in the previous section on variables. 

The undefined value is the data value that is stored in a variable before it has been assigned a value.

The null value is the data value that is stored in a variable when you want to indicate that the variable does not currently have a value. The storage area for holding the value is empty.

