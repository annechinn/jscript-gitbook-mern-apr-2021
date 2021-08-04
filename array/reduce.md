# Reduce

The reduce method is a bit tricky, but once you get used to it you will find it's a very powerful method.

The purpose of the reduce method, is to return a single value at the end of iterating over each element in the array and to allow a function you provide to incremental modify the value as the reduce method iterates through the items.

 For the basic use case, there are two parameters:

* **function\(acc, next\)**: 
  * **acc**: the value that is going to be the eventual return value from the reduce method. This is passed to your function for each iteration.
  * **next**: the element in the array for the current iteration.
* **initial-value**: this is the initial value for the accumulator.

Examples are the best way to understand how this method works.

The goal is to use the reduce function to sum the elements in the array.

```javascript
let array = [1,2,3,4,5];
let sum = array.reduce((acc, next) => {
    return acc + next;
}, 0);

console.log(sum); // 15
```

Again, we can separate the anonymous function and make it a little easier to understand.

**func** is the function we are passing in for the first parameter to the reduce method. It takes two parameters: 

* **acc**: the accumulator, or the eventual return value from the reduce method.
* **next**: the element in the array for the current iteration

We are also passing in 0 for the second parameter to the reduce method. This is the initial value for the accumulator. We want the sum to start out at zero.

```javascript
let func = (acc, next) => {
    return acc + next;
}

let array = [1,2,3,4,5];
let sum = array.reduce(func, 0);
console.log(sum); // 15
```

It helps to to walk through implementing the reduce method yourself as a function.

```javascript
function reduce(array, func, initialValue) {
    let acc = initialValue;
    for (let i=0; i<array.length; ++i) {
        acc = func(acc, array[i]);
    }
    
    return acc;
}
```

What's really powerful about the reduce method is that it doesn't matter what kind of data you are building for your eventual return value, or what the initial value is. It's just a method that iterates over each of the items and allows you to build up a return value based on performing some operations on each element.

For example, we can build a object using the reduce method, that counts the number of students for each teacher.

```javascript

let classes = [
    { teacher: 'msSmith', students: ['bob', 'mary', 'jon'] },
    { teacher: 'mrJones', students: ['bill', 'sally']}
    ];
  
  
let result = classes.reduce((acc, next)=> {
  acc[next.teacher] = next.students.length;
  return acc;
},{});
  
  
console.log(result);

// {
//    "msSmith": 3,
//    "mrJones": 2
// }

```

