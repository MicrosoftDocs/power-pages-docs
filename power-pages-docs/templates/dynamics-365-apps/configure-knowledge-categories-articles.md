---
title: Configure and manage category for knowledge articles
description: Learn how to create and manage a category for knowledge articles.
author: murugesh1985
ms.topic: conceptual
ms.custom: 
ms.date: 04/10/2023
ms.subservice: 
ms.author: murugeshs
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
---

# Configure and manage category for knowledge articles

This section helps you understand how to create a new category for knowledge articles and associate it with an article. You'll also learn how to enable ratings for a knowledge article.

## Create a new category for knowledge articles

1. Sign in to Power Pages.

2. Go to **Settings** > **Service Management**. 

3. In the **Knowledge Base Management** section, select **Categories**. 

4. Select **New**. 

5. Enter a name and description for your category. 

6. Choose a parent category. If you want this category to be a top-level category, leave this field blank.

## Associate a category with a knowledge article

1. In Customer Service Hub, go to **Service** > **Knowledge Articles**.

2. Open a knowledge article.

3. On the command bar, select **Associate Category**. The Associate Category window appears.

4. In the **Select Category to Associate with** field, select the category you want to associate to the article. And then, select **Associate**.

    :::image type="content" source="media/kb-associate-category.png" alt-text="Associate a category to a knowledge article":::

> [!NOTE]
> You can also add related articles, related products, and keywords to a knowledge article. For more information on managing knowledge articles, see [Create and manage knowledge articles](/dynamics365/customer-service/customer-service-hub-user-guide-knowledge-article).

## Remove a category from an article

1. In Customer Service Hub, open the knowledge article from which you want to remove a category.

2. On the **Summary** tab, under **Related information**, select **Related Categories**.

    :::image type="content" source="media/kb-related-categories.png" alt-text="View associate categories to a knowledge article":::

3. Select the category you want to remove.

4. From **More Commands**, select **Remove**.

    :::image type="content" source="media/kb-remove-category.png" alt-text="Delete an associated category from a knowledge article":::

## Delete a knowledge category

1. Sign in to Power Pages.

2. Go to **Settings** > **Service Management**. 

3. In the **Knowledge Base Management** section, select **Categories**. 

4. Choose the category from the list view, and then select **Delete** on the command bar.

>[!NOTE] 
> Knowledge articles associated with the category will be disassociated after the category is deleted.

## Enable ratings for a knowledge article

1. Sign in to the website and go to knowledge article.

2. Edit the article from the inline editor.

3. On the **Options** tab, select **Enable Ratings**.

## Expand and collapse sections

You can add sections that can be expanded and collapsed by adding a **collapsible section** using the *collapsible command button*:

:::image type="content" source="media/collapsible-button.png" alt-text="Collapsible button control":::

You can see the following example with one section expanded and the rest in collapsed positions:

:::image type="content" source="media/collapsible-example.png" alt-text="Example of expandable and collapsible sections":::

Following considerations apply when using collapsible sections:

- Default state of a collapsible section is collapsed.
- Existing web page and web templates can work with collapsible sections without any additional changes.
- If you select **Print**, the state of the sections from current selections persist for print preview.
- The collapsible sections, when added to your articles, have additional JS function and CSS style for the expand/collapse button.

### Customize expand and collapse behavior

You can customize the default CSS and JS files and create additional customization. The default CSS file name is `collapsible.css` and JavaScript file name is `collapsible.js`.

The following example shows a [web template](/power-pages/configure/web-templates) using default JavaScript and CSS files. Update the file name and location for the web template to your customized JavaScript and CSS files:

:::image type="content" source="media/web-template.png" alt-text="Web template":::

### See also
- [Get started with the content editor](/power-apps/maker/portals/portal-content-editor)