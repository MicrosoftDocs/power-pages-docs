---
title: "Tutorial: Setup page permissions"
description: Learn how to allow or restrict access to your pages in your site.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 04/21/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Setup page permissions 

In this tutorial, you learn how to:

> [!div class="checklist"]
> Hide or show an entire page based on the user's log in credentials.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

## Set page permissions

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. In the **design studio**, choose **...** and then select **portal management**.
1. Locate the **Web Page Access Controls Rules** in the Security section.
1. Select **New**.
    - Enter a descriptive name.
    - Choose the website.
    - Choose the web page.
    - Set **Right** to **Restrict Read**.
    - Select **Save**.
1. Navigate to the **Web Roles** tab.
    - Select **Add Existing Web Role**.
    - Choose the **Authenticated Users** role.
    - Close the portal management app.
1. Return to the **design studio** and view your site.  The page no longer appears in the menu.
1. Choose **Sign In**.  You can now navigate to the hidden page.

## Next steps

Advance to the next article to learn how to add a form to a page to create, read and edit Dataverse information.
> [!div class="nextstepaction"]
> [Next steps](tutorial-add-form-to-page.md)

