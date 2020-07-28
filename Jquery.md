# jQuery

jQuery is a fast and concise JavaScript Library created by John Resig in 2006 with a nice motto: **Write less, do more**. jQuery simplifies HTML document traversing, event handling, animating, and Ajax interactions for rapid web development. jQuery is a JavaScript toolkit designed to simplify various tasks by writing less code. Here is the list of important core features supported by jQuery −

- **DOM manipulation** − The jQuery made it easy to select DOM elements, negotiate them and modifying their content by using cross-browser open source selector engine called **Sizzle**.
- **Event handling** − The jQuery offers an elegant way to capture a wide variety of events, such as a user clicking on a link, without the need to clutter the HTML code itself with event handlers.
- **AJAX Support** − The jQuery helps you a lot to develop a responsive and feature rich site using AJAX technology.
- **Animations** − The jQuery comes with plenty of built-in animation effects which you can use in your websites.
- **Lightweight** − The jQuery is very lightweight library - about 19KB in size (Minified and gzipped).

## How to use jQuery?

There are two ways to use jQuery.

- **Local Installation** − You can download jQuery library on your local machine and include it in your HTML code.
- **CDN Based Version** − You can include jQuery library into your HTML code directly from Content Delivery Network (CDN).

## Local Installation

- Go to the https://jquery.com/download/ to download the latest version available.

## $( document ).ready()

A page can't be manipulated safely until the document is "ready." jQuery detects this state of readiness for you. Code included inside `$( document ).ready()` will only run once the page Document Object Model (DOM) is ready for JavaScript code to execute.

```javascript
$(document).ready(function(){
    alert('document loaded');
})
// Shorthand for $( document ).ready()
$(function() {
    console.log( "ready!" );
});
```

The difference between window.onload and  jQuery load is that the onload waits till the  the entire page (images or iframes), not just the DOM, is ready.

```javascript
window.onload=function(){
    this.alert('window loaded');
}
```

## Conflict

There will be  conflicts when we are using the  $  best way is to use  import jQuery first or  assign a  new  alias  by using  noConflict() method

```javascript
const $jq=jQuery.noConflict()
//or
jQuery(document).ready(function( $ ) {
    
});

```

## Selecting Elements

### Selecting Elements by ID

```js
$( "#myId" ); 
```

### Selecting Elements by Class Name

```javascript
$( ".myClass" );
```

### Selecting Elements by Attribute

```javascript
$( "input[name='first_name']" );
```

### Selecting Elements by Compound CSS Selector

```javascript
$( "#contents ul.people li" );
```



## Creating a new Element

It can be done using   append or prepend   

```javascript
// //append
$('.list').append('<li class=\'list\'>append</li>')

// //prepend
$('.list').prepend('<li>prepend</li>')
```

### Manipulating Attributes

jQuery's attribute manipulation capabilities are extensive. Basic changes are simple, but the .attr() method also allows for more complex manipulations. It can either set an explicit value, or set a value using the return value of a function. When the function syntax is used, the function receives two arguments: the zero-based index of the element whose attribute is being changed, and the current value of the attribute being changed

```javascript
// Manipulating a single attribute.
$( "#myDiv a:first" ).attr( "href", "newDestination.html" );

// Manipulating multiple attributes.
$( "#myDiv a:first" ).attr({
    href: "newDestination.html",
    rel: "nofollow"
})
```

## Traversing

Traversing can be broken down into three basic parts: parents, children, and siblings. jQuery has an abundance of easy-to-use methods for all these parts. Notice that each of these methods can optionally be passed string selectors, and some can also take another jQuery object in order to filter your selection down. 

### Parents

The methods for finding the parents from a selection include `.parent()`, `.parents()`, `.parentsUntil()`, and `.closest()`

```html
<div class="grandparent">
    <div class="parent">
        <div class="child">
            <span class="subchild"></span>
        </div>
    </div>
    <div class="surrogateParent1"></div>
    <div class="surrogateParent2"></div>
</div>
```

```javascript
//parent
$( "span.subchild" ).parent();
//parents
$( "span.subchild" ).parents();
//parentsUntil
$( "span.subchild" ).parentsUntil( "div.grandparent" );
//closest
$( "span.subchild" ).closest( "div" )

```

### Children 

