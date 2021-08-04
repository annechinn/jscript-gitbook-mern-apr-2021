# Logical Operators

**&& operator**: The "and" operator tests the first expression and if it evaluates to false, then return false. If the first expression evaluates to true, returns the value of the second expression. So, if either expression is false, then it will return false. If both expressions are true, then it will return true.

```javascript
console.log(false && true);  // false
console.log(true && false);  // false
console.log(true && true);   // true
```

**\|\| operator**: The "or" operator test the first expression and if it evaluates to true, then it returns true. If it evaluates to false, then it returns the value of the second expression. So, if either expression is true, it will return true. If neither expression is true, it will return false.

```javascript
console.log(true || false);  // true
console.log(false || true);  // true
console.log(true || true);   // true
console.log(false || false); // false
```

If the first expression of an \|\| operator evaluates to true, then the second expression will not be evaluated and true will be the result of the expression;

```javascript
itsSaturday = dayOfWeek === "Saturday";
itsSunday = dayOfWeek === "Sunday";

let itsTheWeekend = itsSaturday || itsSunday;
```

If the first expression of an && operator evaluates to false, then the second expression will not be evaluated and false will be the result of the expression.

```javascript
let age = 15;
let canDrive = age>=16 && hasLicense;
```

**! operator**: The "not" operator returns false if the single operand evaluates to true, otherwise return false;

```javascript
console.log(!true);  // false
console.log(!false); // true
```

```javascript
itsSaturday = dayOfWeek == "Saturday";
itsSunday = dayOfWeek == "Sunday";

let itsAWeekDay = itsSaturday == false && itsSunday == false;

// A more succinct format
itsAWeekDay = !itsSaturday && !itsSunday;
```

