---
title: "Tutorial: Set up page permissions"
description: Learn how to allow or restrict access to your pages in your site.
author: ankitavish
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 10/17/2022
ms.subservice:
ms.author: avishwakarma
ms.reviewer: ndoelman
contributors:
    - ankitavish
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Set up page permissions 

When we create our sites, we may want to protect pages to specific audience or users.

In this tutorial, we're going to learn how to hide or show a page based on the authenticated user web role.

> [!div class="checklist"]
> * Create page permissions
> * Assign to the authenticated web role
> * Observe how a page and related menu item is hidden or shown based on the signed-in user

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
- Complete the [Display data securely on pages](tutorial-display-data-securely.md) tutorial.

## Create page permissions

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Choose your site and select **Edit**. 

1. From the page navigation, locate the webpage that you would like to configure Page permissions.

1. Select the ellipses **...** to the right of the page. Select **Page settings**.

1. From the modal window, select **Permissions** from the side tab.

1. You will see two options for page permissions;
    - Anyone can see this page. (default)
    - I want to see who can view this page.

1. Select **I want to see who can view this page**. From the drop down, select the **Authenticated User** [web role](../security/create-web-roles.md).

    :::image type="content" source="media/tutorial-page-permissions/page-settings.png" alt-text="Page settings.":::

1. Select **OK**.

## Observe results

1. From the design studio, select **Preview** to view the site.

1. With no user signed-in, observe that the web page that was protected doesn't appear in the main menu or navigation.

    :::image type="content" source="media/tutorial/page-permissions-no-view.png" alt-text="No visibility because page is protected.":::

1. Sign-in to the site. (You can use **Azure AD** for purposes of this tutorial)

1. You should now see the page link appear in the main menu you should be able to view the page.

    :::image type="content" source="media/tutorial/page-permissions-view.png" alt-text="Page available because of user has access.":::

Page permissions will allow you to specify which users or which roles have access to a specific webpage. Use [table permissions](../security/assign-table-permissions.md) to configure access to Microsoft Dataverse data.

