---
title: Upgrade a Power Pages site
description: Learn how to upgrade a Power Pages site.
author: neerajnandwana-msft
ms.topic: upgrade-and-migration-article
ms.date: 10/16/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
ms.custom:
  - sfi-image-nochange
---
 
# Upgrade a Power Pages site

This section helps you understand the Power Pages release process to prepare for any new release properly and to reduce any effect on your customers. It also talks about various components that are part of your website.

A Power Pages site consists of the following components:

|Component|Description|Update process|
|---------|-----------|--------------|
|[Power Pages solutions](#solution-update)|Solutions that are installed in Microsoft Dataverse environment and contains the metadata tables for any website.|Previously, you had to manually update your solutions and packages to receive the latest features and fixes for your Power Pages sites. However, with the integration of the Dataverse Base Portal package (CDSBasePortal) into the Power Platform's automated update system (PDU), this package is updated automatically in environments where an older version is already installed. This means you no longer need to manually update the Dataverse Base Portal package. The system automatically applies updates, ensuring you have the latest improvements without any extra effort. <br>**Note:** The automatic update applies only to the Dataverse Base Portal package. Other packages, such as standard data model template packages, still require manual updates. If you're using other standard data model template packages like Community, Customer Self-Service, Employee Self-Service, Partner, or any custom templates, you need to continue updating these solutions manually.|
|[Power Pages website host](#website-host-update)|The Power Pages website host is the Azure web application that forms the actual website.|The Power Pages website host updates automatically for all sites.<br>**Note**: A new version of Power Pages website host is backwards compatible with all supported versions of Power Pages solutions. However, once a solution version becomes unsupported, the solution isn't certified to run with the new version of Power Pages website host.|
|||

## Effect of new releases on a Power Pages solution

As part of any Power Pages release, Power Pages website hosts updates automatically to the latest versions while Power Pages solutions need to be updated by customers. It's important to understand the effects of each component update on your live website, so you can plan accordingly.

### Website host update

If you're running a production version of a Power Pages site (you can see it on Power Pages sites area of the Power Platform admin center), there won't be any downtime to your live website when being updated. However, if you're running a trial version of Power Pages, there will be around 6-10 minutes of downtime and you won't be able to access your website.

### Solution update

While installing or updating any solution in your instance, you can see some instability in your instance. The Power Pages solution update process updates solutions available in your instance and will effect your instance that will in turn have an effect of your website as well. Hence, it's always advised doing solution updates in your instance during dark hours.

More details: [Update Power Pages solution](update-solution.md)

## Get notified about new releases

Every customer is notified about new Power Pages releases through Office 365 message center (in Microsoft 365 admin center). Ensure that you either have access to Office 365 message center (service administrators have access) or have discussed with your service administrator to inform you about any new Power Pages releases.

Notifications are sent around 2-5 business days ahead of the release. Notifications are sent to only those customers whose portals are planned to be updated. Each notification provides details of the type of update and the date/time it will be rolled out along with the link to release notes.

## Enable a website for new release

You can enable development or test website to receive an early upgrade ahead of all customers, so you can test all core scenarios on your test site before upgrades are rolled out to your live website. Early upgrades are rolled out at least one week before the global rollout of any release. Also, notifications for early upgrades are sent as described in the [Get notified about new releases](#get-notified-about-new-releases) section.

To enable a Power Pages website for early upgrade:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Select the **Power Pages sites** from under the **Resources** tab.

1. Select the site for which you want to enable early upgrade.

1. On the site information page, select **Edit** in the **Site Details** section.

1. Select **Enable Portal For Early Upgrade**.

    :::image type="content" source="media/power-platform-admin-center/early-upgrade.svg" alt-text="Enable early upgrade.":::

> [!NOTE]
> You can enable or disable a website for early upgrade anytime. However, a snapshot is taken for all websites marked for early access two days before any release, and any website marked for early access after that is not guaranteed to get an early upgrade.

If you encounter any issue during the early upgrade phase, you can report it through Microsoft support.

### See also

- [Update Power Pages solution](update-solution.md) 
- [Administer Power Platform](/power-platform/admin/admin-documentation) 
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)


