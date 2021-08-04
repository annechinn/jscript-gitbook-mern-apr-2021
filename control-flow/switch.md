# Switch

The switch statement is also a statement used when you have conditional branching. It is most often used to map a numeric value to a string, for example, when you are mapping a status code to a string to return to a user.

```javascript

function statusCodeToString(statusCode) {
    let message = "";
    switch (statusCode) {
    case 200:
        message = "OK";
        break;
    // .....
    case 500:
        message = "Internal Server Error";
        break;
    case 501:
        message = "Not Implemented";
        break;
    case 502:
        message = "Bad Gateway";
        break;
    // .......
    default:
        message = `Unrecognized code: ${statusCode}`;
    }
    
    return message;
}

console.log(statusCodeToString(500));
```

If there is a break statement at the end of the case block, the code will return from the switch statement at that line. Otherwise it will "fall through" to the next case statement.  

```javascript
function statusCodeCategory(statusCode) {
    let category = "";
    switch (statusCode) {
    case 200:
    case 201:
    case 202:
        category = "Success";
        break;
    // .....
    case 500:
    case 501:
    case 502:
        category = "Server Error";
        break;
    default:
        category = `Unrecognized code: ${statusCode}`;
    }
    
    return category;
}
```

The code above demonstrates how the cases flow through, but it also demonstrates the limited use-cases for this approach. There are around 100 codes for each category, so you wouldn't actually want to use this technique here. It would be better to use an if statement.

```javascript
let category = "";
if (statusCode >=200 && statusCode < 300) {
    category = "Success";
}
else if (statusCode >=500 && statusCode < 600) {
    category = "Server Error";
}

return category;

```

A better use case is where there a just a small number of cases mapping to a single result. Also notice how you can use a return statement instead of storing the value in a variable and returning that value at the end of the function.

```javascript
function isWeekDay(dayOfWeek) {
    switch (dayOfWeek) {
    case "Saturday":
    case "Sunday":
        return false;
    default:
        return true;
    }
}
```

### Exercise

Write a function that accepts a single letter representing the first character of a DNA nucleotide and return the first letter of the corresponding RNA nucleotide that it maps to. The mapping is as follows:

* G maps to C
* C maps to G
* T maps to A
* A maps to T

