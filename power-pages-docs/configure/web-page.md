---
title: Manage web pages
description: Learn how to manage web pages metadata in Power Pages.
author: DanaMartens

ms.topic: how-to
ms.custom: 
ms.date: 04/13/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Manage web pages

A web page represents a particular URL in a Power Pages website, and is one of the core components of Power Pages. Through parent and child relationships to other web pages, this forms the hierarchy of a website (i.e., its site map).

Web pages also form the basis for including other, specialized components types in the site map – web files, shortcuts, forums, multistep forms, and blogs are all situated in the site map through – and thus derive their URLs from – a relationship to a parent web page.

## Manage web pages

Web pages can be created, edited, and deleted from the Power Pages [design studio](../getting-started/first-page.md). However, advanced customization can be performed from the Portal Management app.  

1. Open the [Portal Management app](portal-management-app.md).

2. Go to **Content** > **Web Pages**.

3. To edit an existing web page, select the web page name.

4. Enter appropriate values in the fields.

5. Select **Save & Close**.

### Web page attributes

The table below explains many of the standard web page attributes used by Power Pages. It's important to note that the way in which many of the content/display-oriented attributes are rendered is controlled by the page template used, and thus by the Power Pages developer.


|        Name         |                                                                                                                                                                                                                                                                                                                                   Description                                                                                                                                                                                                                                                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Name         |                                                                                                                                                                                                                                                     The descriptive name of the table. This value will be used as the page title in most templates, particularly if a Title value isn't provided. This field is required.                                                                                                                                                                                                                                                     |
|       Website       |                                                                                                                                                                                                                                                                                                        The Website to which the table belongs. This field is required.                                                                                                                                                                                                                                                                                                         |
|     Parent Page     |                                                                                                                                                                                                                                                      The parent web page of the table, in the website content hierarchy. <br>All web pages should have a parent page except for the single root (Home) page of a website.                                                                                                                                                                                                                                                      |
|     Partial URL     | The URL path segment used to build the website URL of this page. <br>The single root (Home) page of your website – the single page that has no associated Parent Page – must have a Partial URL value of /.<br>Partial URL values are used as URL path segments. As such, they shouldn't contain illegal URL path characters, such as ?, #, !, %. Since website URLs are generated by joining together partial URL values with slashes (/), they should also not generally contain slashes. Recommended practice would be to restrict partial URL values to letters, numbers, and hyphens or underscores. For example: press-releases, Users_Guide, product1. |
|    Page Template    |                                                                                                                                                                                                                                                                                             The Page Template to be used to render this page on the website. This field is required.                                                                                                                                                                                                                                                                                             |
|  Publishing State   |                                                                                                                                                 The current publishing workflow state of the page, which may dictate whether or not the page is visible on the site. The most common use of this feature is to provide published/draft control over content.<br>Users with content management permissions may be granted the ability to use Preview Mode, which allows these users to see (preview) unpublished content.                                                                                                                                                  |
|    Display Date     |                                                                                                                                                                                                         This attribute is a date/time value that can be used by a template, purely for display purposes. It has no functional implications, but can be useful for things like, for example, manually specifying a published date on a press release or news item page.                                                                                                                                                                                                          |
|    Release Date     | There is no longer any automated functionality linked to this date field.                                                                                                               |
|   Expiration Date   |                                                                                                                                                                There is no longer any automated functionality linked to this date field.                                                                                                                                                                |
|      Multistep  Form       |                                                                                                                                                                                                                                                                                                                   The multistep form to be displayed on this page.                                                                                                                                                                                                                                                                                                                    |
|        Title        |                                                                                                                                                                   An optional title for the page. If this field is provided, this value will be used on the website, instead of the Name field. This is useful in the case that you want a different title to appear on the website, while having the Name be useful for content authors and users.                                                                                                                                                                   |
|       Summary       |                                                                                                                                                                                                                                                      A short description for the page, this value will generally be used to add a description of the page to website navigational elements that render a link to the page.                                                                                                                                                                                                                                                       |
|        Copy         |                                                                                                                                                                                                                                                                                                                    The main HTML content field of the page.                                                                                                                                                                                                                                                                                                                     |
| Hidden from Sitemap |                                                                                                                                                                                                        Controls whether or not the page is visible has part of the site map. If this value is checked, the page will still be available on the site at its URL, and can be linked to, but standard navigational elements (menus, etc.) won't include the page.                                                                                                                                                                                                        |
|       Author        |                                                                                                                                                                                                                                  A Contact record representing the author of the page. This value is used for administrative purposes, but this information could be rendered on a website, if the page's Page Template supports it.                                                                                                                                                                                                                                   |
|    Display Order    |                                                                                                                                                                                       An integer value indicating the order in which the page will be placed, relative to other tables with the same Parent Page. This controls the ordering of pages and other site map tables when, for example, a list of links to the child tables of a given page are rendered on the website.                                                                                                                                                                                        |
|     Navigation      |                                                                       A Web Link Set record. This is used by the WebLinkNavigationPage.aspx Page Template to render a list of navigation links on the left hand side of the page. Create a new [Page Template](page-templates.md) and specify the Rewrite Url property as ~/Pages/WebLinkNavigationPage.aspx. Set the Web Page's Page Template to this template record. This is typically done to the parent page only and all child pages will automatically receive the same list of links of its parent. The current page will have its corresponding link highlighted.                                                                        |
|   Enable Tracking (Deprecated)  |                                                                                                                                                                                                                                              This feature has been deprecated and no longer functions.                                                                                                                                                                                                                                              |
|                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
## Enable page comments

Page comments provide users with the ability to view and post comments on a web page. By default this feature is disabled and can be enabled on a page by page basis.

> [!NOTE]
> Comments are available when pages use **Full page** or **Page** page templates that are provided with the [Dynamics 365 website templates](../templates/dynamics-365-apps/overview.md).

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Content** > **Web Pages**.

1. Select the web page on which you need to enable comments.

1. From the **Comment Policy** list, select the required comment policy:
   - **Inherit**: The comment policy of the parent page will be used. This is the default setting.
   - **Open**: Submissions from all users, anonymous and authenticated, are allowed and displayed immediately.
   - **Open to Authenticated Users**: Only submissions from authenticated users are allowed and they're displayed immediately.
   - **Moderated**: Submissions from all users, anonymous or authenticated, are allowed. The submissions won't be displayed until a moderator approves them.
   - **Closed**: Existing submissions are displayed, but no new submissions are allowed.
   - **None**: User submissions are disabled. No submissions can be made or viewed.

1. Save the changes.


