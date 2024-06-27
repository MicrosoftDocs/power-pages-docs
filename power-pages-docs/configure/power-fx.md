---
title: Use Power Fx in Power Pages (preview)
description: Explore Power Fx, Microsoft's low-code language for expressing logic across the Power Platform, now available in Power Pages.
author: sandhangitmsft
ms.topic: conceptual
ms.date: 06/27/2024
ms.subservice:
ms.author: sandhan
ms.reviewer: dmartens
ms.collection:
  - bap-ai-copilot
contributors:
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:06/07/2024
---

# Use Power Fx in Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[Power Fx](/power-platform/power-fx/overview) is the low-code language for expressing logic across the [Microsoft Power Platform](/power-platform). It's a general-purpose, strong-typed, declarative, and functional programming language.

Power Fx is expressed in human-friendly text. It's a low-code language that makers can work with directly in an Excel-like formula bar. The "low" in low-code is due to the concise and simple nature of the language, making common programming tasks easy for both makers and developers.

> [!NOTE]
> You may find the syntax for authoring Power Fx formula to be a bit different than what you may be used to in Power Apps or Power Automate. To initiate a Power Fx expression, it needs to begin with an '=' (equal sign) similar to the experience in Excel. For more information, see [Important considerations](#important-considerations).

Power Fx enables the full spectrum of development from no-code makers without any programming knowledge to pro-code for professional developers. It enables diverse teams to collaborate and save time and effort.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - The feature is available with Power Pages version [9.6.5.x](/power-platform/released-versions/portals/pagesversion965x).

## Use Power Fx in Power Pages

Within a Power Pages website, Power Fx is available as an expression language for use with the following components and their attributes. This functionality facilitates the dynamic assignment of values based on the outcomes of Power Fx expressions.

|Component  |Properties  |
|---------|---------|
|Text     |     Text    |
|Image     |    Image URL, Alt Text     |
|Button     |   Button URL, Button text      |
|Iframe     |     Iframe URL   |

### Use the Power Fx formula bar

A new **fx** command is available in the toolbar for each component that supports Power Fx:

:::image type="content" source="media/power-fx/command-bar.png" alt-text="Screenshot of the Power Fx command in the command bar of a text control.":::

Select **fx** to access the Power Fx formula bar.

#### Formula bar components

The following screenshot highlights some of the important components of the formula bar:

:::image type="content" source="media/power-fx/formula-bar.svg" alt-text="Screenshot of the Power Fx formula bar in Power Pages.":::

1. A dropdown allows you to choose from the available component properties.

1. A multiline expandable textbox allows authoring of Power Fx formulas.

1. The **Reset** button sets a component property to its default.

1. The **Save** button persists the formula and expressions for the component property. The studio canvas is immediately updated if the resulting value is available and can be shown such as in text properties.

#### Formula bar experiences

The following are some developer centric features for increased productivity:

- **Autocomplete assistance**: suggests formulas, parameters, tables, and objects. Select <kbd>Ctrl</kbd> + <kbd>space</kbd> to manually access this feature.

    :::image type="content" source="media/power-fx/auto-complete-assistance.png" alt-text="Screenshot of the autocomplete experience in Power Fx.":::

- **View problem capability**: helps in early validation and debugging of formulas and expressions.

    :::image type="content" source="media/power-fx/view-problem.png" alt-text="Screenshot of the experience when a problem is detected in a Power Fx formula.":::

- **Unsaved changes dialog**: is shown if you navigate away from the formula bar when there are unsaved changes to a formula.

    :::image type="content" source="../admin/Media/set-up-payments-integration/unsaved-changes.svg" alt-text="Screenshot of the unsaved changes dialog with options for Go back or Discard.":::

    Select **Go back** to continue editing the formula or **Discard** to discard the changes.  

### Important considerations

The following are some important considerations to be aware of when using Power Fx formula bar in Power Pages:

- **Start with an equals sign**: Text can be entered directly as the value. However, to initiate a Power Fx expression, it should begin with an '=' (equal sign) such as in the following example.

    ```power-fx
    =Concatenate("Hello, ", User.FullName)
    ```

- **Tables are accessed securely**: Dataverse tables can be accessed securely using formulas. Verify table permissions are appropriately configured first. Also, the context of a site user is available using the **User** object. For example, the following expression retrieves the DataverseUserId value of the currently authenticated user.

    ```power-fx
    =Concatenate("Hello, ", First(Filter(Contacts,Contact = User.DataverseUserId)).'First Name' & "!")
    ```

    > [!NOTE]
    > The **User** object represents a Power Pages user and hence does not support the same set of properties as the [User](/power-platform/power-fx/reference/function-user) function.

- **Inserting a value within text**: To insert a value within text, use the following syntax.

    ```power-fx
    This text ${variable/ expression} includes a dynamic value.
    ```

    For example:  

    ```power-fx
    The total number is ${Sum(10, 20)}
    ```

## Available Power Fx functions

For the complete list of all available functions in Power Pages, go to [Formula reference – Power Pages](/power-platform/power-fx/formula-reference-power-pages).

## Known issues and limitations

- Some Power Fx functions presented through IntelliSense aren't currently supported in Power Pages. Those functions display the following design time error when used:

    `Parameter 'Value': PowerFx type is not supported.`

- User isn't initialized for anonymous users and results in the following error when used on any form including check for blank. This issue will be fixed in a future release.

     `UserInfo object was not added to service`

- Some users might see problems with Button and Image URL properties not working when the value is set with Power Fx formulas or expressions that contain double quotes. This issue only happens if you have version 9.6.3.x and is fixed when your Power Pages site is upgraded to [version 9.6.5.x](/power-platform/released-versions/portals/pagesversion965x).

## Frequently asked questions

### Should I use Power Fx instead of Liquid?

Power Fx fulfills certain dynamic data scenarios in a low-code way that might also be achieved via [Liquid](liquid-overview.md) code with pro-developer tools. Power Fx, presently in its public preview phase, is recommended for trial or developmental site evaluations. We welcome your feedback during this stage. Liquid is a generally available (GA) feature and comparatively provides more capabilities. Use Liquid for your production websites, particularly in scenarios that are critical and complex.

## See also

- [Microsoft Power Fx overview](/power-platform/power-fx/overview)
- [Formula reference – Power Pages](/power-platform/power-fx/formula-reference-power-pages)
