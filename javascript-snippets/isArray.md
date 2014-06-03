# How to write a robust `isArray`

```js
function isArray(o) {
  return Object.prototype.toString.call(o) === '[object Array]';
}
```

##long long age

'''js
typeof new Function() // function
typeof '' // string
typeof 1 // number
typeof undefined // undefined
typeof true // boolean
typeof {} // object
```
###but
```js
typeof null // object
typeof [] //object
```

###so?
```js
var arr = [];
arr instanceof Array; // true
arr.constructor == Array; // true
```

###but!
```js
var iframe = document.createElement('iframe');
document.body.appendChild(iframe);
xArray = window.frames[window.frames.length-1].Array;
var arr = new xArray(1,2,3); // [1,2,3]

arr instanceof Array; // false
arr.constructor === Array; // false
```


ECMA-262 specs and noticed that there was an easy way to get value of an internal [[Class]] property 
that every native object has. Object.prototype.toString was defined like so:

  Object.prototype.toString( )
  When the toString method is called, the following steps are taken:
  1. Get the [[Class]] property of this object.
  2. Compute a string value by concatenating the three strings “[object ", Result (1), and "]“.
  3. Return Result (2)
  
Contrary to Function.prototype.toString which is implementation dependent and is NOT recommended to be relied upon, 
Object.prototype.toString has a clearly defined behavior for all native objects.

  15.3.4.2 Function.prototype.toString()
  An implementation-dependent representation of the function is returned. 
  This representation has the syntax of a FunctionDeclaration. 
  Note in particular that the use and placement of white space, line terminators, 
  and semicolons within the representation string is implementation-dependent.

```js
/**
 * Returns internal [[Class]] property of an object
 *
 * Ecma-262, 15.2.4.2
 * Object.prototype.toString( )
 *
 * When the toString method is called, the following steps are taken: 
 * 1. Get the [[Class]] property of this object. 
 * 2. Compute a string value by concatenating the three strings "[object ", Result (1), and "]". 
 * 3. Return Result (2).
 *
 * __getClass(5); // => "Number"
 * __getClass({}); // => "Object"
 * __getClass(/foo/); // => "RegExp"
 * __getClass(''); // => "String"
 * __getClass(true); // => "Boolean"
 * __getClass([]); // => "Array"
 * __getClass(undefined); // => "Window"
 * __getClass(Element); // => "Constructor"
 *
 */
function __getClass(object){
  return Object.prototype.toString.call(object)
    .match(/^\[object\s(.*)\]$/)[1];
};
```

###Referers
http://perfectionkills.com/instanceof-considered-harmful-or-how-to-write-a-robust-isarray/
https://github.com/kangax/protolicious/tree/master/experimental
