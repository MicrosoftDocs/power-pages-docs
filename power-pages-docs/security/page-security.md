---
title: Page permissions in Power Pages
description: Learn how to secure your webpages by using page permissions.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 10/04/2022
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Page permissions in Power Pages

Makers control user access to site webpages using page permissions. Settings can be adjusted to make content available anonymously for public access, or to restrict access to users who have specific roles. Depending on your business requirements, you can manage the inheritance of page permissions from a parent page to a child page. A page can have child [web files](../configure/advanced-config.md#web-files), such as downloadable documents, CSS files, or JS files.  The inheritance of page permissions from the page to these child web files is also variable based on the settings a maker chooses.

You can manage page permissions in two ways:

- In Power Pages design studio
- In the Portal Management app

Power Pages design studio makes configuration of webpage access permissions simpler than the Portal Management app. For this reason, we recommended this method for managing page permissions in Power Pages.

## Manage page permissions in Power Pages design studio

>[!IMPORTANT]
> Managing page permissions with design studio only applies to [Restrict Read](/power-apps/maker/portals/configure/webpage-access-control#restrict-read) permissions, which control access to pages by users. To manage [Grant Change](/power-apps/maker/portals/configure/webpage-access-control#grant-change) permissions for managing and publishing content pages with the legacy site content editor, use the [Portal Management app](../configure/portal-management-app.md).

Use design studio to customize your site and manage page permissions quickly and efficiently.

1. From the list of sites in Power Pages, select **Edit** to open [design studio](../getting-started/first-page.md).

1. Select the ellipses next to the page you want to manage permissions for and choose **Page Settings**.

    :::image type="content" source="media/page-security/page-settings.png" alt-text="The Pages workspace with the Page settings menu option emphasized for the Home page.":::

1. Select the **Permissions** tab.

    :::image type="content" source="media/page-security/permissions.png" alt-text="The Page settings window with the Permissions option emphasized.":::

>[!NOTE]
> The options under **Permissions** vary depending on the page you've selected. For example, the options for a parent page will be different from the options for the child page that inherited permissions from the parent page. Review the options for page permissions and options for child page permissions.

## Manage page permissions in the Portal Management app

Managing page permissions with the Portal Management app is accomplished by setting webpage access control rules. You can also set these rules using design studio, the Portal Management app must be used to manage page permissions for other areas.  More information: [Manage page permissions with the Portal Management app](/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-with-the-portal-management-app) 

## Setting options for page permissions

In this section, you'll learn about the different options for managing permissions for a page.

### Anyone can see this page

This option is available on the root page of a website, or a child page that has the parent page with this setting selected. You must disable this setting to make the page available for only specific roles.

When this option is selected, the page is public on the web and available to anyone.  

When this option is not selected, a lock icon appears next to it in the list of pages to signify that the page has restrictions.

### I want to choose who can see this page

When this option is selected, you can choose who has access the page by selecting the roles from the dropdown menu.

> [!NOTE]
> Selecting **Anonymous Users** role using the Portal Management app will result in an alert. More information: [Anonymous users role alert](#anonymous-users-role-alert)

### Apply these permissions to all files inherited by this page

When this option is selected, the child [web files](../configure/advanced-config.md#web-files) of that page are only available to the users who can access this webpage.

> [!CAUTION]
> This setting can't be selected for the home page of a site. Web files such as `Bootstrap.min.css` and `Theme.css` used by themes are under the home page. If you restrict these files to only authenticated users, styles won't be applied to any pages, including the sign-in pages that are available anonymously. More information: [Permissions apply to child files troubleshooting](#permissions-apply-to-child-files-troubleshooting)

## Child page permissions

A child page can inherit permissions from the parent page, or it can be configured with unique permissions. In this section, you'll learn about the different options for managing permissions for child pages.

### Inherit permissions from a parent page

The **Inherit permissions from the parent page** option for a page will display when a child page is selected that has the parent page with **Anyone can see this page** is not selected. When this setting is enabled, the child page is available to all the users who can access its parent page.

> [!NOTE]
> By default, every child page has this option selected.

When this option is not selected, the child page (including the pages that this child page is a parent of) aren't available to the users from the selected roles for the parent page.

### Configure child page with unique permissions

Use this setting to select specific roles that you want to allow to access this child page and the pages that this child page is a parent of.

### Permissions apply to child files

When this option is selected, the child [web files](../configure/advanced-config.md#web-files) of that page are only available to the users who can access this webpage.

When this option is not selected, anyone can access the child web files of the selected page.

### Page hierarchy changes and inheritance

A page can be promoted to a higher level in the page hierarchy, or made a subpage to a lower level in page hierarchy. The effects these actions have on permissions are as follows:

- If a page is made a subpage, the page inherits permissions from its new parent. 
- If a page is promoted, the original permissions of the page are retained.

## Troubleshooting page permissions

Makers may encounter difficulties based on the permissions they select due to the unforeseen effects of their choices.  In this section, you'll learn about these commonly encountered difficulties.

### Anonymous users role alert

If you use the Portal Management app to configure **Anonymous users** role for the selected page, you'll see the following alert:

"Anonymous user role should not be assigned directly to web pages."

To fix this problem, change the permissions.

> [!NOTE]
> Roles with **Anonymous Users Role** set to **Yes** can't be assigned directly to users.

### Multiple page permissions error message

If you have multiple active permissions for the same page in the Portal Management app, you'll see the following error:

"There are multiple, conflicting access control rules applied to this page. Deactivate the extra rules so there is only one with restricted read-write access."

To fix this error, deactivate the permissions not required for the page so that only one permission is active for one webpage.

### Permissions apply to child files troubleshooting

In this section, you'll learn about common problems related to using the **Permissions apply to child files** setting.

#### Child page not inheriting permissions from parent page

If you change **Permissions apply to child files** so that the child permissions no longer inherit from their parents, you'll see the following error with invalid web roles highlighted:

"One or more roles applied to this page are not used for the parent page. This page and its subpages won't be available to those roles. Either add those roles to the parent page or delete them from this page."

To fix this problem, verify and reconfigure your permissions as required.

#### Styles not applied after adjusting page permissions

Ensure that **Permissions apply to child files** is set to **Off** for the home page of the site so that styles remain intact.

:::image type="content" source="media/page-security/inherit-permissions.png" alt-text="Inherit permissions to webfiles.":::
