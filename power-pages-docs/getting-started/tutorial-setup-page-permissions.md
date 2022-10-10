---
title: "Tutorial: Set up page permissions"
description: Learn how to allow or restrict access to your pages in your site.
author: ankitavish
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 10/10/2022
ms.subservice:
ms.author: avishwakarma
ms.reviewer: ndoelman
contributors:
    - ankitavish
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Set up page permissions 

> [!IMPORTANT]
> We are in the process of updating our tutorials. The steps below do not reflect the latest features available to configure page permissions. Please refer to our [feature documentation](../security/page-security.md) to see the latest information.

When we create our sites, we may want to protect pages to specific audience or users.

In this tutorial, we're going to learn how to hide or show a page based on the web role assigned to the signed-in user.

> [!div class="checklist"]
> * Create page permissions
> * Assign to a web role
> * Observe how a page and related menu item is hidden or shown based on the signed-in user

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- Complete the [Add and design a page](tutorial-add-webpage.md) tutorial.
- Complete the [Display data securely on pages](tutorial-display-data-securely.md) tutorial.

## Create page permissions

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Choose your site and select **Edit**. 

1. In the design studio, select the ellipses **...** from the side menu and select **Portal Management** to open the Portal Management app.

1. In the Portals Management app, under the **Security** section, select and view **Web Page Access Permissions**.

1. Select **New** from the command bar.

1. Create the page permission record with the following values:

    | Property | Value |
    | - | - |
    | Name | Any descriptive name. |
    | Website | The web site where the pages exist that are to be protected. |
    | Web Page | The page you want to protect |
    | Right | Restrict Read. This means that contacts related to the associated web role will be restricted to reading the page. Other users will have full restrictions and not be able to view the page at all. |
    | Access Type | All content (Meaning all child pages will be protected as well.) |
    | Description | A description of the page permission. |
    
    :::image type="content" source="media/tutorial/page-permission-setup.png" alt-text="Create web role.":::

1. Select the **Web Roles** tab and choose the **Authenticated Users** web role.

1. Close the Portal Management app.

## Observe results

1. From the design studio, select **Preview** to view the site.

1. With no user signed-in, observe that the web page that was protected doesn't appear in the main menu or navigation.

    :::image type="content" source="media/tutorial/page-permissions-no-view.png" alt-text="No visibility because page is protected.":::

1. Sign-in to the site. (You can use **Azure AD** for purposes of this tutorial)

1. You should now see the page link appear in the main menu you should be able to view the page.

    :::image type="content" source="media/tutorial/page-permissions-view.png" alt-text="Page available because of user has access.":::

## Next steps

Advance to the next article to learn how to upload your own custom CSS file to your site.
> [!div class="nextstepaction"]
> [Add custom styling to your site](tutorial-add-custom-style.md)

