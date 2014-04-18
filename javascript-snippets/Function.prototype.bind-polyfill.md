# Function.prototype.bind
In a project, I fund that iOS5's version of Safari does not support bind().

This is the polyfill for bind()
```js
if (!Function.prototype.bind) {
  Function.prototype.bind = function (oThis) {
    if (typeof this !== "function") {
      // closest thing possible to the ECMAScript 5 internal IsCallable function
      throw new TypeError("Function.prototype.bind - what is trying to be bound is not callable");
    }
  
    var aArgs = Array.prototype.slice.call(arguments, 1), 
        fToBind = this, 
        fNOP = function () {},
        fBound = function () {
          return fToBind.apply(this instanceof fNOP && oThis
                                 ? this
                                 : oThis,
                               aArgs.concat(Array.prototype.slice.call(arguments)));
        };
  
    fNOP.prototype = this.prototype || {};
    fBound.prototype = new fNOP();
  
    return fBound;
  };
}
```
## Related
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#Compatibility
* http://edrooth.com/blog/2012/08/20/no-bind-in-ios5/
* http://davidbcalhoun.com/2011/new-mobile-safari-stuff-in-ios5-position-fixed-overflow-scroll-new-input-type-support-web-workers-ecmascript-5/
