---
title: Use design studio
description: Learn about Power Pages design studio.
author: clromano
ms.topic: conceptual
ms.custom: 
ms.date: 09/13/2022
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

    The first time you visit the site, you'll be presented with a **Get started** button and be able to [sign up for a free, 30-day trial](trial-signup.md).

1. Select your site, and select **Edit** to launch the design studio.

    :::image type="content" source="media/tour-maker-studio/launch-design-studio.png" alt-text="Launch the design studio.":::

1. If you don't have a site created, select **Create a site** to create your website.

The design studio has four marquee experiences—called *workspaces*—that focus on specific user jobs:

- **Pages workspace** enables you to design and build webpages with in-context editing and add content with no-code and low-code widgets such as text, image, video, Power BI reports, lists, forms, and others. [Learn more about the Pages workspace](first-page.md).

- **Styling workspace** lets you apply global site styles. You can apply corporate branding updates, and review the changes in the preview on the right side of the app window. Styling offers 13 preset themes. For each theme, you can customize the color palette, background color, font styles, button styles, and section margins. [Learn more about the Styling workspace](style-site.md).

- **Data workspace** lets you easily model, visualize, and manage business data for the site with tables, forms, and lists. You can create and edit Dataverse tables for the site and create new or edit existing model-driven forms and views. Changes made in the Data workspace are stored in the Common data store. [Learn more about the Data workspace](use-data-workspace.md).

- **Set up workspace** enables site administrators to configure site settings such as identity providers, security and permissions, go-live configurations, and progressive web app (PWA) settings. [Learn more about the Set up workspace](..\configure\setup-workspace.md).

## Page editing options

While working on designing and building your page, you can switch to the [code editor](code-editor.md), **zoom in (+)**,  **zoom out (-)**, or **Reset** the zoom to the default size of the page in the design studio.

:::image type="content" source="media/tour-maker-studio/zoom-page.png" alt-text="Toolbar to preview page layout, code editor and zoom options.":::

## Preview your site

When you're done building, preview your site on desktop or mobile by using the **Preview** option. Selecting **Desktop** opens the site in a new web browser tab. Scanning the QR code with your mobile device opens the site on the mobile web browser.

:::image type="content" source="media/tour-maker-studio/preview-site.png" alt-text="The design studio GUI with preview menu options selected.":::

## Accessing the Portal Management app and sync

For advanced configurations that aren't available in the Power Pages design studio, the [Portal Management app](../configure/portal-management-app.md) is accessible from the overflow menu.

:::image type="content" source="media/tour-maker-studio/portal-management-app.png" alt-text="The design studio GUI with the overflow menu selected.":::

To reflect changes made to the site from the Portal Management app to the Power Pages design studio, select **Sync** in the upper-right corner of the screen.

:::image type="content" source="media/tour-maker-studio/sync.png" alt-text="The design studio GUI with the sync button emphasized.":::

## Next steps

[Create and manage pages](first-page.md)<br>
[Customize pages](customize-pages.md)<br>
[Style your page](style-site.md)
