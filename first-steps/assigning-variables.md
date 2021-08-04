# Assigning Variables

Where the data associated with a variable is stored has important implications for how the data is copied from the source variable to the destination when an assignment is executed.

### Assignment Context

First, we need to consider the different contexts within which an assignment occurs.

#### The Return Value of a Function Call

The result of a call to a function can be assigned to a variable.

```javascript
let answer = add(num1, num2);
```

#### Function Parameters

Function parameters within a function are variables that will be assigned the value passed in as a parameter to the function.

```javascript
function add(num1, num2) {
    return num1 + num2;
}
```

**Assignment of One Variable Value to Another**

Whenever we assign one variable to another, without a function call involved.

```javascript
let num1 = 1;
let num2 = num1;
```

### Assignment - Copy By Value

The term copy by value means that when an assignment occurs, the value stored in the source variable is copied to the destination variable. But, what is a value?

For primitive data types, such as a number, or a boolean value, it is obvious what the value is.  It is the literal number or boolean value.

But for objects, this is not the case. The value of a variable that is storing an object is not a copy of the object's data, but rather a **reference** to the location of the data within the heap memory area. A reference is a memory address, in this case within the heap area of RAM.

When you assign the value of one object variable to another you are copying the **reference** to the data location in the heap. This means that you now have two variables both having as their value the same reference to the same location  in the heap and modifications made to the object through either variable will be modifying the same object.

```javascript
let p1 = { name: 'Joe' }
let p2 = p1;
p2.name = 'Sam';
console.log(p1);  // {name: 'Sam'}
console.log(p2);  // {name: 'Sam'}
```

It also means that when you perform any kind of assignment, be it passing parameters to functions, or assigning the return value of a function to a variable, these all work the same way. Whenever an object is assigned, it is assigning the reference to the data stored in the heap, not the actual data.

The take-away from all of this is that you will always be referring to the same object when you assign on object to a new variable and modifications from either variable are referring to the same object.

![](../.gitbook/assets/image%20%28131%29.png)

![](../.gitbook/assets/image%20%2834%29.png)

