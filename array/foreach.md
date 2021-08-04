# ForEach

### Overview

In the section on looping, we introduced the for loop. Arrays are the frequent source of the items we want to iterate over, and the Array object has a special method for the case when you want to iterate through every element in  the array.

The method takes a function that will be called with the next element in the array passed as a parameter.

The forEach loop can replace the use of the for loop when you want to iterate over every element in the array.

```javascript
let array = [1,2,3,4,5];
array.forEach((x)=> console.log(x));
```

```javascript
let array = [1,2,3,4,5];

let sum = 0;
array.forEach((x)=>sum+=x);
console.log(sum);
```

### No Break and Continue Allowed

You cannot use the break and continue keywords to break out of a forEach loop. This is because the implementation of the forEach method is calling out to your function from the body of its loop.  Let's work through this example to understand. 

When an anonymous function is passed to the forEach method, and it includes multiple statements, you can be tricked into thinking that the body of your function is part of the the body of the for loop that is being executed within the forEach method's implementation.

```javascript
let array = [1,2,3,4,5];
array.forEach((x)=> {
    console.log(x);
    });
```

Let's imagine that the following code sample is what the implementation of the forEach method looks like. It uses the for loop to iterate over each element in the array, and it calls the function passed into it, with the next array element as the parameter, for each element.

```javascript
for(let i = 0; i < array.length; i++) {
    func(array[i]);
}
```

Now, we have our code, and it is calling the forEach method on the array. 

```javascript
let arr = [1,2,3];
arr.forEach((x)=> {
    console.log(x);
    });
```

But this is actually equivalent to a function expression stored in a variable. When you look at it as a separate function, hopefully it makes more sense why you cannot add a break or continue statement in your function.

```javascript
let arr = [1,2,3];

let doThis = (x)=> {
    console.log(x);
}

arr.forEach(doThis);
```

A break or continue statement in our function is not a syntactically correct place for it to be. It doesn't make sense for it to be in the middle of a function body. They can only be placed within a for, while, or do/while loop.

{% hint style="info" %}
It is recommended that you use the forEach method in place of the for loop, as it is more concise and less prone to errors.
{% endhint %}

