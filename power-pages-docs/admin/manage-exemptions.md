---
title: Manage Exemptions for Power Pages Sites
description: Manage exemptions for Power Pages sites to request a time-bound extension when a site can't meet an enforcement date. Learn how to review, select, and confirm.
author: RitGan
ms.author: ritwikganni
ms.reviewer: smurkute
ms.date: 09/01/2026
ms.topic: how-to
---

# Manage exemptions for Power Pages sites 

Some Power Pages updates, such as a feature retirement, a required migration, or a configuration change, have a fixed enforcement date. If you can't update your sites before that date, an admin can use the **Manage exemptions** page in the Power Platform admin center to request a time-bound extension for the impacted sites. This self-service mechanism doesn't require contacting Microsoft Support.

> [!IMPORTANT]
> This feature is being gradually rolled out across regions and might not be available yet in your region.

The process is the same for all updates that support exemptions. Review the update details, identify affected sites, select the sites that need extra time, and confirm the extension request.

> [!NOTE]
> An extension delays enforcement. It doesn't remove the requirement. The update is enforced when the extension expires, and the extension can't be renewed. Use the extension period to complete the required changes.

## Prerequisites

- A Power Platform Admin or Dynamics 365 Administrator role in the Power Platform admin center.
- Knowledge of which sites can't be updated before the enforcement date.

## Open the Manage exemptions page

The **Manage exemptions** page lists the updates that are currently being enforced for your tenant. Each update includes a summary of the change and its enforcement date.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left navigation pane, select **Manage**, and then select **Power Pages**.
1. Select the **Manage exemptions** tab.

:::image type="content" source="media/manage-exemptions/manage-exemptions.png" alt-text="Manage exemptions page in the Power Platform admin center listing updates currently being enforced for the tenant.":::

If an update doesn't appear on this page, it either doesn't apply to your tenant or doesn't support self-service extensions.

## Review the update details

Select an update to open its details pane. Use the details pane to determine whether to update affected sites before the enforcement date or request an extension.

:::image type="content" source="media/manage-exemptions/site-details.png" alt-text="Details pane for an enforced update showing the recommendation, the required action, the list of impacted sites, and next steps.":::

| **Section** | **Description** |
|----|----|
| **What is changing** | Describes the change, the enforcement date, and the effect on sites that aren't updated. |
| **What you need to do** | Lists the required action and provides a **Learn more** link to related guidance. |
| **Impacted sites** | Lists the affected sites in your tenant. Use the search box to find a specific site. |
| **Next steps** | Describes how to make, test, and deploy the required changes before the enforcement date. |

Update as many sites as possible before the enforcement date. Request an extension only for sites that can't be updated in time.

## Request an extension

Select the affected sites and submit an extension request.

1. In the details pane, select the impacted sites that require more time. You can select one or more sites.
1. Select **Request an exemption**.
1. Review the extension details on the confirmation page. The page shows the date when the update will be enforced on the selected sites. Microsoft determines the extension period for each update.

   :::image type="content" source="media/manage-exemptions/extension-request-screen.png" alt-text="Extension confirmation page showing the new enforcement date and the acknowledgment checkbox.":::

1. Read the acknowledgment and select the checkbox to confirm that you understand the risk and that the extension can't be renewed. You can't submit the extension request without selecting it.
1. Confirm the request.

The extension is applied to the selected sites immediately.

## Track an extension

After you submit the request:

- **Enforcement is deferred** on the selected sites until the new date shown on the confirmation page.
- **Notify the site owners of the affected sites**, so they can make the required changes before the extension expires.
- **The update is applied automatically when the extension expires.** No further action is required, and no further extension is available.
- **The request is recorded** that includes who submitted the request, when it was submitted, and which sites were selected. The record remains visible after the extension expires.

Return to **Manage exemptions** at any time to review active extensions and their expiration dates.

> [!NOTE]
> You can request an extension only once per site, per update. After an extension is granted or expires, the same site can't receive another extension for that update. Sites that aren't updated before the extension expires might be affected when enforcement occurs.

## Review updates currently being enforced

The following updates support self-service extensions.

| **Update** | **Description** | **Extension** | **More information** |
|---|---|---|---|
| Web API wildcard (*) operator usage expires on September 14, 2026 | The wildcard (*) field configuration for the Web API is retiring. Sites that continue to use * in Webapi/&lt;table&gt;/fields after the enforcement date might lose access to Web API data, causing affected site experiences to stop working. Replace the wildcard with an explicit list of the columns your site uses, or configure the columns by using a supported system view. | 90 days | [Migrate from the Web API wildcard (*) field configuration](/troubleshoot/power-platform/power-pages/migrate-web-api-wildcard) |

## Related content

- [Important upcoming changes and deprecations in Power Pages](../important-changes-deprecations.md)