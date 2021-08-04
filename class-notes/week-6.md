# Week 6 - Saturday, May 22nd

### Topics Covered

Thinking about how to solve problems with a computer.

Arrays, For loop

```javascript
for (var i = 0; i < colors.length; i++)
{
  console.log(i + ": " + colors[i]);
}

```

The code below

```javascript
let numbers = [1, 2, 4, 3];

for (let i=0; i<numbers.length; ++i) {
    let num = numbers[i];
    console.log(num);
}
```

is the same as

```javascript
let num;
let numbers = [1, 2, 4, 3];

num = numbers[0];
console.log(num);

num = numbers[1];
console.log(num);

num = numbers[2];
console.log(num);

num = numbers[3];
console.log(num);
```

In the second case, you have a lot more code, and it's just repeating the same thing, except you're replacing the index you are using to access the element in the array with a number one higher.

Also, in the second case, you don't have a way to know when to stop repeating the two lines of code to extract the number and print it out on the console. What if there are a billion numbers in the array? You wouldn't want to repeat the statements on lines 4-5 one billion times. And, you may not know ahead of time how many numbers are in the array, so it's not even possible to write the code ahead of time as we're doing above.

That's why there is a for loop.

It allows you to write the statements that you want to execute for each element a single time within the body of the for loop and it provides a mechanism to track what position your are currently at and when to stop.

```text
for (let=0; i<numbers.length; ++i) {
    num = numbers[i];
    console.log(num);
}
```

#### Class Video

{% embed url="https://www.youtube.com/watch?v=8KHZ5x1BlKo" %}



### Homework

Turn in the assignment by either showing me your solution, or pasting in the code from the jscript exercises files into Canvas for the assignment jscript-hw-2.

Download and unzip the project file from the github repository.

{% embed url="https://github.com/annechinn/jscript-hw-2" %}

I have included three JavaScript files in the index.html file. Each will be loaded and any statements in any of the three files will be evaluated.

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script src="exercise1.js"></script>
  <script src="exercise2.js"></script>
  <script src="exercise3.js"></script>
</body>
</html>
```

You can open any of the exercise files and start working on it. If you want to prevent the code from one of the files from being evaluated while you are working on another exercise, then just comment out those lines in the html file.

For example, to comment out exercise1.js, you would

```markup
<body>
  <!-- <script src="exercise1.js"></script> -->
  <script src="exercise2.js"></script>
  <script src="exercise3.js"></script>
</body>
```

#### Exercise 1

The code for this exercise is in the source file exercise1.js

#### Exercise 2

The code for this exercise is in the source file exercise2.js

#### Exercise 3

The code for this exercise is in the source file exercise3.js.

### Solutions

#### Exercise 1

```javascript
let sallysAge = 10;
let jonsAge = 9;
let bobsAge = 12;

// write the code to figure out what the largest age
// is among the three values above.
// write the answer to the console.
// expect the console output to be
// 12

// hint: you will need to use a variable to 
// track the largestAge.

if (sallysAge > jonsAge && sallysAge > bobsAge) {
  console.log(sallysAge);
}
else if (jonsAge> sallysAge && jonsAge > bobsAge) {
  console.log(jonsAge);
}
else {
  console.log(bobsAge);
}
```

#### Exercise 2

Step 1

```javascript
for (let i=0; i<numbers.length; ++i) {
  console.log(numbers[i]);
}
```

Step 2

```javascript
let total = 0;
for (let i=0; i<numbers.length; ++i) {
  let number = numbers[i];
  total = total + number;
}

console.log(total);
```

#### Exercise 3

Sorry,  I picked a bad name for the array of words. I originally named it letters \(not sure why\). I renamed it words here. Hopefully, it now makes more sense.

```javascript
let letters = ["cat", "cut", "bat"];

// use a for loop to check each element in the
// array and write to the console "the word cut is in the list", 
// if the word "cut" is in the list.

for (let i=0; i<letters.length; ++i) {
  let word = letters[i];
  if (word === "cut") {
    console.log("the word cut it is in the list");
  }
}
```

Talked about in class

```javascript
function isWordInArray(array, wordToLookFor) {

  for (let i=0; i<array.length; ++i) {
    let word = array[i];
    if (word === wordToLookFor) {
      return true;
    }
  }

  return false;
}

console.log(isWordInArray(["bar", "bat"], "bottle"))
```

### 

