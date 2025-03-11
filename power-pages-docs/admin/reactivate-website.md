---
title: Reactivate sites
description: Learn how to reactivate Power Pages websites.
ms.topic: conceptual
ms.custom: 
ms.date: 09/06/2023
ms.subservice: 
ms.author: pudupa
ms.reviewer: danamartens
contributors:
    - dileepsinghmicrosoft
    - vashr
---

# Reactivate sites

On the Power Pages home page, you can see both **Active** and **Inactive** websites.

If the website configuration data exists in Microsoft Dataverse (you see an active **web site** record in the [Power Pages management app](../configure/portal-management-app.md)), but there's no active website host, the website is listed in the **Inactive sites** list on the Power Pages home page.

A website may be inactivated for the following reasons:
- When a website trial expires or a website host is deleted from the [Power Pages home page](manage-sites.md) or the [Power Platform admin center](delete-website.md), the website host is deleted but the configuration data is kept, and the website appears in the list of **Inactive** websites. 
- When you [transfer website configuration](migrate-site-configuration.md) from another environment, the website appears in the list of **Inactive** websites in the destination environment until it is reactivated.

## Reactivate the website

1. On the target environment, on the Power Pages home screen, select **Inactive sites**, you should see inactive websites in your environment.

1. Select **Reactivate**.

    :::image type="content" source="media/migrate-portal-config/reactivate-website.png" alt-text="Reactivate website.":::

1. You can specify the **Reactivated website** name and **Create a web address** or leave default values.

1. Select **Done**.

1. The website is active in the environment. 

> [!NOTE]
> A website appearing in the **Inactive sites** list on the Power Pages home page will appear in the list of **Active Websites** in the [Portal Management app](../configure/portal-management-app.md).

## See also

- [Create a site](../getting-started/create-manage.md)
- [Manage sites](manage-auth-key.md)
- [Migrate Power Pages website configuration](migrate-site-configuration.md)
