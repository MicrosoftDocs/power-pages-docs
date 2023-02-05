---
title: Upgrade a Power Pages site
description: Learn how to upgrade a Power Pages site.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 02/05/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---
 
# Upgrade a Power Pages site

This section helps you understand the Power Pages release process to prepare for any new release properly and to reduce any impact on your customers. It also talks about various components which are part of your website.

A Power Pags site consists of the following components:

|Component|Description|Update process|
|---------|-----------|--------------|
|[Power Pages solutions](#solution-update)|Solutions which are installed in Microsoft Dataverse environment and contains the metadata tables for any website.|Updated by customers themselves from the Power Platform admin center.|
|[Power Pages website host](#website-host-update)|The Power Pages website host is the Azure web application which forms the actual website.|The Power Pages website host is updated automatically for all sites.<br>**Note**: A new version of Power Pages website host is backwards compatible with all supported versions of Power Pages solutions. However, once a solution version becomes unsupported, it is not certified to run with the new version of Power Pages website host.|
|||

## Impact of new releases on a Power Pages solution

As part of any Power Pages release, Power Pages website hosts are updated automatically to the latest versions while Power Pages solutions are updated by customers. It is important to understand the impact of each component update on your live website, so you can plan accordingly.

### Website host update

If you are running a production version of a Power Pages site (you can see it on Power Pages sites area of the Power Platform admin center), there will not be any downtime to your live website when being updated. However, if you are running a trial version of Power Pages, there will be around 6-10 minutes of downtime and you will not be able to access your website.

### Solution update

While installing or updating any solution in your instance, you can see some instability in your instance. The Power Pages solution update process updates solutions available in your instance and will impact your instance which will in turn have an impact of your website as well. Hence, it is always advised to do solution updates in your instance during dark hours.

More details: [Update Power Pages solution](update-solution.md)

## Get notified about new releases

Every customer is notified about new Power Pages releases through Office 365 message center (in Microsoft 365 admin center). Ensure that you either have access to Office 365 message center (Global administrator and service administrator have access) or have discussed with your global administrator or service administrator to inform you about any new Power Pages releases.

Notifications are sent around 2-5 business days ahead of the release. Notifications are sent to only those customers whose portals are planned to be updated. Each notification provides details of the type of update and the date/time it will be rolled out along with the link to release notes.

## Enable a website for new release

You can enable development or test website to receive an early upgrade ahead of all customers, so you can test all core scenarios on your test site before upgrades are rolled out to your live website. Early upgrades are rolled out at least one week before the global rollout of any release. Also, notifications for early upgrades are sent as described in the [Get notified about new releases](#get-notified-about-new-releases) section.

To enable a Power Pages website for early upgrade:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Select the **Power Pages sites** from under the **Resources** tab.

1. Select the site for which you want to enable early upgrade.

1. On the site information page, select **Edit** in the **Site Details** section.

1. Select **Enable Portal For Early Upgrade**.

    :::image type="content" source="media/power-platform-admin-center/early-upgrade.png" alt-text="Enable early upgrade.":::

> [!NOTE]
> You can enable or disable a website for early upgrade anytime. However, a snapshot is taken for all websites marked for early access two days before any release, and any website marked for early access after that is not guaranteed to get an early upgrade.

If you encounter any issue during the early upgrade phase, you can report it through Microsoft support.

### See also

- [Update Power Pages solution](update-solution.md) 
- [Administer Power Platform](/power-platform/admin/admin-documentation) 
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)


