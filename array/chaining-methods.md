# Chaining Methods

The array methods that return a new array, such as map, filter, reduce, and sort, can be chained together.

Let's start with the example data below. An array of objects that contain information about the distance between two cities. The distance is expressed in kilometers.

```javascript
let distances = [
    { from: 'New York', to: 'Atlanta', distance: 880},
    { from: 'Austin', to: 'Seattle', distance: 1200},
    { from: 'Kansas', to: 'Portland', distance: 1340}
   ];
```

Let's say we want to find the total distance in miles \(not kilometers\) for  those items that have a distance less than 1000km.

Here is the solution using a for loop.

```javascript
let total = 0
for (let i = 0; i < distances.length; i++){
  if (distances[i].distance < 1000){
    total += distances[i].distance * 0.621371;
  }
}
console.log(total);
```

And here's the solution chaining together filter, map and reduce.

```javascript
let total = distances
        .filter(item => item.distance < 1000)
        .map(item => item.distance * 0.621371)
        .reduce((prev, distance) => prev + distance, 0);
console.log(total);
```

This solution looks nice, but there's actually a problem that you should be aware of. Each method, filter, map, and reduce, perform their own for loop to iterate through the elements in the array and call the function we supply. 

That means there are three iterations through the array, compared to just one in our own for loop implementation. 

This isn't a big deal in our very small sample size, but imagine you have a billion elements in the array. In that case you need to consider the performance implications of using this technique.

