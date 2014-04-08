## Example usage

    // Define some models
    var FooModel = Backbone.Model.extend({
        resourceType: 'foo',
        ...
    });
    var BarModel = Backbone.Model.extend({
        resourceType: 'bar',
        ...
    });
    
    // Instantiate the models
    var foo = new App.FooModel(...);
    var bar1 = new App.BarModel(...);
    var bar2 = new App.BarModel(...);
    
    // Create the listener, and listen to the models
    listener = new ResourceListener();
    listener.listen(foo);
    listener.listen(bar1);
    listener.listen(bar2);
    
    // Add event handlers
    listener.on('sync:foo', function (model, request, options) {
        // Called when foo has loaded
    });
    listener.on('sync:bar', function (model, request, options) {
        // Called when either bar1 or bar2 has loaded
    });
    listener.on('resource:complete', function (type)) {
        // Called after foo loads with type="foo"
        // Also called after bar1 and bar2 are both loaded with type="bar"
    });
    listener.on('resource:complete), function () {
        // Called after foo, bar1, and bar2 have all loaded or failed.
    });
    
