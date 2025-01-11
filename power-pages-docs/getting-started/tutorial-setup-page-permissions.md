---
title: "Tutorial: Set up page permissions"
description: Learn how to allow or restrict access to pages in your site in Microsoft Power Pages.
author: ankitavish
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 02/14/2023
ms.subservice:
ms.author: avishwakarma
ms.reviewer: danamartens
contributors:
    - ankitavish
---

# Tutorial: Set up page permissions

When you create your site, you may want to protect one or more pages so that only specific users or roles can view them. In this tutorial, we'll hide or show a page based on an authenticated user's web role.

> [!div class="checklist"]
>
> * Create page permissions
> * Assign to the authenticated web role
> * Observe how a page and a related menu item are hidden or shown based on the signed-in user's role

## Prerequisites

* Have an active Power Pages subscription or [start a trial](trial-signup.md).
* [Create a Power Pages site](create-manage.md).
* Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
* Complete the [Display data securely on pages](tutorial-display-data-securely.md) tutorial.

## Create page permissions

This video shows you how to restrict access to a specific webpage.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=51dd98d2-4faa-4a33-a5cc-1471bd5c165b]

The following steps outline how to configure page permissions to restrict access to a specific page.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).

1. Select your site, and then select **Edit**.

1. In the page navigation, select the ellipses **...** to the right of a page, and then select **Page settings**.

1. In the side tab, select **Permissions**.

1. Select **I want to see who can view this page**.

1. In the list, select the **Authenticated Users** [web role](../security/create-web-roles.md).

    :::image type="content" source="media/tutorial-page-permissions/page-settings.png" alt-text="Screenshot of page settings in Microsoft Power Pages.":::

1. Select **OK**.

## Observe results

1. In the design studio, select **Preview** to view your site.

1. With no user signed in, observe that the web page that you protected doesn't appear in the main menu or navigation.

    :::image type="content" source="media/tutorial-page-permissions/page-permissions-no-view.png" alt-text="Screenshot that confirms the protected page isn't visible to a user who isn't signed in.":::

1. Sign in to your site. You can use **Microsoft Entra ID** for the purposes of this tutorial.

    The link to the protected page should be visible in the main menu and you should be able to view the page.

    :::image type="content" source="media/tutorial-page-permissions/page-permissions-view.png" alt-text="Screenshot that confirms the protected page is visible because the user has signed in.":::

Page permissions allow you to specify which users or which roles have access to a specific webpage. Use [table permissions](../security/assign-table-permissions.md) to configure access to Microsoft Dataverse data.
