# Client-Side Presenters

## Overview
The term client-side presenters is used to describe the use of a javascript class to act in a similar manner to the code-behind classes found in ASP.NET.  Only instead of being the code-behind the server-side markup, it is the code-behind the client-side html.  The primary purpose of a client-side presenter is to encapsulate the client-side logic for the UI that the widget renders.  

## Registration
Registration of a client side presenter is typically done in the Widget's razor markup with the following code

``` csharp
Html.RegisterControlPresenter(Model, "videre.widgets.admin.widgetmanifest")
```

When the widget is rendered to the client, the instance of this specific widget will be associated to an instance of the videre.widgets.admin.widgetmanifest client-side object.  I purposefully say instance to call out the fact that it is possible that multiple widgets of the same type exist on the same page, therefore their internal state needs to be managed in an instance.

It is also possible to have the server side code pass data to the client presenter.  This is done with the properties argument

``` csharp
Html.RegisterControlPresenter("videre.widgets.admin.widgetmanifest", Model, new { data = Widget.GetWidgetManifests() });
```

This code assumes that there will be a property defined on the client called data.  Since javascript does not have broad support for getters/setters a property is defined as two methods (get_data / set_data).

## Anatomy of a Client-Side Presenter

``` js
videre.registerNamespace('videre.widgets.admin');
 
videre.widgets.admin.widgetmanifest = videre.widgets.base.extend(
{
    get_data: function() { return this._data; },
    set_data: function(v) { this._data = v; },
 
    init: function()  //constructor
    {
        this._base();  //call base method
 
        //member variables
        this._data = null;
 
        //delegates that are re-used multiple times
        this._delegates = {
            onDataReturn: videre.createDelegate(this, this._onDataReturn)
        }
    },
 
    _onLoad: function(src, args)
    {
        this._base(); //call base
    },
 
    //public methods
    refresh: function()
    {
        this.ajax('~/core/Widget/GetManifests', {}, this._delegates.onDataReturn);
    },
 
    //private methods
    _onDataReturn: function(result, ctx)
    {
        if (!result.HasError)
        {
            this.set_data(result.Data);
            this.bind();
        }
    },
 
    //event handlers
    _onSaveClicked: function(e)
    {
        this.save();
    },
 
    //events
    add_onSelection: function(handler) { this.get_events().addHandler("OnSelection", handler); },
    remove_onSelection: function(handler) { this.get_events().removeHandler("OnSelection", handler); },
    raiseOnSelection: function(item)
    {
        var handler = this.get_events().getHandler("OnSelection");
        if (handler)
            return handler(this, { data: this._data });
        return true;
    }
});
```
In order to provide consistency in widget development a guideline has been offered in how the items within it are organized.

Most languages offer namespaces to ensure there is no clashing between components that share the same names.  Our presenters are no different in this and offer an easy way to register a hierarchical namespace.

``` js
videre.registerNamespace('videre.widgets.admin');
```

## Class Definition
Our client-side presenter is also able to provide a class definition along with inheritance via the following syntax.

``` js
videre.widgets.admin.widgetmanifest = videre.widgets.base.extend({ ... });
```
This code declares a class called widgetmanifest in the videre.widgets.admin namespace.  It also inherits from the videre.widgets.base class (found in videre.js).

