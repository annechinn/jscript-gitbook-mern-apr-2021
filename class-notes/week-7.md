# Week 7 - Saturday, May 29th

### Class Video

{% embed url="https://www.youtube.com/watch?v=Eu6KfHsvrm8" %}

### Topics Covered

#### Let vs Var keyword

The let keyword was added to the JavaScript language in 2015. It was added as a replacement to the use of the var keyword because there are some problems with the var keyword.

Variables declared with the var keyword do not obey scope rules. Any variable declared with the var keyword is considered to be a global variable, except in the case when it is declared within a function.

The take-away is that you should always use let \(or const\) to declare your variables instead of var.

```javascript
for (var i = 0; i<array.length; ++i) {
    console.log(i);
}

// i is valid outside of the for loop
console.log(i);
```

```javascript
if (3 > 2) {
    var i = 0;
    console.log(i);
}

// i is valid outside of the if loop
console.log(i);
```

```javascript
function test() {
    var i = 0;
}

// i is not defined outside of a function. this
// is the only case the follows expected scope rules
console.log(i):
```

#### Functions

We worked through several functions to practice basic setup and executing expressions using best-practices.

```javascript
function max(a,b) {
  if (a>b) {
    return a;
  }
  else {
    return b;
  }
}

// the body block begin/end braces, {} are not necessary
// when there is a single 

function max(a,b) {
  if (a>b) return a;
  else return b;
}
```

```javascript
function isLandscape(width, height) {
  if (width>height) return true;
  return false;
}

// the return true and return false are not necessary
function isLandscape(width, height) {
  return (width>height);
}
```

```javascript
// using a for loop to generate a string of start
// num=3 => ***
// num=10 => **********

function stars(num) {
  let answer = "";
  for (let i=1; i<=num;++i) {
    answer+="*";
  }
  return answer;
}
```

```javascript
// divisible by 3 ==> Fizz
// divisible by 5 ==> Buzz
// divisible by both 3 and 5 ==> FizzBuzz
// not divisible by 3 or 5 ==> input

function fizzBuzz(num) {
  const divisibleBy3 = num%3 ===0;
  const divisibleBy5 = num%5===0
  
  // this test needs to happen first to
  // catch the case because a number lik 15
  // will also match the other cases and 
  // you want it to match this case.
  if (divisibleBy3 && divisibleBy5) {
    return "FizzBuzz";
  }
  else if (divisibleBy3) {
    return "Fizz";
  }
  else if (divisibleBy5 ) {
    return "Buzz";
  }
  else {
    return num;
  }
}


// this is also allowed
// some style-guides say they want you to always
// use {} for code blocks, even if there is a single
// statement in the block. the exception
// would be when the condition is very small,
// so the overall line is very small and it makes
// it more readable.
// in this case it's kind of borderline. the
// first line is getting a little long, but the overall
// code is pretty readable in the condensed version.

function fizzBuzz(num) {
  const divisibleBy3 = num%3 ===0;
  const divisibleBy5 = num%5===0
  
  if (divisibleBy3 && divisibleBy5) return "FizzBuzz";
  else if (divisibleBy3) return "Fizz";
  else if (divisibleBy5) return "Buzz";
  else return num;
}

```

#### Passing Functions to Functions

Functions in JavaScript are objects, just like an array or a string is an object. You can pass a function  as an argument to another function, allowing the function that is receiving it as a parameter to execute the function.

```javascript
// this function accepts a function as a parameter
function doThis(func) {
    // to execute the function, it needs to be called
    func();
}

function sayHello() {
    console.log(sayHello);
}

// sayHello is being passes as a function, it is not
// being called. To call a function you must use
// the (), i.e. sayHello()

doThis(sayHello);

// you can also pass in the function directly without having
// to declare it

doThis(function sayHello() {
    console.log(sayHello);
});

// and it can be further shortened to
doThis(() => {
    console.log(sayHello);
});

// in all these cases, the function sayHello isn't being called until 
// inside the doThis function when it is called like func();

```

