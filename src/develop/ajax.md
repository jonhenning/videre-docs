# AJAX

## Introduction
Instead of traditional postbacks, the majority of the Videre CMS utilizes AJAX to transfer data to and from the webserver.  Several advantages to this approach are

* The data that is round-tripped is only the data necessary for the call to function.  It does not include all the markup/form values unrelated to the call.
* State management becomes much easier as the state of the widget can be maintained within the client-side presenter instead of persisting to a cookie, session-state, or viewstate (ugh!).
* Complex objects can be easily passed to / from the web server via JSON instead of placing in HTML elements.

## Invoking AJAX 
As mentioned in the [Client-Side Presenters](client-side-presenters.md) page, a widget presenter's base class provides a method that can perform all the common logic for an ajax call.  In this example a method called SaveRole is invoked, passing a comples role object.  The delegate for a successful result is provide, whereas, the default implementation for an AJAX call that fails us used.  Finally, we are specifying that the scope of the call is within our dialog, thus causing the dialog's progress bar to be displayed as opposed to the widgets.

``` js
this.ajax('~/core/Account/SaveRole', { role: role }, this._delegates.onSaveReturn, null, this._dialog);
```

## AJAX Server Method
Since we are using ASP.NET MVC for our web-server, we will code the service endpoint within a Controller.  The following is an example of the expected logic found within an AJAX controller method.

``` csharp
public JsonResult<bool> SaveRole(CoreModels.Role role)
{
    var result = new JsonResult<bool>();
    try
    {
        if (verifyAntiForgeryToken && AntiForgeryTokenVerification)
            VerifyAntiForgeryToken();
 
        CoreServices.Security.VerifyActivityAuthorized("Account", "Administration");
        result.Data = !string.IsNullOrEmpty(CoreServices.Account.SaveRole(role));
    }
    catch (Exception ex)
    {
        result.AddError(ex);
        Logging.Logger.Error("API Error", ex);
        if (ex.InnerException != null)
            result.AddError(ex.InnerException);
    }
    return result;
}
```
You may have noticed that there is quite a bit of "boiler-plate" code within that method.  So instead of re-writing the same logic over and over, the Videre framework allows you to accomplish the same thing with the API.Execute method

``` csharp
public JsonResult<bool> SaveRole(CoreModels.Role role)
{
    return API.Execute<bool>(r => {
        CoreServices.Security.VerifyActivityAuthorized("Account", "Administration");
        r.Data = !string.IsNullOrEmpty(CoreServices.Account.SaveRole(role));
    });
}
```

## AJAX Return Delegate
A typical event handler for a successful AJAX call would look something like this.

``` js
_onSaveReturn: function(result)
{
    if (!result.HasError && result.Data)
    {
        this.refresh();
        this._dialog.modal('hide');
    }
},
```
It should be noted, that because we are using the base widget's ajax method, a couple things are handled for us like the invoking of unlock and the displaying of any messages from the AJAX call.