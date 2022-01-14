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