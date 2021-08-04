# Week 14 - Wednesday, July 21

### Class Video

{% embed url="https://www.youtube.com/watch?v=kVbp6VyLoNQ" %}



### Practice Problems

```javascript

let distances = [
    { from: 'New York', to: 'Atlanta', distance: 880},
    { from: 'Austin', to: 'Seattle', distance: 1200},
    { from: 'Kansas', to: 'Portland', distance: 1340}
  ] 
```

Write a function that returns an array that is the same as the input array, except that the distance is converted to miles \(\*.621371\)

```javascript
function f1(array) {
    let result = [];
    for (let i=0; i<distances.length;++i) {
       result.push(
           {
           ...distances[i],
           distance: distances[i]* 0.621371
           })
    }
    
    return result;
}

function f2(array) {
    return distances.map((x)=> { return { ...x, distance: x* 0.621371 }});
}

```

Write a function that returns the elements in the array that have a distance &lt; 1000

```javascript
function f1(array) {
    let filterDistances = []
    for (let i = 0; i < distances.length; i ++) {
        if (distances[i].distance < 1000) {
            filterDistances.push(distances[i])
        }
    }
    return filteredDistances;
}

function f2(array) {
    return distances.filter(item => item.distance < 1000);
}
```

Write a function that returns the total distance of all the elements in the array.

```javascript
function f1(array) {
   let total = 0
   for (let i = 0; i < distances.length; i++) {
      total += distances[i].distance;
   }
   return total;
}

function f2(array) {
   return distances.reduce((acc, item) => acc+ item.distance, 0);
}

```

Write a function that returns the total distance \(in miles\) of all of the items that are &lt; 1000 km

```javascript
function f1(array) {
  let total = 0
  for(let i = 0; i < distances.length; i++){
    if(distances[i].distance < 1000){
      total += distances[i].distance * 0.621371;
    }
  }
  return total;
}

function f2(array) {
  return distances
        .filter(item => item.distance < 1000)
        .map(item => item.distance * 0.621371)
        .reduce((prev, distance) => prev + distance, 0);
}
```

Write a function **capitalize** that takes a string and uses .map to return the same string in all caps. 

// ex. capitalize\('whoop'\) // =&gt; 'WHOOP'

```javascript
  function capitalize(input) {
    return [...input].map(x => x.toUpperCase()).join("");
  }
```

Now write a new function called **swapCase** that takes a string of words and uses .map and your newly written capitalize\(\) function to return a string where every other word is in all caps. 

```javascript
function swapCase(input) {
  return input
    .split(" ")
    .map((x, idx) => (idx % 2 ? x : capitalize(x)))
    .join(" ");
}
```

Write a function that takes a string and returns an object representing the character count for each letter. Use .reduce to build this object. 

 ex. countLetters\('abbcccddddeeeee'\) =&gt; {a:1, b:2, c:3, d:4, e:5}

```javascript
function countLetters(input) {
  let map = {};
  for (let i=0;i<input.lenght;++i) {
    const ch = input[i];
    const count = map[ch];
    if (count) map[ch] = count++;
    else map[ch] = 1;
  }
  
  return map;
}

function countLetters(input) {
  return input.reduce(
    (acc, value) => ({
      ...acc,
      [value]: !acc[value] ? 1 : ++acc[value]
    }),
    {}
  );
}
```

```javascript
let grid = [
  [1, 1, 1, 2, 2, 2, 3, 3, 3],
  [1, 1, 1, 2, 2, 2, 3, 3, 3],
  [1, 1, 1, 2, 2, 2, 3, 3, 3],
  [4, 4, 4, 5, 5, 5, 6, 6, 6],
  [4, 4, 4, 5, 5, 5, 6, 6, 6],
  [4, 4, 4, 5, 5, 5, 6, 6, 6],
  [7, 7, 7, 8, 8, 8, 9, 9, 9],
  [7, 7, 7, 8, 8, 8, 9, 9, 9],
  [7, 7, 7, 8, 8, 8, 9, 9, 9]
];

function countNumInGrid(grid, num) {
  let count = 0;
  for (let i=0;i<grid.length;++i) {
    for (let j=0;j<grid.length;++j) {
      if (grid[i][j]===num) count++;
    }
  }
  return count;
}
```

Binary Search Algorithm



![](https://lh4.googleusercontent.com/S3DXQFHCMeK6Lcujn7Dj63dLu-AmDYJZ7imjjPHGtJT0wE_GElbCQRjHE7_QA8hxFSZ44qmdLWxkO3yOcHPwB3Jr0UCutRe5GGdCJnUdfjoXi5nBvwdXRUr63ZpLlRcmDkvAqYHx_Q)

![](https://lh4.googleusercontent.com/Mjd9Y9MkyiCdBSV_iTa1GulPOa-tf0k_vMGs9TAxGAo4EMif0nvtz82OyR_Za3ge8NctlYhYVbEBvZang21WTZY1lfV4jF4MvEbgr4hnBbnT-vyx6e1nl3PvOVBVgjVIx6oXwMkO6w)

![](https://lh6.googleusercontent.com/ZcML1l_KLfXSYI5J6m91hGRqIcLwxRey1kMzLbRGW7AXtoKIh5WSiZmevEkq63zzMA1ZSlC5NTxiie0jG8a6NZ0V2tIcd0Z98jgfMkiWUijzC1X9hqdiFysg8Kbv0LeQ9gskgl8P8w)

![](https://lh4.googleusercontent.com/GrChgNj-QGwY5pw_bZ6P5j2veV9maCPJY-0i-mX1h-2Eh7EXNm_T2Wz4wedfJJJuQuaYv5RZTA3i0JSPkV8C55RLU2lDbdUQssP4ENkNrjYfj2BWIounZ9Tg4rjrkT_HrcXnTwX8eQ)

![](https://lh3.googleusercontent.com/UxOKcfsxC3gPsKWUGhhA_CG_dKXtWKIYYZdHgXV59EUIfEk0wMKO6Aa_inaS5GDdNoxWRcwMbH2BIv-_IbWnV6bqqgHGOtSS6HFHmxKovAFnKvXJXGfFYIIWXcfIIwow-afVhmoxSw)

```javascript
const binarySearchIterative = (arr, target) => {
    
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



