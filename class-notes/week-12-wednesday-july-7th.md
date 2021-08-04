# Week 12 - Wednesday, July 7th

### Class Lecture Video

{% embed url="https://www.youtube.com/watch?v=qgBW8CZvlA0" %}



### Where/How Data is Stored in Memory

This topic is necessary to better understand what's happening when we are working with arrays and objects, especially in the context of React, which uses the new ES6 spread and destructing operators heavily and also  relies on the equality operator, ===, to determine whether state variables have changed, and therefore should trigger an update to a component's render function to update the UI. 

#### Computer Memory - RAM

Think of the computer's memory \(RAM\) as a very tall bookshelf.  Each bookshelf as an address, just like a house address, so that when your computer code references a variable, it is actually referring to the shelf in the RAM bookcase at the specified address.

![](../.gitbook/assets/image%20%28418%29.png)

The bookshelf is divided into different sections for each program that is currently running.

![](../.gitbook/assets/image%20%28424%29.png)

And within a section for an individual program, it is further divided into sections for the different types of data in a program. For example, the machine instructions are stored in a certain section of your program's memory space and data associated with variables is stored in other sections.

There are two important areas where data associated with variables that you declare are stored. They are called the **stack** and the **heap**. 

![](../.gitbook/assets/image%20%28176%29.png)

### The Stack

When you call a function the computer sets aside space in memory for the function to do its work. This memory space that is set aside for the function call is called a **stack frame**. The stack frame contains space for all the variables that are allocated for the function to run, such as input parameters, local variables, and a return value.

The stack section of memory is like a a stack of plates in a cafeteria. Each plate represents a stack frame, and you can push new stack frames on to the top of the stack and pop ones that are done off the top of the stack.



