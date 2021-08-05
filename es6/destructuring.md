# Destructuring

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

### Arrays

Assigning the values in the array to variables

```javascript
let [a, b] = [1, 2];
console.log(a, b);
//=> 1 2
```

Combine with spread/rest operator \(accumulates the rest of the values\)

```javascript
let [a, ...b] = [1, 2, 3];
console.log(a, b);
// => 1 [ 2, 3 ]
```

Omit values

```javascript
const address = [221, 'Baker Street', 'London'];
const [ houseNo, , city ] = address;
console.log(houseNo, city)
// 221 'London'
```

Swap values without a temp variable

```javascript
var a = 1, b = 2;
[b, a] = [a, b];
console.log(a, b);
// => 2 1
```

### Objects

Selecting only some of the fields to destructure

```javascript
const details = { firstName: 'Code', lastName: 'Burst', age: 22 };
const { firstName, age } = details;
console.log(firstName, age);
// Code 22
```

Combines spread and destructuring

```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }
```

#### Advanced Usage

First understand this case

```javascript
const { user } = {user: "Name1"};
console.log(user);
```

Now, think about how the above is being applied to the parameter passed to the map function.

```javascript
var users = [
  { user: "Name1" },
  { user: "Name2" },
  { user: "Name2" },
  { user: "Name3" }
];

var names = users.map( ({ user }) => user );
console.log(names);
// => [ 'Name1', 'Name2', 'Name2', 'Name3' ]
```

#### In a for of loop

```javascript
var users = [
  { user: "Name1" },
  { user: "Name2", age: 2 },
  { user: "Name2" },
  { user: "Name3", age: 4 }
];

for (let { user, age = "DEFAULT AGE" } of users) {
  console.log(user, age);
}

// => Name1 DEFAULT AGE
// => Name2 2
// => Name2 DEFAULT AGE
// => Name3 4
```

### Resources

{% embed url="https://ui.dev/object-array-destructuring/" %}

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment" %}

