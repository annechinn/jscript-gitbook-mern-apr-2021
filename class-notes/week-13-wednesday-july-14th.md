# Week 13 - Wednesday, July 14th

### Class Video

{% embed url="https://www.youtube.com/watch?v=p1iV05EVYEg" %}



### JavaScript Practice Problems

**Biggest Number:** write a function that returns the biggest of the two numbers passed in.

```javascript
 function biggestNum(num1, num2) {
 }

  console.log(biggestNum(3,4))
```

```javascript
 function biggestNum(num1, num2) {
    return (num1>num2)?num1:num2;
  }

  console.log(biggestNum(3,4))
```

**Return New Array With Same Elements:** write a function that creates a new array containing the same elements as in the passed in array.

```javascript
function newArray(arr) {
}
console.log(newArray([1,2,3,4]);
```

```javascript
function newArray(arr) {
    return arr.map(x=>x);
}
console.log(newArray([1,2,3,4]);
```

**Numbers In Range**: write a function that returns an array containing the subset of numbers in the input array that are between the min and max values.

```javascript
function numsInRange(array, min, max) {
}

console.log(numsInRange([ 1, 2, 3, 5, 8], 1,5));
console.log(numsInRange([ 1, 2, 3, 5, 8], 1,3));
```

```javascript
 function numsInRange(array, min, max) {

    let results = [];
    array.forEach(num=> {
      if (num>=min && num<=max) {
        results.push(num);
      }
    });
  
    return results;
  }
  
```

```javascript
function numsInRange(array, min, max) {
    return array.filter(x=>x>=min && x<=max);
}
```

**Users In Range**: write a function that returns an array containing the subset of users in the input array that have an age between the min and max values.

```javascript
function usersInRange(array, minAge, maxAge) {

}

const users = [
  {firstName:'Sally', lastName: 'Smith', age:26},
  {firstName:'Jeff', lastName: 'Jones', age:16},
  {firstName:'Bob', lastName: 'Baker', age:55},
];

console.log(usersInRange(users, 10,50));
```

```javascript
function usersInRange(array, minAge, maxAge) {
  return array.filter(x=>x.age>=minAge && x.age<=maxAge);
}
```

**User Ages In Range**: same as the previous problem, except this time only return an array of the ages that are in the range.

```javascript
function agesInRange(array, minAge, maxAge) {

}

const users = [
  {firstName:'Sally', lastName: 'Smith', age:26},
  {firstName:'Jeff', lastName: 'Jones', age:16},
  {firstName:'Bob', lastName: 'Baker', age:55},
];

console.log(agesInRange(users, 10,50));
```

```javascript
  function agesInRange(array, minAge, maxAge) {
    return array.filter(x=>x.age>=minAge && x.age<=maxAge).map(x=>x.age);
  }
```



### React - Updating State, Communicating with Child Components 

We're going to simulate an e-commerce site that has some products that you can add and remove from your cart prior to checkout.

There's a handy public API that you can use to retrieve some sample product data. We'll use that to fill out our products.

{% embed url="https://fakestoreapi.com/products" %}

![](../.gitbook/assets/image%20%28291%29.png)

There are three components:

* **Store \(container\)**: the container component \(smart component\) that holds the state
  * products: an array of products to display
  * cartItems: an array of objects in the shopping cart. Each item contains a reference to the product, as well as the quantity of the product.
* **ProductList \(bottom\)**: a child component \(presentation component\) that displays the list of components on the left side. Allows user to add items to the cart. 
* **ShoppingCart \(top\)**: a child component \(presentation component\) that display info about the list of components in the shopping cart and a total. Allows the user to add and remove items from the cart.

#### Loading the product data

The first task for the Store component is to retrieve the list of products. 

```javascript
import axios from 'axios';

async function getProducts() {
  const response = await axios.get('https://fakestoreapi.com/products');
  return response.data;
}
```

The data returned looks like this. An array of product objects.

