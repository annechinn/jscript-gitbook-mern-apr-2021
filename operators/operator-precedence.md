# Operator Precedence

### Combining Operators

You can combine as many operators as you want into a single expression.

```javascript
let dayOfWeek = getDayOfWeek();
let hourOfDay = getHourOfDay();

if (dayOfWeek == "Saturday" || 
    dayOfWeek == "Sunday" || 
    hourOfDay > 18) {
   alert("after hours, call back later");
}

```

**Precedence of \|\| and && operator**

The expressions on the left and the right of the && or \|\| operator will be evaluated before the && or \|\| operator is applied.

This expression

```javascript
let afterHours = dayOfWeek === "Saturday" || 
                 dayOfWeek === "Sunday" || 
                 hourOfDay > 18);
```

is the same as

```javascript
let afterHours = (dayOfWeek === "Saturday") || 
                 (dayOfWeek === "Sunday") || 
                 (hourOfDay > 18));
```

and the same as

```javascript
itsSaturday = dayOfWeek === "Saturday";
itsSunday = dayOfWeek === "Sunday";
itsAfter6PM = hourOfDay > 18;

let afterHours = itsSaturday || itsSunday || itsAfter6PM;
```

```javascript
itsSaturday = dayOfWeek === "Saturday";
itsSunday = dayOfWeek === "Sunday";

let itsTheWeekend = itsSaturday || itsSunday;

let itsAWeekDay = itsSaturday == false && 
                  itsSunday == false;
                  
itsAWeekDay = !itsSaturday && !itsSunday;
```

### Operator Precedence

There are rules for the precedence of the different operators when there is more than one operator in an expression. But those rules can be hard to remember, beyond the simple ones, like multiplication has precedence over addition.

We're familiar with how to use parentheses with arithmetic expressions to make the intended precedence explicit. This same practice can be employed with all of the operators we've discussed above and is a good practice to avoid unintended errors.

