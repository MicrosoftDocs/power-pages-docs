---
title: Use admin APIs
description: Learn how to use the Power Pages admin APIs
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 11/09/2022
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - nickdoelman

---

# Use Power Pages admin APIs

The Power Pages admin APIs are available through the [Microsoft Power Platform API](/rest/api/power-platform/powerpages).

> [!NOTE]
> Please note the following limitation when configuring the [steps to get the authentication token](/power-platform/admin/programmability-authentication-v2) when using the admin APIs for Power Pages;
> - [Username and password flow](/power-platform/admin/programmability-authentication-v2#username-and-password-flow) is supported.
> - [Service Principal flow](/power-platform/admin/programmability-authentication-v2#service-principal-flow) support is not currently available.

## Call a REST API method for Power Pages admin APIs

Microsoft Power Platform APIs allow users to invoke using REST API methods in following format. The **namespace** for Power Pages APIs is **powerpages**.

```http
{HTTP method} https://api.powerplatform.com/powerpages/{resource}?api-version={version}
```

Read [here](/rest/api/power-platform/#call-a-rest-api-method) to learn more about the request format and request components.

## Power Pages operations

See [Websites](/rest/api/power-platform/powerpages/websites) for detailed information.

| Operation | Details |
| - | - |
| List websites | Get a list of all the Power Pages websites in your environment. |
| Create a website | Trigger the creation of a new Power Pages website. |
| Get the website by the ID | Get Website details from Website ID. |
| Delete a website | Trigger the deletion of a Power Pages site from the given website ID. |
| Restart a website | Restart the Power Pages website for the given site ID. |
