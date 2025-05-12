---
title: Site Checker startup issues
description: Learn about Site Checker diagnostics results for startup issues.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 04/05/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - dileepsinghmicrosoft
---

# Site Checker startup issues

In this article, you'll learn about Site Checker diagnostics results related to startup issues, and how to resolve common issues or problems.

## Website doesn't load and displays server error

This issue can be caused by several different reasons, such as when a website isn't able to connect to the underlying Dataverse environment, the Dataverse environment doesn't exist or its URL has changed, or when a request to the Dataverse environment has timed out. When you run the Site Checker tool, it tries to determine the exact reason and point you to the correct mitigation. 

Below is a list of common causes for this error and their corresponding mitigation steps.

### URL of the connected Microsoft Dataverse environment has changed 

This happens when the URL of the Dataverse environment is changed by a user after a website is provisioned against the organization. To fix this issue, update the Dynamics 365 URL:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Page sites**.

1. Select the website.

1. When the website details page appears, select the ellipse (**...**) to the right of the **Site Actions** menu item and choose **Update Dynamics 365 URL**.

Once this action is successfully completed, your Dataverse environment URL is updated, and your website will start working.

### Microsoft Dataverse environment connected to your website is in administration mode

This issue occurs when the Dataverse environment is put in administration mode either when changing the organization from production to sandbox mode or manually by an organization administrator.

If this is the cause, you can disable administration mode by following the steps listed [here](/power-platform/admin/admin-mode#set-administration-mode). Once administration mode is disabled, your website should work.

### Authentication connection between Dataverse environment and website is broken

This issue occurs when the authentication connection between the Power Platform organization and the website is broken because the Dataverse environment was either restored from a backup or was deleted and re-created from a backup. To fix this issue:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under the **Resources** section, select **Power Pages sites**.

1. Select your website.

1. When the site page opens, from the main menu, select **Shut down this site**. On the prompt, select **Stop**.

1. From the main menu, select **Start this site**. On the prompt, select **Start**.

Once these steps are completed, the website restarts and can now make an authentication connection.

In certain situations, especially if the organization ID changes after the restore operation (or if you reprovisioned the organization), these mitigation steps won't work. In these situations, you can reset and reprovision the website against the same instance. For information on how to reset a portal, see [Reset a website](/power-apps/maker/portals/admin/reset-portal).

### Request to Microsoft Dataverse environment has timed out

This issue can occur if the API request to your Dataverse environment has timed out. This issue should automatically mitigate itself once the API request starts working. You can also try restarting the website:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under the **Resources** section, select **Power Pages sites**.

1. Select the your website.

1. When site details page appears, select **Site Actions** from main menu and select **Restart site**.

If restarting the website doesn't work and the issue continues for a long period of time, contact Microsoft Support for help.

### Website binding not found

This issue occurs when the website binding records for the website are deleted from the underlying Dataverse environment and the website isn't able to create binding automatically. To fix this issue:

1. Open the [Portal Management app](../configure/portal-management-app.md).
1. Go to **Website** > **Website Bindings**.
1. Delete all the website binding records that are pointing to your portal. The **Sitename** field helps you to identify the website binding records for your portal.
1. Restart the website.

Once you complete these steps, your website will restart, and should re-create website binding records automatically.

There are situations in which the website won't be able to re-create website binding records automatically, such as when the GUID of the website record available in your instance is different than the one created during default installation of your website. In this situation, do the following:

1. Delete all website binding records related to your website.
1. Create a website binding record manually with the following values:

      - **Name**: This can be any string.
      - **Website**: Select the website record that you want to be rendered on your portal.
      - **Sitename**: Type in the host name of your website (portal URL without `https://` in the beginning). If your website is using a custom domain name, use that custom domain name here.
      - Leave all other fields blank.
1. Once the website binding record is re-created, restart your website from the Power Platform admin center.

### An unexpected error has occurred while trying to connect to your Microsoft Dataverse environment

This situation can arise because of some unexpected issue. To mitigate this situation, try reprovisioning the website. First, delete the website host, see [Delete a website](delete-website.md). Do not delete the website configuration. Re-create the website using the existing website data. You will need to reconfigure items such as custom domain names and other integrations.

If a reprovision doesn't solves the issue, contact Microsoft Support for help.

#### See also

[Run Site Checker](site-checker.md)


