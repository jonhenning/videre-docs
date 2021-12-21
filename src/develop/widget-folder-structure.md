# Widget Folder Structure

<ImageComponent src="/folderstructure.png" style="float: right;" />

When developing a widget it is important to keep in mind the way it will be packaged and deployed within the Videre CMS.  As discussed in the [Help -> Packages](../guide/packages.md) page, upon installation, a widget will be extracted into the root of your videre portal.  Therefore the folders created in your widget should match up with where you want the files deployed. 

## Controllers
Controllers are similar to what you find in ASP.NET MVC.  The difference being that in most MVC sites you use controllers to render views.  In the Videre CMS the Views are handled by Videre.  So controllers in a widget are generally used to facilitate communication from the client to the server via AJAX.

## Models
Models are usually simple Plain Old CLR Objects (POCOs) that contain little to no logic and are usually serialized via JSON to and from the client.

## Scripts
The Scripts folder contains external javascript files specific to your widget.  They need to follow the following structure (`Scripts\widgets\YOURNAMESPACE`) to ensure that your scripts do not overwrite another widgets files.  Note:  If you have a more general purpose script you should register it as a Web Reference.  More information on Web References can be found in the [Help -> Web References](../guide/webreferences.md) page.

## Services
Services is the typical location for your server-side business logic.  While not necessary to put in this folder as it ends up in a compiled dll, if it represents logic as a service this is recommended.

## Views
Like Scripts this must follow a folder convention (`Views\Shared\Widgets\YOURNAMESPACE`) so it will not overwrite another widgets files.  This folder contains the markup files for your widget.

## Registration.cs
While not necessary to be called registration.cs, it is a common convention to use this file to contain the class that implements the IWidgetRegistration interface.  The class that implements this interface is responsible for both the registration and initialization of your widget.
 
## package.manifest
The manifest file for your widget.  More information on this can be found in the [Help -> Packages](../guide/packages.md) page.
build.targets
This file contains the MSBuild scripts to package and deploy your widget to your local Videre portal.