---
title: Implement portals Web API code components sample
description: This page walks you through a sample code component that uses the portal Web API.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 03/02/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
  - sandhangitmsft
 
---

# Implement a sample portal Web API component

The following is an example of implementing a code component that uses the portal Web API to perform create, retrieve, update, and delete actions. The component renders four buttons, which can be clicked to invoke different Web API actions. The result of the Web API call is injected into an HTML `div` element at the bottom of the code component.

:::image type="content" source="media/implement-webpi-component/webapi-component.png" alt-text="Example component using the portal Web API.":::

## Prerequisites

- Your portal version must be [9.3.10.x](/power-platform/released-versions/portals/portalupdate9310x) or higher.
- Your starter portal package must be [9.2.2103.x](/power-apps/maker/portals/versions/package-version-9.2.2103) or higher.
- You need to enable the site setting to enable the portals Web API for your portal. [Site settings for the Web API](web-api-overview.md#site-settings-for-the-web-api)
- Configure table security using table permissions. [Table permissions](../security/assign-table-permissions.md)

## Code

You can download the complete sample component from [here](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/PortalWebAPIControl).

By default, in the sample, the component is configured to perform the create, retrieve, set the name and revenue fields in the Web API examples.

To change the default configuration to any table or column, update the below configuration values as shown

`private static \_entityName = "account";`

`private static \_requiredAttributeName = "name";`

`private static \_requiredAttributeValue = "Web API Custom Control (Sample)";`

`private static \_currencyAttributeName = "revenue";`

`private static \_currencyAttributeNameFriendlyName = "annual revenue";`

The `createRecord` method renders three buttons, which allows you to create an account record with the revenue field set to different values (100, 200, 300).

When you select one of the create buttons, the button's `onClick` event handler checks the value of the button selected and uses the Web API action to create an account record with the revenue field set to the button's value. The name field of the account record will be set to *Web API code component (Sample)* with a random `int` appended to the end of the string. The callback method from the Web API call injects the result of the call (success or failure) into the custom control's result `div`.

The `deleteRecord` method renders a button which deletes the selected record in the dropdown. The dropdown control allows you to select the account record you want to delete. Once an account record is selected from the dropdown and the **Delete Record** button is selected, the record is deleted. The callback method from the Web API call injects the result of the call (success or failure) into the custom control's result `div`.

The [FetchXML](/powerapps/developer/data-platform/use-fetchxml-construct-query) `retrieveMultiple` method renders a button in the code component. When the `onClick` method of this button is called, FetchXML is generated and passed to the `retrieveMultiple` function to calculate the average value of the revenue field for all the accounts records. The callback method from the Web API call injects the result of the call (success or failure) into the custom control's result `div`.

The OData `retrieveMultiple` method renders a button in the code component. When the `onClick` method of this button is called, an OData string is generated and passed to the `retrieveMultiple` function to retrieve all account records with a name field that is like *code component Web API (Sample)*, which is true for all account records created by this code component.

On successful retrieve of the records, the code component has logic to count how many account records have the revenue field set to 100, 200 or 300, and display this count into an OData status container div on the code component. The callback method from the Web API call injects the result of the call (success or failure) into the custom control's result `div`. 

### See also

- [Power Apps component framework overview](/powerapps/developer/component-framework/overview) 
- [Download sample components](https://github.com/microsoft/PowerApps-Samples/tree/master/component-framework) 
- [How to use the sample components](/powerapps/developer/component-framework/use-sample-components)
- [Create your first component](/powerapps/developer/component-framework/implementing-controls-using-typescript)
- [Add code components to a field or table in model-driven apps](/powerapps/developer/component-framework/add-custom-controls-to-a-field-or-entity)
- [Liquid template tag for code components](liquid/component-framework-liquid.md)
- [Portals Web API](web-api-overview.md)

