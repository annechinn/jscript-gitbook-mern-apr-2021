# Array Length

### Dense Array

When the elements in the array are contiguous, then the length property indicates the number of elements in the array and the array is considered to be a dense array. This is true when there are no empty slots in the array.

```javascript
let array = [1,2,3,4,5];
console.log(array.length); // 5
```

### Sparse Array

When there are empty slots in the array, then it is called a sparse array. This happens when you explicitly leave empty spaces when initializing the elements in a literal array, or when you assign the values at only some of the array indices.

The length property does not indicate the number of elements in the array when the array is sparsely populated.  The length property will return one more than the highest index 

```javascript
let array = [1, ,3,4,5];
console.log(array.length); // 5

array = [];
array[5] = 'cat'; 
array[20] = 'dog';
console.log(array); // 21
```

If you view the array in the debugger, you can see that there are five empty slots before the value 'cat' at index 5, and 14 more empty slots before the value 'dog'  at index 20.

![](../.gitbook/assets/image%20%28394%29.png)

### Changing the Length

JavaScript allows you to change the length of an array.

#### Emptying an Array

```javascript
let array = [1,2,3,4,5];
array.length = 0;
console.log(array); // []
console.log(array.length); // 0
```

#### Removing Elements Beyond an Index

```javascript
let array = [1,2,3,4,5];
array.length = 3;
console.log(array); // [1,2,3]
console.log(array.length); // 3
```

{% hint style="info" %}
Setting the length of a dense array to a value greater than the length will make it a sparse array, and the length will no longer reflect the number of elements in the array.
{% endhint %}

