---
title: Use admin APIs
description: Learn how to use the Power Pages admin APIs
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 11/10/2022
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - nickdoelman

---

# Use Power Pages admin APIs

The Power Pages admin APIs are available through the [Microsoft Power Platform API](/rest/api/power-platform/powerpages/websites).

> [!NOTE]
> The following limitations apply when configuring the [steps to get the authentication token](/power-platform/admin/programmability-authentication-v2) while using the admin APIs for Power Pages:
> - [Username and password flow](/power-platform/admin/programmability-authentication-v2#username-and-password-flow) is supported.
> - [Service Principal flow](/power-platform/admin/programmability-authentication-v2#service-principal-flow) support is not currently available.
> - Ensure the `username` used to request the token has the appropriate [roles required for portal administration](/power-apps/maker/portals/admin/portal-admin-roles) assigned.

## Call a REST API method for Power Pages admin APIs

Microsoft Power Platform APIs allow users to invoke using REST API methods in following format. The **namespace** for Power Pages APIs is **powerpages**.

```http
{HTTP method} https://api.powerplatform.com/powerpages/{resource}?api-version={version}
```

To learn more about the request format and request components, go to [Call a REST API method](/rest/api/power-platform/#call-a-rest-api-method).

## Power Pages operations

| Operation | Details |
| - | - |
| [Create Website](/rest/api/power-platform/powerpages/websites/create-website) | Trigger the creation of a new Power Pages website. |
| [Delete Website](/rest/api/power-platform/powerpages/websites/delete-website) | Trigger the deletion of a Power Pages site from the given website ID. |
| [Get Website by Id](/rest/api/power-platform/powerpages/websites/get-website-by-id) | Get Website details from Website ID. |
| [Get Websites](/rest/api/power-platform/powerpages/websites/get-websites) | Get a list of all the Power Pages websites in your environment. |
| [Restart Website](/rest/api/power-platform/powerpages/websites/restart-website) | Restart the Power Pages website for the given site ID. |