The methods for finding child elements from a selection include `.children()` and `.find()`. The difference between these methods lies in how far into the child structure the selection is made. `.children()` only operates on direct child nodes, while `.find()` can traverse recursively into children, children of those children, and so on.

```javascript
$( "div.grandparent" ).children( "div" );
//find
$( "div.grandparent" ).find( "div" );
```

### Siblings

The rest of the traversal methods within jQuery all deal with finding sibling selections. There are a few basic methods as far as the direction of traversal is concerned. You can find previous elements with `.prev()`, next elements with `.next()`, and both with `.siblings()`. There are also a few other methods that build onto these basic methods: `.nextAll()`, `.nextUntil()`, `.prevAll()` and `.prevUntil()`.

```javascript
// Selecting a next sibling of the selectors:
 
// returns [ div.surrogateParent1 ]
$( "div.parent" ).next();
 
// Selecting a prev sibling of the selectors:
 
// returns [] as No sibling exists before div.parent
$( "div.parent" ).prev();
 
// Selecting all the next siblings of the selector:
 
// returns [ div.surrogateParent1, div.surrogateParent2 ]
$( "div.parent" ).nextAll();
 
// Selecting all the previous siblings of the selector:
 
// returns [ div.surrogateParent1, div.parent ]
$( "div.surrogateParent2" ).prevAll();
 
```

## CSS, Styling, & Dimensions

jQuery includes a handy way to get and set CSS properties of elements:

```javascript
// Getting CSS properties.

$( "h1" ).css( "fontSize" );
// Setting CSS properties.
 
$( "h1" ).css( "fontSize", "100px" ); // Setting an individual property.

// Setting multiple properties.
$( "h1" ).css({
    fontSize: "100px",
    color: "red"
});
```

### CSS Classes

1.addClass

​     Add the given class to the selected element 

```css
.highlight {
    background: yellow;
  }
$('h1').addClass("highlight")
```

2.removeClass

 		Removes the given class to the selected element.

```javascript
$('h1').removeClass("highlight")
```

3.toggleClass

​	 It is similar to  toggle button if the given class is present it remove it if not it will add the class

```javascript
$( "p" ).click(function() {
  $( this ).toggleClass( "highlight" );
});

```

4 hasClass

​	Checks  if the given class is present or not

### Dimensions

jQuery offers a variety of methods for obtaining and modifying dimension and position information about an element

```javascript
 
// Sets the width of all <h1> elements.
$( "h1" ).width( "50px" );
 
// Gets the width of the first <h1> element.
$( "h1" ).width();
 
// Sets the height of all <h1> elements.
$( "h1" ).height( "50px" );
 
// Gets the height of the first <h1> element.
$( "h1" ).height();
```

## Utility Methods

### $.trim()

Removes leading and trailing whitespace:

```javascript
// Returns "lots of extra whitespace"
$.trim( "    lots of extra whitespace    " );
```

### $.each()

Iterates over arrays and objects:

```javascript
$.each([ "foo", "bar", "baz" ], function( idx, val ) {
    console.log( "element " + idx + " is " + val );
});

$.each({ foo: "bar", baz: "bim" }, function( k, v ) {
    console.log( k + " : " + v );
});
```

The method .each() can be called on a selection to iterate over the elements contained in the selection. .each(), not $.each(), should be used for iterating over elements in a selection.

### $.inArray()

Returns a value's index in an array, or -1 if the value is not in the array:

```javascript
var myArray = [ 1, 2, 3, 5 ];

if ( $.inArray( 4, myArray ) !== -1 ) {
    console.log( "found it!" );
}
```

### $.extend()

Changes the properties of the first object using the properties of subsequent objects:

```javascript
var firstObject = { foo: "bar", a: "b" };
var secondObject = { foo: "baz" };

var newObject = $.extend( firstObject, secondObject );

console.log( firstObject.foo ); // "baz"
console.log( newObject.foo ); // "baz"
```

If you don't want to change any of the objects you pass to $.extend(), pass an empty object as the first argument:

```javascript

var firstObject = { foo: "bar", a: "b" };
var secondObject = { foo: "baz" };

var newObject = $.extend( {}, firstObject, secondObject );

console.log( firstObject.foo ); // "bar"
console.log( newObject.foo ); // "baz"
```

