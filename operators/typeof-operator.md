# typeof Operator

The typeof operator can be used to determine the type of a variable. It returns a string representing the datatype of the value.

The typeof operator has two forms, an operator or a function. 

```javascript
// function
typeof(10); // returns "number"

// operator
typeof 10;  // return "number"

typeof("hello"); // return "string"

typeof(true);  // return "boolean"

typeof(undefined); // returns "undefined"

typeof(null); // returns "object" it's a bug!!
```

{% hint style="info" %}
The typeof operator applied to the null value returns the value "object", which is actually a bug. It should return "null", but has been left as it is due to code depending on the original return value.
{% endhint %}

