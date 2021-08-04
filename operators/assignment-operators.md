# Assignment Operators

An assignment operator assigns a value to its left operand based on the value of its right operand.  We're not going to cover the advanced ones here, just the ones you'll use frequently. As you get more comfortable with JavaScript, you can refer to the reference guide on MDN and see the full list.

```javascript
// simple assignment
let name = "Joe";
let ready = false;
let x = 10;

// short cuts for arithemetic operators
x+=5;  // x = x + 5;
x=-5;  // x = x - 5;
x*=5;  // x = x * 5;
x/=5;  // x = x / 5;


```

Some style guides recommend avoiding the increment and decrement operators, ++ and --, to avoid unintentional errors cause be the pre and post notation. It is suggested to use the += or -= assignment operators instead.

The order only matters when the value of the variable is used in an expression, but can lead to unintentional errors.

```javascript
let counter = 0;
// counter will be incremented prior to being
// passed to the alert function
alert(++counter); // 1
```

```javascript
let counter = 0;
// counter will be incremented after being
// passed to the alert function
alert(counter++); // 0
```

The += and =- operators achieve the same goal and works for changes greater than one. 

```javascript
let counter = 0;
counter+=1;
counter-=1;

counter+=10;
counter-=10;
```

### 

