## Packages

A package is simply a zipped file that follows a simple convention.  Packages are the primary extensibility point within Videre.   They allow new capabilities to be added to your portal.  A package is simply a file that contains a zipped file/folder structure that will be extracted into the root of your Videre website (the Web folder).  So if you wish to create a package that places a new dll into the bin folder you would create a zip file with a single file in it (myfile.dll) that is in a relative path of bin.

## Package Manifest
In order to provide information about your package an optional manifest file can be included in your zip.  A manifest is any file that has the .manifest extension.  A sample manifest for the jQuery library would look like this

``` js
{
  "Id": null,
  "Name": "jQuery",
  "Type": "WebReference",
  "FileName": null,
  "Version": "1.10.2",
  "Description": "jQuery files",
  "Source": "http://jquery.com/",
  "Thumbnail": null,
  "PackagedDate": "2013-11-25T14:32:22.4792433Z",
  "InstallDate": null
}
```

## Package Content
A package can also include content.  Content is specified by including a file with the .json extension.  A simple content file that adds the jQuery information into the portal's WebReferences would look like this

``` js
{
  "Portal": {
    "Id": "PortalId"
  },
  "WebReferences": [
    {
      "Id": "Id1",
      "PortalId": "PortalId",
      "Name": "jQuery",
      "Url": "~/scripts/jQuery-1.10.2/jquery-1.10.2.min.js",
      "Text": null,
      "Sequence": null,
      "Type": 0,
      "LoadType": 0,
      "Group": "jQuery",
      "DependencyGroups": []
    }
  ]
}
```
Finally, a full sample of the content file used to create the initial portal looks something like this

