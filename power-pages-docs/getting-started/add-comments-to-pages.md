---
title: Add comments to pages in design studio (preview)
description: Learn how to add comments to your Power Pages site.
author: GitanjaliSingh33msft
ms.topic: how-to
ms.date: 10/23/2023
ms.subservice:
ms.author: gisingh
ms.reviewer: danamartens
contributors:
    - GitanjaliSingh33msft
ms.custom:
  - sfi-image-nochange
---

# Add comments to pages in design studio (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

You can collaborate and communicate while building Power Pages sites in design studio by using comments. Comments help your team review the changes, provide feedback, and provide additional information on site customization. 

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
## Add a comment to a page

Add your comments directly to a page in the design studio from the Pages workspace.

> [!NOTE]
> Makers must have permission to edit the site before they can add comments.
1. Open the [design studio](use-design-studio.md).
1. Go to the **Pages** workspace.
1. Select the **comments** icon on the command bar to open the comments pane for the selected page. 

:::image type="content" source="media/add-comments-to-pages/comments.svg" alt-text="The Pages workspace inside design studio with commenting features emphasized.":::

Legend:

1. The comments icon in the design studio command bar. Select this icon to open the comments pane for the selected page.
1. The comments pane. Select the ellipsis (**...**) next to a comment to access options such as [edit](#edit-or-delete-a-comment), [delete](#edit-or-delete-a-comment), or [resolve](#resolve-a-comment).
1. You can also add a new comment by selecting the ellipsis (**...**) for the page you'd like to add a comment to. **New comment** appears in the menu options for the page.
1. In the design studio, anchors depict comments added to a page and let you add new comments as well.

## Edit or delete a comment

Edit your comments or remove existing comments in design studio from the comments pane.

1. Select the ellipsis (**...**) next to the comment in the comment pane.
1. Choose **Edit comment** or **Delete comment**.

## Resolve a comment

Resolve or reopen a comment thread to better track the active comments from the comments pane.

1. Select the ellipsis (**...**) next to the comment in the comment pane.
1. Choose **Resolve comment**. 

The comment thread appears as **Resolved**. To reopen, select **Reopen thread**. To delete the comment thread, select **Delete thread**.

## Tag someone in a comment

You can tag makers in a comment by using @ followed by their name.

If you tag a maker who doesn't have access to your app, you're prompted to grant the maker site edit permission.

When someone tags you in a comment, you receive an email. The email includes the name of the person who tagged you, which page you're tagged in, the comment text, and a direct link to the comment.

## Moving comments between environments

Comments in Power Pages sites can't be exported or imported as solution components because they contain user collaboration data. However, you can export the Comment table to Excel and then import the Excel file into your environment. More information: [Export data](/power-apps/maker/data-platform/data-platform-import-export#export-data)

## Known limitations

- When new comments are added to a page in design studio after sync, they are saved as empty comments. To avoid this, reload the design studio and then add the comment.
