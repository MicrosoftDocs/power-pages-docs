---
title: Adding a view details page
description: Learn how to add a view details page on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 04/06/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Adding a view details page

Lists can also be configured in the Power Pages design studio. See [Add a list](../getting-started/add-list.md) for more information.

## Configure list view details in the Portal Management app

Using the [Portal Management app](portal-management-app.md), you can set the **Web Page for Details View** lookup to a webpage, the details of a record listed in the grid can be viewed as read-only or editable, depending on the configuration of the associated form or page.

This page can be a customized page template, which may be created by using Liquid. The most common scenario is probably to have the details page be a webpage that either contains a basic form or multistep form.

Each record listed in the grid will have a hyperlink to the details page, and the link will contain a named query string parameter with the ID of the record. The name of the query string parameter depends on the **ID Query String Parameter Name** value specified on the list. The targeted details webpage must also be aware of the name of this query string parameter to get the ID of the record that it needs to query and load its data.

> [!NOTE]
> The **Web Page for Details view** is a default setting configured for a list. The hyperlink on the grid will navigate to the default web page if the list is not configured using the **View** or **Edit** action settings in the **Grid Configuration** section on the **Options** tab. If either of the **View** or **Edit** action settings are configured with target type as a basic form, clicking the hyperlink in the list grid will open a dialog.

:::image type="content" source="media/lists/add-view-details-page.png" alt-text="Add view details page.":::

### Using a basic form to display details

To create a basic form, refer the instructions found on the [basic form](basic-forms.md) page.

The following are the important settings to be aware of for ensuring that the record from the list is loaded in the basic form.

The **Record ID Parameter Name** on the basic form must match the **ID Query String Parameter Name** on the list.

The **Mode** can be either *Edit* or *ReadOnly*, depending on your needs.

### Using multistep form to display details

The following are the important settings to be aware of for ensuring that the record from the list is loaded in the multistep form.

The **Primary Key Query String Parameter Name** on the multistep form step must match the **ID Query String Parameter Name** on the list.

The **Mode** can be either *Edit* or *ReadOnly*, depending on your needs.

### Using a details page for creating a new record

You can use a custom page, basic form, or multistep form in the same fashion for creating a new record. This method is an alternative to defining a **Create** action on the list on the **Grid Configuration** section under the **Options** tab. You can't define both a **Create** action *and* a custom page for create: defining a **Create** action takes precedence.

If you assign a webpage to the **Web Page for Create** lookup on the list and don't specify a **Create** action in the **Grid Configuration** section, a create button will be rendered on the list; this button will link the user to the custom page you've designated.

### See also

- [Work with lists](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL on a portal](add-redirect-url.md)