![](https://lh3.googleusercontent.com/j_LfQtWOwbbtl3L48wxqAs-ck9v7yPHFWfnKqcUXcS3E-FAjxSrKDNuoiNQvq9vHeXi_HAvAjpHxFUs2j3sQXJWVVco5Nf2d__YG8MjQzhvtSutkAvkyHLTvxTrcNT5WAKBP0ME66w)

When a function is called, a stack frame is pushed onto the top of the stack. When it has completed, the stack frame associated with the function is popped off the top of the stack. Only the stack frame on the top of the stack is "active" at a given time. The stack frames below are on "pause", waiting for the functions, or stack frames, above it to complete and be removed.

The act of adding something onto the top of a stack is known as "pushing" and the act of removing something from the top of a stack is known as "popping". So you can push and pop stack frames as the function calls execute.

When a stack frame for a function call is complete, such as it returns a value, then the stack frame is popped, and the stack frame immediately below it becomes the active frame, at the line where it was calling the function that was just popped off the stack.



![](https://lh4.googleusercontent.com/W46nRTVwXW_DRtdV-BiRk0DPL2bolB7Bk-WujrDpWe7aBYUVvJdR_HZoi9NMGMLVevIxSpvZN2lcBBntay4ITgWghcObnAL4CbShVOCWgXLAv4CBpMXafYLXHvpzynSUmV70owR-JQ)

Let's walk through an example. We've got a function named fact, which will return the factorial of a number. 

![](../.gitbook/assets/image%20%28219%29.png)

The implementation of the fact function is **recursive**, meaning that it calls itself. It's a little tricky to visualize what is happening in a recursive function, so we can step through it.

```javascript
function factorial(n) {
    if (n===1) return 1;
    else return n * factorial(n-1);
}

let answer = factorial(6);
console.log(answer);
```

There's a really helpful visualization in the following article for calculating factorial of 6.

{% embed url="https://medium.com/swlh/visualizing-recursion-6a81d50d6c41" %}

We can also step through the code in the debugger, to see the stack frames pushed and popped as we move down through the recursive calls to the fact function.

What you can see from this process, is that the stack memory area is used for the short-term allocation of data associated with executing a function.

### Stack-Overflow Exception

The stack memory are typically grows downward while the heap memory area grows upward and the available memory is in between.

![](../.gitbook/assets/image%20%2868%29.png)

If you accidentally call a function recursively, without an exit path, then you can end up continually adding new stack frames until you run out of space. This will trigger a "stack-overflow" exception by the operating system and the program will end.

Here's a C\# program to demonstrate this.

![](../.gitbook/assets/image%20%28364%29.png)

You can see the call stack continue to grow.

![](../.gitbook/assets/image%20%289%29.png)

Until it eventually is halted with an exception.

![](../.gitbook/assets/image%20%28192%29.png)

### 

### Primitive vs Reference Variables

It's important to understand how the variable values stored on the stack work, because there is a very big difference when the variable's value is a primitive datatype, such as a number or a boolean value, and when the value is an object.

#### Primitive Data Types

Let's start with depicting the stack memory space as a section of the bookshelf and each shelf as a number associated with it. The number is the address of the shelf, or where the variable's value is located.

We'll declare a variable, named num1, that is going to store a number. We're using small numbers to represent the shelf addresses to simplify the picture. 

For this example, the declaration of the variable num1 is associating num1 with shelf \#7 in the computer's stack memory area.

#### Variable Declaration and Initialization

```javascript
// allocate space for the variable num1 on shelf #7
let num1 = 10;
```

![](../.gitbook/assets/image%20%2854%29.png)

#### Variable Assignment

When you assign a new value  to a variable. you are asking the computer to change the value that is stored on the shelf reserved for that variable.

```javascript
// put the value 2 on shelf #7
num1 = 2;
```

![](../.gitbook/assets/image%20%28126%29.png)

#### Assigning One Variable to Another

When you assign the value of one numeric variable to another, the computer copies the value stored on the shelf for the variable on the right-hand side of the assignment operator to the shelf of the variable on the left-hand side of the assignment operator.

Each variable now contains its own value, and modifying either of them does not impact the value stored in the other.

![](../.gitbook/assets/image%20%28261%29.png)

![](../.gitbook/assets/image%20%28234%29.png)

This explanation is the way it works for primitive datatypes, such as numbers and boolean values. 

#### Objects

Variables that store object data work differently.

When you declare a variable that is an object or an array, the variable also refers to a shelf in the computer's stack memory to store the variable's data. But the data associated with an object can be very large, and the size isn't always known when the program is being compiled, so the actual data associated with the variable is stored in a special section of the computer's memory, known as the **heap.** 

The location **\(shelf \#\)** in the heap where the data is stored is what is stored for the value of the variable in the stack memory area.

```text
let arr1 = [12, 5, 2, 8, 3];
```

![](../.gitbook/assets/image%20%28348%29.png)

Like the variable that held a numeric value, you can assign one variable to another that is storing an object. In both cases, the value of the variable is what is copied. But in the case of a variable storing an object, the value is the address of the shelf in the heap where the object's data is stored.

![](../.gitbook/assets/image%20%2810%29.png)

As you can see in the image below, it is the memory address of of the data associated with the object in the heap area that is copied when one object variable is assigned to another. That means that arr1 and arr2 are now both referring to the same array in the heap. 

![](../.gitbook/assets/image%20%2898%29.png)

So, when a modification is made through either arr1 or arr2, they are both modifying the same array. This is the way it works for any variable that is an array or object.

![](../.gitbook/assets/image%20%28298%29.png)

#### Heap Objects and Garbage Collection

Objects in the heap are not removed when the function's call stack is popped. When a function completes, the stack frame holding the memory in the stack is popped. That means that the shelves that were set aside for the local variables in the function are available for the next function call, and the shelves will be loaded with new values when that happens.

#### During Function Execution

The local variables within the function are added to the stack frame and the top of the stack is indicated by the red line.

```javascript
  function f1() {
    let arr1 = [1, 2, 3, 4];
  
    let num = 10;
    let done = false;
  }
    
  f1();
```

![](../.gitbook/assets/image%20%28363%29.png)

#### After Function Execution

When the function is done, the stack frame pointer \(the red line\) is just moved to the top of the previous stack frame. Nothing is done to the values in the memory from the popped stack frame. It is just that the memory is now available, and will be overwritten by the next function call's stack frame.

![](../.gitbook/assets/image%20%28154%29.png)

As you can see, the actual object values being referred to by the variables on the stack stick around in the heap. In fact, they stick around until the JavaScript Engine's Garbage Collector determines that they are no longer being referenced.

For example, if your function creates a new array, and returns it as the return value from the function, and your code does not store that returned array in a local variable, that array will still exist in the heap. The Garbage Collector runs periodically, and has a complicated algorithm for determining when objects are no longer being referenced, and it re-organizes them to efficiently run the algorithm.

#### Strings

Strings are also objects, and the data associated with the variable is also stored on the heap. So they work similarly to arrays and objects in how the memory associated with the variable is stored.

But there is an important difference with string data. Strings are "immutable". That means that you cannot change the value associated with a string variable. For example, you cannot use bracket notation like you would in an array to change the character at a particular location in a string.

![](../.gitbook/assets/image%20%2823%29.png)

Like other objects, the string's data is stored in the heap, and when one string variable is assigned to another, they will both refer to the same string in the heap.

![](../.gitbook/assets/image%20%28351%29.png)

In the example below, str1 and str2 will be referring to the same string after line 2 is complete.

```javascript
  let str1 = "hello";
  let str2 = str1;
```

But, if you try appending a value to one of the variables, a new string will be allocated and assigned to the variable, and then the two variables will refer to different strings.

So, when the string "world" is appended to the variable str1, a new string will be allocated and that new string with the appended value will be assigned to the variable str1 and str2 will still refer to the string that it was assigned initially.

![](../.gitbook/assets/image%20%28116%29.png)

So, the take-away for string is that they work like other objects in where their data is stored, and how the variable refers to that data, but, because they are "immutable", they appear to work more like primitive datatypes that "copy" the value when the assignment occurs.

### Primitive vs Object Data View

The image below shows the difference between primitive data types and objects in how the data associated with the value of the variable is stored. The variables that are objects and arrays hold a value that is the location to \(a reference\) the shelf in the portion of memory called the heap where the actual object dat is stored.

When an assignment occurs, the value in the stack is what is copied from the source variable's shelf to the destination variables shelf. For objects, that is the address of the variable's data in the heap.

![](../.gitbook/assets/image%20%282%29.png)

### Comparing Values

This has important implications when two variables are compared. 

For example, if you have two variables holding numbers, and you compare them with the === operator, the result will be true if both variables are storing the same value.

![](../.gitbook/assets/image%20%28320%29.png)

And if you change the value of one variable and compare them, they will no longer be equal.

![](../.gitbook/assets/image%20%28337%29.png)

If you do the same with two arrays, you need to understand how the === operator works. It compares the value of the two variables. Which is the address of the data for each variable, not the actual data.

![](../.gitbook/assets/image%20%2831%29.png)

![](../.gitbook/assets/image%20%28148%29.png)

### Reference Variables

It's important to understand that it's not just object variables that you declare at the top-level in your code that have references to object data on the heap. The properties of objects, or the elements within an array are also variables, and if they are objects or arrays, then the value for the object properties, or array elements are also going to be the memory address for the data associated with the object.

For example, below we have an array that contains two elements. Each element is an object that has two properties: name and age. 

The top-level variable, named array, that was declared by you in your code, has as its value the memory address in the heap where the array data is stored.

But the array data elements are objects as well, so the value stored in the array in the heap for each element is also a memory address, referring to where the object for that array element is stored in the heap.

This is how the computer stores your data in memory. Anything data that is an object \(object includes arrays\) is going to be stored on the heap, and the variable that refers to it \(either a top-level variable you declared, or a property of an object, or an element in an array\) will have as its value, the memory address of where that object is stored in the heap.

It is necessary because you cannot have all of your memory allocated in a contiguous arrangement. It would be too difficult to manage memory that way. The computer needs to be able to allocate data where there is room, and move data around to organize it more efficiently. 

![](../.gitbook/assets/image%20%2875%29.png)

### Shallow Copy

It's important to understand what happens when we create a new array and push objects onto the array. We are not creating a copy of the object. We are just copying the reference to the object. So the new array will contain references to the same elements as the old array.

Take a look at the example below. array1 currently contains four elements that are each objects with two properties: x and y.

We've also declared a second array, named array2, that is currently empty \(I'm showing four empty elements just to indicate where the new elements will go\).

```javascript
const array1 = [{x:1, y:45}, {x:2, y:34}, {x:12, y:42}, {x:23, y:34}];
let array2 = [];
```

![](../.gitbook/assets/image%20%28345%29.png)

![](../.gitbook/assets/image%20%28244%29.png)

![](../.gitbook/assets/image%20%28325%29.png)

When the element from array1 is pushed onto array2, it is pushing the value that is stored in the shelf for the array1 element. That is the memory address of the object at that array element, not the actual data. So what is being copied is a reference to the object.

### Spread Operator

The spread operator is a feature that allows you to access content of an iterable object, such as an array or an object literal.

![](../.gitbook/assets/image%20%28242%29.png)

It's a convenient way to copy an array and add new values in one step. 

![](../.gitbook/assets/image%20%28144%29.png)

Or to combine two arrays into a new array:

![](../.gitbook/assets/image%20%28123%29.png)

It works the same for objects

![](../.gitbook/assets/image%20%2820%29.png)

### Using the Spread Operator to make a copy of an array

The spread operator is performing the same operation as the forEach loop above. It first creates a new array, then pushes each element into the new array.

![](../.gitbook/assets/image%20%28200%29.png)

### React's State Comparison 

This knowledge has implications for how React compares whether the state has changed since the last update.

#### Primitive State

First, let's start with a simple example where are React component is just storing a primitive value for its state. In this case, when we call the update function for the state variable, React will compare the old and new value and detect that it has changed, and trigger a call to the render function to update the component's UI.

```javascript
function NumState() {
  const [num, updateNum] = useState(1);


  return (
    <>
    <div class="container">
      num: {num}
    </div>
    <input id="newNum" type='text' onChange={({target})=>updateNum(target.value)}/>
    </>
  )
}
```

#### Array State

But, if we are storing the state of an array variable, things work differently.

React compares the current array to the one passed into the update function with the === operator. It is a "shallow" compare. It is not comparing the elements in the array, just whether the two arrays are the same.

So, if the code just pushes a new value on to an array, or changes the value stored in an element within the array, but passes the same array to the React update function, React will find that the two arrays are the same and will not re-render the component's UI.

```javascript
function ArrayState() {
  const [nums, updateNums] = useState([1,2,3,4]);

  return (
    <>
    <div class="container">
      {nums.map(x=><div>{x}</div>)}
    </div>
    <Button variant="primary" size="sm" onClick={
      ()=>{
        nums.push(5); 
        updateNums(nums);
        }
      }>Add Number</Button>
    </>
  )
}
```

In order to get React to find a difference, you need to pass in a new array to the update function.

In the code below, instead of pushing a new element onto the array, a new array is created, and the spread operator is used to copy the values from the old array into the new array, and the five is added to the array.

```javascript
function ArrayState() {
  const [nums, updateNums] = useState([1,2,3,4]);

  return (
    <>
    <div class="container">
      {nums.map(x=><div>{x}</div>)}
    </div>
    <Button variant="primary" size="sm" onClick={
      ()=>{
        //nums.push(5); 
        updateNums([...nums, 5]);
        }
      }>Add Number</Button>
    </>
  )
}
```

#### Object State

This is the same issue for objects

```javascript
function ObjectState() {
  const [user, updateUser] = useState({firstName: 'Anne', lastName: 'Chinn'});

  return (
    <>
    <div>
      firstName: {user.firstName}
    </div>
    <div>
      lastName: {user.lastName}
    </div>
    <Button variant="primary" size="sm" onClick={
      ()=>{
        user.firstName = "Sally";
        updateUser(user);
        }
      }>Change Name to Sally</Button>
    </>
  )
}
```

You need to create a new object, and use the object spread operator to copy the parameters of the first object into the new object, and then update the field that changed.

```javascript
function ObjectState() {
  const [user, updateUser] = useState({firstName: 'Anne', lastName: 'Chinn'});

  return (
    <>
    <div>
      firstName: {user.firstName}
    </div>
    <div>
      lastName: {user.lastName}
    </div>
    <Button variant="primary" size="sm" onClick={
      ()=>{
        //user.firstName = "Sally";
        updateUser({...user, firstName: 'Sally'});
        }
      }>Change Name to Sally</Button>
    </>
  )
}
```

### React

In the case of the React examples above, we used the spread operator to create a new array and add a new value, and then passing the new array to React's update function.

```javascript
updateNums([...nums, 5]);
```

and, we used the same technique to create a new object, first copying the properties of the old object, and then updating the property that changed.

```javascript
updateUser({...user, firstName: 'Sally'});
```

### Destructuring

Destructuring allows you to pull out values from either an array or an object literal and assign them to one or more variables in a single step.

It can be used for objects

![](../.gitbook/assets/image%20%28396%29.png)

 And arrays

![](../.gitbook/assets/image%20%28127%29.png)

### - React's useParams function uses array destructuring

The useState function is used to tell React that it should manage the state of a variable in your component. You give it one parameter, which is the initial value for the state variable. In the code below, we are going to store an array of numbers, and we want the initial value for the array to be the number 1.

```javascript
function ArrayState() {
  const result = useState(1);
  ...
  result[1](2);
  
  return (
    <h1>{result[0]}</h1>
    );
}
```

The useState function returns an array with two values.

* result\[0\]: the current value of the variable.
* result\[1\]: the function your code must call to update the value of the variable.

But, it is cumbersome to reference the array to get the value and update function, so it is expected that you will use array destructuring to create two variables that hold the values in the first and second elements of the array.

So, in the code below:

* num: holds the current value of the variable
* updateNum: the function your code must call to update the value of the variable.

```javascript
function ArrayState() {
  const [num, updateNum] = useState(1);
  ...
  updateNum(2);
  
  return (
    <h1>{num}</h1>
  );
}
```

### React uses object destructuring for component function props params

In our ArticleSection component, we create an ArticleGrid component in our JSX and we pass it the array of article data for it to render. 

React creates a special object, called props, that contains a property for every attribute that is on the component and passes that object as the parameter to the function.

```javascript
<ArticleGrid articles={articles}/>
```

The ArticleGrid component could have been written with the parameter named "props" and to access the articles passed into it from the ArticleSection component, we would refer to it with object notation "props.articles" as shown in the first example below.

```javascript
function ArticleGrid(props) {
  return (
    <section className="articles">
      {props.articles.map(x=><ArticleCard key={x._id} article={x}/>)}
    </section>

    );
}
```

But, the preferred way to do it is to use object destructuring to get the specific property out of the passed in props object as demonstrated below.

```javascript
function ArticleGrid({articles}) {
  return (
    <section className="articles">
      {articles.map(x=><ArticleCard key={x._id} article={x}/>)}
    </section>

    );
}
```

This might now seem as clear when destructuring a function parameter, but you have to remember that an assignment is occurring when a parameter is passed to a function call. The props parameter is being assigned the value passed in by React. And so we can destructure the props object and assign any of its properties to specific variables. In this case, we're assigning the props.articles property to the variable articles.

### let vs const

These two keywords are relevant to this discussion. When we use the keyword const to declare a variable, what we are saying is that you cannot change the value that is stored in the variable's memory location. 

For a primitive data type, such as a variable storing a number, it means that you can not assign the variable a different number. 

But, for a variable that is storing an object as its data, it means that you cannot change the address of the object on the heap that the variable is referring to. You can change anything within the object tough, such as modifying an array, or the properties within an object.

#### Homework

I want you to create three components in your practice folder, following the examples I demoed during class.

* NumState - a state variable that stores a single number and changes the value of the number.
* ArrayState - a state variable that stores an array of numbers, and adds a number to the array
* ObjectState - state variable that stores an object and updates one of the properties.

Each of these components was demonstrated in the class video, and the code for the components is shown above in the section on this page for React State Comparison. I have also checked in my code samples so you can do a git pull in the main branch to see my solutions.

Re-watch the video and review the content on this page, and then try to implement the components on your own without copying the code samples, and then review the code when you get stuck.

