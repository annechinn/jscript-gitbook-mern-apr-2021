# Event Handlers

### Responding to Events

Once a web page is loaded, it is just waiting until the user interacts with it. For example, a user can click a button, move his mouse, push a key on his keyboard, or resize the window. The web browser is detecting all of these events and you can tell the web browser that it is interested in being notified when a particular type of event occurs on a particular element on the page.  This process is known as registering for an event handler. An event handler is a block of code, typically a JavaScript function that the web developer writes, that will be run when the event fires.

### Registering an Event Handler

There are several ways to register an event handler.

#### **Inline as an HTML attribute**

For example, to register for the click event, you would create an attribute with the name onclick and assign in the JavaScript code to execute when the event occurs.

```javascript
<input value="Click me" onclick="alert('Clicked!')" type="button"/>
```

It is a better practice to move the event handler into a separate function in your script code, rather than directly inline in the attribute value.

```javascript
function clickHandler() {
    alert('Clicked!');
}
```

```javascript
<input value="Click me" onclick="clickHandler()" type="button"/>
```

#### DOM Property

The element has an id attribute and the script can register the event handler by referencing the element id as demonstrated below.

```javascript
<input id="elem" type="button" value="Click me">
<script>
  elem.onclick = function() {
    alert('Clicked!');
  };
</script>
```

Note that the browser will read the onclick attribute below and generate the DOM Property method, so the HTML inline attribute is just a convenience method for generating a DOM Property

{% hint style="info" %}
It is important to understand why in the inline attribute method, the clickHandler function is specified as clickHandler\(\) instead of clickHandler.  It is because the attribute value is a string, not a function call, and the string is just placed in the body of the generated code in the &lt;script&gt; block. The clickHandler method will not be called until the event occurs.
{% endhint %}

```javascript
// If it is specified like this...
<input type="button" onclick="clickHandler()" value="Button">

// The browser will generate this ...
<input type="button" id="button" value="Button">
<script>
  button.onclick = function() {
    clickHandler();
  };
</script>
```

#### addEventListener/removeEventListener

The problem with the two previous ways of registering an event handler is that it is only capable of registering a single handler for the event. The addEventListener and removeEventListener methods on the DOM element gets around this issue.

```javascript
<input id="button1" type="button" value="Button">
```

```javascript
function clickHandler() {
  alert( 'Clicked!' );
}

button1.addEventListener("click", clickHandler);
```

#### Event Data

When an event happens, the browser creates an _event object_, initializes it with information about the event, and passes it as an argument to the handler. The information included includes the type of event, and the coordinates of the mouse at the time the event was fired.

```javascript
function clickHandler(event) {
  alert( 'Clicked!' );
}
```



