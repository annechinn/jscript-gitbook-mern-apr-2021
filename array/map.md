# Map

The map method is described as a method to **transform** each element in some way, and return a new array containing the transformed elements.

The map method accepts a function that it will call with each element, and that function is expected to return the transformed element that should be included in the results array.

```javascript
let array = [1,2,3,4,5];
let result = array.map(x=>x*2);
console.log(result); // [2,4,6,8,10];
```

The transformation can perform any type of transformation it wants. The code below transforms each element in the array to split the name into two fields, and leaves out the age field. The new array will contain an array of elements that have this structure: { firstName: 'Jon', lastName: 'Jones'}

```javascript
const people = [
    { name: 'Jon Jones', age: 30},
    { name: 'Sally Smith', age: 17}
];

let result = people.map(x=> {
    let nameParts = x.name.split(' ');
    return {
        firstName: nameParts[0],
        lastName: nameParts[1]
    }
    });

console.log(result);  
```

