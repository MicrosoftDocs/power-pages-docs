---
title: Power Pages Sites in Power Platform Inventory (preview)
description: Power Pages sites in Power Platform inventory give admins a tenant-wide view of sites, owners, and access settings. Learn how to discover and govern your sites.
ms.date: 11/06/2026
ms.topic: concept-article
author: shwetamurkute
ms.author: ritwikganni
ms.reviewer: smurkute
---

# Power Pages sites in Power Platform inventory overview (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

**Power Platform inventory** is a tenant-wide administrative view that shows **Power Pages sites** alongside apps, flows, agents, environments, and environment groups. Administrators use inventory to discover sites, review ownership and configuration, and query site metadata for governance reporting and admin operations.

> [!IMPORTANT]
> - This feature is in preview.
> - This feature is being rolled out gradually across regions and might not be available yet in your region.

Understanding how Power Pages sites appear in inventory helps administrators maintain visibility across the tenant, support ownership transitions, and identify sites whose access or visibility settings need review.

## Prerequisites

- One of the following Microsoft Entra roles:
  - Global administrator
  - Power Platform administrator
  - Dynamics 365 administrator
- Familiarity with the shared inventory experience. For an overview, see [Power Platform inventory](/en-us/power-platform/admin/power-platform-inventory).

## Governance scenarios

Inventory supports several common administrative and governance scenarios for Power Pages sites:

- **Discover sites**: Find Power Pages sites across your tenant and see which environments contain them.
- **Review ownership**: Identify site owners to support ownership transitions and business continuity.
- **Review anonymous access**: Identify and review sites that allow anonymous visitors, so you can confirm each one is intentional and avoid exposing data by mistake.
- **Review developer site visibility**: Find developer sites whose visibility is set to public.
- **Review site URLs**: Identify sites with custom site URLs for domain and operational reviews.
- **Understand resource distribution**: Review sites alongside other Power Platform resources by environment.

## Power Pages sites in the inventory grid

Power Pages sites are available in the inventory grid in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) under **Manage** > **Inventory**. Filtering the **Item type** column to sites limits the grid to Power Pages sites. You can then search, filter, and sort the results to find the sites you need.

For example, filter by environment to review sites in a specific environment, by owner to review a user's sites, or by creation date to review recently created sites.

Change the columns displayed in the grid by selecting **Add or remove columns** next to the **Search** box. For shared instructions, see [Filter, sort, and search](/power-platform/admin/power-platform-inventory#filter-sort-and-search) and [Display more columns](/power-platform/admin/power-platform-inventory#display-more-columns).

## Site data

Each Power Pages site is represented in the `PowerPlatformResources` table in Azure Resource Graph with the resource type `microsoft.powerpages/sites`. The record includes the following information.

| Information | Available fields |
|----|----|
| Site identity and location | Site ID (`name`), resource ID (`id`), resource type (`type`), tenant ID (`tenantId`), region (`location`), site name (`properties.displayName`), and environment ID (`properties.environmentId`). |
| Ownership and changes | Owner (`properties.ownerId`), creator (`properties.createdBy`), creation date (`properties.createdAt`), and last modification date (`properties.lastModifiedAt`). Dates are in UTC. |
| Site state | Operational status (`properties.status`), provisioning state (`properties.provisioningState`), and maintenance mode (`properties.maintenanceMode`). |
| Access and site type | Anonymous access (`properties.anonymousAccessAllowed`), site visibility (`properties.siteVisibility`), and site type (`properties.siteType`). |
| Site URLs | Default URL (`properties.siteUrl`) and custom site URL (`properties.customSiteUrl`). The custom site URL is empty when one isn't configured. |

The site ID is returned in `name`; the display name is returned in `properties.displayName`. User identifiers are object IDs, not user display names.

For field types, descriptions, examples, and the resource ID format, see [Power Pages sites (preview)](/power-platform/admin/inventory-schema#power-pages-sites-preview) and [shared resource fields](/power-platform/admin/inventory-schema#shared-resource-fields).

## Query options

You can query Power Pages inventory through Azure Resource Graph, the Power Platform API, or the Power Platform for Admins V2 connector. Use `microsoft.powerpages/sites` to select Power Pages records.

> [!IMPORTANT]
> The **Query Power Platform resources** action in the Power Platform API and the Power Platform for Admins V2 connector requires delegated user authentication. Service principals and managed identities aren't supported for this action and receive HTTP 403 Forbidden.

For API setup and request details, see [Getting started with Power Platform API](/power-platform/admin/powerplatform-api-getting-started) and [Power Platform inventory API](/power-platform/admin/inventory-api). For Power Automate workflows, see the [Power Platform for Admins V2 connector](/connectors/powerplatformadminv2/#query-power-platform-resources).

## Query examples

The following examples use Kusto Query Language (KQL) against the `PowerPlatformResources` table in Azure Resource Graph. For instructions on running the queries, see [How to run these queries](/power-platform/admin/inventory-sample-queries#how-to-run-these-queries).

### List Power Pages sites

This query returns a tenant-wide inventory of Power Pages sites with their environment, owner, and creation and modification dates.

```kusto
PowerPlatformResources
| where type =~ "microsoft.powerpages/sites"
| extend properties = parse_json(properties)
| project siteName = tostring(properties.displayName),
    siteId = name,
    environmentId = tostring(properties.environmentId),
    ownerId = tostring(properties.ownerId),
    createdOn = todatetime(properties.createdAt),
    lastModifiedOn = todatetime(properties.lastModifiedAt)
| order by siteName asc
```

### Sites with anonymous access enabled

This query finds sites whose inventory metadata indicates that anonymous access is allowed.

```kusto
PowerPlatformResources
| where type =~ "microsoft.powerpages/sites"
| extend properties = parse_json(properties)
| extend anonymousAccessEnabled = tobool(properties.anonymousAccessAllowed)
| where anonymousAccessEnabled == true
| project siteName = tostring(properties.displayName),
    siteId = name,
    environmentId = tostring(properties.environmentId),
    websiteUrl = tostring(properties.siteUrl)
| order by siteName asc
```

### Public developer sites

This query uses the site type and visibility fields together to identify developer sites whose inventory metadata reports public visibility.

```kusto
PowerPlatformResources
| where type =~ "microsoft.powerpages/sites"
| extend properties = parse_json(properties)
| where tostring(properties.siteType) =~ "Developer"
| where tostring(properties.siteVisibility) =~ "Public"
| project siteName = tostring(properties.displayName),
    siteId = name,
    environmentId = tostring(properties.environmentId),
    websiteUrl = tostring(properties.siteUrl)
| order by siteName asc
```

For more examples, including counts by environment or owner, recently created sites, custom site URLs, and resource distribution across Power Platform, see [Power Pages queries (preview)](/power-platform/admin/inventory-sample-queries#power-pages-queries-preview).

## Inventory data export

Select **Download** in the inventory command bar to export inventory data to a CSV file. The export includes the entire inventory, not just the rows currently loaded in the grid. Queries can also retrieve site data for reporting and analysis. For shared instructions, see [Export your inventory](/power-platform/admin/power-platform-inventory#export-your-inventory).

For continuous data retrieval, you can query the same inventory data programmatically through the Power Platform APIs. For more information, see [Power Platform inventory](/power-platform/admin/power-platform-inventory).

## Related content

- [Power Platform inventory](/power-platform/admin/power-platform-inventory)
- [Power Platform inventory schema reference](/power-platform/admin/inventory-schema)
- [Power Platform inventory sample queries](/power-platform/admin/inventory-sample-queries)
- [Power Platform inventory API](/power-platform/admin/inventory-api)