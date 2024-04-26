---
title: Add custom JavaScript to a list
description: Learn how to add custom JavaScript to a website.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 04/06/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - sandhangitmsft
    - ProfessorKendrick
---

# Add custom JavaScript to a list

The **Options** tab on the list configuration in the [Portal Management app](portal-management-app.md) contains a text area where you can enter custom JavaScript. If your page includes jQuery library, you can use that here as well. The script block will be added at the bottom of the webpage just before the page’s closing form tag.

:::image type="content" source="media/add-custom-javascript/custom-javascript-example.png" alt-text="Custom JavaScript example.":::
  
The list gets its data asynchronously, and when it's complete it will trigger an event `loaded` that your custom JavaScript can listen for and do something with items in the grid. The following code is a trivial example:

```javascript
$(document).ready(function (){
    $(".entitylist.entity-grid").on("loaded", function () {
        $(this).children(".view-grid").find("tr").each(function (){
        // do something with each row
        $(this).css("background-color", "yellow");
        });
    });
}); 
```

Find a particular attribute field and get its value to possibly modify the rendering of the value. The following code gets each table cell that contains the value of the `accountnumber` attribute. Replace `accountnumber` with an attribute appropriate for your table and view.

```javascript
$(document).ready(function (){
   $(".entitylist.entity-grid").on("loaded", function () {
      $(this).children(".view-grid").find("td[data-attribute='accountnumber']").each(function (i, e){
         var value = $(this).data(value);
         // now that you have the value you can do something to the value
      });
   });
});
```

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)
