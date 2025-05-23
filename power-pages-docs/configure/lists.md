---
title: Lists overview
description: Learn how to add and configure lists to render a list of records on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 2/24/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Lists overview

Lists can be configured in the Power Pages design studio. See [Add a list](../getting-started/add-list.md) for more information.

## List metadata configuration

A list is a data-driven configuration that you use to add a webpage that will render a list of records without the need for a developer to surface the grid on a website. By using lists, you can expose Dataverse records for display on a webpage.

The grid supports sorting and will be paginated if the number of records is larger than the page size specified. 

If **Web Page for Details View** has been specified, each record will contain a link to the page, and the Id of the record will be appended to the query string along with the Id query string parameter name. The behavior of the target form (read-only or edit) will be determined by the configuration of the [form mode](../getting-started/add-form.md) and the [table permissions](../security/table-permissions.md) assigned to the web roles associated with the user.

The list also supports multiple views. If more than one view has been specified, a drop-down list will be rendered to allow the user to switch between the various views.

The data can also be filtered by the current website user, the current website user's parent Customer account, and the current website. If a value exists for both filter conditions **Portal User Attribute** and **Account Attribute**, the website will render a drop-down list to allow the user to view their own (My) data or their parent Customer account's data.

## Add a list to your website

The list contains relationships to webpages and various properties to control the initialization of the list of records within the website. The relationship to the webpage allows dynamic retrieval of the list definition for a given page node within the website. To view existing table views or to create new table views, go to **Content** > **Lists** in the [Portal Management app](portal-management-app.md).

> [!Note]
> - A list must be associated with a webpage in a given website for the list to be viewable within the site.

The webpages associated with the list can be viewed by selecting the **Web Pages** link listed in the **Related** navigation links in the leftmost menu. When creating your list, the first step is to choose the table for which you want to render a list on the website. You'll then choose one or more model-driven app views to render.

When creating or editing a webpage, you can specify a list in the lookup field provided on the webpage form. The page template typically will be the Page template, but can be one of several other templates designed for content because the master templates contain the necessary logic to determine whether a list should be rendered.

## Add a list using Liquid

Add list can also be added to a website by adding the Liquid tag `{% include 'entity_list' key: '<<list name>>' %}` to a content area such as the webpage **Page Copy** field or to a web template.

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
