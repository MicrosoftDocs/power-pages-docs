---
title: "Tutorial: How to use code components in Power Pages"
description: Walk through example steps for creating a sample code component and adding it to a Dataverse form used to create a form component inside Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 03/02/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: dmartens
contributors:
  - sandhangitmsft
  - HemantGaur
---

# Tutorial: Use code components in portals

In the tutorial, you'll add a custom component to a Microsoft Dataverse form, and enable the custom control to be visible on a webpage.

This tutorial will use the **Feedback** table and the **Contact us** webpage that is available in the **Starter layout** templates. 

## Prerequisites

- Your portal version must be [9.3.3.x](/power-apps/maker/portals/versions/version-9.3.3.x) or higher.
- Your starter portal package must be [9.2.2103.x](/power-apps/maker/portals/versions/version-9.3.3.x) or higher.
- A site using one of the **Starter layout** [templates](../templates/site-design.md).

To create a sample component, follow the steps in the tutorial [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript). At the end of that tutorial, you'll have the component named TSLinearInputComponent packaged and uploaded to your Dataverse environment which you can use in Power Pages.

You can also use some of the out of the box controls that are available. In our example we will use the number input control.

## Step 1. Add the code component to a field in a form

1. In the design studio, select the [Data workspace](../getting-started/use-data-workspace.md).

1. Select the **Feedback** table.

1. Select **Forms** and then choose to edit the **simple contact us form**.

1. Select **+ Add field** and choose the **Rating** field.

1. Position the **Rating** field on the form.

1. With the **Rating** field selected, choose **+ Component** and select the **Number input** component.

    :::image type="content" source="media/component-framework/add-component-to-form.png" alt-text="Add component to form.":::

1. Configure the control to have a **Type** of **Whole Number** and a **Static value** of **1**.

1. Select **Done**.

1. Select **Save** and **Publish form**.

## Step 2. Configure form component on webpage

In the following steps we will configure the existing feedback page, you can also [create your own page](../getting-started/first-page.md) and add your own [form](../getting-started/add-form.md) component.

1. In the **Pages** workspace, select the **Contact us** page.

1. The ratings field should appear on the form with the message **Enable custom component to see this field in preview**.

1. Select the field and choose **Edit field**.

1. Select the **Enable custom component** field.

    :::image type="content" source="media/component-framework/enable-code-component.png" alt-text="Enable custom component in design studio.":::

1. Select **OK**.

1. When you preview the site, you should see the custom component enabled.

    :::image type="content" source="media/component-framework/custom-component-on-form.png" alt-text="Custom component on a form.":::

## Next steps

[Overview: Use code components in Power Pages](component-framework.md)

### See also

- [Power Apps component framework overview](/power-apps/developer/component-framework/overview)
- [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript)
- [Add code components to a field or table in model-driven apps](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity)