```javascript
[
    {
    id: 1,
    title: "Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops",
    price: 109.95,
    description: "Your perfect pack for everyday use and walks in the forest. Stash your laptop (up to 15 inches) in the padded sleeve, your everyday",
    category: "men's clothing",
    image: "https://fakestoreapi.com/img/81fPKd-2AYL._AC_SL1500_.jpg"
    },
    {
    id: 2,
    title: "Mens Casual Premium Slim Fit T-Shirts ",
    price: 22.3,
    description: "Slim-fitting style, contrast raglan long sleeve, three-button henley placket, light weight & soft fabric for breathable and comfortable wearing. And Solid stitched shirts with round neck made for durability and a great fit for casual fashion wear and diehard baseball fans. The Henley style round neckline includes a three-button placket.",
    category: "men's clothing",
    image: "https://fakestoreapi.com/img/71-3HjGNDUL._AC_SY879._SX._UX._SY._UY_.jpg"
    },
    ...
]
```

Since this data will be incorporated into the component's UI, we'll need to have React manage it. So we create a state variable to hold it.

```javascript
  const [products, updateProducts] = useState([]);
```

We'll register the function to retrieve the product data using the React useEffect hook so that React can schedule it to happen at the correct time. We specify an empty trigger array so that the product list is only retrieve after the first render of the component.

```javascript
 useEffect(()=> {
      (async ()=> {
        updateProducts(getProducts());
      })();
}, [])
```

#### ProductList component

We'll created a simple component to render the list of products and one to render a specific product. We pass the list of products to the ProductList component, and then the ProductList component passes the individual product to the Product component.

In each case, we are using destructuring to extract the property from the props object passed into the component function.

```javascript
function Product({product}) {
  return (
    <Card className="product-card">
      <Card.Img src={product.image}/>
      <Card.Body>
        <Card.Title>{product.title}</Card.Title>
        <Card.Text>{product.price}</Card.Text>
      </Card.Body>
    </Card>
  )
}

function ProductList({products}) {
  return (
    <div className="products">
      {products.map(x=><Product key={x.id} product={x}/>)}
    </div>
  )
}
```

Now, we can display the list of products...

![](../.gitbook/assets/image%20%28259%29.png)

#### 

#### Adding Items to the Cart

The Store component is responsible for maintaining the list of products, as well as the products that are currently in the shopping cart and how many of each there are.

We need to create a state variable to hold the items that are in the cart.

```javascript
 const [cartItems, updateCartItems] = useState([]);
```

And we need to two functions: addItemToCart and removeItemFromCart. For each, it will accept a product data object.

There are two scenarios we have to handle

1. This is the first item in the cart, in which case we need to create a new cart item and add it to the list of cart items.
2. The items is already in the cart and we just need to find the item and increase the quantity.

In both cases, we need to generate a new array, using map, or the spread operator, to trigger a re-render.

A cart Item is going to be an object, that has two properties: a reference to the product item that is being added to the cart, and the quantity, which will start out as 1 when they add it to the cart.

```javascript
{product: item, quantity:1};
```

```javascript
function addItemToCart(item) {
    // see if the item is already in the shopping cart items
    let found = cartItems.find(x=>x.product.id===item.id);
    if (!found) {
      // create a new item
      const newCartItem = {product: item, quantity:1};
      // use the spread operator to create a shallow copy
      // of the old array and add our new item to it
      const newCartItemsArray = [...cartItems, newCartItem];
      updateCartItems(newCartItemsArray);
    }
    else {
      // update the item
      found.quantity++;
      // use map to create a shallow copy of the old array
      // to trigger a re-render
      updateCartItems(cartItems.map(x=>x));
    }
  }
```

#### Removing items from the Cart

Again, there are two scenarios

1. If the quantity is 1, then we need to remove it from the cart
2. Otherwise, we just need to decrement the quantity

In both cases, we need to generate a new array, using map or filter, to trigger a re-render

```javascript
  function removeItemFromCart(item) {

    // see if the item is already in the list
    let found = cartItems.find(x=>x.product.id===item.product.id);
    if (found.quantity===1) {
      // we should remove the item from the cart
      updateCartItems(cartItems.filter(x=>x.product.id!==item.product.id))
    }
    else {
      // decrement the quantity and use map to create a shallow
      // copy of the array to trigger a re-render.
      found.quantity--;
      updateCartItems(cartItems.map(x=>x));
    }
  }
```

#### Passing the functions to the components

The Store component needs to pass the addItemToCart function to the ProductList component and the ProductList component will pass it on to the Product component.

We'll add a button to the Product component that will call the function to add the item to the cart when the button is clicked.

