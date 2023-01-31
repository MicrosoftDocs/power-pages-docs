---
title: "Tutorial: How to use code components in Power Pages"
description: Walk through example steps for creating a sample code component and adding it to a Dataverse form used to create a form component inside Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 01/31/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
  - nickdoelman
  - sandhangitmsft
  - HemantGaur
---

# Tutorial: Use code components in portals

In this tutorial, you'll create a sample component using Power Apps component framework. You'll package this component to a Dataverse environment and add the component to a model-driven app. You'll then configure Power Apps portals to add the component to a basic form and add the basic form to a webpage. Finally, you'll visit the portals webpage and interact with the component.

## Prerequisites

- Your portal version must be [9.3.3.x](/power-apps/maker/portals/versions/version-9.3.3.x) or higher.
- Your starter portal package must be [9.2.2103.x](/power-apps/maker/portals/versions/version-9.3.3.x) or higher.

> [!NOTE]
> This tutorial is based on the existing Power Apps component framework tutorial that walks you through creating the [TSLinearInputComponent](/power-apps/developer/component-framework/implementing-controls-using-typescript) for the **Opportunity** table on the **Main** form. You can also use any existing or new component, and any other table for this tutorial. In this case, be sure to use your component and form when following the steps in this tutorial.

## Step 1. Create your first component

To create a sample component, follow the steps in the tutorial [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript).
At the end of this tutorial, you'll have the component named TSLinearInputComponent packaged and uploaded to your Dataverse environment.

## Step 2. Add the code component to a field in a model-driven app

Now that you have the TSLinearInputComponent uploaded to your Dataverse environment, follow the steps in the tutorial [Add a code component to a field in model-driven apps](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity) to add the component to the **Opportunity** table on the **Main** form.

## Step 3. Verify the model-driven app with the new component

You can [update an existing model-driven app](/power-apps/maker/model-driven-apps/design-custom-business-apps-using-app-designer) or [create a new app](/power-apps/maker/model-driven-apps/build-first-model-driven-app) with the form to which you added the component. For example, the following image shows how the **Opportunity** table **Main** form looks when using the code component in this tutorial.

:::image type="content" source="media/component-framework/model-driven-app.png" alt-text="Slider control added to the Budget Amount field in model-driven app form.":::

## Step 4. Add code component to a basic form in portals

In this step, you’ll create a new basic form in portals and then add the component to the created basic form. You can also use an existing basic form instead.

### Step 4.1. Create a new basic form

1. Open the [Portals Management](portal-management-app.md) app.

1. On the left pane, under **Content**, select **Basic Forms.**

1. Select **New**.

1. Enter **Name**. For example, *Opportunities basic form with code
    component*.

1. Select **Basic Name** as *Opportunity*.

1. For **Form Name**, select the model-driven app form that you added the code
    component to earlier in this tutorial.

1. Select the **Tab Name**.

1. Select your portal **Website**.

    :::image type="content" source="media/component-framework/new-entity-form.png" alt-text="Configure basic form using Portal Management app.":::

1. Select **Save & Close**.

### Step 4.2. Add code component to the basic form

1. Open the [Portals Management](portal-management-app.md) app.

1. On the left pane, under **Content**, select **Basic Forms.**

1. Select the basic form you created in the previous step.

1. Select **Related**.

1. Select **Basic Form Metadata**.

1. Select **New Basic Form Metadata**.

1. Select **Type** as **Attribute**.

1. Select **Attribute Logical Name** as *Budget Amount (budgetamount)*.

    :::image type="content" source="media/component-framework/attribute-logical-name.png" alt-text="Budget Amount attribute logical name.":::

1. Enter **Label**. For example, *Budget Amount*.

1. For **Control Style**, select **Code component**.

    :::image type="content" source="media/component-framework/control-style.png" alt-text="Text used by screen readers.":::

1. Select **Save & Close**.

## Step 5. Create a webpage in portals with the basic form

1. Open your portal in [Power Apps portals Studio](portal-designer-anatomy.md).

1. On the top-left corner, select **New page**.

1.  Select **Blank**.

1.  On the right-side property pane, update the webpage name. For example, *Opportunities.*

1.  Update partial URL. For example, *opportunities.*

1.  Expand **Permissions**.

1.  Disable **Page available to everyone**.

1.  Select the web roles that should be allowed access to this page.

1.  Inside the page editor, below the Header section, select the **Column** section.

1. On the left pane, select **Components**.

1. Under **Portal components**, select **Form**.

1. On the right-side property pane, select **Use existing**.

1. Under **Name**, select the basic form that you created earlier in this tutorial.

    > [!TIP]
    > If you don’t see the form available, try **Sync Configuration** to synchronize changes from Dataverse.

1. On the top-right corner, select **Browse website**.

The webpage will now show the basic form for the **Opportunities** table with the code component as the slider, similar to how it appears using the model-driven app for the same form.

:::image type="content" source="media/component-framework/example-preview.png" alt-text="Example preview of the Budget Amount slider control on portals page.":::

## Next steps

[Overview: Use code components in Power Pages](component-framework.md)

### See also

- [Power Apps component framework overview](/power-apps/developer/component-framework/overview)
- [Create your first component](/power-apps/developer/component-framework/implementing-controls-using-typescript)
- [Add code components to a field or table in model-driven apps](/power-apps/developer/component-framework/add-custom-controls-to-a-field-or-entity)


