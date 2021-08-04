# For Loop

The for loop is an entry-controlled loop and is used more frequently then the while and do/while loop. It has a more complex syntax to control the entry/exit conditions.

There are three parts to the test condition, separated by semi-colons.

```javascript
for (initialization; condition; post-expression) {
    // statements
}
```

**Initialization**: The initialization expression is where you perform any initialization before the first iteration begins. Typically, a for loop has a variable that is counting the iterations and it would be initialized here. If you define the variable with the let keyword, the variable will only be accessible within the scope of the loop.

**Condition**: The condition is an expression that is evaluated once before every iteration. The statement inside the loop is executed only when the condition evaluates to true. The loop is terminated if the condition evaluates to false. 

**Post-expression**: The for loop statement evaluates the post-expression after each loop iteration. Typically, you update the counter variable in the post-expression.

```javascript
let sum = 0;

// initialization:  let i=0;
// condition: i<10;
// post-expression: ++i
for (let i=0; i<10; ++i) {
    sum+=i;
}
```

You can go from a higher starting value and decrement as well.

```javascript
let sum = 0;

for (let i=10; i>0; --i) {
    sum+=i;
}
```

It is possible to use a variable that is not defined in the initialization component of the for loop, but should be avoided unless there is a reason requiring it.

```javascript
let sum = 0;
let i = 0;
for (; i<10; ++i) {
    sum+=i;
}
```

It is also possible to leave out the condition, but would require the use of a break statement in the loop to force an exit. Again, this is not a recommended technique and should be avoided. The post-expression can also be omitted, but it's rather non-sensical to do so, when a while loop would achieve the same goal with more clarity.

```javascript
let sum = 0;

for (let i=0; ; ++i) {
    sum+=i;
    if (i==10) break;
}
```

