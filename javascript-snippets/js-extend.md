#javascript extend method, 
```js
(function (window, document, undefined) {
    var utils = window.utils = window.utils || {};

    var emptyArray = [],
        slice = emptyArray.slice,
        class2type = {},
        toString = class2type.toString;

    utils.type = function (obj) {
        if (obj == null) {
            return obj + "";
        }
        return typeof obj === "object" || typeof obj === "function" ?
            class2type[ toString.call(obj) ] || "object" :
            typeof obj;
    };

    utils.isFunction = function (value) {
        return utils.type(value) == "function";
    };

    utils.isWindow = function (obj) {
        return obj != null && obj == obj.window;
    };

    utils.isDocument = function (obj) {
        return obj != null && obj.nodeType == obj.DOCUMENT_NODE;
    };

    utils.isObject = function (obj) {
        return utils.type(obj) == "object";
    };

    utils.isPlainObject = function (obj) {
        return utils.isObject(obj) && !utils.isWindow(obj) && Object.getPrototypeOf(obj) == Object.prototype;
    };

    utils.isArray = Array.isArray || function (object) {
        return object instanceof Array;
    };

    var extend = function (target, source, deep) {
        for (var k in source) {
            if (deep && (utils.isPlainObject(source[k]) || utils.isArray(source[k]))) {
                if (utils.isPlainObject(source[k]) && !utils.isPlainObject(target[k])) {
                    target[k] = {};
                }
                if (utils.isArray(source[k]) && !utils.isArray(target[k])) {
                    target[k] = [];
                }
                extend(target[k], source[k], deep);
            } else if (source[k] !== undefined) {
                target[k] = source[k];
            }
        }
    };

    utils.extend = function(target){
        var deep, args = slice.call(arguments, 1);
        if (typeof target == 'boolean') {
            deep = target;
            target = args.shift();
        }
        args.forEach(function(arg){ extend(target, arg, deep) });
        return target;
    };
})(window, document);
```

## usage
```js
obj1 = extend(true, {}, obj1, obj2);
```
