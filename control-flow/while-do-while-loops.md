# While Do/While Loops

### While Loop

The while loop will test the entry condition before each iteration and only perform the next iteration if the entry condition is true.

A while loop is what's known as an entry-controlled loop, because the condition is tested prior to entering the loop body.

```javascript
let continuePlaying = confirm("Want to play a game?");
let age = 20;
while (continuePlaying) {
    let guess= prompt("Guess my age");
    if (guess == age) {
        alert("You're right. We're all done.");
        continuePlaying = false;
    }
    continuePlaying = confirm("Want to try again?");
}
```

### Do While Loop

This loop should be used when you want to execute the block of code once before testing the exit condition. The do while loop will test the exit condition at the completion of each iteration. If the exit condition is false, the loop will exit. 

The do/while loop is what's known as an exit-controlled loop, because the condition is tested prior to exiting the loop body.

```javascript
let convert = true;
do{
   cosnt binaryNum = 
      prompt("Enter the binary number to convert");
   let decimalNum = convertBinaryToDecimal(binaryNum);
   alert(`The answer is: ${decimalNum}`);
   convert = confirm("Do you want to convert another?");
} while (convert);
```

### Exercise

Prompt the user for a number between 1 and 100, if they enter a number, then start with the number entered and calculate the sum of every number from 1 through the number entered. Use the alert function to return the sum.

For example, if 10 is entered the sum would be 1+2+3+4+5+6+7+8+9+10 = 55.

![](../.gitbook/assets/image%20%2895%29.png)

![](../.gitbook/assets/image%20%2855%29.png)

