# Spread Syntax

The spread syntax allow an object, such as an array or string, to spread to expand in place where zero or more arguments are expected. An object expression can also be expanded in place where zero or more key-value pairs are expected.

The advantage of the spread syntax is that a declarative approach can be used to modify the literal array instead of an imperative approach that programmatically creates the new array.

### Use Cases

#### Inserting into literal arrays

```javascript
let array1 = [1, 2, 3];
let array2 = [4, 5, 6];

// inserting at the end
let newArray = [...array1, ...array2];
console.log(newArray); // [1,2,3,4,5,6]

// inserting at the beginning
newArray = [...array2, ...array1];
console.log(newArray); // [1,2,3,4,5,6]

```

#### Copying an array

```javascript
let array1 = [1, 2, 3];
let array2 = [...array1];
```

It is important to understand that the spread syntax only goes one level deep, so that if you are copying the contents of an array that contains objects, rather than primitive values, you will be copying the reference to the objects and therefore both arrays will refer to the same objects.

```javascript
const people = [
    { name: 'Jon Jones', age: 30},
    { name: 'Sally Smith', age: 17}
];

const copy = [...people];
copy[0].name = 'Paul Peters';
console.log(people);

// log output
// [
//     {
//         "name": "Paul Peters",
//         "age": 30
//     },
//     {
//         "name": "Sally Smith",
//         "age": 17
//     }
// ]
```

#### Passing Multiple Values to a Function

```javascript
Math.max(1,3,5) // 5
Math.max([1,3,5]) // NaN
Math.max(...[1,3,5]) // 5
```

#### Combining two objects

```javascript
let obj1 = { x: 1, y: 2 };
let obj2 = { a: 5, b: 6 };
let obj3 = {...obj1, ...obj2};
console.log(obj3);

// obj3 = 
//  {
//     "x": 1,
//     "y": 2,
//     "a": 5,
//     "b": 6
// }

```

#### Adding new fields to an object

```javascript
let obj1 = { firstName: 'joe' }
let obj2 = { ...obj1, lastName: 'jones' };
```

#### Updating the value of a subset of the fields after initial values have been set

```javascript
let obj1 = { firstName: 'joe', lastName: 'jones'}
let obj2 = { ...obj1, lastName: 'jenson' };
```

