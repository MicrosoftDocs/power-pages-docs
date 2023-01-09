---
title: Use the admin center
description: Learn how to use the Power Pages admin center
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 11/17/2022
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Use the admin center

Power Pages uses the Power Platform admin center to provide administrators with various site configuration capabilities.

> [!NOTE]
> You will need to be assigned certain roles to perform administrative tasks. See [Roles required for portal administration](/power-apps/maker/portals/admin/portal-admin-roles) for more information.

1. To access the admin center, from the design studio, select the **Set up** workspace.

1. In the **Site Details** section, select **Open admin center**.

    :::image type="content" source="media/admin-center.png" alt-text="Navigating to the Power Platform admin center.":::

1. This will open up the **Power Platform admin center** and allow you to configure your site.

    :::image type="content" source="media/power-platform-admin-center.png" alt-text="Power Platform admin center.":::

The following capabilities are accessible from the admin center. More information on these features may be linked to the Power Apps documentation.

## Site Actions

Select **Site Actions** to perform the following actions on your site.

:::image type="content" source="media/site-actions.png" alt-text="Select site actions.":::

| Action | More Information |
| - | - |
| Restart site | Restart the site. |
| Shut down this site | Turn off the site. |
| Delete this site | See [Delete a portal](/power-apps/maker/portals/admin/reset-portal#delete-a-portal) |
| Disable custom errors | See [Disable custom errors](/power-apps/maker/portals/admin/view-portal-error-log#disable-custom-error) |
| Enable diagnostic logs | See [Enable diagnostic logging](/power-apps/maker/portals/admin/view-portal-error-log#enable-diagnostic-logging)
| Enable maintenance mode | See [Maintenance mode for a portal](/power-apps/maker/portals/admin/enable-maintenance-mode) |

## Site Actions (...)

Select **...** for more site actions.

:::image type="content" source="media/more-site-actions.png" alt-text="Selecting additional site actions.":::

| Action | More Information |
| - | - |
| Manage Dynamics 365 Instance | See [Update the Dynamics 365 instance for your portal](/power-apps/maker/portals/admin/update-dynamics365-instance) |
| Update Dynamics 365 URL | |
| Metadata translations | See [Import metadata translation](/power-apps/maker/portals/admin/import-metadata-translation)
| Install Field Service Extension | See [Integrate Field Service](/power-apps/maker/portals/customer-engagement-apps/integrate-field-service) |
| Install Project Service Extension | See [Integrate Project Service Automation](/power-apps/maker/portals/customer-engagement-apps/integrate-project-service-automation) |

## Switch to Classic
| Action | More Information |
| - | - |
| Switch to classic | Switch to the classic admin center [portals admin center](/powerapps/maker/portals/admin/admin-overview). Note that the Power Apps portals admin center is now deprecated and no longer available as of June 2023. |

## Site Details

| Action | More Information |
| - | - |
| Edit | Edit site details. |
| Connect Custom Domain | See [Add a custom domain name](/power-apps/maker/portals/admin/add-custom-domain) |
| Convert to Production | See [Convert a portal](/power-apps/maker/portals/admin/convert-portal) |

## Security

| Action | More Information |
| - | - |
| IP Restrictions | See [Restrict portal access by IP address](/power-apps/maker/portals/admin/ip-address-restrict) |
| Custom Certificates | See [Manage custom certificates](/power-apps/maker/portals/admin/manage-custom-certificates) |
| Website Authentication Key | See [Manage portal authentication key](/power-apps/maker/portals/admin/manage-auth-key) |
| Manage Site Visibility Permissions | See [Site visibility in Power Pages](../security/site-visibility.md) |

## Site Health

| Action | More Information |
| - | - |
| Site Checker | See [Run Portal Checker](/power-apps/maker/portals/admin/portal-checker) |

## Performance & Protection

| Action | More Information |
| - | - |
| Content Delivery Network | See [Content Delivery Network](/power-apps/maker/portals/configure/configure-cdn) |
| Web Application Firewall | |

## Services

| Action | More Information |
| - | - |
| Power BI Visualization | See [Enable Power BI visualization](/power-apps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-visualization) |
| Power BI Embedded Service | See [Enable Power BI Embedded service](/power-apps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-embedded-service) |
| SharePoint Integration | See [Manage SharePoint documents](/power-apps/maker/portals/manage-sharepoint-documents) |

## See also
- [Power Pages admin APIs](admin-api.md)
