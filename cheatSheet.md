# About
jQuery is the **most widely-used JavaScript library** and allows you to program many different cool effects on your web pages, including **color changes**, **animations**, and **fade in/fade out effects**. 

## What do JavaScript and jQuery look like?
Here's a sample chunk of JavaScript that adds a "starred" class to each list item:
```js
var listItems = document.querySelectorAll('li');
var i;
for (i = 0; i < listItems.length; i++) {
    listItems[i].className = 'starred';
}
```
Here's a sample chunk of jQuery that does the same thing:
```js
$("li").addClass("starred");
```
**jQuery is simply a JavaScript file.**

# jQuery Documentation
https://api.jquery.com/

# Basic JS concepts
## DOM
The Document Object Model (DOM) can be one of the most difficult, abstract concepts in programming. It requires an understanding of the interplay between the HTML you write and the browser's representation of it.

A web page you see in your browser is a document object. This is the modeling of your page in the browser. The DOM is not the exact HTML that you wrote; instead, it's the exact HTML you wrote **modeled** by the browser. Often, the two will look identical, but a browser's modeling of HTML allows the targeting of elements within the HTML by other programming languages like JavaScript.
## Operators
Programming isn't that different from math. You have a set of operations chained together with an eventual result. Operators are a simple representation of this concept!
## Functions & Variables
Functions and variables are two JavaScript concepts you'll use often in jQuery.

A variable is a piece of data stored under a different name or "identifier." Storing this data allows the scripts you write to keep information organized for future reference.
```js
var firstName = "Emily";
```

A function is a set of code that executes or performs an action.
```js
function greetStudents() { //defined function
    alert('Hello students!'); //statement
}
greetStudents(); //called function
```

# Including jQuery to project
First, you need to include jQuery in your web projects. There are **two different formats** in which jQuery is available: **development and production formats**.
- The **development file** is **larger** because it's annotated in a way that makes it easier for developers to understand what's going on in the code. There are code comments, useful whitespace to separate sections, and more. `jquery-1.12.2.js`.
- The **production format** is **smaller** and therefore faster to use on your live web pages. Most of the annotations you'd find in the development format have been removed, since the end "user" will be a web page and not a human being who would benefit from additional remarks about the code. `jquery-1.12.2.min.js`. 

**Use the development format when** you're working on your project so you see the helpful comments and annotations. **Use the production format** once you make your project live on the web so it performs better.

https://jquery.com/download/

- Latest version now: https://code.jquery.com/jquery-3.6.0.min.js
- CDN: https://code.jquery.com/jquery-3.6.0.min.js
- CDN: https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.js
- CDN: https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
        <link rel="stylesheet" href="css/styles.css" />
    </head>
    <body>
        <p>Page content here</p>
        <!-- include jQuery via CDN -->
        <script src="//code.jquery.com/jquery-1.12.0.min.js"></script>
        <!-- your own file in your project folder -->
        <script src="js/javascript_file_where_you_write.js"></script>
    </body>
</html>
```

# Working with jQuery
## Selecting Elements
Think of selecting an element as identifying it. You might need to identify an individual elements, multiple elements, elements that meet a set of criteria, etc. jQuery lets you identify and select elements using a 
https://developer.mozilla.org/en/docs/Web/Guide/CSS/Getting_started/Selectors . For example select by element type, by class, by ID.

Enter the **famous jQuery dollar sign!** `$()` is shorthand for a function called `jQuery()`  that **finds elements in a page and creates jQuery objects** that reference the found elements.

- `$('p')` : selects all `p` (paragraph) elements
- `jQuery('p')` : same thing, but takes more time to type. **Use the dollar sign!**

**jQuery cannot be used on elements until those elements are jQuery objects**, which gives them access to the whole jQuery world. Enrobing them in the `$()` method turns them into jQuery objects on which you can call jQuery methods. Before that, they're simply elements in the DOM.
### Select by relationship
https://api.jquery.com/category/selectors/hierarchy-selectors/

**Parent**, **child**, and **sibling** elements.

- Descendants:

`$("ancestor descendent")` : Select all elements that are underneath and within an ancestor element.
```js
$("ol li") // select all <li>'s that are within <ol>
```
- Parents and children:

`$("parent > child")` : Select **all children** that are **immediate descendants** of a parent element (also called a **child combinator selector**).
```js
$("ol > li") // select all <li>'s that are direct descendants of <ol>
```
- Siblings:

`$(element ~ siblings)` : Select **any siblings** of the first specified element. `element` not be selected.
```js
$("li#first ~ li") // select the <li> siblings of the first <li>
```
`$(element  + sibling)`  : Select the **sibling element** that immediately follow the first specified element.
```js
$("li#first + li") // select the first sibling of a specified <li>
```

### Filters
https://api.jquery.com/category/selectors/basic-filter-selectors/

Sometimes you don't care about the relationships between your elements; you just care about what they **are** or **aren't**.
- `:first` : selects the first of an element
```js
$("p:first") // select first <p>
```
- `:last` : selects the last of an element
- `:eq(index)` : selects the element at a specified index number (this is where arrays come in handy!)
```js
$("li:eq(1)")
```
```html
<ul>
    <li>First (so index = 0)</li>
    <li>Second (so index = 1)</li> <!-- selected -->
    <li>Third (so index = 2)</li>
