---
title: Use design studio
description: Learn about Power Pages design studio.
author: clromano
ms.topic: conceptual
ms.custom: 
ms.date: 05/26/2023
ms.author: clromano
ms.reviewer: kkendrick
contributors:
    - clromano
    - nickdoelman
    - ProfessorKendrick
---

# Use design studio

The Power Pages design studio is an intuitive interface that enables low-code makers to build and configure rich business web apps.

> [!NOTE]
> To use the design studio, you will need to be assigned the [system administrator role](/power-platform/admin/assign-security-roles) in the same Microsoft Dataverse environment as your site. 

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

    The first time you visit the site, select the **Try it for free** button to [sign up for a free, 30-day trial](trial-signup.md).

1. Locate your site in the **Active sites** list.

    - Select **Edit** to go to the [Pages workspace](first-page.md) and edit your site without writing a single line of code.
    - If you prefer, you can choose the **Edit site code** option to edit your site's code with [Visual Studio Code for the Web](../configure/visual-studio-code-editor.md#edit-code-available-in-design-studio).

    :::image type="content" source="media/tour-maker-studio/launch-design-studio.png" alt-text="Launch the design studio.":::

    If you don't have a site created yet, select **Create a site** to create your website. More information: [Create a site with Power Pages](create-manage.md)

The design studio has four marquee experiences—called *workspaces*—that focus on specific user jobs:

- **Pages workspace** empowers you to design and build webpages with in-context editing and add content with no-code and low-code widgets such as text, image, video, Power BI reports, lists, forms, and others. More information: [Pages workspace](first-page.md).

- **Styling workspace** lets you apply global site styles. You can apply corporate branding updates and review the changes in the preview on the right side of the app window. Styling offers preset themes. For each theme, you can customize the color palette, background color, font styles, button styles, and section margins. More information: [Styling workspace](style-site.md).

- **Data workspace** lets you easily model, visualize, and manage business data for the site with tables, forms, and lists. You can create and edit Dataverse tables for the site and create new or edit existing model-driven forms and views. Changes made in the Data workspace are stored in the Common data store. More information: [Data workspace](use-data-workspace.md).

- **Set up workspace** enables site administrators to configure site settings such as identity providers, security and permissions, go-live configurations, and progressive web app (PWA) settings. More information: [Set up workspace](..\configure\setup-workspace.md).

## Page editing options

While designing and building your page, you can **zoom in (+)**, **zoom out (-)**, or **Reset** the zoom to the default size of the page in the design studio, or switch to [code editor](code-editor.md).

:::image type="content" source="media/tour-maker-studio/zoom-page.png" alt-text="Toolbar to preview page layout, code editor, and zoom options.":::

## Preview your site

When you're done building, preview your site on desktop or mobile with the **Preview** option. Select **Desktop** to open the site in a new web browser tab. Scan the QR code to preview the site with your mobile device. You can also email a preview link for mobile site viewing.

:::image type="content" source="media/tour-maker-studio/preview-site.png" alt-text="The design studio GUI with preview menu options selected.":::

## Accessing the Portal Management app and sync

For advanced configurations that aren't available in the Power Pages design studio, the [Portal Management app](../configure/portal-management-app.md) is accessible from the overflow menu. Select the **ellipsis icon** from the left-hand menu to view more items, then select **Portal management**.

To reflect changes made to the site from the Portal Management app to the Power Pages design studio, select **Sync** in the upper-right corner of the design studio.

## Next steps

- [Create and manage pages](first-page.md)
- [Customize pages](customize-pages.md)
- [Style your page](style-site.md)