```javascript
function Product({product, addItemToCart}) {
  return (
    <Card className="product-card">
      <Card.Img src={product.image}/>
      <Card.Body>
        <Card.Title>{product.title}</Card.Title>
        <Card.Text>{product.price}</Card.Text>
        <Button variance="primary" size="sm" onClick={()=> {addItemToCart(product)}}>Add Item</Button>
      </Card.Body>
    </Card>
  )
}

function ProductList({products, addItemToCart}) {
  return (
    <div className="products">
      {products.map(x=><Product key={x.id} product={x} addItemToCart={addItemToCart}/>)}
    </div>
  )
}
```

```javascript
return (
      <>
      <div class="store">
         <ProductList products={products} addItemToCart={addItemToCart}/>
      </div>
      </>
    )
```

### Logging the Change

If we put a console.log\(cartItems\) in the addToCart function, and watch the console log, we can see that the cartItems array is not immediately updated after the call to updateCartItems. This is because React does not immediately update the state. It waits until the appropriate time in the life cycle of the component to update the state.

### Adding the ShoppingCart component

Finally, we'll add the ShoppingCart component to display the items in the cart, and also allow the user to add or remove items from the cart.

```javascript
function ShoppingCart({cartItems, addItemToCart, removeItemFromCart}) {
  return (
    <>
    <div class="cart">
      <div class="cart-item">
        <div class="price-info">
          <div>Num</div>
          <div>Name</div>
          <div>Price</div>
          <div>Total</div>
        </div>
      </div>

      {cartItems.map(x=>
        <div class="cart-item" key={x.product.id}>
          <div class="price-info">
            <div>{x.quantity}</div>
            <div>{x.product.title}</div>
            <div>{x.product.price}</div>
            <div>{(x.product.price*x.quantity).toFixed(2)}</div>
          </div>
          <div class="cart-item-buttons">
            <Button variant="primary" size="sm" onClick={()=>{addItemToCart(x.product)}}>+</Button>
            <Button variant="primary" size="sm" onClick={()=>{removeItemFromCart(x)}}>-</Button>
          </div>
        </div>
      )}

      <hr/>
      <div class="cart-total">
        Total: {(cartItems?.reduce((acc, x)=>{acc+=(x.product.price*x.quantity); return acc;},0)).toFixed(2)}
      </div>
    </div>
    </>
  )
}
```

```javascript
 return (
      <>
      <div className="store">
        <ShoppingCart cartItems={cartItems} addItemToCart={addItemToCart} removeItemFromCart={removeItemFromCart}/>
        <ProductList products={products} addItemToCart={addItemToCart}/>
      </div>
      </>
    )
```

### Code Challenges

**\#1** - log the numbers between between 1 and 10 to the console.

**\#2** - log the numbers less than 100 that are even to the console.

**\#3** - log the multiplication table through 10 for the number 7.

7 \* 1 = 7

7 \* 2 = 14

7 \* 3 = 21

etc..

7 \* 10 = 70

**\#4** - log the multiplication table through 10 for the numbers 1-10.

**\#5** - log the sum of the numbers 1-10.

**\#6** - create a function that accepts two arrays and returns a new array that contains all the elements in both arrays.

### Solutions

**\#1** - log the numbers between between 1 and 10 to the console.

```javascript
for (let i=0;i<10;++i) {
    console.log(i);
}
```

**\#2** - log the  odd numbers less than 100 to the console.

```javascript
for (let i=1;i<100;i+=2) {
    console.log(i);
}
```

**\#3** - log the multiplication table through 10 for the number 7.

```javascript
for (let i = 1; i <= 10; i++)
{
    var row = "7 * " + i + " = " + 7 * i;
    console.log(row);
}
```

**\#4** - log the multiplication table through 10 for the numbers 1-10.

```javascript
for (let i = 1; i <= 10; i++)
{
    printTable(i);
    console.log("");
}

function printTable(n)
{
    for (let i = 1; i <= 10; i++)
    {
        var row = n + " * " + i + " = " + n * i;
        console.log(row);
    }
}
```

**\#5** - log the sum of the numbers 1-10.

```javascript
let sum = 0;

for (let i = 1; i <= 10; i++)
{
    sum += i;
}

console.log(sum);
```

**\#6** - create a function that accepts two arrays and returns a new array that contains all the elements in both arrays.

```javascript
function combineArrays(arr1, arr2) {
    return [...arr1, ...arr2];
}
```

