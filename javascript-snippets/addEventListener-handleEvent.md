#addEventListener, handleEvent and passing objects

Here’s a super awesome trick I had no idea about until someone pointed out you could do this. addEventListener can take an object as a second argument that will look for a method called [handleEvent](http://www.w3.org/TR/DOM-Level-2-Events/events.html#Events-EventListener-handleEvent) and call it! No need for binding “this” so it will pass around the context correctly, the context is the object you’ve just set as the event listener callback.

```js
var obj = {
    handleEvent: function() {
        alert(this.dude);
    },
    dude: "holla"
};

element.addEventListener("click", obj, false);
```

##Why is this awesome?
We can do things like this:
```js
var obj  =  {
    init: function() {
        document.getElementById("btn").addEventListener("click", this, false);
        document.getElementById("btn").addEventListener("touchstart", this, false);
    },
    handleEvent: function(e) {
        switch(e.type) {
            case "click":
                this.button();
                break;
            case "touchstart":
                this.button();
                break;
        }
    },
    dude: "holla",
    button: function() {
        alert(this.dude);
    }
};

obj.init();
```

As you can see our object has an init() method which binds all the events and just passes in “this” as the callback, handleEvent then delegates off to whatever method it needs based on the event being triggered, rad.

##But wait there’s more
Another awesome thing we can do is change the buttons behaviour without having to remove and re-attach the event handler. The second button in the demo changes what the first button does by redefining the handleEvent method.

```js
changeHandleEvent: function(evt) {
    this._handleEvent = this.handleEvent;
    // Change the the handleEvent method without needing to remove 
    // and re-attach the event(s)
    this.handleEvent = function(e) {
        var t = evt.target;
        
        if (t.id === "btn") {
            // Check the button being clicked and do new stuff
        } else if(t.id === "btn3") {
            this.revertHandleEvent();
        }
    }
}
```

Makes for some pretty powerful stuff. The third button re-instates the first buttons behaviour back to its original form.

This works in nearly all browsers that support addEventListener, Blackberry 6 browser being one that doesn’t. Blackberry OS7 has fixed this bug.

##Polyfill it
IE9 was the first to support addEventListener + handleEvent in the IE family, so for the older ones we can polyfill in support for <IE8 and other non-supporting browsers (BBOS6).

```js
// fn arg can be an object or a function, thanks to handleEvent
function on(el, evt, fn, bubble) {
    if("addEventListener" in el) {
        // BBOS6 doesn't support handleEvent, catch and polyfill
        try {
            el.addEventListener(evt, fn, bubble);
        } catch(e) {
            if(typeof fn == "object" && fn.handleEvent) {
                el.addEventListener(evt, function(e){
                    // Bind fn as this and set first arg as event object
                    fn.handleEvent.call(fn,e);
                }, bubble);
            } else {
                throw e;
            }
        }
    } else if("attachEvent" in el) {
        // check if the callback is an object and contains handleEvent
        if(typeof fn == "object" && fn.handleEvent) {
            el.attachEvent("on" + evt, function(){
                // Bind fn as this
                fn.handleEvent.call(fn);
            });      
        } else {
            el.attachEvent("on" + evt, fn);
        }
    }
}
```
For oldIE it checks if the callback is an object and if it contains handleEvent. Using call we can change the “this” context to the object passed.

For BBOS6 we wrap a try catch around addEventListener and if the attaching throws, check the callback is an object and has the handleEvent method otherwise don’t swallow the error.

We handle all this by wrapping up the event attaching into a nice method which handles the process for us.

## Referers
* http://www.thecssninja.com/javascript/handleevent
* http://ajaxian.com/archives/an-alternative-way-to-addeventlistener
* https://github.com/h5bp/mobile-boilerplate/blob/master/js/helper.js#L214