</ul>
```
- `:gt(index)` : selects element(s) at a greater index number than the specified number
```js
$("li:gt(0)")
```
```html
<ul>
    <li>First (so index = 0)</li>
    <li>Second (so index = 1)</li> <!-- selected -->
    <li>Third (so index = 2)</li> <!-- selected -->
</ul>
```
- `:lt(index)` : same concept but for elements at a lesser index number than the specified number
- `:not(selector)` : selects elements that aren't, well, the selector!
```js
$("li:not('.vegetable')")
```
```html
<ul id="groceries">
    <li class="vegetable">Eggplant</li>
    <li class="vegetable">Carrot</li>
    <li class="fruit">Apple</li> <!-- selected -->
</ul>
```
### Additional filters

- `:hidden`: selects hidden elements (elements that have a CSS display value of none, are `type="hidden"`, have width and height values of 0, or have hidden ancestor elements)
- `:visible` : selects visible elements
- `:contains("text")` : elements that contain the specified text
- `:has("element")` : elements that contain the specified element
- `[attribute]` : elements that have the specified attribute, ex. `$("[align]")`
- `[attribute="value"]` : elements that have the specified attribute and value, ex. `$("[align=center]")`
- `[attribute!="value"]` : elements that do not have the specified attribute and value, ex. `$("[align!=center]")`

### Form selectors

https://api.jquery.com/category/selectors/form-selectors/

These filters are shorthand for `$("[type=XXXXXXX]")`. For example,`$(":checkbox")` is the same thing as`$("[type=checkbox]")`.

- `:input` : selects input elements
- `:password` : selects password inputs
- `:text` : selects text inputs
- `:checkbox`: selects checkboxes
- `:radio` : selects radio buttons
- `:submit` : selects submit buttons

## Methods
### Effects
- `.show()` : displays the selected element(s).
- `.hide()` : hides the selected element(s).
- `.toggle()` : displays or hides element(s) depending on the element's current state.
- `.fadeIn()` : fades in element(s).
- `.fadeOut()` : fades out element(s).
- `.fadeTo()` : fade element(s) to a certain opacity.
- `.slideUp()` : hide element(s) with a sliding up motion.
- `.slideDown()` : hide element(s) with a sliding down motion.
- `.slideToggle()` : hide or show element(s) with a sliding motion depending on the element's current state.

For all of the above elements, you can pass several **optional parameters**. You'll commonly pass the effect duration in milliseconds. For example,`.fadeIn(1000)` will cause an element to fade in over the course of 1000 milliseconds (1 second). The higher the number, the slower the effect. Alternatively, the strings`'fast'` and`'slow'` can be passed instead of numbers.`'slow'` represents a duration of 600 milliseconds, and`'fast'` represents a duration of 200 milliseconds. Without any parameters, the effects happen over the default duration of 400 milliseconds.

### Content manipulation
- `.find()` : find element(s) within current selection that match parameter
- `.parent()` : access direct parent of element(s) or parents if .parents()
- `.children()` : access children of element(s)

- `.height()` - box height **without margin, padding, or border**
- `.width()` - box width **without margin, padding or border**
  
- `.innerHeight()` : height **including padding**
- `.innerWidth()` : width including padding
- `.outerHeight()` : height **including padding and border**
- `.outerWidth()` : width including padding and border
- `.outerHeight(true)` : the same method as above, but **passing the parameter true includes the margin too**.
- `.outerWidth(true)` : the same method as above, but passing the parameter true includes the margin too.

- `.offset()` : set element **coordinates relative to the very top-left of the document object**
- `.position()` : set element coordinates relative to its offset parent, useful for **positioning elements within the same DOM element**. You'll probably use `.offset()` more.

## Events
The jQuery `.on()` method is your key to working with events. You **pass the event**  (for example ‘click’) as a parameter to the `.on` method, followed by a **second parameter** containing what’s called a **event handler function**. Within the function, you write your usual jQuery code that will be executed upon the event’s happening. Using.on() creates what’s called an **event listener**, which means the code is waiting for the certain event to happen.
```js
.on('click', function() { … }
.on('scroll', function() { … }
.on('hover', function() { … }
.on('mouseover', function() { … }
.on('mouseenter', function() { … }
.on('mouse leave', function() { … }
.on('keydown', function() { … }
.on('keyup', function() { … }
.on('keypress', function() { … }
.on('focus', function() { … }
.on('blur', function() { … }
.on('resize', function() { … }
```
Previously, jQuery had specific methods for each event, like: `.click()`, `.blur()`, `.mouseover()`. But `.on()` clearer!
```js
$('p').on('click', function() {
    alert('Someone clicked on a paragraph!')
});
// vs
$('p').click(function() {
    alert('Someone clicked on a paragraph!')
});
```
### Event Object
Sometimes you’ll need to have **information about the event**. The event object has several property types. Of course, you have `type` property, which describe which type of event occurred. You also have event’s `target` property (which element kicked off the event, such as `click`), `pageX` and `pageY` (mouse positions from the left and top of what the user sees of the page), `timeStamp` (how many milliseconds it’s been since 1/1/1970).

To interact with the event object in your function, you **pass the `event` as a parameter there in**. 
```js
// Declare variable that references all paragraphs:
var $p = $('p');
// Pass event as parameter to function:
$p.on('click', function(event) { 
  // Create a date variable that grabs event’s timestamp
  var date = new Date(event.timeStamp);
  // Replace paragraphs with the text 
  $p.text("You clicked on: " + date)
});
```