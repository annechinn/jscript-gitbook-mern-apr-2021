# The Call Stack

As we have already learned, your JavaScript code consists of statements, with some statements contained within function. The statements are compiled by the JavaScript engine into machine instructions that the CPU executes.

How function calls are executed is an important concept to understand because it has to do with how the memory associated with the variables in our program are stored. And this will help you better understand what is happening when an assignment from one variable to another happens.

When a program is executing, all of the machine instructions, as well as the data associated with the variables, are loaded into RAM. 

When the CPU encounters an instruction to execute a function, it sets up a special area in RAM to set up the context for the function call. This special area is called the Call Stack.

Think of a Call Stack as vertical array, where new items are added and removed from the top only. It's known as a last-in-first-out, or LIFO, data structure.

![](https://lh4.googleusercontent.com/W46nRTVwXW_DRtdV-BiRk0DPL2bolB7Bk-WujrDpWe7aBYUVvJdR_HZoi9NMGMLVevIxSpvZN2lcBBntay4ITgWghcObnAL4CbShVOCWgXLAv4CBpMXafYLXHvpzynSUmV70owR-JQ)

The CPU builds what is called a "Stack Frame", for each function call and pushes it onto the Call Stack to prepare for its execution. The Stack Frame stores the values for variables such as the function parameters, local variables declared within the function, and a return value, if there is one. 

When you are in the Chrome Developer Tools debugger, you can see the Call Stack in action on the right panel in the lower half.

Below is the source code for the invocation of three successive function. level1 is called, and inside level1 a call is made to level2, and inside level2 and call is made to level3. So the Call Stack will grow to have three stack frames pushed onto it by the time the statements within level3 are reached.

```javascript
function level3() {
    let l3Var = "level3";
    console.log("enter level3");
    console.log("exit level3");
}

function level2() {
    let l2Var = "level2";
    console.log("enter level2");
    level3();
    console.log("exit level2");
}

function level1() {
    let l1Var = "level1";
    console.log("enter level1");
    level2();
    console.log("exit level1");
}

level1();
```

In the three images below, moving from the first to the third, the highlighted boxes are showing how the Call Stack is growing as the code moves down into another nested function.

In the first image the program is within the function level1 and the Call Stack is showing level1. In the second image, we have stepped into the call to level2 from the function level1. So we are currently two levels deep in function calls and we can see that in the Call Stack view on the right.

In the third image, I have stepped one level deeper into the function level3 and again you can see that in the Call Stack on the right.

![](../.gitbook/assets/image%20%28305%29.png)

![](../.gitbook/assets/image%20%2886%29.png)

![](../.gitbook/assets/image%20%2824%29.png)

Below, the code has completed execution of the function level3 and is back in the function level2, just after the call to level3. And as you can see, the Call Stack no longer is showing the function level3 because it has completed, so the CPU pops that stack frame off the Call Stack. 

![](../.gitbook/assets/image%20%28388%29.png)

This pushing and popping pf stack frames onto and off the Call Stack is the essence of how the memory for the variables associated wit a function call works. 

It is important to understand where the data associated with the variables stored on the stack is located. The data associated with variables that are storing objects are stored in another memory area called the heap. The Call Stack allocates a space to hold the reference to the data in the heap, but the actual data associated with the variable is not stored in the Call Stack area.

Here is a graphic that shows the relationship to the variables stored in the heap and where their value is stored \(the char data type is not available in JavaScript, but is in many other languages, such as C\# and Java\). What's important to take away from this graphic is that the data associated with objects, such as an array or user-defined object, has a reference to the actual data associated with the variable, not the actual value. The actual value is stored in the heap memory area.

![](../.gitbook/assets/image%20%28121%29.png)

In the next section on Assigning Variables, you'll see why this is important.

