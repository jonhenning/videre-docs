# Bootstrap FluentAPI

## Introduction
The Videre CMS made a decision from the beginning to utilize the Bootstrap UI framework.  This started with Bootstrap version 2.  At the time a few Html extensions were created to enable the easy addition of what were known as control groups to a page.

``` csharp
@Html.InputControlGroup(Model, "txtUrl", "Url.Text", "Url", "Url", "input-xlarge")
```

With the migration to [Bootstrap](https://getbootstrap.com) version 3, the HTML changed quite a bit for what used to be called control groups.  It was during this conversion that the decision was made to move away from having method with many different overrloads to something more maintainable and developer friendly, a Fluent API.

``` csharp
@Html.Bootstrap().FormGroup(Html.Bootstrap().Label("Url.Text", "Url").GridSize(BootstrapUnits.GridSize.MediumDevice3), 
    Html.Bootstrap().TextBox("txtUrl").DataColumn("Url").Required(), BootstrapUnits.GridSize.MediumDevice4)
```

The markup above would output HTML similar to this

``` html
<div class="form-group">
    <label class="control-label col-md-3">Url</label>
    <div class="col-md-4">
        <input id="w3_txtUrl" class="form-control" data-column="Url" required="required" type="text">
    </div>
</div>
```

## IFluentBootstrapControlBase Interface

|                   |                           |
| ----------------- | ------------------------- |
| .Css("some-class")	| <... class="some-class"> |
| .DataAttribute("attributename", "AttributeValue")	| <... data-attributename="AttributeValue" > |
| .DataColumn("ColumnName")	| <... data-column="ColumnName" >|
|.GridSize(BootstrapUnits.GridSize.MediumDevice4) | <... class="col-md-4" > |
| .HtmlAttributes(new {somename="Value", x="1" }) | <... somename="Value" x="1" > |
| .StyleAttribute("width", "100px")	| <... style="width:100px;" > |
| .StyleAttributes(new {width="100px", height="100px"})	| <... style="width:100px;height:100px;" > |
| .ToolTip("Token.Text", "Default Translation")	| <... title="Default Translation" > |

## IFluentBootstrapInputControl Interface
|                   |                           |
| ----------------- | ------------------------- |
| .Append(Html.Bootstrap().Button()) | ...><button /> |
| .ControlType("mycontroltype")	| <... data-controltype="mycontroltype"> |
| .DataType("number") | <... data-datatype="number"> |
| .DisableAutoComplete() | <... autocomplete="off" > |
| .InputSize(BootstrapUnits.InputSize.Small) | <... class="input-sm"> |
| .MaxLength(10) | <... maxlength="10"> |
| .MustMatch("txtPassword")	| <... data-match="w1_txtPassword"> |
| .Prepend(Html.Bootstrap().Button()) | <button /><... |
| .ReadOnly() | <... readonly="readonly" > |
| .Required() | <... required="required" > |
| .PlaceHolder("Token.Text", "Default Translation")	| <... placeholder="Default Translation" > |
| .Val("123") | <... value="123" > |

## Controls
| Control           | Interface(s)              |
| ----------------- | ------------------------- |
| AnchorButton	| IFluentBootstrapControlBase |
| Button | IFluentBootstrapControlBase |
| CheckBox | IFluentBootstrapControlBase |
| DateTimePicker | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| DropDownList | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| FormGroup	| IFluentBootstrapControlBase |
| Label	| IFluentBootstrapControlBase |
| Paragraph	| IFluentBootstrapControlBase |
| Password | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| RadioButton | IFluentBootstrapControlBase |
| Span | IFluentBootstrapControlBase |
| Tabs | IFluentBootstrapControlBase |
| TextArea | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| TextBox | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| TextEditor | IFluentBootstrapControlBase, IFluentBootstrapInputControl |
| UnorderedList	| IFluentBootstrapControlBase | 
| Upload | IFluentBootstrapControlBase |
