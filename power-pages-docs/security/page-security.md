---
title: Page permissions in Power Pages
description: Learn how to secure your webpages by using page permissions.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 09/12/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Page permissions in Power Pages

Makers control user access to site webpages using page permissions. Settings can be adjusted to make content available anonymously for public access, or to restrict access to users who have specific roles. Depending on your business requirements, you can manage the inheritance of page permissions from a parent page to a child page. A page can have child [web files](/power-apps/maker/portals/configure/web-files), such as downloadable documents, CSS files, or JS files.  The inheritance of page permissions from the page to these child web files is also variable based on the settings a maker chooses.

You can manage page permissions in two ways:

- In Power Pages design studio
- In the Portals Management app

Power Pages design studio makes configuration of webpage access permissions simpler than the Portals Management app. For this reason, it's the recommended method for managing page permissions in Power Pages. 

## Manage page permissions in Power Pages design studio

>[!IMPORTANT]
> Managing page permissions with design studio only applies to [Restrict Read](/power-apps/maker/portals/configure/webpage-access-control#restrict-read) permissions, which control access to pages by users. To manage [Grant Change](/power-apps/maker/portals/configure/webpage-access-control#grant-change) permissions for managing and publishing content pages with the legacy site content editor, use the [Portals Management app](/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-using-portal-management-app).

Use design studio to customize your site and manage page permissions quickly and efficiently.

1. From the list of sites in Power Pages, select **Edit** to open [design studio](../getting-started/first-page.md).

    IMAGE GOES HERE

1. Select the ellipses next to the page you want to manage permissions for and choose **Page Settings**.

    IMAGE GOES HERE

1. Select the **Permissions** tab.

    IMAGE GOES HERE

>[!NOTE]
> The options under **Permissions** vary depending on the page you've selected. For example, the options for a parent page will be different from the options for the child page that inherited permissions from the parent page. Review the options for page permissions and options for child page permissions.

## Manage page permissions in the Portals Management app

Managing page permissions with the Portals Management app is accomplished by setting *webpage access control rules*. You can also set these rules using design studio, the Portals Management app must be used to manage page permissions for other areas.  More information: [Portals Management app](/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-using-portal-management-app) 

## Setting options for page permissions

Let's review the different options for managing permissions for a page.


|Option|Description  |
|---------|---------|
|Page available to anyone|A page with **Page available to anyone** selected is public on the web and available to anyone. This option is available on the root page of a website, or a child page that has the parent page with this option set to **On**.<br /><br />When **Page available to everyone** is **Off**, a lock icon appears next to it in the list of pages to signify that the page has restrictions.
|Anonymous Users role|Any role with the **Anonymous users role** set to **Yes** is excluded from the list of roles that you can select for restricting access to a page.<br /><br />When using this permission setting in the Portals Management app, an alert may appear.<br /><br />More information: [Anonymous users role alert](#anonymous-users-role-alert)|
|Permissions apply to child files|When **Permissions apply to child files** is set to **On**, the child [web files](/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage.<br /><br />Web files such as Bootstrap.min.css and Theme.css used by themes are under the home page.  If you restrict these files to only authenticated users, styles won't be applied to any pages, including the sign-in pages that are available anonymously.<br /><br />When **Permissions apply to child files** is set to **Off**, everyone can access the child web files of the selected page.<br /><br />More information: [Permissions apply to child files troubleshooting](#permissions-apply-to-child-files-troubleshooting)|
|Restriction in page hierarchy|| 

### Child page permissions

A child page can inherit permissions from the parent page, or it can be configured with unique permissions.  Let's review the different options for managing permissions for child pages.

|Option|Description|
|---------|---------|
|Inherit permissions from a parent page|The **Inherit parent from the parent page** option for a page will display when a child page is selected that has the parent page with **Page available to everyone** set to **Off**.<br /><br />By default, every child page has **Inherit parent page permissions** set to **On**. This setting makes the child page available to all the users who can access its parent page.<br /><br />When a child page has **Inherit parent page permissions** set to **Off**, the child page—and the pages that this child page is a parent of—aren't available to the users from the selected roles for the parent page access|
|Configure child page with unique permissions|Use this setting to select specific roles that you want to allow to access this child page and the pages that this child page is a parent of.|
|Permissions apply to child files|When **Permissions apply to child files** is set to **On**, the child [web files](/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage.<br /><br />When **Permissions apply to child files** is set to **Off**, everyone can access the child web files of the selected page.|

### Page hierarchy changes and inheritance

A page can be promoted to a higher level in the page hierarchy, or made a subpage to a lower level in page hierarchy. The effects these actions have on permissions are as follows:

- If a page is made a subpage, the page inherits permissions from its new parent. 

- If a page is promoted, the original permissions of the page are retained.

## Troubleshooting page permissions

Makers may encounter difficulties based on the permissions they select due to the unforeseen effects of their choices.  Let's review some of these commonly encountered difficulties.

### Anonymous users role alert

If the Portals Management app was used to configure this role for the selected page, an alert is shown for the applicable role when you manage the page permissions. 

IMAGE GOES HERE

If this alert appears, change the permissions. Roles with **Anonymous Users Role** set to **Yes** can't be assigned directly to users.

### Multiple page permissions error message

If multiple permissions are active for same page in the Portal Management app, makers will see the following error. 

IMAGE GOES HERE

You can fix this error by deactivating the permissions not required for the page and keeping only one active permission for one webpage.

### Permissions apply to child files troubleshooting

Makers may encounter one of several difficulties when working with the **Permissions apply to child files** setting. Let's review these specific difficulties.

#### Error message

When **Permissions apply to child files** is changed so that child permission no longer inherits it from parent, makers will see the following error with invalid web roles highlighted. 

IMAGE GOES HERE

You can use this information to adjust your permissions and resolve the error. 

#### Styles not applied after adjusting page permissions

Ensure that **Permissions apply to child files** is set to **Off** for the home page of the site so that styles remain intact.

IMAGE GOES HERE




