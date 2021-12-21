# Widget Registration and Initialization

A widget needs to register itself with the portal it is contained within.  It does this having a class with that implements the IWidgetRegistration interface

``` csharp
public interface IWidgetRegistration
{
    int Register();
    int RegisterPortal(string portalId);
}
```

## Register
The class' Register method is called during the Application_Start cycle of your website.  This is the location you typically place code to 

### Register your widget's AJAX endpoints (routes)

``` csharp
RouteTable.Routes.MapRoute(
    "Blog_route",
    "blogapi/{controller}/{action}/{id}",
    new { action = "Index", id = UrlParameter.Optional },
    null,
    new string[] { "Videre.Blog.Widgets" }
);
```

### Register your widget manifest
``` csharp
var updates = Videre.Core.Services.Update.Register(new List()
{
  new CoreModels.WidgetManifest() { Path = "Core/Account", Name = "UserProfile", Title = "User Profile", Category = "Account" }
});
```

### Register any portal Attribute Definitions (configuration values specific to your widget)

``` csharp
CoreServices.Update.Register(new CoreModels.AttributeDefinition() { GroupName = "Core", 
    Name = "SearchIndexDir", DefaultValue = "~/App_Data/SearchIndex", Required = true, 
    LabelKey = "SearchIndexDir.Text", LabelText = "Search Index Directory" });
```

## RegisterPortal
Similar to the Register method, the RegisterPortal method is called during application start as well, only it gets called for each portal your CMS may be hosting.  Settings that are portal specific get initialized here.  Typically you place code here to 

### Register any Secure Activities

``` csharp
updates += CoreServices.Update.Register(new List()
{
    new CoreModels.SecureActivity() { PortalId = portalId, Area = "Portal", Name = "Administration", 
        RoleIds = new List() {CoreServices.Update.GetAdminRoleId(portalId)} }
});
```
### Any portal specific customization code
``` csharp
public int RegisterPortal(string portalId)
{
    var updates = 0;
    updates += CoreServices.Update.Register(new List<CoreModels.Role>()
    {
        new CoreModels.Role() { Name = "admin", PortalId = portalId, Description = "Administrative Priviledges" }
    });
    return updates;        
}
```
