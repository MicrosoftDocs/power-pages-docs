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

# Manage Page Permissions in Power Pages

Page permissions allow you to control user access to site webpages. You can allow pages to be available anonymously for public access, or restrict access to users who have specific roles. Depending on your business requirements, you can manage the inheritance of page permissions from a parent page to a child page. A page can have child [<u>web files</u>](/power-apps/maker/portals/configure/web-files)—such as downloadable documents, CSS files, or JS files—and you can also manage the inheritance of page permissions from the page to such child web files.

You can manage page permissions in two ways:

-   [<u>Power pages design Studio</u>](/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-using-portals-studio) *can point to new documentation*

-   [<u>Site Management app</u>](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-using-portal-management-app) (*can point to existing PMA documentation)*

Power pages design studio simplifies the configuration of webpage access permissions compared to using the Site Management app, and is the recommended method. Managing page permissions with the Site Management app is accomplished by setting *webpage access control rules*. You can also set these webpage access control rules by using design Studio, but you must use the Site Management app to manage page permissions for other areas that can't be managed using design Studio.

** Note**

Managing page permissions with design Studio applies only to [**<u>Restrict Read</u>**](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/webpage-access-control#restrict-read) permissions, which control access to pages by users. To manage [**<u>Grant Change</u>**](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/webpage-access-control#grant-change) permissions for managing and publishing content pages with the legacy site content editor, use the [**<u>Site Management app</u>**](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/webpage-access-control#manage-page-permissions-using-portal-management-app).

## Manage page permissions with Power Pages design studio

Use design studio to customize your site and manage page permissions quickly and efficiently.

**To get started with managing page permissions using design Studio**

1.  Go to Power Pages

2.  From list of sites, select **Edit** to open design studio

3.  Select the 3 dotes next page that you want to manage permissions for and choose 'Page settings'

4.  On the dialogue select **Permissions** tab

The options under **Permissions** vary depending on the page you've selected. For example, the options for a parent page will be different from the options for the child page that inherited permissions from the parent page.

Let's look at different options for managing permissions for a page.

### Allow anonymous access to a page

A page with **Anyone can see this page**  is selected is available anonymously. This option is available on the root page of a website, or a child page that has the parent page with this option set to **On**.

### Restrict access to a page

When **Page available to everyone** is set to **Off**, the page isn't available to anyone by default. You can select specific roles that you want to allow access to this page.

Select **roles** from drop-down to choose which roles will be allowed to access the page. Only users from the roles you select here will have access.

### Anonymous Users role

**Fwd link for this section shared by Nick -** <https://go.microsoft.com/fwlink/?linkid=2207019>

Any role with the [**Anonymous Users**<u> role</u>](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/create-web-roles#attributes-and-relationships) set to **Yes** is excluded from the list of roles that you can select for restricting access to a page.

If the Site Management app was used to configure this role for the selected page, an alert is shown for the applicable role when you manage the page permissions.

&lt;Ankita to update screenshot&gt;

If this alert appears, change the permissions, because roles with **Anonymous Users Role** set to **Yes** can't be assigned directly to users.

### Permissions apply to child files

When **Permissions apply to child files** is set to **On**, the child [<u>web files</u>](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage. When set to **Off**, everyone can access the child web files of the selected page.


** Caution**

**Permissions apply to child files** must be set to **Off** for the home page for the site. Web files such as Bootstrap.min.css and Theme.css used by themes are under the home page. If you restrict these files to only authenticated users, styles won't be applied to any pages, including the sign-in pages that are available anonymously.

**Restriction in page hierarchy**

When a page is set to **Off** for **Page available to everyone**, a lock icon appears next to it in the list of pages to signify that the page has restrictions.


## Child page permissions

A child page can inherit permissions from the parent page, or it can be configured with unique permissions.

**Inherit permissions from a parent page**

**Permissions** section shows **Inherit parent from the &lt;parent&gt; page** when a child page is selected that has the parent page with **Page available to everyone** set to **Off**.

By default, every child page has **Inherit parent page permissions** set to **On**. This setting makes the child page available to all the users who can access its parent page.

**Configure child page with unique permissions**

When a child page has **Inherit parent page permissions** set to **Off**, the child page—and the pages that this child page is a parent of—aren't available to the users from the selected roles for the parent page access.

Select specific roles that you want to allow to access this child page and the pages that this child page is a parent of.

**Child page permissions apply to child files**

When **Permissions apply to child files** is set to **On**, the child [<u>web files</u>](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/web-files) of that page are only available to the users who can access this webpage. When set to **Off**, everyone can access the child web files of the selected page.

**The effect of subpage changes on permissions**

A page can be promoted to a higher level in the page hierarchy, or made a subpage to a lower level in page hierarchy. The effects these actions have on permissions are as follows:

-   If a page is made a subpage, the page inherits permissions from its new parent. &lt;Ankita to update screenshot with new dialogue text changes&gt;

-   If a page is promoted, the original permissions of the page are retained.

**The effect of parent permissions change on child page permissions**

**Fwd link for this section shared by Nick -** <https://go.microsoft.com/fwlink/?linkid=2205442>

When **Permissions of Parent** page is changed so that child permission no longer inherits it from parent. The maker will see the following error. The web roles which aren't valid will be highlighted.

**The effect of multiple page permissions**

**Fwd link for this section shared by Nick -** <https://go.microsoft.com/fwlink/?linkid=2206118>

When using Portal management app, there are multiple permissions active for same page. The maker will see the following error. The maker can fix this by deactivate the permissions not required for page and keep only 1 active permissions for 1 webpage.