### Array forEach

The forEach method takes a function as a parameter and the function will be called for each element in the array and the function will be passed the current element.

```javascript
numbers = [1, 2, 3, 4];

function forEach(array, func) {
  for (let i=0;i<array.length; i++) {
    func(array[i]);
  }
}

// we can pass in a function to the Array.forEach method

function logNum(num) {
  console.log(num);
}

numbers.forEach(logNum);

// or an annonymous arrow function
numbers.forEach(num=>console.log(num));


let total = 0;
numbers.forEach(num=>total+=num);
console.log(total);


let maxNum = 0;
numbers.forEach(num=> {
  if (num>maxNum) {
    maxNum = num;
  }
}
console.log(maxNum);
```

### Practice

I've provided a bunch of sample functions to practice. You should be starting to feel more comfortable with understanding what the function is asking you to do and thinking about how to approach solving the problem. You don't need to solve all of these, but push yourself to solve some that are beyond your comfort level.

For any of the problems that require looping you can create your own for loop or use the Array.forEach method.

```javascript
write a function called sum that accepts three parameters, all numbers,
and returns the sum of the three numbers.

call the function a log the result to the console.
```

```javascript
write a function named longArray that accepts an array and return true if the 
number of elements in the array is greater than 5, otherwise false.

sample call

console.log(longArray([1, 4, 3, 6, 5, 10])); // return true
console.log(longArray([1, 4, 3, 6])); // return false
```

```javascript
write a function called findElement, that accepts an array of numbers
and a number to search for in the array.

if the number is in the array, return true. otherwise return false;

sample call

console.log(findElement([1, 2, 5], 2)); // returns true

console.log(findElement([1, 2, 5], 3)); // returns false
```

```javascript
write a function called logMessage that accepts two parameter,
firstName and lastName, and creates a message by concatenating
the input parameters together to form a new string and returns the 
new string.

sample call (note the spaces between the words)

logMessage("Anne", "Chinn") should return "Hello Anne Chinn".
log the return value to the console.
```

These ones are more challenging, using several different things we've been learning to build a larger series of steps.

```javascript
write a function numsInRange that accepts an array of numbers
and a min and max value. The function should return a new array
that contains all of the numbers in the input array that are 
between min and max (including min and max).

you can use the Array.filter method for this. We didn't use filter
in today's class, but did in last Wedneday's class. You can also search
for it on google to see how to use it. You can also write your own
for loop.

sample calls
console.log(numbsInRange([ 1, 2, 3, 5, 8], 1,5)); // rturns [1,2,3,5];
console.log(numbsInRange([ 1, 2, 3, 5, 4], 2,5)); // rturns [2,3,4,5];

```

```javascript
write a function called calculateGrade, that takes an array of grades,
such as [80, 86, 75, 90], and calculates the average of the grades.

NOTE: average = sum of all of the grades/number of grades.

after you have calculated the average, determine the letter grade 
for that corresponds to the class average. So we want to return the average
letter grade for the test.

0-59: F
60-69: D
70-79:C
80-89: B
90-100:A

Hints: 

You'll need to use an if/else if block to test whether the average grade is
>= the lower number and <= the higher number in each range.

console.log(calculateGrade([23, 56, 78, 89, 90]));  // "D"


```

```javascript
write a function called longestWord that accepts a string and 
returns the longest word in the string.

sample call

console.log(longestWord ("the cow jumped over the moon")); // return "jumped"

hints:
enter the string in the console and see what it returns. you can
also look up the String.split method on google
> "the cow jumped over the moon".split(" ")

the function you need to write is very similar to the one we did to
return the maximum number in an array of numbers. 

Re-watch that section of the class video to see how we calculated 
the maxNum in an array of number.

in this case you need to store the longest word you've seen so far 
and update that value when the length of the next word in the longest
seen so far.

```

### Resources

{% embed url="https://javascript.info/" %}

### 



