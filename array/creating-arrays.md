# Creating Arrays

There are several ways to create an array. The first case is using the **literal** syntax. The second is calling the JavaScript Array object constructor.

```javascript
let array1 = [1,2,3];
let array2 = new Array(1,2,3);
let array3 = new Array('1', '2', '3');
```

An odd quirk of the JavaScript language that can cause an unintentional error is the following:

```javascript
// This is creating an array of length 1, 
// not an array with an initial value of 1!
let array4 = new Array(1);
```

JavaScript also allows you to omit the new keyword in the Array constructor syntax.

```javascript
// these are equivalent

let array1 = new Array(1,2,3);
let array2 = Array(1,2,3);
```

{% hint style="info" %}
In practice, it is much more common to use the literal syntax, except for special cases where you need to create an array of an initial size but not set the values, or specify an initial value for all the elements in a large array.
{% endhint %}

