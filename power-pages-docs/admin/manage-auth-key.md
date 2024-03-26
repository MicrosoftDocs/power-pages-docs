---
title: Manage website authentication key
description: Learn how to manage the authentication key used by Power Pages.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 11/09/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
    - vamseedillimsft
---

# Manage website authentication key

Power Pages connectivity architecture explained how a website connects to Microsoft Dataverse environment. When a website is created, a new authentication key is generated with the public key uploaded to Microsoft Entra application. Power Pages uses this authentication key to connect to the Dataverse environment. You must renew the key every two years to ensure that your website can connect to Dataverse environment. If the authentication key is renewed, your website isn't accessible to your end users once the authentication key expires. 

## Check authentication key details

> [!TIP]
> To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

The details of an authentication key are displayed on Power Platform admin center and the website.

**Power Platform admin center**

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Select the site for which you want to manage the website authentication key.

1. In the site details page, select **Website Authentication Key** in the **Security** section.

    :::image type="content" source="media/auth-key/manage-auth-key.png" alt-text="Manage authentication key.":::

**Website**

1. Sign in to the website with a user that is assigned the administrator [webrole](../security/create-web-roles.md).

1. Navigate to the URL `<website_path>/_services/about`. The authentication key expiration date is displayed. 

    :::image type="content" source="media/auth-key/services-page.png" alt-text="Website services page.":::

> [!NOTE]
> To view authentication key information, you must sign in to the website in the same browser session and you must have all website access permission.

## Check authentication key expiration notification

Before the authentication key expires, you receive notifications via emails, Power Platform admin center, and the website.

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
> You must sign in to your website in the same browser session, and you must be assigned all website access permission.

## Renew authentication key

Use the following steps if the authentication key for your website is near expiration.

> [!NOTE]
> To renew the key, you must have permissions to manage your website.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Select the site for which you want to manage the website authentication key.

1. In the site details page, select **Website Authentication Key** in the **Security** section.

    :::image type="content" source="media/auth-key/manage-auth-key.png" alt-text="Manage authentication key.":::

1. Select **Update key**.

1. Select **OK** in the message. The update process starts, and a message is displayed.

> [!NOTE]
> - While this process runs in the background, the website will restart.
> - When you update a key, it's valid for next two years.
> - This process will take five to seven minutes.
> - Updating authentication key doesn't change any other website configuration or the website state.

### Troubleshooting renewal of authentication key

If the key update fails, an error message is displayed along with the following action:

- **Retry Authentication Key Update**. This action allows you to restart the website authentication key update process. If the update fails multiple times, contact Microsoft support.

### See also

- [Website connectivity to a Microsoft Dataverse environment](/power-apps/maker/portals/admin/connectivity)
