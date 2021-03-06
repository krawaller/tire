# Tire
Tire is a lightweight JavaScript library for modern browsers. The goal is to create a framework that's around 10-11kb minified and 5kb minified and gzipped. The syntax is inspired from jQuery. It's modular so you can extend it however you like, also replace our features with your own. 

Fixes for older browsers increase the file size and we don't want that. So if you like a library to support Internet Explorer 6 or 7, Tire isn't for you. 

That said, all features can probably be rewritten/extended to add support for old browsers. In that case, you have to create a fork of Tire and fix it yourself.

## Why did we create Tire?

To offer a more lightweight alternative to libraries such as jQuery, Prototype and Zepto. Sometimes you just need the most basic features and that's where Tire comes into the picture.

## Browser support

* Chrome
* Safari 4
* Internet Explorer 8
* Firefox 3.5
* Opera 10

### Older browsers

Tire doesn't support Internet Explorer 6 or 7 as it would increase the file size. 

## Why don't you have this method?

We don't want to create a jQuery or Prototype clone. Nor do we want a big file size. Those are the biggest reasons we don't support all methods. 

If you think that Tire need a certain method please create an [issue](http://github.com/frozzare/tire/issues) and tell us why!

## Download

Current release: 1.0

* [tire.js](http://tirejs.com/dist/tire.js) - _11kB uncompressed, for development_
* [tire.min.js](http://tirejs.com/dist/tire.min.js) - _4kB when gzipped, for production_

Please do not hotlink directly to the files hosted on tirejs.com. Download a local copy instead.

[Source on GitHub](http://github.com/Frozzare/tire)

## Core

### $()

<span class="us">$(selector [, context])</span> <span class="re">Tire</span>

`$()` is just a shortcut for `tire()`. If another framework or library is using `$()` and you like to continue to use it, you can use tire's `$.noConflict()` to fix it.

This function is used to create Tire collections, wrapp DOM nodes or create elements from HTML string. Tire support the basic selectors, but in a modern browser advanced selectors are supported as well via `document.querySelectorAll`.

The function will take two parameters, the first is a selector and the second is the context where you are searching for the DOM node. If no context is given the context will be `document`. If a tire collection is given it will just return the given collection.

```javascript
$('#foo') // returns the element with the id foo

$('.bar') // returns all elements with the class name bar.

$('p') // returns all elements with the tag name p.

// More advanced selectors via document.querySelectorAll.

$('input[type=text]') // returns all input elements with the type text.

$('a, div') // returns all a and div elements;

$('ul li') // returns all li elements that are inside an ul tag.

$('ol > li') // the same as above but for ol tag.
```

If a function is given it will be used as a callback for the dom ready event. `$(function () {})` is a shortcut for `$.ready()` or `$().ready`. When the dom is ready, the function is executed.

### $.each

<span class="us">$.each(object, callback)</span> <span class="re">collection</span>

Iterate over array items or object key-value pairs. 

```javascript
$.each([1, 2, 3], function (index, item) {
  // Item is 1, 2, 3 and so on. Index is the position in the array
});

$.each({ hello: 'world' }, function (key, value) {
  // Key is `hello` and value is `world`
});
```

### $.extend

<span class="us">$.extend(target, [source [, source2, ..]])</span> <span class="re">target</span>

Extends target with members of other objects.

### $.isArr

<span class="us">$.isArr(object)</span> <span class="re">boolean</span>

Returns true if the given object is a array.

### $.isFun

<span class="us">$.isFun(object)</span> <span class="re">boolean</span>

Returns true if the given object is a function.

### $.isNum

<span class="us">$.isNum(object)</span> <span class="re">boolean</span>

Returns true if the given object is a number.

### $.isObj

<span class="us">$.isObj(object)</span> <span class="re">boolean</span>

Returns true if the given object is a object.

### $.isStr

<span class="us">$.isStr(object)</span> <span class="re">boolean</span>

Returns true if the given object is a string.

### $.matches

<span class="us">$.matches(element, selector)</span> <span class="re">boolean</span>

Returns true if the given element matches the given selector. `$().is(selector)` is an alias for it.

### $.noConflict

<span class="us">$.noConflict([name])</span> <span class="re">Tire</span>

Many JavaScript libraries use `$` as a function or variable name, just as Tire does. If you like to use another JavaScript library alongside Tire, we can return control back of `$` to the other library with `$.noConflict`.

If true is given as a parameter it will return control back to `Tire` if some other library is using it as variabel or function name.

### $.slice

<span class="us">$.slice(array [, begin])</span> <span class="re">array</span>

Returns a one-level deep copy of a portion of an array. The real `Array.slice` can take an end argument too, but `$.slice` can't. You can read more about `Array.slice` on [Mozilla Developer Network](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/slice)

### $.trim

<span class="us">$.trim(string)</span> <span class="re">string</span>

The trim method returns the string stripped of whitespace from both ends. It does not affect the value of the string.

### $.parseJSON

<span class="us">$.parseJSON(string)</span> <span class="re">object or null</span>

Parse JSON string to JSON object. This will also work for older browsers that don't include `JSON`.

```javascript
$.parseJSON('{"a":"b"}') // Returns { "a": "b"} as a object
```

### addClass

<span class="us">.addClass(name)</span> <span class="re">Tire</span>

Add class name to the selected elements. Multiple class names can be given in a space-separated string.

### after

<span class="us">.after(html)</span> <span class="re">Tire</span>

Add html to the DOM after each element in the collection. The html can be HTML string or Tire collection.

### append

<span class="us">.append(html)</span> <span class="re">Tire</span>

Append html to the DOM inside each element in the collection. The html can be a HTML string or Tire collection.

### attr

<span class="us">.attr(name [, value])</span> <span class="re">value or Tire</span>

Read or set DOM attributes. When no value is given it will read specified attribute from the first element and return the value of it. When a value is given, it sets the attribute to that value on each element in the collection.

### before

<span class="us">.before(html)</span> <span class="re">Tire</span>

Add html to the DOM before each element in the collection. The html can be a HTML string or Tire collection.

### children

<span class="us">.children([selector])</span> <span class="re">Tire</span>

Get immediate children of each element in the current collection. If a selector is given, it filters the results to only include the ones matching the CSS selector.

### closest

<span class="us">.closest(selector [, context])</span> <span class="re">Tire</span>

Get the first element that matches the selector, beginning at the current element and progressing up through the DOM tree. Context can be a DOM element in which a matching element may be found. If no context is passed in then the context of the jQuery set will be used instead.

### css

<span class="us">.css(property [, value])</span> <span class="re">value or Tire</span>

Read or set CSS properties on DOM elements. When no value is given it will read specified CSS property from the first element and return the value of it. When a value is given, it sets the property to that value on each element in the collection.

### each

<span class="us">.each(callback)</span> <span class="re">Tire</span>

Iterates trough every element in the collection. Inside the iterator function, the `this` keyword refers to the current item. If the iterator function returns `false` it will stop the iteration. Returns the Tire collection.

```javascript
$('div').each(function () {
  $(this).trigger('tap');
}); 
```

### empty

<span class="us">.empty()</span> <span class="re">Tire</span>

Clear DOM contents of each element in the collection. Returns the Tire collection.

### eq

<span class="us">.eq(index)</span> <span class="re">Tire</span>

Get the element at position specified by index from the current collection.

```javascript
$('div').eq(0); //=> Returns the first element
```

It's easy to extend Tire with `.first()` and `.last()` with `.eq(index)`.

```javascript
(function ($) {
  $.extend($.fn, {
    first: function () { return this.eq(0); },
    last: function () { return this.eq(-1); }
  });
}(tire));
```

### filter

<span class="us">.filter(object)</span> <span class="re">Tire</span>

Extend Tire with custom filters. Inside the iterator function, the `this` keyword refers to the current item. If a string is given it will return all elements in the collection matching that selector.

```javascript
// Returns all elements with the class `tire`
$('div').filter(function () {
  if ($(this).hasClass('tire')) return this;
});

$('div').filter('.wrapper'); // Returns all elements with CSS class name .wrapper
```

### find

<span class="us">.find(selector)</span> <span class="re">Tire</span>

Find elements that match a CSS selector executed in the scope of nodes in the current collection.

### hasClass

<span class="us">.hasClass(name)</span> <span class="re">boolean</span>

Check if the first element in the collection has the specified class.

### hide

<span class="us">.hide()</span> <span class="re">Tire</span>

Hide each element in the collection by setting CSS `display` to `none`.

### html

<span class="us">.html([html])</span> <span class="re">string or Tire</span>

Read or set HTML contents of elements in the collection. When no html is given it will return `innerHTML` of the first element. When html is given it used to replace `innerHTML` of each element in the collection. The html can be a HTML string or Tire collection.

### is

<span class="us">.is(selector)</span> <span class="re">boolean</span>

Returns true if the given element matches the given CSS selector. [jQuery CSS extensions](http://api.jquery.com/category/selectors/jquery-selector-extensions/) are not supported. Some will be supported later.

### not

<span class="us">.not(selector)</span> <span class="re">Tire</span>

Filter the current collection to get a new collection of elements that don't match the CSS selector.

### parent

<span class="us">.parent([selector])</span> <span class="re">Tire</span>

Get immediate parents of each element in the collection. If CSS selector is given, filter results to include only ones matching the selector.

### pluck

<span class="us">.pluck(property)</span> <span class="re">array</span>

Get values from a named property of each element in the collection. `null` and `undefined` will be removed before returning the array.

```javascript
$('span').pluck('nodeName') //=> ['SPAN', 'SPAN']
```

### prepend

<span class="us">.prepend(html)</span> <span class="re">Tire</span>

Prepend content to the DOM inside each element in the collection. The html can be a HTML string or Tire collection.

### ready

<span class="us">.ready(callback)</span> <span class="re">Tire</span>

Attach an event handler for the `DOMContentLoaded` or `onreadystatechange` event that fires when the DOM on the page is ready.

### remove

<span class="us">.remove()</span> <span class="re">Tire</span>

Remove all elements in the collection from their parent nodes, effectively detaching them from the DOM.

### removeAttr

<span class="us">.removeAttr(name)</span> <span class="re">Tire</span>

Remove the specified attribute from all elements in the collection.

### removeClass

<span class="us">.removeClass(name)</span> <span class="re">Tire</span>

Remove the specified class name from all elements in the collection. 

### show

<span class="us">.show()</span> <span class="re">Tire</span>

Restore the default value of CSS `display` property for each element in the collection.

### text

<span class="us">.text(content)</span> <span class="re">value or Tire</span>

Get or set text content of each element in the collection. When no content is given it returns text content for the first element. When content is given it sets `textContent` for each element in the collection.

### val

<span class="us">.val(value)</span> <span class="re">value or Tire</span>

Get or set the value of form controls. When no value is given, it returns the value of the first element. For `<select multiple>`, an array of values is returned. 

## Ajax

### $.ajax

<span class="us">$.ajax(options [, callback])</span> <span class="re">Tire</span>

Perform an Ajax request. It can be a to local resource or JSONP. No support for cross-domain (yet). It´s a async Ajax request, no sync request is supported and no support is planned.

If a string is passed in as the first argument it will be the URL to request. The seconds argument should be a function that is used as success function if the request succeeds.

If a URL contains `callback=?`, `callback=string` or `dataType` is `jsonp` it will be a JSONP request. The response data will automatic be parsed as a JSON object if it's a JSONP or JSON request.

Options

* `type` HTTP request method. GET is default.
* `url` URL to which the request is made.
* `data` Data for the request. Non-string objects will get serialized with `$.param`
* `contentType` Which content type to post to server. Default is `application/x-www-form-urlencoded`.
* `dataType` Response type to expect from the server. Default is none. Can be `json, jsonp, xml, html, text`.
* `headers` Object of additional HTTP headers for the Ajax request.
* `success` The function to execute when the request is done with data as a argument.
* `error` The function to execute on error with error arguments.

Options like `async, global, context` and `timeout` isn't supported. `timeout` will be supported later and maybe `context`.

```javascript
$.ajax('http://echo.jsontest.com/hello/world?callback=?', function (data) {
  console.log('Hello %s!', data.hello); 
});
```

### $.param

<span class="us">$.param(object)</span> <span class="re">string</span>

Serialize an object to a URL-encoded string representation for use in Ajax request query strings and post data.

```javascirpt
$.param({ num: [1, 2, 3] })
// => "num[]=1&num[]=2&num[]=3"
```

## Event

### on

<span class="us">.on(eventName, callback)</span> <span class="re">Tire</span>

Add an event handler function to one or more events to the selected elements. The event handler have one parameter, the event itself. Tire don't have any support for delegate events (yet).
```javascript
$('a').on('click', function (e) {
  // Add on click event to all anchor elements
});

$('a').on('click touchstart', function (e) {
  // Add on click and tap event to all anchor elements
});
```

### off

<span class="us">.off(eventName [, callback])</span> <span class="re">Tire</span>

Remove all event handler or a specified one from the selected elements. Tire don't have any support for undelegate events (yet).

```javascript
// Remove all click events from anchor elements
$('a').off('click'); 

// Remove both click and tap events from anchor elements
$('a').off('click tap'); 

// Remove specified click event handler from anchor elements
$('a').off('click', eventHandler);
```

### trigger

<span class="us">.trigger(eventName)</span> <span class="re">Tire</span>

Trigger the specified event on elements collection. Tire don't have any support for passing on data via trigger.
Trigger only takes one event name and not multiple like `on` and `off`.

```javascript
$('a').trigger('click');
```

## Changelog

* 1.0 - First stabel release

## Thanks

We like to __thank__ all of the [contributors](http://github.com/frozzare/tire/contributors). A personal thanks to [Caroline Millgårdh](http://caromill.com/) that has helped as a sounding board and participated in writing this documentation.

Tire API is based on [jQuery's Core API](http://jquery.com/), which is released under the [MIT license](https://github.com/jquery/jquery/blob/master/MIT-LICENSE.txt).

Thanks to [Jerome Gravel-Niquet](https://github.com/jeromegn) for [DocumentUp](https://github.com/jeromegn/DocumentUp). Tire using it to generate this documentation.

## Copyright

Copyright 2012 Fredrik Forsmo.
Tire is released under the terms of the [MIT license](https://github.com/Frozzare/tire/blob/master/MIT-LICENSE).