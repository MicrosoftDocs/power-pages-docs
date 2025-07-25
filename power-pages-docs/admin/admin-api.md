---
title: Use admin APIs
description: Learn how to use the Power Pages admin APIs
author: neerajnandwana-msft
ms.topic: concept-article
ms.date: 02/23/2023
ms.author: nenandw
ms.reviewer: dmartens
contributors:
ms.custom:
  - sfi-ropc-nochange

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
| [Create Website](/rest/api/power-platform/powerpages/websites/create-website) | Trigger the creation of a new Power Pages website.</br></br>**Note:** It isn't recommended to create a site in the default environment as it is shared across all the users in the tenant, and has a risk of sharing data with unintentional users. |
| [Delete Website](/rest/api/power-platform/powerpages/websites/delete-website) | Trigger the deletion of a Power Pages site from the given website ID. |
| [Get Website by Id](/rest/api/power-platform/powerpages/websites/get-website-by-id) | Get website details from Website ID. |
| [Get Websites](/rest/api/power-platform/powerpages/websites/get-websites) | Get a list of all the Power Pages websites in your environment. |
| [Restart Website](/rest/api/power-platform/powerpages/websites/restart-website) | Restart the Power Pages website for the given site ID. |
