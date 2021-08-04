# Filter

The filter method returns a new array that contains the elements that return true for the condition tested in the function supplied.

You can filter on the value of a primitive data type.

```javascript
let array = [1,2,3,4,5];
let result = array.filter(x=>x<=3);
console.log(result); // [1,2,3]
```

You can filter on a property of an object.

```javascript
const people = [
    { name: 'Deven', age: 30},
    { name: 'Joshua', age: 17},
    { name: 'Anthony', age: 42},
    { name: 'Malik', age: 20},
];

let result = people.filter(x=>x.age>40);
console.log(result); // [{ name: 'Anthony', age: 42}]
```

