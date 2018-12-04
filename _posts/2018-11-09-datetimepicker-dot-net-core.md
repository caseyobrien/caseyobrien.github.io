---
title: Adding a JQuery datetimepicker to ASP .NET Core 2.1
categories: [code]
tags: [tutorials, .NET Core]
---

<!-- * Do not remove line.
{:toc} -->

<!-- {% include figure image_path="/assets/screenshots/jquery-datetimepicker.png" caption="JQuery datetimepicker" %} -->

![JQuery datetimepicker](/assets/screenshots/jquery-datetimepicker.png){: .align-center}{:style="max-width: 50%"} 

## Install datetimepicker with LibMan

- Right-click the project in the Solution Explorer. Select **Add** > **Client-Side Library**.
- Make sure the "Provider" is **cdnjs**. 
- Search for "jquery-datetimepicker".
- Select **Include all library files**.
- Click **Install**.

## Install moment with LibMan

- Right-click the project in the Solution Explorer. Select **Add** > **Client-Side Library**.
- Make sure the "Provider" is **cdnjs**. 
- Search for "moment.js".
- Select **Choose specific files**.
- Select *only* the following files:
    - `moment.js`
    - `moment.min.js`

## Include CSS and JS References in _Layout.cshtml

- In the `<head>` section, within `<environment include="development">`, add the following style sheet reference:
  ```html
  <link rel="stylesheet" href="~/lib/jquery-datetimepicker/jquery.datetimepicker.css" />
  ```

- Before the closing body tag, `</body>`, within `<environment include="development">`, add the following script references after any references to `jquery.js`: 
  ```html
  <script src="~/lib/jquery-datetimepicker/jquery.datetimepicker.js" type="text/javascript"></script>
  <script src="~/lib/moment.js/moment.js"></script>
  <script src="~/js/DateTimePickerReady.js" type="text/javascript"></script>
  ```

## Create JS to Add the datetimepicker

- Create a file `wwwroot/js/DateTimePickerReady.js` that contains the following function:
  ```js
  $(function () {
    $.datetimepicker.setDateFormatter('moment');
    $(".datetimefield").datetimepicker({
        format: 'MM/DD/YYYY hh:mm A',
        formatTime: 'h:mm A'
    });
  });
   ```  

## Create An EditorTemplate

- Create a view `Views/Shared/EditorTemplates/DateTime.cshtml` that contains the following Razor code:
```js
@model DateTime
@Html.TextBox("", Model.ToString("MM/dd/yyyy hh:mm tt"),
  new { @class = "form-control datetimefield", type = "text", autocomplete="off"})
```

## Use Razor Syntax in Razor Code 

```html
@Html.EditorFor(e => e.StartDate)
```

## Versions and Credits

- .NET Core 2.1
- jquery-datetimepicker@2.5.20
- moment.js@2.22.2