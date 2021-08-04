---
description: Learn about the basic functionality of arrays.
---

# Array Intro

JavaScript has a built-in object for representing lists of data. 

Arrays are just a data structure for holding a collection of items. The syntax looks like this. You can store any type of data in an array.

![](../.gitbook/assets/image%20%28369%29.png)

```javascript
let arr = [1, 2, 3];
let arr2 = ["apples", "oranges", "grapes"];
```

An array is a list, and items can be accessed by their position in the list relative to the beginning. This is know as their index. Array indices are zero-based, so to access the first element you would specify 0 for the index.

```javascript
let arr = [1, 2, 3];
let firstElement = arr[0];
let secondElement = arr[1];

console.log(firstElement);  // 1
console.log(secondElement); // 2
```

And to access the last element in the list, the index would be the length of the array minus 1.

```javascript
let arr = [1, 2, 3];
let lastIndex = arr.length-1;
let lastElement = arr[lastIndex];
console.log(lastElement); // 3
```

You can also store objects in an array.  For example, you may have a list of users or a list of products in a shopping cart. 

```javascript
let jon = { firstName: 'Jon', lastName: 'Jones' };
let sally = { firstName: 'Sally', lastName: 'Smith' };

let users = [ jon, sally ];
        
let products = [
    { name: 'basketball', price: '29.99' },
    { name: 'tent', price: '49.99' }
    ];
```

You can change an element in the array using the bracket notation and an assignment operator.

```javascript
let array = [1,2,3,4,5];
array[0] = 6;
console.log(array); // [6,2,3,4,5]
```

### Array Methods

An array is an object, and has methods for performing actions on the elements in the array, such as adding and removing elements from the array.

```javascript
let arr = [1, 2, 3];
arr.shift(); // removes the first element
console.log(arr); // [2,3];
```

```javascript
let arr = [1, 2, 3];
arr.push(4); // adds an element to the end
console.log(arr); // [1,2,3,4];
```

```javascript
let arr = [1, 2, 3];
arr.pop(); // removes the last element
console.log(arr); // [1,2];
```

JavaScript arrays are dynamically sized, meaning that it will never run out of room. You can continue to add new items, and the array will grow as needed.

JavaScript arrays have another characteristic that is unusual. It allows different types of data to be stored in the list. For example, you can store an object, and a string, and a number, all in the same array. It's not a common use-case, but is another example of the flexibility of the JavaScript language.

```javascript
let myWierdList = [ 1, 'hello', true, {name: 'Joe'} ];
```

