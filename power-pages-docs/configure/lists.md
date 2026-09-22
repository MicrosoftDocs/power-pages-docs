---
title: Lists overview
description: Learn how to add and configure lists to render a list of records on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 09/22/2026
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: smurkute
contributors:
    - sandhangitmsft
---

# Lists overview

Configure lists in the Power Pages design studio. Modern list is the default experience when you add a list to a newly created site. To use the classic list experience, turn off the **Modern list** toggle when you add or edit the list. For more information, see [Add a list](../getting-started/add-list.md).

## List metadata configuration

A list is a data-driven configuration that you use to add a webpage that renders a list of records. You don't need a developer to surface the grid on a website. By using lists, you can expose Dataverse records for display on a webpage.

Both modern and classic lists support sorting. Modern lists use infinite scrolling and automatically load more records as users scroll. Classic lists use pagination when the number of records is larger than the configured page size. 

If you specify **Web Page for Details View**, each record contains a link to the page, and the ID of the record is appended to the query string along with the ID query string parameter name. The configuration of the [form mode](../getting-started/add-form.md) and the [table permissions](../security/table-permissions.md) assigned to the web roles associated with the user determine the behavior of the target form (read-only or edit).

Modern and classic lists support multiple views. If you specify more than one view, a dropdown list is displayed so users can switch between the available views.

The current website user, the current website user's parent Customer account, and the current website can filter the data. If a value exists for both filter conditions **Portal User Attribute** and **Account Attribute**, the website renders a drop-down list to allow the user to view their own (My) data or their parent Customer account's data.

## Add a list to your website

The list contains relationships to webpages and various properties to control the initialization of the list of records within the website. The relationship to the webpage allows dynamic retrieval of the list definition for a given page node within the website. To view existing table views or to create new table views, go to **Content** > **Lists** in the [Portal Management app](portal-management-app.md).

> [!NOTE]
> - To view the list within the site, associate the list with a webpage in a given website.

Select the **Web Pages** link in the **Related** navigation links in the leftmost menu to view the webpages associated with the list. When creating your list, choose the table for which you want to render a list on the website. Then choose one or more model-driven app views to render.

When creating or editing a webpage, specify a list in the lookup field provided on the webpage form. The page template is typically the **Page** template, but it can be one of several other templates designed for content because the master templates contain the necessary logic to determine whether a list should be rendered.

## Add a list by using Liquid

You can add a list to a website by adding the Liquid tag `{% include 'entity_list' key: '<<list name>>' %}` to a content area, such as the webpage **Page Copy** field, or to a web template.

## See Also

- [List attributes and relationships](list-attributes-relationships.md)
- [Sort lists](sort-lists.md)
- [Add custom Javascript](add-custom-javascript-list.md)
- [List configuration](list-configuration.md)
- [Securing lists](securing-lists.md)
- [Adding a view details page](list-view-details.md)
- [List filter configuration](list-filter-configuration.md)
- [List map view](list-map-view.md)
- [List calendar view](list-calendar-view.md)
- [Enhanced view filter for lists](list-enhanced-view-filter.md)
