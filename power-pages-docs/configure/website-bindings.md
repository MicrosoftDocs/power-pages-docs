---
title: Create and manage website bindings
description: Learn how to create and manage website bindings in Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 04/13/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Website bindings

In the [Portal Management app](portal-management-app.md), you can view **Website Bindings** metadata records. These records provide the link between the site metadata stored in Microsoft Dataverse and the Power Pages site Azure web application.

> [!WARNING]
> - It is not recommended that you modify the website binding record. Instead, that you use the **Edit** option in the **Site Details** section in the Power Pages hub of the [Power Platform admin center](../admin/admin-overview.md#site-details) and selecting the **Website Record** value.
> - You should be careful while modifying the website binding records as they may cause your site to no longer function.

## Website binding attributes

These are the attributes common to all bindings.

|Name|Description|
|-----|----------|
|Name| A title to identify the website binding when viewing the records.|
|Website|The [website](websites.md) that should be selected by the website host.|

> [!NOTE]
> The **Release Date** and **Expiration Date** attributes are legacy settings and no longer apply to selecting a website record.


### See also
- [Create and manage websites](websites.md)


