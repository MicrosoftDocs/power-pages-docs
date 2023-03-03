---
title: Page permissions in Power Pages
description: Learn how to secure your webpages by using page permissions.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 3/3/2023
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

## Manage page permissions with the Portal Management app

Using the Portal Management app, you can manage page permissions through webpage access control rules. These rules allow you to control the publishing actions that a web role can perform across the pages of your website. Also, you can control which pages are visible to which web roles.

### Webpage access control rules

**To manage webpage access control rules with the Portal Management app**

1. Go to the [Portal Management app](../configure/portal-management-app.md).

1. On the left pane, under **Security**, select **Web Page Access Control Rules**.

1. Select a webpage access control rule to edit, or select **New** to create a new rule.

    Set the following attributes for the webpage access control rule.


    |    Name     |                                                                                                                                                                  Description                                                                                                                                                                   |
    |-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |    Name     |                                                                                                                                                        A descriptive name for the rule.                                                                                                                                                        |
    |   Website   |                                                                                                           The website that this rule applies to; this must match the website of the page to which this rule is applied.                                                                                                        |
    |  Web Page   |                            The webpage that this rule applies to. The rule will affect not only this page but all of its child pages, making this attribute select the branch of the website to which the rule will apply. If the rule is applied to the home page, it will apply to the entire portal.                            |
    |    Right    |                                                                                                                                    [Grant change](#grant-change) or [Restrict read](#restrict-read)                                                                                                                                      |
    |    Scope    | <ul><li><strong>All content</strong>: All descendant content is included in security validation.</li><li><strong>Exclude direct child web files</strong>: All child web files directly related to this webpage are excluded from security validation. This option doesn't exclude the descendants of the child web file.</li></ul>By default, **All content** is selected. |
    | Description |                                                                                                                                                     (Optional) A description of the rule.                                                                                                                                                      |

1. Select **Save & Close**.

### View access control rules for a page

After you create a new access control rule, it gets associated with the selected page. This association causes it to affect both the page you assign the rule to and all child pages&mdash;in other words, the entire branch of the website.

**To view the associated webpage access control rules for a page**

1. In the Portal Management app, on the left pane under **Content**, select **Web Pages**.

1. Select the webpage that you want to associate the access control rule with.

1. Select **Access Control Rules**.

1. View all the webpage access control rules for the page.


There are two types of access control rules: **Grant Change** and **Restrict Read**.

#### Grant Change

Use a **Grant Change** rule to allow a user who has the web role associated with the rule to publish content changes for this page, and all child pages of this page. **Grant Change** rules take precedence over **Restrict Read** rules.

For example, you have a news branch in your site, which you want to be editable by users who have the news editor web role. These users might not have access to the entire site, and certainly can't edit the entire site, but within this branch you want them to have full content publishing authority. You'd create a webpage access control rule called "grant news publishing to news editors."

Next, you set **Right** to **Grant Change** and **Web Page** to the parent page of the entire news branch of your site. You then assign this web role to any users you want to designate as news editors. (One user can have many web roles.)

A **Grant Change** rule should always be present in any portal that you want to enable front-side editing for. This rule will apply to the home page of the site, making it the default rule for the entire site. This rule will be associated with a web role that is to represent the administrative role for the site. Users who are to be given front-side content publishing rights will be assigned to this role.

#### Restrict Read

Use a **Restrict Read** rule to limit the viewing of the contents of a page (and its child pages) to specific users. In comparison, **Grant Change** is a *permissive* rule (it grants users the ability to do something), whereas **Restrict Read** is a *restrictive* rule in that it restricts an action to a limited set of users. For example, you might have a branch of the site meant to be used by employees only. You want to restrict the ability to read this section to people who have the employee web role. In this scenario, you create a new rule called "restrict read to employees only."

You then set **Right** to **Restrict Read** and **Web Page** to the page at the top of the branch that you want to be read only by employees. You then associate this rule with the employee web role, and then assign users to this role.

> [!NOTE]
> If you apply the **Restrict Read** right to the root (home) page of a website and select **Exclude direct child web files** as the **Scope**, the home page's direct child web files will be accessible to all users.

## Manage page permissions with legacy Power Apps portals Studio

Not only can you use portals Studio to customize your portal, you can manage page permissions quickly and efficiently.

To get started with managing page permissions using portals Studio:

1. Go to [Power Apps](https://make.powerapps.com).

1. On the left pane, select **Apps**.

1. Select your portal.

1. Select **Edit** to open the portal in portals Studio.

    More information: [Edit the portal](/power-apps/maker/portals/manage-existing-portals#edit) and [Studio anatomy](/power-apps/maker/portals/portal-designer-anatomy.md)

1. Select the page that you want to manage permissions for.

1. On the **Component** pane (on the right side of the screen), expand **Permissions**.

The options under **Permissions** vary depending on the page you've selected. For example, the options for a parent page will be different from the options for the child page that inherited permissions from the parent page.

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
