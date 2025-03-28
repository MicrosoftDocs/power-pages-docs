---
title: Manage knowledge articles by using content access levels
description: Learn how to manage knowledge articles by using content access levels in a Power Pages site.
author: murugesh1985
ms.topic: conceptual
ms.custom: 
ms.date: 4/10/2023
ms.subservice: 
ms.author: murugeshs
ms.reviewer: danamartens
contributors:
---

# Manage knowledge articles by using content access levels

Content access levels give another level of control separate from web roles to control access to knowledge articles in a Power Pages site. Content access levels make a well-designed knowledge base more capable of providing the right content to the right audience. This allows for more structured learning paths that keep irrelevant content from surfacing.

By default, three content access levels are available: Default, Registered Users, and Premium Users. The Default content access level is associated with the Anonymous Users and Authenticated Users web roles. You can create additional content access levels and associate each of them with account, contact, or web role.

When you create a new knowledge article, the Default content access level is applied to it by default. When you translate or version your knowledge articles, the associated products and content access levels are copied to the new version or translation, thereby simplifying the authoring experience. You can validate the content access levels and products associated with an article before publishing it.

Website navigation and search results consider the content access level(s) associated to the logged-in user. If the user does not have the necessary content access level permission to view a knowledge article, or if the user attempts to open an article under [faceted search conditions](/power-pages/configure/search/faceted), the Article Unavailable message is displayed.

To enable content access level based filtering of knowledge articles on your website, set the value of the **KnowledgeManagement/ContentAccessLevel/Enabled** site setting to true. By default, the value of the site setting is set to false.

## Create content access levels

1. Sign in to Power Pages and go to **Security** &gt; **Content Access Levels**.
1. In the ribbon, select **New**.
1. Fill in the **Name** and **Description**.
1. Change **Default Access Level** from **No** to **Yes** if it should be the default.
1. In the ribbon, select **Save**.

## Assign content access levels to knowledge articles

**Customer Service Hub app**

If you want to add content access level in a knowledge article from the Customer Service Hub app, you must add the **Portal Knowledge Article for Interactive experience** form to the Knowledge Article entity.

1. Open the Customer Service Hub app in App designer.

    :::image type="content" source="media/csh-app-designer.png" alt-text="Open app designer":::

1. Under **Table View**, select the **Forms** tile for the **Knowledge Article** entity.

1. In the **Components** pane, select **Portal Knowledge Article for Interactive experience**.

    :::image type="content" source="media/kb-content-access-level.png" alt-text="Add knowledge article form":::

1. Save and publish the changes.

1. Open Customer Service Hub.

1. Navigate to the knowledge article you want to assign content access level.

1. From the **Knowledge Article** box, select **Portal Knowledge Article for Interactive experience**.

    :::image type="content" source="media/kb-portal-select.png" alt-text="Select knowledge article form":::

1. On the **Summary** tab, under **Related information**, select **Content Access Levels** (lock icon) from the toolbar to add content access level.


1. From **More Commands**, select **Add Existing Content Access Level**.


1. In the **Lookup Records** pane, browse and select the content access level.

1. Select **Add**.


**Power Pages**

In Power Pages, you can access a knowledge article and add content access level to it by going to **Portals** > **Knowledge Article**.

1. Open the Power Pages app.

1. Go to **Portals** > **Knowledge Article** and open the knowledge article you want to assign content access level.

1. On the **Summary** tab, under **Related information**, select **Content Access Levels** (lock icon) from the toolbar to add content access level.

1. From **More Commands**, select **Add Existing Content Access Level**.

1. In the **Lookup Records** pane, browse and select the content access level.

1. Select **Add**.

**Interactive Service Hub**

1.  Open the Interactive Service Hub.

1.  Select the knowledge article you want to edit, or create a new article.

1.  Select **Summary** just above the progress bar.

1.  Under **Related Information** (third column), select the symbol that looks like a lock.

1.  Select **+** to add a new Content Access Level or the **Trash Can** symbol next to a Content Access Level to remove it.

## Assign content access levels to users

1. Sign in to Power Pages and go to **Portals** &gt; **Security** &gt; **Contacts**
2. Select the Contact you wish to edit.
3. Under the **Details** tab, find the **Content Access Levels** section.
4. Press **+** to add a new content access level or the **Trash Can** symbol next to a content access level to remove it.

> [!NOTE] 
> A user can also inherit a content access level if it is assigned to a Web Role, Parent Contact, or Account that the user is connected to. This inheritance avoids the need to reassign or update content access levels at an individual level. You can assign Web Roles to a content access level by navigating to **Portals** &gt; **Security** &gt; **Web Roles** and then following the same steps. You can assign accounts to a content access level by navigating to **Sales** &gt; **Accounts** and then selecting the account to edit. After the account is selected, find the **Content Access Levels** section on the rightmost side of the screen and use the **+** and **Trash Can** buttons to add or remove a content access level.
