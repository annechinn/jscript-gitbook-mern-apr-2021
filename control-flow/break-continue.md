# Break/Continue

These can be used in any of the loop constructs.

### Break

If you need exit out of a loop in the middle of an iteration you use the break statement.

```javascript
while (true) {
    if (!confirm("Do you still want to continue?")) {
        break;
    }
}
```

### Continue

If you want to skip the remaining steps in an iteration, but continue on with the next iteration, you use the continue statement;

```javascript
// sum odd numbers only

let sum = 0;

for (let i=0; i<10; ++i) {
    let even = i%2==0;
    if (even) continue;
    
    sum+=i;
}
```

