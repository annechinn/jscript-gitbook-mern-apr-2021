# Algorithm vs Language

### Searching for an element in a sorted array

#### Iterative Search

```javascript
function linearSearch(arr, target) {
    for (let i=0; i<arr.length; ++i) {
        if (arr[i]===target) {
            return arr[i];
        }
    }
}
```

#### Binary Search

```javascript
function binarySearchIterative(arr, target) {
    
    let left = 0;
    let right = arr.length-1;

    while (left<=right) {
        let mid = left + Math.floor((right-left)/2);
        if (arr[mid]===target) {
            return target;
        }
        if (target>arr[mid]) {
            left = mid+1;
        }
        else {
            right = mid-1;
        }
    }

    return -1;
}

```

![](https://lh6.googleusercontent.com/0qvE0ptCGSu7cpS_rrEJ28jqXk_TT_h5fqk_POS0ssG8eSPBPB2aBiLt5-L1FSh_oIl8F-xWcqMmGJYuOfIAkAw5lNINLnDT9Y08LFDq-C-mSlh6A_Je-bOCZzSUKSaclL2HaU2wNw)

### Sum From 1 to N

#### Iterative Search

```javascript
function sumToNumber(n) {
    let total = 0;
    for (let i=1; i<=n; ++i) {
        total+=i;
    }
    return total;
}
```

#### Single calculation/instruction

```javascript
function sumtoNumber(n) {
    return n*(n+1)/2;
}
```

### Insert/Delete Item in an Array

![](../.gitbook/assets/image%20%28175%29.png)

```javascript
function insert(arr, num) {

  if (num>arr[arr.length-1]) {
    arr[arr.length] = num;
    return arr;
  }

  for (let i=0; i<arr.length;++i) {
    if (num<=arr[i]) {
      for (let j=arr.length;j>=i;j--) {
        arr[j] = arr[j-1];
      }
      arr[i] = num;
      break;
    }
  }
  
  return arr;
}
```

