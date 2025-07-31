---
title: Use admin APIs
description: Learn how to use the Power Pages admin APIs
author: neerajnandwana-msft
ms.topic: concept-article
ms.date: 07/31/2025
ms.author: nenandw
ms.reviewer: dmartens
contributors:
ms.custom:
  - sfi-ropc-nochange

---

# Use Power Pages admin APIs

Power Pages admin APIs are available through the [Microsoft Power Platform API](/rest/api/power-platform/powerpages/websites).

> [!NOTE]
> These limitations apply when configuring the [steps to get the authentication token](/power-platform/admin/programmability-authentication-v2) while using admin APIs for Power Pages:
> - [Username and password flow](/power-platform/admin/programmability-authentication-v2#username-and-password-flow) is supported.
> - The [service principal flow](/power-platform/admin/programmability-authentication-v2#service-principal-flow) isn't currently available.
> - Make sure the `username` used to request the token has the appropriate [roles required for portal administration](/power-apps/maker/portals/admin/portal-admin-roles) assigned.

## Call a REST API method for Power Pages admin APIs

Microsoft Power Platform APIs let users invoke REST API methods in the following format. The **namespace** for Power Pages APIs is **powerpages**.

```http
{HTTP method} https://api.powerplatform.com/powerpages/{resource}?api-version={version}
```

Learn more about the request format and request components at [Call a REST API method](/rest/api/power-platform/#call-a-rest-api-method).

## Power Pages operations

| Operation | Details |
| - | - |
| [Create Website](/rest/api/power-platform/powerpages/websites/create-website) | Trigger the creation of a new Power Pages website.</br></br>**Note:** It isn't recommended to create a site in the default environment as it is shared across all the users in the tenant, and has a risk of sharing data with unintentional users. |
| [Delete Website](/rest/api/power-platform/powerpages/websites/delete-website) | Trigger the deletion of a Power Pages site from the given website ID. |
| [Get Website by ID](/rest/api/power-platform/powerpages/websites/get-website-by-id) | Get website details from Website ID. |
| [Get Websites](/rest/api/power-platform/powerpages/websites/get-websites) | Get a list of all the Power Pages websites in your environment. |
| [Restart Website](/rest/api/power-platform/powerpages/websites/restart-website) | Restart the Power Pages website for the given site ID. |
| [Add Allowed IP Addresses](/rest/api/power-platform/powerpages/websites/add-allowed-ip-addresses) | Add allowed IP addresses on a Power Pages website.|
| [Create WAF Rules](/rest/api/power-platform/powerpages/websites/create-waf-rules) | Create web application firewall rules on a Power Pages website.|
| [Disable WAF](/rest/api/power-platform/powerpages/websites/disable-waf)  | Disable web application firewall on a Power Pages website.  |
| [Enable WAF](/rest/api/power-platform/powerpages/websites/enable-waf)  | Enable web application firewall on a Power Pages website. |
| [Get Security Scan Report](/rest/api/power-platform/powerpages/websites/get-security-scan-report) | Get deep scan report for a Power Pages website.  |
| [Get Security Scan Score](/rest/api/power-platform/powerpages/websites/get-security-scan-score) | Get deep scan score for a Power Pages website. |
| [Get WAF Rules](/rest/api/power-platform/powerpages/websites/get-waf-rules) | Get the web application firewall rules. |
| [Get WAF Status](/rest/api/power-platform/powerpages/websites/get-waf-status)  | Get the web application firewall status. |
| [Set Portal Bootstrap V5 Enabled](/rest/api/power-platform/powerpages/websites/set-portal-bootstrap-v5-enabled) | Stamp Bootstrap version five (5) status as enabled for a website. |
| [Set Portal Data Model Version](/rest/api/power-platform/powerpages/websites/set-portal-data-model-version)   | Stamp data model version for a website.  |
| [Start Deep Scan](/rest/api/power-platform/powerpages/websites/start-deep-scan)   | Start deep scan for a Power Pages website.  |
| [Start Quick Scan](/rest/api/power-platform/powerpages/websites/start-quick-scan)  | Execute quick scan for a Power Pages website.   |
| [Start Website](/rest/api/power-platform/powerpages/websites/start-website) | Start a Power Pages website.                                               |
| [Stop Website](/rest/api/power-platform/powerpages/websites/stop-website)  | Stop a Power Pages website.  |
| [Update Portal Security Group](/rest/api/power-platform/powerpages/websites/update-portal-security-group)    | Update security group for site visibility for a website.  |
| [Update Site Visibility](/rest/api/power-platform/powerpages/websites/update-site-visibility)    | Update site visibility for a website.   |