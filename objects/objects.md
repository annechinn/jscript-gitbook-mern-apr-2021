# Objects In-depth

### JavaScript Objects

In JavaScript an object a collection of key-value pairs, called properties. The key, or property name, is a string. The value, can be a primitive datatype, or an object, such as an array, or event a function \(called method in this case\).

There are many different ways to create an object. The most common way is to use the object literal syntax.

```javascript
let emptyObject = {};
```

To add a property to an object you add the key-value pair as follows:

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com'
}
```

There are two ways to access the value of a property.

```javascript
let firstName;

firstName = contactInfo.firstName;
firstName = contactInfo['firstName'];

```

Property name can contain spaces, but the name must be enclosed in quotes and they property value must be accessed using array notation.

```javascript
let contactInfo = {
    'first name': 'Jon',
    'last name': 'Jones',
    email: 'jj@company.com'
}

let firstName = contactInfo['first name'];
```

{% hint style="info" %}
It is recommended to use camelCase property names instead of names with spaces.
{% endhint %}

If you attempt to access a property that does not exist, a value of undefined will be returned.

```javascript
let address = contactInfo.address; 
console.log(address); // undefined
```

You can change the value of a property.

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com'
}

contactInfo.email = 'jjones@company.com';
```

You can add a property after the object is created.

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com'
}

contactInfo.address = '1234 5th Street';
```

You can delete a property. If you try to access the property value after it has been deleted, a value of undefined will be return \(the same value that is returned if you access a property that never existed\).

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com'
}

delete contactInfo.email;

console.log(contactInfo.email); // undefined
```

You can test for the existence of a property.

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com'
}

let exists = 'firstName' in contactInfo;
console.log(exists); // true

exists = 'address' in contactInfo;
console.log(exists); // false
```

To iterate over all of the properties in an object.

```javascript
for (let prop in contactInfo) {
    let name = prop;
    let value = contactInfo[prop];
    console.log(`prop: ${name} value: ${value}`);
}
```

Objects can have methods. If you want to access the value of another property of the object you must use the **this keyword**, which refers to the object.

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com',
    fullName : function() {
        return `${this.firstName} ${this.lastName}`;
    }
}

console.log(contactInfo.fullName());
```

In the latest version of JavaScript, ES6, there is a shorter syntax to define a property that is a function.

```javascript
let contactInfo = {
    firstName: 'Jon',
    lastName: 'Jones',
    email: 'jj@company.com',
    fullName() {
        return `${this.firstName} ${this.lastName}`;
    }
}

```