## Properties
As mentioned javascript properties are still not supported across browsers [without some hacking](http://stackoverflow.com/questions/1077106/javascript-getters-setters-in-ie).  The Videre CMS chose not to utilize this hacking technique, but instead simply expose properties as methods prefixed with either a get_ or a set_.

``` js
get_data: function() { return this._data; },
set_data: function(v) { this._data = v; },
```

## Constructor
The constructor in our class is defined in the init method

``` js
init: function()  //constructor
{
    this._base();  //call base method

    //member variables
    this._data = null;

    //delegates that are re-used multiple times
    this._delegates = {
        onDataReturn: videre.createDelegate(this, this._onDataReturn)
    }
},
```

It is required that you call the base class's constructor as well by invoking this._base();  The constructor is where all of your presenter's member variables should be declared and initialized.  Additionally, it is common to store any delegates that will be used more than once in the this._delegates dictionary.  A common delegate to define here is the callbacks from an AJAX call, as typically these will be invoked more than a single time.

## _onLoad
Although the _onLoad method is an event handler and should therefore show up later in our class definition, we make an exception and place it towards the top.  This is because it pairs nicely with the class' constructor in that it initializes the class.  The difference between the constructor and the _onLoad is that by the time the _onLoad is called, our HTML DOM is ready to interact with.  Therefore adding logic to hook up event handlers and changing the css of our markup is common.  Similar to the constructor, it is necessary to call the base _onLoad event by calling this._base()

## Base Class Properties and Methods
The videre.widgets.base class is typically the class your client-side presenter will inherit from.  The following are some of the more common properties and methods used by the presenters

### .getControl(id)
The `this.getControl` method is probably the most common method used in the base class.  It enables the presenter to grab a jQuery element reference by an id within the namespace of the widget.  Any element that uses the `@Model.GetId('MyElement')` syntax in its markup can then have the presenter obtain a reference with `this.getControl('MyElement')` without the need to worry about a unique id generated by the framework.  Under the covers the framework will prefix the names to something like w3_MyElement to ensure uniqueness on a rendered page.  Then in the presenter when getControl is used, the proper namespace will be prefixed.

### .getId(id)
For cases where the presenter will be responsible for generating markup that requires an ID attribute to be assigned, the getId method may be used to generate a unique id.

### .ajax(url, params, onSuccess, onFail, parent, ctx, options)
The ajax method. enables an easy way for the developer to invoke an AJAX method on the server.  While it defers the actual AJAX logic to the videre.ajax method found in videre.js, the base class does the common logic of clearing any previous error messages, assigning the lock property, assigning HTTP headers like the widget ID making the request, and providing a default AJAX fail method implementation.  A sample implementation looks like this

``` js
this.ajax('~/core/Account/SaveUserProfile', { user: user }, this._delegates.onSaveReturn);
```

### ._widget
Most widget's HTML markup should contain as its outermost DOM an element with the id of Widget

``` csharp
<div id="@Model.GetId("Widget")">
```

The base class will automatically grab a jQuery reference to the outermost element and assign it to the this._widget property.  A common use for this property is in the jQuery selectors where you wish to find elements within your widget that are not by a unique id.  For example, `this._widget.find('input');` would grab all input elements within your widget.

this._widget, lock/unlock, ajax, progressbar, message container

### .bindData(data, parent)
The bindData method allows a javascript object to be bound to DOM elements that specify the column to bind via the `data-column` attribute.  A parent DOM element can be optionally passed in to minimize the scope of the elements bound.  If not passed, the current widget DOM element will be used.  *It should be noted that controls other than simple textboxes along with data types other than strings are supported in an extensible manner via [Control Types and Data Types](control-types-and-data-types.md).*

``` html
<!--Markup-->
<input type="text" data-column="FirstName" />
<input type="text" data-column="LastName" />
```

``` js
//Script
var data = {FirstName: 'John', LastName: 'Doe'};
this.bindData(data);
```

### .persistData(data, clone, parent, includeReadOnly)
The persistData method allows DOM elements to be applied to a javascript object.  This method will look at all properties defined in the data object passed and attempt to find the matching DOM elements via the data-column attribute.   An option to return a cloned instance of the data object is provided along with the ability to limit the scope of elements searched via the parent property.

### .lock() / .unlock()
The lock / unlock methods in the base class serve two purposes:  set the this._locked property and show/hide the widgets progressbar (if present).  If additional functionality is desired upon the locking of the widget like hiding/showing buttons, the method can be overridden.  An important thing to note is that locking a widget is as simple as setting the property, it does nothing that prevents the other code in the widget from executing (for example it doesn't stop "happy clicking").   It is therefore advised that any method that does a lock first checks the `this._locked` property.

## Public Methods
Methods that may be called by an code outside the presenter should be camelCased.  Common public methods are `save`, `reset`, and `bind`.

## Private Methods
Methods that should not be called by outside code should be prefixed with an underscore and _camelCased.

## Event Handlers
While event handlers are really just private methods, the convention is to group them together below all other private methods.  A general rule for event handlers is that they should not contain more than a couple lines of code.  If you find that an event handler needs quite a bit of logic, have it simply invoke a separate private method.   The reason for this is the action associated with an event handler typically will need to be invoked by multiple actions on your widget, for example, a button click or the ENTER key pressed. 

## Events
Widgets not only can invoke each others public methods, they also can expose events to be consumed by an outside piece of code. 

``` js
//sample.widget1
add_onSave: function(handler) { this.get_events().addHandler('OnSave', handler); },
remove_onSave: function(handler) { this.get_events().removeHandler('OnSave', handler); },
raiseOnSave: function(data)
{
    var handler = this.get_events().getHandler('OnSave');
    if (handler)
        handler(this, { src: this, data: data });
    return true;
},
```

``` js
//sample.widget2
this._editor = videre.widgets.findFirstByType('sample.widget2');
this._editor.add_onSave(this._delegates.onWidgetSave);
```