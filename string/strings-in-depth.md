# Strings In-depth

### Creating String

#### String Literals

Most of the time you will create string as literals.

```javascript
let str = "Hello";
```

But, like an Array, you can create a string by using the String constructor.

```javascript
let str = "Hello";
console.log(str);
console.log(typeof(str));

str = new String("Hello");
console.log(str);
console.log(typeof(str));

str = String("Hello");
console.log(str);
console.log(typeof(str));
```

It's interesting to look at the output of these three cases in the debugger. The second case shows an object with an internal array that has a length of 5. The other two cases return a literal string.

![](../.gitbook/assets/image%20%28301%29.png)

You can use the String constructor to convert a different type to a string. It doesn't work to convert an object, except for an array of primitive types.

```javascript
str = String(500);
console.log(str); // 500

str = String(true);
console.log(str);  true

str = String([1,2,3]);
console.log(str);  // 1,2,3

str = String(["1", "2", "3"]);
console.log(str);  // 1,2,3

str = String({name: 'Jon'});
console.log(str); // [Object, Object]

```

### Operators

**Assignment**

We learned in the introduction to the String object that you can concatenate string. We can also use the assignment operator to concatenate.

```javascript
let output = "";
output+= "another thing";
output+= " and one more";
console.log(output); // another thing and one more.
```

#### Comparison

You can compare two strings, based  on their ascii codes.

```javascript
console.log("a" < "b");  // true
```

### Conversion

```javascript
let str = new String(true);
console.log(str); // "true"
```

### Methods

Here are a few example. There are more, but the are all pretty straight forward to use and easy to look up so I'll just link to the documentation.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String\#instance\_methods" %}



#### Splitting a string into an array

```javascript
let str = "this is a string";
let array = str.split(" ");
console.log(array); // ["this", "is", "a", "string"];
```

#### Finding the Index Of a sub string in a string

Returns the index of the first occurrence of the sub string in the string. If the sub string cannot be found, -1 will be returned.

You can pass the start index as the second parameter.

```javascript
let str = "this is a string";
let index = str.indexOf("is");
console.log(index); // 2

index = str.indexOf("is", 3);
console.log(index); // 5
```

#### Return a section of the string

```javascript
let str = "this is a string";
let substr = str.substring(0, 6);
console.log(substr); // this i
```

```javascript
let email = 'jonjones@gmail.com';
let domain = email.substring(email.indexOf('@') + 1);

console.log(domain); // gmail.com
```

