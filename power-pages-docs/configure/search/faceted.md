---
title: Faceted Search
description: Learn how to enable or disable faceted search.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 1/24/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Faceted Search

Users can search site content using filters based on selected characteristics. These filters allow customers to find the content they want more quickly than traditional search.

## Enable faceted search

Out-of-the-box faceted search is enabled in your Power Pages site. To control or enable it, follow these steps:

1. Open the [Portal Management app](../portal-management-app.md) and go to **Portals** &gt; **Website** &gt; **Site Settings**.
1. Select the **Search/FacetedView** site setting. 
1. Change the **Value** to **True** to enable or **False** to disable faceted search.

## Disable faceted search

To disable a single piece of the faceted view:

1. Open the [Portal Management app](../portal-management-app.md) and go to **Portals** &gt; **Web Templates**.
1. Select the view to disable (that is, Knowledge Management – Top Rated Articles)
1. Select **Deactivate** at the top of the page.

## Group tables as part of a record type for faceted view

The site setting **Search/RecordTypeFacetsEntities** allows you to group similar tables together so users have logical ways of filtering search results. For example, instead of having separate options for forums, forum posts, and forum threads, these tables are grouped under the Forums record type.

Go to **Portals** &gt; **Websites** &gt; **Site Settings** and open the **Search/RecordTypeFacetsEntities** site setting. 

The different tables are preceded by the word **Forums:** because the first value is the name with they're grouped as. This word will be translated based on the language that is being used on the site.

## Use faceted search to improve knowledge search results

Faceted search enables Power Pages sites to have search filters on the leftmost side.  These filters allow you to choose between items like forums, blogs, and knowledge articles. More filters are added for specific search types. For example, knowledge articles can be filtered by Record Type, Modified Date, Rating, and Products to help customers find the content they need. The rightmost side also has a drop-down box that sorts results based on the customer’s choice of Relevance or View Count (specific to knowledge articles). Below is a screen capture with an example of some of the available filters.

### See also

[Progressive search](progressive.md)

