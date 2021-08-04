# Week 7 - Wednesday, June 2nd

#### Review Exercises

I created a new video where I just show the solutions to the exercises we did in class. One thing I am noticing during class is that you are often not understanding what the function is expected to do before you start coding. That should be the first step. You should be able to outline the problem you need to solve before you begin. 

* What is the name of the function?
* What is the task the function is supposed to achieve?
* What is the input data \(parameters\)?
* What is the return value of the function?
* What variables do I need to accomplish the task?
* What steps does the function need to perform to accomplish the task?

Watch through the video and pause it after I have given the description of the function and try to think through the steps above before you begin coding.

Next, start to setup your function step by step.

```javascript
// declare the function and its input parameters
function max(num1, num2) {
}
```

```javascript
function max(num1, num2) {
    // function needs to return the max number
    // requires a comparison
    // (num1>num2)
    // if num1 > num2 then num1 is max number
    // else num2 is max number
    // 
    // translate these steps into javascript code
    if (num1 >num2) return true;
    else return false;
    
    // or, a more concise version 
    return (num1>num2);
    
}
```

For this week's assignment, watch through this video and attempt to do these on your own, working through the steps above before starting to code.

{% embed url="https://www.youtube.com/watch?v=MIX4IGZjRRg" %}

```javascript
function longestWord(sentence) {

  let longestWordSeen = "";
  const words = sentence.split(" ");
  words.forEach(word=>{
    if (word.length>longestWordSeen.length) {
      longestWordSeen=word;
    }
  });

  return longestWordSeen;
}

console.log(longestWord ("the cow jumped over the moon"));
```

```javascript

function numbsInRange(array, min, max) {

  let results = [];
  array.forEach(num=> {
    if (num>=min && num<=max) {
      results.push(num);
    }
  });

  return results;
}

console.log(numbsInRange([ 1, 2, 3, 5, 8], 1,5));
console.log(numbsInRange([ 1, 2, 3, 5, 8], 1,3));
```

```javascript
function calculateGrade(grades) {
  let total = 0;

  grades.forEach((grade) => {
    total += grade;
  });

  let average = total / grades.length;

  if (average >= 0 && average <= 60) {
    return "F";
  } else if (average >= 61 && average <= 70) {
    return "D";
  } else if (average >= 71 && average <= 80) {
    return "C";
  } else if (average >= 81 && average <= 90) {
    return "B";
  } else if (average >= 91 && average <= 100) {
    return "A";
  }
  // returns 'A', 'B', 'C', 'D', 'F'
}

console.log(calculateGrade([65, 56, 78, 89, 90]));

console.log(calculateGrade([23, 56, 78, 89, 90]));
```

#### Review Git

Go to the section below and review the content carefully, watching each of the videos provided.

### Git Bash

It is easier to use the Git Bash shell to perform git operations because it has nice support for color-coding your branches. In Wednesday's class no on seemed to have Bash as a option for the Terminal window shell. 

I've been researching, and found a few bits of info that might help.

{% embed url="https://stackoverflow.com/questions/65676287/git-bash-is-not-showing-up-as-a-terminal-option-in-vscode" %}

{% embed url="https://stackoverflow.com/questions/65438333/how-to-add-git-bash-to-vscode" %}

{% embed url="https://vishnupadmanabhan.com/styling-git-bash/" %}



