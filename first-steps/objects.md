# Objects

The other category of data we can store in variables are objects. 

### Objects

A web application usually deals with more complex data than the primitive data value types provide. JavaScript allows you to build more complex objects out of the primitive data types. An object is just a collection of property-value pairs to describe the data unique to the object.

For example, an object to represent a user would likely have properties such as the first and last name, the user name, and the email address, among others.

```javascript
let user = {
    firstName: 'Joe',
    lastName: 'Jones',
    email: 'jj@company.com'
    address: '1234 5th St. Seattle, WA'
}
```

The object can be as complex as you need it to be. For example, the user object above could contain an embedded object representing the address, rather than just a string.

```javascript
let user = {
    firstName: 'Joe',
    lastName: 'Jones',
    email: 'jj@company.com'
    address:  {
        street: '1234 5th St.',
        city: 'Seattle',
        state: 'WA'
    }
}
```

### Dot Notation for Accessing Properties

Default way for accessing properties.

```javascript
// access property
let firstName = user.firstName;

// assign a new value to a property
user.firstName = "Sally";

// access the city property within the address object
user.address.city
```

### Shopping Cart Example

We're all familiar with online shopping and the concept of a shopping cart. The user selects items they intend to buy and those items are stored in what is called a "cart". When you are ready to check-out, you get a view of everything in your cart, and the total that it will cost. We're going to work through how to represent that data.

Each item that can be purchased has multiple pieces of data that need to be stored together. So we create an object that aggregates that data together in one data structure.

> A _data structure_ is a collection of _data_ values, the relationships among them, and the functions or operations that can be applied to the _data_. - Wikipedia

```javascript
let item = {
    id: 1,
    name: 'Whole Grain Bread',
    category: 'bread',
    price: 5.99,
    onSale: true,
    discount: .79
}
```

Above, we've created the object directly in our JavaScript code. For data such as this, it would be more likely that the data about the products would be initially defined and stored in a database and the JavaScript code would call a function that would request the data from the web API. 

```javascript
function getProductsInCategory(category) {
    /* do stuff to get the data from the database */
    return http.get('myWebAPI/products');
}


let products = getProductsInCategory('bread');
/* display the bread products on the screen */

```

Here's a real-world example of the NY Times website calling the webAPI for its site to retrieve all of the top stories in the arts section.

{% embed url="https://api.nytimes.com/svc/topstories/v2/arts.json?api-key=5Vd8O8baGS3WEG1eQVAaS2mG6K0VyHH8" %}

So, typically you would receive an array of items.

```javascript
let items = getProducts();

// would look like this after it was done
let items = [
  {
    id: 1,
    name: 'Whole Grain Bread',
    category: 'bread',
    price: 5.99,
    onSale: true,
    discount: .79
  },
  {
    id: 2,
    name: 'Potato Chips',
    category: 'chips',
    price: 3.99,
    onSale: false,
    discount: 0
  },
  { 
    id: 3,
    name: 'Roasted Nut Mix',
    categry: 'nuts',
    price: 7.99,
    onSale: false,
    discount: 0
  }
];

```

Now, let's implement our shopping cart.

An object can have properties whose value is a function. A function is a special kind of object.

```javascript
let shoppingCart = {
  items: [],

  addItem: function(item) {
   this.items.push(item);
  },
  
  removeItem: function(itemId) {
    for (let i=0;i<this.items.length; ++i) {
      this.items.splice(i, 1);
      break;
    }
  },
  total: function() {
    let total = 0;
    for (let i=0; i<this.items.length; ++i) {
      total+= this.items[i].price;
    }

    return total;
  }
}
```

Just like you can access a property within an object, you can do the same to execute a function within an object.

```javascript
shoppingCart.addItem(items[0]);
```



