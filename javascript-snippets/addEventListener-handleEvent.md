#addEventListener, handleEvent and passing objects

Here’s a super awesome trick I had no idea about until someone pointed out you could do this. addEventListener can take an object as a second argument that will look for a method called handleEvent and call it! No need for binding “this” so it will pass around the context correctly, the context is the object you’ve just set as the event listener callback.
