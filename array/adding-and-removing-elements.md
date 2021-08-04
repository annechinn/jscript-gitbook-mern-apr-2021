# Adding and Removing Elements

#### Adding and Removing Elements

**push** - adds an element to the end of an array.

```javascript
let array = [1,2,3,4,5];
array.push(6);
console.log(array); // [1,2,3,4,5,6]
```

**pop** - removes the element at the end of the array. returns the element.

```javascript
let array = [1,2,3,4,5];
let element = array.pop();
console.log(array);   // [1,2,3,4]
console.log(element); // 5
```

**unshift** - adds an element to the beginning of an array

```javascript
let array = [1,2,3,4,5];
array.unshift(0);
console.log(array); // [0,1,2,3,4,5,6]
```

**shift** - removes an element from the beginning of an array. returns the element.

```javascript
let array = [1,2,3,4,5];
let element = array.shift();
console.log(array);   // [2,3,4,5]
console.log(element); // 1
```

#### Splicing Elements 

**splice** - combines adding and removing elements in a single method. This method is difficult to learn all the options for the parameters, but you can just focus on the simple use-cases, which are the majority, and it's not too hard.

start: at which index to start the change

deleteCount: the number of elements to remove

items: a comma-separated list of elements to add

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/splice" %}

**Splicing in a single value**

```javascript
let months = ['jan', 'feb', 'apr'];
months.splice(2, 0, 'mar');
console.log(months); // ['jan', 'feb', 'mar', 'apr']
```

**Splicing in multiple values**

```javascript
let months = ['jan', 'feb', 'may'];
months.splice(2, 0, 'mar', 'apr');
console.log(months); // ['jan', 'feb', 'mar', 'apr', 'may']
```

**Removing an element in the middle**

```javascript
let months = ['jan', 'feb', 'mar', 'mar'];
months.splice(2,1);
console.log(months); // ['jan', 'feb', 'mar']
```

**Replace an element in the middle**

```javascript
let months = ['jan', 'feb', 'mur', 'apr'];
months.splice(2,1, 'mar');
console.log(months); // ['jan', 'feb', 'mar', 'apr']
```