``` js
{
  "Portal": {
    "Id": "1511fd73-5003-46f1-ac4e-7932b0faee56",
    "Name": "Default",
    "Title": null,
    "LogoUrl": null,
    "ThemeName": "",
    "Default": true,
    "Aliases": [],
    "Attributes": {}
  },
  "Roles": [
    {
      "Id": "f919b2c6-6a10-4957-963a-543ed3b65a0a",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Name": "admin",
      "Description": "Administrative Priviledges"
    }
  ],
  "SecureActivities": [
    {
      "Id": "977840dd-eb9e-47ab-a1fe-a71ea3136a91",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Comment",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "22aa4d09-78f8-462a-a3d9-be586db08621",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "File",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "199ab983-491f-420e-93c4-4c424ddf4d48",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Localization",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "60ca5475-bc7a-4b18-80e0-ac8079fc1465",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Search",
      "Name": "Upload",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "7e7a9524-9d64-4599-94aa-903369d27107",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Portal",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "759c746c-b0d9-42e5-be31-6bf9ccb01b6f",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "PageTemplate",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "b907dead-ba77-452a-941c-298847c4f520",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "LayoutTemplate",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "0dd9de1a-7a3d-4d50-b7c8-0289c8e19ab0",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "File",
      "Name": "Upload",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "90ed0b62-7ec2-4221-b975-f597a5487322",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Account",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    },
    {
      "Id": "f6e6c381-3d51-4644-b186-3d7a0daa6344",
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Area": "Content",
      "Name": "Administration",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null
    }
  ],
  "Users": null,
  "UserProfiles": null,
  "Manifests": [
    {
      "Id": "f03851db-e96c-45d6-a681-aaf61aac85a8",
      "Path": "Core/Admin",
      "Name": "File",
      "Title": "File Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/File",
      "AttributeDefinitions": []
    },
    {
      "Id": "4352359c-5b88-42c4-a789-840f44d89d6d",
      "Path": "Core/Admin",
      "Name": "FileBrowser",
      "Title": "File Browser",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/FileBrowser",
      "AttributeDefinitions": []
    },
    {
      "Id": "d16b7aea-c5d8-4413-8cb8-d5cc5e32345a",
      "Path": "Core/Admin",
      "Name": "Localization",
      "Title": "Localization Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Localization",
      "AttributeDefinitions": []
    },
    {
      "Id": "7ed63b29-c625-4b4c-9bdb-2f8fc0bdedc4",
      "Path": "Core/Account",
      "Name": "LogOn",
      "Title": "Log On",
      "Category": "Account",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Account/LogOn",
      "AttributeDefinitions": []
    },
    {
      "Id": "b31be961-c926-46fe-b4f9-d19cb451045b",
      "Path": "Core",
      "Name": "Menu",
      "Title": "Menu",
      "Category": "Navigation",
      "ContentProvider": "Videre.Core.Widgets.ContentProviders.MenuContentProvider, Videre.Core.Widgets",
      "EditorType": "videre.widgets.editor.menu",
      "EditorPath": "Widgets/Core/MenuEditor",
      "FullName": "Core/Menu",
      "AttributeDefinitions": [
        {
          "LabelKey": "AlwaysOnTop.Text",
          "LabelText": "Always On Top",
          "Name": "AlwaysOnTop",
          "DataType": null,
          "Required": false,
          "Values": [
            "Yes",
            "No"
          ],
          "DefaultValue": "Yes",
          "Dependencies": []
        },
        {
          "LabelKey": "InverseColors.Text",
          "LabelText": "Inverse Colors",
          "Name": "InverseColors",
          "DataType": null,
          "Required": false,
          "Values": [
            "Yes",
            "No"
          ],
          "DefaultValue": "No",
          "Dependencies": []
        },
        {
          "LabelKey": "ShowLogo.Text",
          "LabelText": "Show Logo",
          "Name": "ShowLogo",
          "DataType": null,
          "Required": false,
          "Values": [
            "Yes",
            "No"
          ],
          "DefaultValue": "No",
          "Dependencies": []
        },
        {
          "LabelKey": "ShowSearch.Text",
          "LabelText": "Show Search",
          "Name": "ShowSearch",
          "DataType": null,
          "Required": false,
          "Values": [
            "Yes",
            "No"
          ],
          "DefaultValue": "No",
          "Dependencies": []
        }
      ]
    },
    {
      "Id": "a4a8c2f1-a01c-4b53-832d-8c285036f555",
      "Path": "Core/Admin",
      "Name": "Package",
      "Title": "Package Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Package",
      "AttributeDefinitions": []
    },
    {
      "Id": "ac794813-0282-4fa8-b7df-79d94cd47c83",
      "Path": "Core/Admin",
      "Name": "Portal",
      "Title": "Portal Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Portal",
      "AttributeDefinitions": []
    },
    {
      "Id": "3c8f52a5-97d0-45d4-8f2c-3d97c1214f80",
      "Path": "Core/Admin",
      "Name": "Role",
      "Title": "Role Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Role",
      "AttributeDefinitions": []
    },
    {
      "Id": "2ac1ba38-d0f5-45f3-8bec-ec6583bb14e0",
      "Path": "Core/Admin",
      "Name": "Search",
      "Title": "Search Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Search",
      "AttributeDefinitions": []
    },
    {
      "Id": "f101a9c6-a20b-42e8-bf33-6c0d81d677f3",
      "Path": "Core",
      "Name": "SearchResult",
      "Title": "Search Result",
      "Category": "General",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/SearchResult",
      "AttributeDefinitions": []
    },
    {
      "Id": "a07c5c03-4db5-4556-be3d-270537b879fe",
      "Path": "Core/Admin",
      "Name": "SecureActivity",
      "Title": "Secure Activity Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/SecureActivity",
      "AttributeDefinitions": []
    },
    {
      "Id": "3b95299a-68cc-41b5-9e61-41814d373959",
      "Path": "Core/Admin",
      "Name": "Security",
      "Title": "Security Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Security",
      "AttributeDefinitions": []
    },
    {
      "Id": "95ac97d1-bd50-4765-b28d-6868eda46ad3",
      "Path": "Core/Admin",
      "Name": "Template",
      "Title": "Template Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Template",
      "AttributeDefinitions": []
    },
    {
      "Id": "cb342459-7dc1-4f20-a2bb-b3934de6ffed",
      "Path": "Core",
      "Name": "TextHtml",
      "Title": "Text Html",
      "Category": "General",
      "ContentProvider": "Videre.Core.ContentProviders.LocalizationContentProvider, Videre.Core",
      "EditorType": "videre.widgets.editor.texthtml",
      "EditorPath": "Widgets/Core/TextHtmlEditor",
      "FullName": "Core/TextHtml",
      "AttributeDefinitions": []
    },
    {
      "Id": "ab4f55fe-ec76-4739-aa3e-f8f6a93286bd",
      "Path": "Core/Admin",
      "Name": "User",
      "Title": "User Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/User",
      "AttributeDefinitions": []
    },
    {
      "Id": "2acb2e76-a0c7-46e5-a3cc-15d7c67955e7",
      "Path": "Core/Account",
      "Name": "UserProfile",
      "Title": "User Profile",
      "Category": "Account",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Account/UserProfile",
      "AttributeDefinitions": []
    },
    {
      "Id": "c514dfea-4306-4628-9b15-3b1310be39df",
      "Path": "Core/Admin",
      "Name": "WebReference",
      "Title": "Web Reference Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/WebReference",
      "AttributeDefinitions": []
    },
    {
      "Id": "316ef368-390f-4d00-ac20-f2db672c0fa4",
      "Path": "Core/Admin",
      "Name": "Widget",
      "Title": "Widget Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/Widget",
      "AttributeDefinitions": []
    },
    {
      "Id": "84824494-35ee-4505-8a2e-2ed200f8c753",
      "Path": "Core/Admin",
      "Name": "WidgetManifest",
      "Title": "Widget Manifest Admin",
      "Category": "Admin",
      "ContentProvider": null,
      "EditorType": null,
      "EditorPath": null,
      "FullName": "Core/Admin/WidgetManifest",
      "AttributeDefinitions": []
    }
  ],
  "Localizations": null,
  "Files": [
    {
      "Id": "74afad07-6799-44e5-9d4c-57db11a34e91",
      "MimeType": "image/png",
      "Size": 8631,
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Url": "poweredby"
    }
  ],
  "Templates": [
    {
      "Id": "f994cefd-8ad1-43f0-899f-a09a793e6794",
      "Title": "Localization Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/Localization"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "4b00c185-5381-4936-8352-62579b6f2a4c",
          "ContentIds": [],
          "ManifestId": "d16b7aea-c5d8-4413-8cb8-d5cc5e32345a",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "b7442acf-245c-44b0-87bf-24a9accd549a",
      "Title": "Page Template Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/PageTemplate"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "1b0b884b-0196-46c3-a58e-d43c7fbfe649",
          "ContentIds": [],
          "ManifestId": "95ac97d1-bd50-4765-b28d-6868eda46ad3",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "fcbc8231-a49b-4285-9a54-ba1db7a4670f",
      "Title": "Portal Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/Portal"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "8f1f735e-d2e8-4b4a-a3b3-68fdad0b6c84",
          "ContentIds": [],
          "ManifestId": "ac794813-0282-4fa8-b7df-79d94cd47c83",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "8692691a-a4a3-4bcf-8f95-6c8ae52aa085",
      "Title": "Package Admin",
      "LayoutName": "General",
      "ThemeName": "",
      "Urls": [
        "Admin/Package"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "198457c7-5710-450b-9c37-aeac611ae5b1",
          "ContentIds": [],
          "ManifestId": "a4a8c2f1-a01c-4b53-832d-8c285036f555",
          "Css": "",
          "Style": "",
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "4ab5156f-045e-486f-a0b2-607568978067",
      "Title": "User Profile",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Account/UserProfile"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "526daf1b-a669-40e8-8990-0f32eb83be1e",
          "ContentIds": [],
          "ManifestId": "2acb2e76-a0c7-46e5-a3cc-15d7c67955e7",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "a404e021-c8ec-4351-8bea-56b08dc92a5d",
      "Title": "User Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/User"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "eb2b27a9-16f4-4a45-9b4a-b48fc64f0af1",
          "ContentIds": [],
          "ManifestId": "ab4f55fe-ec76-4739-aa3e-f8f6a93286bd",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "661d2810-cd29-40f3-a30a-921e3205bec8",
      "Title": "File Browser",
      "LayoutName": "Blank",
      "ThemeName": null,
      "Urls": [
        "Admin/FileBrowser"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "8f447051-f75c-44f0-97cb-535b0d76facc",
          "ContentIds": [],
          "ManifestId": "4352359c-5b88-42c4-a789-840f44d89d6d",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "cfa8314b-1916-41dc-981f-fa290f913b01",
      "Title": "Web Reference Administration",
      "LayoutName": "General",
      "ThemeName": "",
      "Urls": [
        "Admin/WebReference"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "a7054f2c-77aa-4b48-ab32-ffb8a7d43578",
          "ContentIds": [],
          "ManifestId": "c514dfea-4306-4628-9b15-3b1310be39df",
          "Css": "",
          "Style": "",
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "656c7043-7c65-4ca9-af67-74c85cb1cd11",
      "Title": "Widget Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/Widget"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "7816b798-7c7f-4fe0-b190-e7a95fe8201c",
          "ContentIds": [],
          "ManifestId": "316ef368-390f-4d00-ac20-f2db672c0fa4",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "c8915712-5698-4cec-b7a7-a939c752ced2",
      "Title": "Log On",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Account/LogOn"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "58b0045a-33ad-42f2-ac93-6fbc42519740",
          "ContentIds": [],
          "ManifestId": "7ed63b29-c625-4b4c-9bdb-2f8fc0bdedc4",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "b584188a-8fbf-49b3-938d-ed7b737c5b91",
      "Title": "Layout Template Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/LayoutTemplate"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "c45a1b09-a661-472f-b331-1a50a725aac3",
          "ContentIds": [],
          "ManifestId": "95ac97d1-bd50-4765-b28d-6868eda46ad3",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {
            "IsLayout": true
          }
        }
      ]
    },
    {
      "Id": "6a5763c9-3ec8-4f30-89f8-9433709669d8",
      "Title": "Search Results",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "search"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "cc0adac9-b03b-42da-8491-c1700531bd0f",
          "ContentIds": [],
          "ManifestId": "f101a9c6-a20b-42e8-bf33-6c0d81d677f3",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "c735ebb3-0ceb-4edc-a8e2-e2a1105ffc35",
      "Title": "Home",
      "LayoutName": "General",
      "ThemeName": "",
      "Urls": [],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": []
    },
    {
      "Id": "5116de2a-c63a-447d-ae79-7cd672f6e423",
      "Title": "File Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/File"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "612625a5-c44f-4aca-9fc1-6aa9a01547fb",
          "ContentIds": [],
          "ManifestId": "f03851db-e96c-45d6-a681-aaf61aac85a8",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "5aa51190-28bc-438c-a3bc-12d424dcdcd2",
      "Title": "Security Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/Security"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "21c8d078-f2b2-4a60-a9dc-0f5e896afd9a",
          "ContentIds": [],
          "ManifestId": "3b95299a-68cc-41b5-9e61-41814d373959",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    },
    {
      "Id": "ce8202aa-4d31-4fdf-a401-faa3ab683fa0",
      "Title": "Search Administration",
      "LayoutName": "General",
      "ThemeName": null,
      "Urls": [
        "Admin/Search"
      ],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "Roles": [
        "f919b2c6-6a10-4957-963a-543ed3b65a0a"
      ],
      "Authenticated": null,
      "WebReferences": [],
      "Widgets": [
        {
          "Id": "2ba8c857-d1ca-40d8-9447-0350cda91f0c",
          "ContentIds": [],
          "ManifestId": "2ac1ba38-d0f5-45f3-8bec-ec6583bb14e0",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 0,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ]
    }
  ],
  "LayoutTemplates": [
    {
      "Id": "b43412cd-7546-405e-8651-efccfd9ce3d4",
      "LayoutName": "Blank",
      "ThemeName": null,
      "Widgets": [],
      "Roles": [],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "WebReferences": []
    },
    {
      "Id": "59204851-e916-42c2-977b-f3fab0c32a3b",
      "LayoutName": "General",
      "ThemeName": "",
      "Widgets": [
        {
          "Id": "88bb5da0-ab66-4421-bce2-d2e2e5820e93",
          "ContentIds": [
            "0a2bef36-cb0e-4a87-84af-5a9d286c7055"
          ],
          "ManifestId": "b31be961-c926-46fe-b4f9-d19cb451045b",
          "Css": "",
          "Style": "",
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {
            "AlwaysOnTop": "Yes",
            "InverseColors": "No",
            "ShowLogo": "No",
            "ShowSearch": "No"
          }
        },
        {
          "Id": "4ad6946d-2801-40ce-8f66-2eca73f87632",
          "ContentIds": [
            "e7e2dc8e-977a-4ba6-9a80-daa11c204c3e"
          ],
          "ManifestId": "cb342459-7dc1-4f20-a2bb-b3934de6ffed",
          "Css": "",
          "Style": "",
          "PaneName": "Footer",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ],
      "Roles": [],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "WebReferences": []
    },
    {
      "Id": "59c31673-8e7d-4e9f-a4ee-76e4cfff61d1",
      "LayoutName": "SidebarRight",
      "ThemeName": "",
      "Widgets": [
        {
          "Id": "da320931-6b5c-4419-91df-09efeaa534c1",
          "ContentIds": [
            "0a2bef36-cb0e-4a87-84af-5a9d286c7055"
          ],
          "ManifestId": "b31be961-c926-46fe-b4f9-d19cb451045b",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        },
        {
          "Id": "e1a39f82-8b10-46ed-be04-385d6dc91e1f",
          "ContentIds": [
            "e7e2dc8e-977a-4ba6-9a80-daa11c204c3e"
          ],
          "ManifestId": "cb342459-7dc1-4f20-a2bb-b3934de6ffed",
          "Css": "",
          "Style": "",
          "PaneName": "Footer",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ],
      "Roles": [],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "WebReferences": []
    },
    {
      "Id": "04ac392a-77f0-4fee-a2ad-9a87184cf62a",
      "LayoutName": "TwoPane",
      "ThemeName": "",
      "Widgets": [
        {
          "Id": "b599b3d5-0b79-4f7b-94ca-82bb7059730d",
          "ContentIds": [
            "0a2bef36-cb0e-4a87-84af-5a9d286c7055"
          ],
          "ManifestId": "b31be961-c926-46fe-b4f9-d19cb451045b",
          "Css": null,
          "Style": null,
          "PaneName": "Main",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        },
        {
          "Id": "31140b7f-dd98-4433-a080-8660bb006e75",
          "ContentIds": [
            "e7e2dc8e-977a-4ba6-9a80-daa11c204c3e"
          ],
          "ManifestId": "cb342459-7dc1-4f20-a2bb-b3934de6ffed",
          "Css": "",
          "Style": "",
          "PaneName": "Footer",
          "ShowHeader": false,
          "Seq": 1,
          "Roles": [],
          "Authenticated": null,
          "WebReferences": [],
          "Attributes": {}
        }
      ],
      "Roles": [],
      "PortalId": "1511fd73-5003-46f1-ac4e-7932b0faee56",
      "WebReferences": []
    }
  ],
  "WidgetContent": null,
  "FileContent": null
}
```

## Installation
Installation of a package can be done by the administrator using the Admin -> Package widget.  There will be a install button where you can choose to upload your package file.  The Package Admin widget also allows you to see packages hosted on another site (configured on the Admin -> Portal -> Core -> Repote Package Url).  You can use the grid to compare the remote package versions against your installed packages.  If you wish to update the package from the remote site, simply choose Download Package from the menu.  Once downloaded, you can then choose to Install the package.  The goal here is to allow you to specify a trusted server (store) to grab updates for your packages.  A final way to get a package installed is by directly copying it into your Videre web folder called _updates.  Videre monitors this folder for new files added and will automatically install the package.  

## Package Folders
Videre has three special folders relating to packages.

* _updates:  a monitored folder that whenever a file gets placed here, Videre will attempt to automatically install
* _packages:  a folder where packages get placed once installed or downloaded from a remote source.  Just because a package exists here doesn't necessarially mean it has been installed.  It means it can be installed or re-installed.
* _publish:  this folder is where any packages that are published are placed.  A published package means another Videre portal can point to this one and easily download packages from it, thus allowing your Videre portal to operate as a store or host for package updates.

