# If/Else

### If

In the code below we are prompting the user to enter a username and password, and the code checks to see whether the user is authorized to access the site. **If** he is, **then** we will re-direct him to his dashboard page.

The **if keyword** indicates an if statement. This is followed by a set of opening and closing parentheses which contains a condition to test.   And finally a block of code to execute if the condition is true. The block of code can be a single statement, or a sequence of statements surrounded by curly braces. 

```javascript
let userName = prompt("Enter your username:");
let password = prompt("Enter your password:");
let authorized = isUserAuthorized(userName, password);

if (authorized) {
    goToDashboardPage();
}
```

If there is only a single statement in the body of the code block, then the curly braces surrounding the code block are not required. Requiring the braces is often a style convention within companies. For example, here is the style-guide from Google for this issue.

![](../.gitbook/assets/image%20%2825%29.png)

### Else

In many cases you will want your code to take a different path when the condition evaluated in the if expression is false. In this case you use can add the **else block** to the if statement.

```javascript
let userName = prompt("Enter your username:");
let password = prompt("Enter your password:");
let authorized = isUserAuthorized(userName, password);
if (authorized) {
    goToDashboardPage();
}
else {
  alert("Wrong username or password");
}
```

### More Than Two Paths

With the if/else use case above, the condition is evaluated and if it is true, then one path is taken, otherwise an alternate path is taken. If there are multiple pathways that could result then there are two ways to handle that condition.

#### Nested If Statements

You can use the following structure:

{% hint style="info" %}
The prompt function returns a string. To convert the string to a number, use the JavaScript parseInt function.
{% endhint %}

```javascript
// prompt will return null if user clicks Cancel
let grade = prompt("Enter points out of 100");
if (grade) {
    // convert the string to a number
    grade = parseInt(grade);
    if (grade >=90) {
        alert("A");
    }
    else if (grade >= 80) {
        alert("B");
    }
    else if (grade >= 70) {
        alert("C");
    }
}
```

You are actually nesting the if statements here. It doesn't look like it because you are not required to use curly braces for the action when the if or else path contains a single statement. 

These following two code samples are equivalent. It works because the formatting of the source code makes it very readable, even though it's goes against the style guide of requiring block braces, unless it can all fit on a single line. Most style guides would allow this exception as long as the code is formatted this way.

```javascript
let grade = prompt("Enter points out of 100");
if (grade) {
    grade = parseInt(grade);
    if (grade >=90) {
        alert("A");
    }
    else if (grade >= 80) {
        alert("B");
    }
    else if (grade >= 70) {
        alert("C");
    }
}
```

```javascript
let grade = prompt("Enter points out of 100");
if (grade) {
    grade = parseInt(grade);
    if (grade >=90) {
        alert("A");
    }
    else  {
        if (grade >= 80) {
            alert("B");
        }
        else {
            if (grade >= 70) {
                alert("C");
            }
        }
    }
}
```

### Exercise

You're going to write an interactive program that simulates you on the phone with your roommate. You forgot to bring your grocery list for the recipe you are cooking for dinner, so you've called your roommate to make sure you pick up the correct items.

You are making a fruit salad, so you know you need different types of fruit, but you can't remember how many of each, so you're going to ask your roommate.

* how many pounds of apples?
* how many pounds pears?

Once you've collected these values through the prompt function, you need to figure out how much the fruit costs altogether based on their cost per pound.  

* apples are $2.29/lb.
* pears are 2.99/lb.

Now you need to figure out how much the total is when you add the sales tax, which is 10%  \(I know we don't charge sales tax on food in stores, but this is just an exercise\).

Once you calculate the total, you need to use the confirm function to check with your roommate that it's ok to spend the total amount that you calculated. If he says ok, then use the alert function to say you bought everything and coming home. If he cancels, then user the alert function to say you put everything back and are coming home.

Here's a few requirements:

* use **const** variables whenever possible.
* write a function calculateTotalWithTax, that has two parameters, the total before taxes, and the tax rate, that returns the total, including with taxes included.
* the confirm message should contain the total cost.
  * the cost should be the nearest dollar amount, not including cents.
    * use the Math.floor function to round down.
  * use back-ticks, \`\`,  with the ${} syntax to build the string to pass to the confirm function that includes the total spent.

You can assume the user clicks the Ok button rather than Cancel when entering the number of pounds.

![](../.gitbook/assets/image%20%28282%29.png)

![](../.gitbook/assets/image%20%28410%29.png)

![](../.gitbook/assets/image%20%28218%29.png)

If the user clicks Ok

![](../.gitbook/assets/image%20%281%29.png)

If the user clicks Cancel

![](../.gitbook/assets/image%20%28416%29.png)

