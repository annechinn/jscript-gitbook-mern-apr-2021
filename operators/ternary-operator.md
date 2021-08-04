# Ternary Operator

The operator has three operands: the condition, the value if the conditions evaluates to true, and the value if the condition evaluates to false.

condition? expression1: expression2

If condition evaluates to true, return expression1, else return expression2. 

```javascript
let age = 15;
let canDrive = age>15?'yes':'no';

let amount = 10;
let amount = confirm("Add Tax?")?amount+amount*.10:amount;
```

