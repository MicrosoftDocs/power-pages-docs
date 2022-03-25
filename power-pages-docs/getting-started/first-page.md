---
title: Create your first Power Pages site
description: Learn how to create Power Pages sites.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/17/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - ndoelman
    - ProfessorKendrick
---

# Create and design pages

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

A page in Power Pages is a webpage, a document that is identified by a unique URL in a website. It is one of the core objects of the website and builds a hierarchy of the website through parent and child relationships to other webpages.

## Create a page

1. Open the [Power Apps Portals Studio](/powerapps/maker/portals/portal-designer-anatomy) to edit the content and components of the portal.

1. Ensure that the toggle for New Design Studio is on and then navigate to the pages workspace.

    :::image type="content" source="media/first-page/new-design-toggle.png" alt-text="The new design toggle within maker studio.":::

1. From the left command bar, select Pages and choose any of the **"+"** signs.

    - Clicking the components icon in the Main Navigation section will add a new page which will come up on the header of home page.

        :::image type="content" source="media/first-page/add-component.png" alt-text="The add a component menu within maker studio.":::

    - Clicking the components icon on the Other Pages will add a new page outside of the header

1. Choose a page from Standard layouts, or create a Custom layout.

    :::image type="content" source="media/first-page/add-page.png" alt-text="The add a page menu within maker studio.":::

## Manage page

1. When you have created a few pages, the page hierarchy will display in a nested structure on the Main navigation menu.

1. To change page hierarchy, select the ellipses icon on the page you would like to move, and a dialog box will appear.

    :::image type="content" source="media/first-page/subpage-2.png" alt-text="The context menu.":::

1. Select the required action from the context menu:

    | Action | Description |
    | ----------- | ----------- |
    | Move to Other Pages| Moves the page into the Other Pages. |
    | Move to Main Navigation | Shows the page in the Header of Home page. |
    | Move up | Moves the page up in the hierarchy. |
    | Move down | Moves the page down in the hierarchy. |
    | Add a new subpage | Adds a child page to the selected page. The child page inherits the page template of its parent page. |
    | Promote this subpage | Decreases the indent and makes the child page at the level of the previous page in the hierarchy. |
    | Make this a subpage | Increases the indent and makes the page a child page of the previous page in the hierarchy. |
    | Delete | Deletes the page. |