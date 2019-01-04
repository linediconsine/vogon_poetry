# Get Elements by ID, Tag, Name, Class, CSS selector


## Per element by ID

==getElementById("xyz")==

[single element]

~~~ javascript
const elem = document.getElementById("xyz");
~~~

## Per Tag Name (type of nodes)

==document.getElementsByTagName("p")==

[multiple elements] 

~~~javascript
const list = document.getElementsByTagName("p"); // get all p elements

list.length; // show number of items

list[0].style.color = "red"; // make the first one red
~~~

## Per Class name

==document.getElementsByClassName("class_values")==

[multiple elements] 

Return a live HTMLCollection.

**NOTE:** The class_values can be multiple classes separated by space. For example: "aa bb", and it'll get elements, where each element is in both class “aa” and “bb”.

~~~html
<p class="aa">1</p>

<p class="bb">2</p>

<p class="bb aa">3</p>

<p class="bb cc aa">4</p>

<script>document.getElementsByClassName("aa bb");</script>

<!-- it'll get 3 and 4. -->
~~~

## Get Elements by Matching the Value of the 「name」 Attribute

==document.getElementsByName("xyz")==

[multiple elements] 

**NOTE:** Supported on all common browsers but some bugs on IE9 (http://quirksmode.org/dom/core/#t134 )

#### Example

```html
<p name="abc">1</p>
<div class="zz" name="xyz">2</div>
<div class="zz" name="xyz">3</div>

<form>
<input name="xyz" type="text" size="20">
</form>
```

~~~javascript
// get element by value of the “name” attribute

const xyz = document.getElementsByName("xyz");

xyz[0].style.color="red"; // make the first one red
~~~


## CSS Selector

==document.querySelector(css_selector==

[single element]

**NOTE:** Return a non-live HTMLCollection of the first element that match the CSS selector css_selector. The css_selector is a string of CSS syntax, and can be several selectors separated by comma.

==document.querySelectorAll(css_selector)==

[multiple elements] 

**NOTE:** Return a non-live HTMLCollection, of elements that match the CSS selector css_selector. The css_selector is a string of CSS syntax, and can be several selectors separated by comma.

[CSS Syntax](http://xahlee.info/js/css_selector_syntax.html)
