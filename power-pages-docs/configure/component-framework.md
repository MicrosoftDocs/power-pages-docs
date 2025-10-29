---
title: Use code components in Power Pages
description: Learn about creating code components for model-driven and canvas apps using Power Apps component framework inside Power Pages.
author: GitanjaliSingh33msft

ms.topic: how-to
ms.custom: 
ms.date: 10/29/2025
ms.subservice: 
ms.author: nabha
ms.reviewer: dmartens
contributors:
  - GitanjaliSingh33msft
  - HemantGaur
  - nabha
---

# Use code components in Power Pages

Power Apps component framework enables professional developers and app makers to create code components for model-driven and canvas apps. These code components can provide an enhanced experience for users working with data on forms, views, and dashboards. More about [Power Apps component framework overview](/power-apps/developer/component-framework/overview).

Power Pages now support controls built for model-driven apps created using Power Apps component framework. To use code components in Power Pages site webpages:

:::image type="content" source="media/component-framework/steps.png" alt-text="Create code component using component framework, then add the code component to a model-driven app form, and configure the code component field inside the basic form for portals.":::

After completing these steps, users can interact with the code component using the webpage that has the respective [form](../getting-started/add-form.md) component.  

## Prerequisites

- You need system administrator privileges to enable the code component feature in the environment.
- Your Power Pages site version needs to be [9.3.3.x](/power-apps/maker/portals/versions/version-9.3.3.x) or higher.
- Your starter site package needs to be [9.2.2103.x](/power-apps/maker/portals/versions/package-version-9.2.2103) or higher.

## Create and package code component

To learn about creating and packaging code components in Power Apps component framework, go to [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript).

### Supported field types and formats

Power Pages supports restricted field types and formats for using code components. The following field data types and formats are supported:

**Numeric**
    - Currency
    - Decimal
    - Floating Point Number
    - Whole

**Date and Time**
    - DateAndTime.DateAndTime
    - DateAndTime.DateOnly

**Text**
    - SingleLine.Email
    - SingleLine.Phone
    - SingleLine.Text
    - SingleLine.TextArea
    - SingleLine.Ticker
    - SingleLine.URL

**Choice**
    - Enum
    - Multiple
    - OptionSet
    - TwoOptions

For more information, see [Attributes list and descriptions](/power-apps/developer/component-framework/manifest-schema-reference/property#remarks).

### Unsupported code components in Power Pages

- The following code component APIs aren’t supported:
    - [Device.captureAudio](/power-apps/developer/component-framework/reference/device/captureaudio)
    - [Device.captureImage](/power-apps/developer/component-framework/reference/device/captureimage)
    - [Device.captureVideo](/power-apps/developer/component-framework/reference/device/capturevideo)
    - [Device.getBarcodeValue](/power-apps/developer/component-framework/reference/device/getbarcodevalue)
    - [Device.getCurrentPosition](/power-apps/developer/component-framework/reference/device/getcurrentposition)
    - [Device.pickFile](/power-apps/developer/component-framework/reference/device/pickfile)
- [Utility](/power-apps/developer/component-framework/reference/utility)
- The [uses-feature](/power-apps/developer/component-framework/manifest-schema-reference/uses-feature) element must not be set to **true**.
- [Value elements not supported](/power-apps/developer/component-framework/manifest-schema-reference/property#value-elements-that-are-not-supported) by Power Apps component framework.
- Power Apps Component Framework (PCF) controls bound to multiple fields in a form isn't supported.

## Add a code component to a field in a model-driven app

To learn how to add a code component to a field in a model-driven app, go to [Add a code component to a field](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity#add-a-code-component-to-a-column).

> [!IMPORTANT]
> Code components for Power Pages are available for web browsers using the client option of **Web**.

You can also add a code component to a form using [Data workspace](data-workspace-forms.md).

1. When editing a Dataverse form in the Data workspace form designer, select a field.

1. Choose **+ Component** and select an appropriate component for the field.

    :::image type="content" source="media/component-framework/add-component-to-form.png" alt-text="Add component to form.":::

1. Select **Save** and **Publish form**.

## Configure Power Pages site for code component

After the code component is added to a field in a model-driven app, you can configure Power Pages to use the code component on a form.

There are two methods to enable the code component.

### Enable code component in design studio

To enable a code component on a form using the design studio.

1. After you [add the form to a page](../getting-started/add-form.md), select the field where you added the code component and select **Edit field**.

1. Select the **Enable custom component** field.

    :::image type="content" source="media/component-framework/enable-code-component.png" alt-text="Enable custom component in design studio.":::

1. When you preview the site, you should see the custom component enabled.

### Enable code component in Portals Management app

To add a code component to a basic form by using the Portals Management app:

1. Open the [Portals Management](portal-management-app.md) app.

1. On the left pane, select **Basic Forms**.

1. Select the form to which you want to add the code component.

1. Select **Related**.

1. Select **Basic Form Metadata**.

1. Select **New Basic Form Metadata**.

1. Select **Type** as **Attribute**.

1. Select **Attribute Logical Name.**

1. Enter **Label**.

1. For **Control Style**, select **Code Component.**

1. Save and close the form.

## Code components using the portal Web API

A code component can be built and added to a webpage that can use the [portal Web API](web-api-overview.md) to perform create, retrieve, update, and delete actions. This feature allows greater customization options when developing portal solutions. For more information, see [Implement a sample portal Web API component](implement-webapi-component.md).

## Next steps

[Tutorial: Use code components in portals](component-framework-tutorial.md)

## See also

- [Power Apps component framework overview](/power-apps/developer/component-framework/overview) 
- [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript) 
- [Add code components to a column or table in model-driven apps](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity)


