Aerial Applications version of the code-guide.
-----------------
To be used internally.


=================


# HTML, and CSS Code Guide
Standards for developing flexible, durable, and sustainable HTML, and CSS.


----------


## Table of contents

* [Golden rule](#golden-rule)
* [HTML](#html)
  * [Syntax](#html-syntax)
  * [HTML5 doctype](#html5-doctype)
  * [Pragmatism over semantics](#pragmatism-over-semantics)
  * [Attribute order](#attribute-order)
  * [JavaScript generated markup](#javascript-generated markup)
* [CSS](#css)
  * [CSS syntax](#css-syntax)
  * [Declaration order](#declaration-order)
  * [Formatting exceptions](#formatting-exceptions)
    * [Prefixed properties](#prefixed-properties)
    * [Rules with single declarations](#rules-with-single-declarations)
  * [Human readable](#human-readable)
    * [Comments](#comments)
    * [Classes](#classes)
    * [Selectors](#selectors)
  * [Organization](#organization)
* [Writing copy](#copy)
  * [Sentence case](#sentence-case)


----------


## Golden rule

> All code in any code base should look like a single person typed it, no matter how many people contributed.

This means strictly enforcing these agreed upon guidelines at all times. For additions or contributions, please [file an issue on GitHub](https://github.com/Ganginator/code-guide-aerial).


----------


## HTML


### HTML syntax

* Use hard-tabs, the actual Tab key, not soft-tabs, with two spaces.
* Nested elements should be indented once. (1 Tab key)
* Do not nest the body, or any page wrappers.
* Add two spaces between sections, and one space between content.
* Always use double quotes, never single quotes.
* Include a trailing slash in self-closing elements.
* Comment close all elements with their id's, and classes.


**Incorrect example:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<div id="incorrect" class="example">
<img src='images/company-logo.png' alt='Company'>
<h1 class='hello-world'>Hello, world!</h1>
</div>
</body>
</html>
````


**Correct example:**

````html
<!DOCTYPE html>


<html>


<head>


	<title>Page title</title>
 	
 	
</head>


<body>


<div id="correct" class="example">


	<img src="images/company-logo.png" alt="Company" />
 	
	<h1 class="hello-world">Hello, world!</h1><!-- / .hello-world -->
 	
 	
</div><!-- / #correct .example -->


</body>


</html>
````


### HTML5 doctype

Enforce standards mode in every browser possible with this simple doctype at the beginning of every HTML page.

````html
<!DOCTYPE html>
````


### Pragmatism Over Semantics

Strive to maintain HTML standards, and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricacies whenever possible.


### Attribute order

HTML attributes should come in this particular order for easier reading of code.

This order considers CSS Specificity, see below.

* id
* class
* data-*
* for|type|href

Such that your markup looks like:

````html
<a id="" class="" data-modal="" href="">Example link</a>
````


### JavaScript Generated Markup

Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. Don't do it.


----------


## CSS


### CSS Specificity

````
1 = !important Class
	+10000 Points
2 = Inline Styling, Style Attributes
	+1000 Points
3 = Identifiers, Types, Psuedo-elements
	+100 Points
4 = Classes, Psuedo-classes, Attributes
	+10 Points
5 = HTML, Elements, Content Elements
	+1 Points
````


### CSS syntax

* Use hard-tabs, the actual Tab key, not soft-tabs, with two spaces.
* When grouping selectors, keep individual selectors to a single line.
* Include one space before the opening brace of declaration blocks.
* Place closing braces of declaration blocks on a new line.
* Include one space after <code>:</code> in each property.
* Nest each declaration with one indent. (1 Tab key)
* Declarations within declarations should be indented twice, and so on.
* End all declarations with a semi-colon.
* Each declaration should appear on its own line.
* Add one space between selectors, and declaration groups.
* Comma-separated values should include a space after each comma.
* Don't include spaces after commas in RGB, or RGBa colors, and don't preface values with a leading zero.
* Lowercase all hex values, (i.e <code>#fff</code> instead of <code>#FFF</code>)
* Use shorthand hex values where available, e.g., <code>#fff</code> instead of <code>#ffffff</code>
* Quote attribute values in selectors, (i.e <code>input[type="text"]</code>)
* Avoid specifying units for zero values, (i.e <code>margin: 0;</code> instead of <code>margin: 0px;</code>)


**Incorrect example:**

````css
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
  position: absolute;
  top:0;
  right:0;
  bottom:0
  left:0;
  z-index:100;
}
.selector-other{
  background-color:#f5f5f5;
  border: 1px solid#e5e5e5
  border-radius:3px;}
  @media (max-width: 979px){.navbar .container{padding: -40px;}}
````


**Correct example:**

````css
.selector,
.selector-secondary,
.selector[type="text"] {
	
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0
	left: 0;
	z-index: 100;

	padding: 15px;
	margin: 0 0 15px;
	background-color: rgba(0,0,0,.5);
	box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
	
}

.selector-other {

	background-color: #f5f5f5;
	border: 1px solid #e5e5e5;
	border-radius: 3px;
	
}

@media (max-width: 979px) {

	.navbar .container {
		padding: -40px;
	}
	
}
````

Questions on the terms used here? See the [syntax section of the Cascading Style Sheets article](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) on Wikipedia.


### Declaration order

Related declarations should be grouped together, placing positioning and box-model properties closest to the top, followed by typographic, and visual properties.

````css
.declaration-order {

/* Positioning */
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	left: 0;
	z-index: 100;

/* Box-model */
	display: block;
	float: right;
	width: 100px;
	height: 100px;

/* Typography */
	font: normal 13px "Helvetica Neue", sans-serif;
	line-height: 1.5;
	color: #333;
	text-align: center;

/* Visual */
	background-color: #f5f5f5;
	border: 1px solid #e5e5e5;
	border-radius: 3px;

/* Misc */
	opacity: 1;
	
}
````

For a complete list of properties and their order, please see [Recess](http://twitter.github.com/recess).


### Formatting exceptions

In some cases, it makes sense to deviate slightly from the default [syntax](#css-syntax).


#### Prefixed properties

When using vendor prefixed properties, indent each property such that the value lines up vertically for easy multi-line editing.

````css
.selector {

  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
          
}
````

In Textmate, use **Text &rarr; Edit Each Line in Selection** (&#8963;&#8984;A). In Sublime Text 2, use **Selection &rarr; Add Previous Line** (&#8963;&#8679;&uarr;) and **Selection &rarr;  Add Next Line** (&#8963;&#8679;&darr;).


#### Rules with single declarations

In instances where several rules are present with only one declaration each, consider removing new line breaks for readability and faster editing.

````css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {

	display: inline-block;
	width: 16px;
	height: 15px;
	background-image: url(../img/sprite.png);
  
}

.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
````


### Human readable

Code is written, and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.


#### Comments

Great code comments convey context, or purpose, and should not just reiterate a component, or class name.


**Bad example:**

````css
/* Modal header */
.modal-header {

  ...
  
}
````


**Good example:**

````css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {

  ...
  
}
````


#### Class names

* Keep classes lowercase, and use dashes. (Not underscores, or camelCase.)
* Avoid arbitrary shorthand notation.
* Keep classes as short, and succinct as possible.
* Use meaningful names; use structural, or purposeful names over presentational.
* Prefix classes based on the closest parent component's base class.


**Bad example:**

````css
.t { ... }
.red { ... }
.header { ... }
````


**Good example:**

````css
.tweet { ... }
.important { ... }
.tweet-header { ... }
````


#### Selectors

* Use classes over generic element tags.
* Keep them short, and limit the number of elements in each selector to three.
* Scope classes to the closest parent when necessary. (i.e. When not using prefixed classes.)


**Bad example:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**Good example:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````


### Organization

* Organize sections of code by component.
* Develop a consistent commenting hierarchy.
* If using multiple CSS files, break them down by component.


----------


## Copy


### Sentence case

Always write copy, including headings in [sentence case](http://en.wikipedia.org/wiki/Letter_case#Usage). In other words, aside from titles, and proper nouns, only the first word should be capitalized.

Always write code comments, in CAPS LOCK, with lowercase references. In other words, all upercase letters, unless you are refering to an element, class, id, etc... (i.e. <code><!-- FIXED body .class, AND #id LOCATION --></code>)

----------


### Thanks

Heavily inspired by [Idiomatic CSS](https://github.com/necolas/idiomatic-css) and the [GitHub Styleguide](http://github.com/styleguide). Made with all the love in the world by [@mdo](http://twitter.com/mdo).


==========


EDITED by: [Jesse Gangi](http://jessegangi.com), [Aerial Applications](http://aerialapps.com) for use internally.
