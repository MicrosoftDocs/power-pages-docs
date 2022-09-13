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

1. Go to Power Pages.

    IMAGE GOES HERE

1. From list of sites, select **Edit** to open design studio.

    IMAGE GOES HERE

1. Select the ellipses next page that you want to manage permissions for and choose **Page Settings**.

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
|Allow anonymous access to a page|A page with **Anyone can see this page**  selected is available anonymously. This option is available on the root page of a website, or a child page that has the parent page with this option set to **On**.|
|Restrict access to a page|When **Page available to everyone** is set to **Off**, the page isn't available to anyone by default. You can select specific roles that you want to allow access to this page.<br /><br />|
|Anonymous Users role|Any role with the [Anonymous Users role](/power-apps/maker/portals/configure/create-web-roles#attributes-and-relationships) set to **Yes** is excluded from the list of roles that you can select for restricting access to a page.<br /><br />
|Permissions apply to child files|When **Permissions apply to child files** is set to **On**, the child [web files](/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage. When set to **Off**, everyone can access the child web files of the selected page.|
|Restriction in page hierarchy|When a page is set to **Off** for **Page available to everyone**, a lock icon appears next to it in the list of pages to signify that the page has restrictions.| 

## Setting options for child page permissions

A child page can inherit permissions from the parent page, or it can be configured with unique permissions.  Let's review the different options for managing permissions for child pages.

|Option|Description|
|---------|---------|
|Inherit permissions from a parent page|**Permissions** section shows **Inherit parent from the parent page** when a child page is selected that has the parent page with **Page available to everyone** set to **Off**.<br /><br />By default, every child page has **Inherit parent page permissions** set to **On**. This setting makes the child page available to all the users who can access its parent page.|
|Configure child page with unique permissions|When a child page has **Inherit parent page permissions** set to **Off**, the child page—and the pages that this child page is a parent of—aren't available to the users from the selected roles for the parent page access.<br /><br />Select specific roles that you want to allow to access this child page and the pages that this child page is a parent of.|
|Child page permissions apply to child files|When **Permissions apply to child files** is set to **On**, the child [web files](/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage. When set to **Off**, everyone can access the child web files of the selected page.|

### Hierarchy changes and inheritance

A page can be promoted to a higher level in the page hierarchy, or made a subpage to a lower level in page hierarchy. The effects these actions have on permissions are as follows:

- If a page is made a subpage, the page inherits permissions from its new parent. 

- If a page is promoted, the original permissions of the page are retained.

## Troubleshooting page permissions

Makers may encounter difficulties based on the permissions they select due to unforeseen effects of their choices.  Let's review some of these commonly encountered difficulties.

### Alert displayed when selecting anonymous users role

If the Portals Management app was used to configure this role for the selected page, an alert is shown for the applicable role when you manage the page permissions. If this alert appears, change the permissions, because roles with **Anonymous Users Role** set to **Yes** can't be assigned directly to users.

### Styles not applied when selecting permissions apply to child pages

When using the **Permissions apply to child pages** setting, **Permissions apply to child files** must be set to **Off** for the home page of the site.  Web files such as Bootstrap.min.css and Theme.css used by themes are under the home page.  If you restrict these files to only authenticated users, styles won't be applied to any pages, including the sign-in pages that are available anonymously.

### Error when selecting permissions apply to child file

When **Permissions apply to child file** is changed so that child permission no longer inherits it from parent, makers will see the following error with invalid web roles highlighted. 

IMAGE GOES HERE

### Error when setting multiple page permissions

If multiple permissions are active for same page in the Portal Management app, makers will see the following error. 

IMAGE GOES HERE

You can fix this error by deactivating the permissions not required for the page and keeping only one active permission for one webpage.


