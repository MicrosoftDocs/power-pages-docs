---
title: Configure site markers for Power Pages sites.
description: Learn how to add and configure site markers for Power Pages sites.
author: gitanjalisingh33msft

ms.topic: how-to
ms.custom: 
ms.date: 04/25/2023
ms.subservice: 
ms.author: gisingh
ms.reviewer: dmartens
contributors:
    - gitanjalisingh33msft
---

# Configure site markers for websites

A site marker is a configurable, named value that points to a page on your website that is accessed in code in place of a hard-coded URL.

Using a site marker instead of hard-coded URL means that page can be moved in the website hierarchy and the link will continue to work without any other modification.

## Manage site markers

1. Using the [Portal Management app](portal-management-app.md), select **Site markers** under the **Website** section.

1. To create a new site marker, select **New**.

1. To edit an existing setting, select the **Site Marker** listed in the grid.

1. Specify values for the fields provided: 

    - **Name**:  A label referenced by website code to retrieve the appropriate page and location. The name should be unique for the associated website, because the code retrieving the setting will take the first record found with the matching name.
    
    - **Website**:  The associated website. 
    
    - **Page**: The webpage that the site marker will reference.

1. Select **Save & Close**.

## Using site markers in code

A site marker can be accessed using the following [Liquid object](liquid/liquid-objects.md#sitemarkers):

`{{ sitemarkers["<<marker name>>"].url }}`

Example:

If you create a **Site Marker** record called **subpage** which points to the web page called **Subpage 1**, you'll be able to reference the URL from Liquid code.

:::image type="content" source="media/site-marker/create-site-marker.png" alt-text="Configure site marker.":::

You can place the following Liquid code on a web page, web template, or content snippet:

`<a href={{ sitemarkers['subpage'].url }}>Subpage 1 link</a>`

If the page is relocated in the [site navigation](../getting-started/structure-site.md), the link will continue to work.

