---
title: Using the Set up workspace
description: Learn how to use the Set up workspace.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/14/2023
ms.subservice:
ms.author: nenandw
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Overview of the Power Pages Set up workspace

You use the **Set up** workspace to configure key aspects of your Power Pages site.

:::image type="content" source="media/setup-workspace/setup-workspace.png" alt-text="Setup workspace from within design studio.":::

## General

The general section allows you to configure site-specific details, and the checklist that helps prepare for the site to go live.

### Site details

The **Site details** section shows the following site details:

- **Name** - editable field for the name of the site that helps you identify the site among all other sites that you work on.
- **Owner** - name of the owner of the site.
- **Created on** - when the site was created.
- **Modified on** - when the site was last modified.
- **Type** - shows whether the site is in trial or production. When in trial, you can also select **Convert** to convert the site into production.
- **Language** - the language of the site.
- **URL** - the URL to access the site.
- **Application ID** - a unique ID that helps differentiate the current app from all other apps. To copy the Application ID, select the copy icon.
- **Early Upgrade** - enable or disable early upgrade for this site to access newly launched features earlier.
- **Admin actions** - takes you to the admin center for site admin actions such as adding a custom domain, enable/disable CDN, or set up IP restrictions.

You can also **Run Site Checker**. More information: [Run Site Checker](../admin/site-checker.md)

### Go-live checklist

Go-live checklist includes interactive tasks that guide you to review and complete the recommended actions. This interactive experience includes running the site checker, and configuring several other settings for the site that help you prepare the site before the general roll out. For more information, go to [Go-live checklist](../go-live/checklist.md)

## Authentication

Use **Identity providers** section to configure various authentication providers to allow access to protected pages and data. For more information, go to [Configure Power Pages site authentication](../security/authentication/configure-site.md).

## Security

Security section allows you to configure permissions for tables used by your site, and change the site's visibility settings to make the site public or keep private.

### Table permissions

You can configure table permissions on Dataverse tables used in your Power Pages site. For more information, go to [Configure table permissions](../security/table-permissions.md).

### Site visibility

Site visibility section enables you to manage who has access to your website. All new sites created in Power Pages are **private** by default. Only makers or people in the organization granted permission by makers will have website access, making your site secure. For more information, go to [Site visibility](../security/site-visibility.md)

## Mobile

You'll be able to configure progressive web apps (PWAs) using Power Pages. For more information, go to [Progressive Web Applications](progressive-web-apps.md)

## Administration

The Administration section is where you can access the Power Pages admin center.
