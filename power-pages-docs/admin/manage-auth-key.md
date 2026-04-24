---
title: Manage website authentication key
description: Learn how to manage the authentication key used by Power Pages, including checking expiration, renewing keys, and troubleshooting renewal failures.
author: neerajnandwana-msft
ms.topic: how-to
ms.date: 04/23/2026
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - vamseedillimsft
ms.custom:
  - sfi-image-nochange
ms.collection:
  - ai-assisted
---

# Manage website authentication key

When a Power Pages site is created, a new authentication key is generated with the public key uploaded to the Microsoft Entra application. Power Pages uses this authentication key to connect to the Microsoft Dataverse environment. You must renew the key once every year to ensure that your site can connect to Dataverse. If the authentication key isn't renewed, your site stops being accessible to end users after the key expires.

## Prerequisites

Before you manage the authentication key, ensure you have:

- **System Administrator** or **System Customizer** security role, or equivalent permissions, in the Dataverse environment connected to your Power Pages site.
- Access to the [Power Platform admin center](https://aka.ms/ppac).

To learn more about the roles required for this task, see [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

## Check authentication key details

The details of an authentication key are displayed in the Power Platform admin center and on the site itself.

**Power Platform admin center**

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Select **Manage**, and then select **Power Pages**.

1. Select the site for which you want to manage the website authentication key.

1. In the site details page, select **Website Authentication Key** in the **Security** section.

**Website**

1. Sign in to the site with a user that is assigned the administrator [web role](../security/create-web-roles.md).

1. Navigate to the URL `<website_path>/_services/about`. The authentication key expiration date is displayed.

    :::image type="content" source="media/auth-key/services-page.png" alt-text="Website services page.":::

> [!NOTE]
> To view authentication key information, you must sign in to the site in the same browser session and you must have all website access permission.

## Check authentication key expiration notification

Before the authentication key expires, you receive notifications via email, the Power Platform admin center, and the site.

**Email**

Email is sent to users who signed up for email notification for the organization connected to their Power Pages site. More information about signing up for email notification: [Manage email notifications to admins](/power-platform/admin/manage-email-notifications)

Email notifications are sent at the following intervals:

- 90 days
- 60 days
- 30 days
- 15 days
- Seven days
- Six days
- Five days
- Four days
- Three days
- Two days
- One day
- 12 hours
- Six hours
- Three hours

You'll also be notified after the key expires every day until one week after key expiration.

> [!NOTE]
> - Intervals are calculated in UTC from the key expiration date.
> - Email is not guaranteed to be exactly at the intervals as listed. Email notification can be delayed or missed. Be sure to check for the key expiration date online as well.

**Power Platform admin center**

A message about key expiration is displayed at the top of the page.

### Website

When you navigate to the URL `<website_path>/_services/about`, a notification about key expiration is displayed at the bottom of the page.

> [!NOTE]
> You must sign in to your site in the same browser session, and you must be assigned all website access permission.

## Renew authentication key

Use the following steps when the authentication key for your site is near expiration.

> [!IMPORTANT]
> To renew the key, you must have the **System Administrator** or **System Customizer** security role, or equivalent permissions, for the Dataverse environment connected to your Power Pages site.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Select **Manage**, and then select **Power Pages**.

1. Select the site for which you want to manage the website authentication key.

1. In the site details page, select **Website Authentication Key** in the **Security** section.

    :::image type="content" source="media/auth-key/manage-auth-key.svg" alt-text="Manage authentication key.":::

1. Select **Update key**.

1. Select **OK** in the message. The update process starts, and a message is displayed.

> [!NOTE]
> - While this process runs in the background, the website will restart.
> - When you update a key, it's valid for the next one year.
> - This process will take five to seven minutes.
> - Updating authentication key doesn't change any other website configuration or the website state.

### Troubleshooting renewal of authentication key

If the key update fails, an error message is displayed along with the following action:

- **Retry Authentication Key Update**. This action allows you to restart the website authentication key update process. If the update fails multiple times, contact Microsoft support.

> [!TIP]
> If your site becomes inaccessible after the authentication key expires, renew the key by following the steps in [Renew authentication key](#renew-authentication-key). The site restarts automatically after the key is updated. If the site remains inaccessible after key renewal, [contact Microsoft support](/power-platform/admin/get-help-support).

### See also

- [Website connectivity to a Microsoft Dataverse environment](/power-apps/maker/portals/admin/connectivity)
- [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles)
- [Power Pages lifecycle](lifecycle.md)
