---
title: Create and manage publishing states
description: Learn how to create and manage publishing states in Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom:
ms.date: 04/12/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Create and manage publishing states

Publishing states allow for the definition of a content lifecycle in a Power Pages website. At a basic level, a publishing state can determine whether content should be considered visible/published on a website. In more complex configurations, they can define a multi-stage process for content review and publishing, with security restrictions on each stage.

Publishing states can be used with [web pages](web-page.md), [web files](web-files.md), [web links](manage-web-links.md), forums, and advertisements.

By default, two publishing states are available: **Draft** and **Published**. Draft specifies content that shouldn't be visible to non-content-author users, while Published specifies content that should be visible to website users (with appropriate permissions). You can modify the default configuration to meet your specific requirements, if wanted – by adding new states or renaming states.

## Manage publishing states

Publishing states can be created, edited, and deleted within Power Pages.

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Website** > **Websites**.

1. Select the website to manage publishing states.

1. Go to the **Publishing States** tab (you may have to select the ellipse **...**). The list of available publishing states is displayed.

    :::image type="content" source="media/publishing-states/publishing-states.png" alt-text="Manage publishing states.":::

1. To add a new publishing state, select **New publishing state**.

1. To edit an existing publishing state, select the publishing state name.

1. In the Publishing State window, enter appropriate values in the fields.

1. Select **Save & Close**.

### Publishing state attributes

|Name|Description|
|-----|--------|
|Name|The descriptive name of the state. This field is required.|
|Website|The website to which the state belongs. This field is required.|
|Is Default|If checked, sets this state as the default state for the website. This option will determine the default state selected when creating new tables through the legacy front-side editing interface.<br>**Note**: Only one Publishing State in a given website should be marked as the default state.|
|Is Visible|If checked, sets the content associated with this state will be considered visible (or published) on the website.<br>While content associated with a non-visible state won't be visible on the website, content associated with a visible state may also not be visible, because of the security permissions, expiration dates, or other visibility rules.<br>Users with content management permissions may be granted the ability to use Preview Mode, which allows these users to see (preview) unpublished content.|
|Display Order|An integer value indicating the order in which the state will be placed, in menus and drop-down lists for selecting a Publishing State – mostly found in the legacy front-side editing interfaces.|
|||

> [!IMPORTANT]
> Creating new pages using the design studio will fail if you don't have any default publishing state. Ensure that you have a default publishing state by selecting a publishing state record and set the **Is Default** attribute value to **Yes**.

> [!NOTE]
> Web pages with no associated Publishing State may cause issues with the navigation menu and affect the page visibility. You may see a warning about such missing Publishing State associations for the pages when editing your website. To fix this warning, select a Publishing State for each [Web Page record](web-page.md) using the [Portal Management app](portal-management-app.md).

### Considerations for publishing state when editing websites

When you edit the website using the design studio, you may see one of the following warning messages. To fix the warnings, follow the steps described in the description.

| Message | Description |
| - | - |
| `Found missing publishing state association for the page(s): {list of pages}. To avoid issues with the page(s), ensure each webpage has a publishing state configured.` | Web pages with no associated publishing state may cause issues with the navigation menu and affect the page visibility. You may see a warning about such missing publishing state associations for the pages when editing your website. <br> To fix this warning, select a publishing state for each [web page](web-page.md). |
| `Found multiple default publishing states configured. Publishing state {name} will be used as the default.` | More than one publishing state is set as the default. Since only one publishing state should be set as the default, the design studio will choose one from the configured multiple default publishing states. <br> To fix this warning, ensure only one publishing state is set as the default. |
| `No default publishing state configured. Publishing state {name} will be used as the default.` | None of the available publishing state is set as the default. The design studio will choose one from the available publishing states as the default. <br> To fix this warning, ensure you set one publishing state as the default. |
| `Found publishing states missing. Please create at least one publishing state as the default.` | There are no publishing states available. <br> To fix this warning, create at least one publishing state and set it as the default. |

## Publishing state transition rules

Publishing state transition rules allow you granular control over which web roles have the right to make what content changes on the website for publishing state.

To be precise, publishing state transition rules govern the transitions between publishing states (Draft or Published). When a user attempts to switch the publishing state of an item from one to another, if a rule exists for this transition, then the security provider will assert that the web role for the logged-in user has permission to do this transition.

If the logged-in user who is attempting the change is in any of the roles you assign to the rule, the transition will be successful. If a user doesn't have permissions to make a change from one rule to another, then the front-side editing won't allow them to make that change. Instead, you can create the rule; then as you create web roles add the rule to the web roles. One rule can be associated with any number of web roles and the other way around.

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Websites** > **Publishing State Transition Rules**.

1. To create a new rule, select **New**.

1. To edit an existing rule, select the rule name.

1. In the Publishing State Transition Rule window, enter appropriate values in the fields.

1. Select **Save** so you can continue adding web roles to it.

    :::image type="content" source="media/publishing-states/publishing-states.png" alt-text="Create publishing state transition rule.":::

1. On the **Web Roles** tab, select **Add Existing Web Role**. In the **Lookup Records** pane, browse and add the appropriate web roles.

1. Select **Save**.

## State-based control rules

[Webpage security](../security/page-security.md) can be linked with publishing states to allow or deny the right to view or modify content based on the branch of the website and the publishing state of content within that branch. To accomplish this task, associate a web page access control rule with a publishing state. Once it's associated with a publishing state, the rule will only be applied to web pages when that publishing state is active.

For example, say you wanted someone in the content publishing role who can modify a page's content, but only when that page is in Draft mode. This scenario would ensure that changes to the page aren't done while the page is 'live' and would allow for an approval process to be undertaken on pending changes.

To do this, you would create a rule with the grant change permission and apply it to the branch in question (or the home page if the rule is to apply to the entire site). You would then associate this rule with the draft state.

:::image type="content" source="media/publishing-states/state-based-control-rule.png" alt-text="Create state-based control rule.":::

You would then associate this rule with the appropriate web role, for example, Content publishing. Assuming this web role isn't associated with a more permissive rule (a rule that grants change no matter which publishing state) then users in the content publishing web role can modify pages in the draft state but can't modify pages in the published state.