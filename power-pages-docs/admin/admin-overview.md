---
title: Use the admin center
description: Learn how to use the Power Pages admin center
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 01/11/2023
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Use the admin center

Power Pages uses the Power Platform admin center to provide administrators with various site configuration capabilities.

> [!NOTE]
> You will need to be assigned certain roles to perform administrative tasks. For more information, see [Roles required for portal administration](/power-apps/maker/portals/admin/portal-admin-roles).

1. To access the admin center, from the design studio, select the **Set up** workspace.

1. In the **Site Details** section, select **Open admin center**.

    :::image type="content" source="media/admin-center.png" alt-text="Navigating to the Power Platform admin center.":::

1. The **Power Platform admin center** will open and allow you to configure your site.

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
| Switch to classic | Switch to the classic admin center [portals admin center](/powerapps/maker/portals/admin/admin-overview). The Power Apps portals admin center is now deprecated and no longer available as of June 2023. |

## Site Details

| Action | More Information |
| - | - |
| See All | Opens a side panel displaying all the attributes of the current site. |
| Edit | **Edit site details.**</br> A side panel will open allowing you to make the following updates to a site:<ul><li>Change the **Site Name**.</li><li>Change the **Website Record**, which associates the site to the corresponding site metadata stored in Microsoft Dataverse. This action will update the corresponding [website bindings](/power-apps/maker/portals/configure/website-bindings) record.</li><li>Selecting the **Enable Portal for Early Upgrade** allows you to specify that the site can be updated to the latest code. This setting is only recommended for development and testing sites.</li><li>You call also update the **Site URL** to a new unique URL using the **powerappsportals.com** domain.</li></ul>|
| Convert to Production | See [Convert a portal](/power-apps/maker/portals/admin/convert-portal) |
| Connect Custom Domain | See [Add a custom domain name](/power-apps/maker/portals/admin/add-custom-domain) |
| Application Type | Indicates the application status of the site (Trial or Production) |
| Early Upgrade | Indicates if site has been enabled for an early upgrade. |
| Site Visibility | Indicates the visibility of the site. See [Site Visibility](../security/site-visibility.md). |
| Site State | Indicates the site's running state. |
| Application Id | The site's application id. |
| Org URL | The organization URL of the Microsoft Dataverse instance the site is associated with. |

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

## Add yourself as an owner of the Azure AD application

If you aren't a global administrator and you try to manage a website that has already been provisioned, or you resubmit the provisioning if it failed, you must be the owner of the Azure Active Directory (Azure AD) application connected to your portal.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select site to which you want to be the associated as the Azure AD application owner. 

1. From the **Site Details** section, copy the value of the **Application Id** field.    

1. Go to Azure AD associated with your tenant. More information: [Take over an unmanaged directory as administrator in Azure Active Directory](/azure/active-directory/active-directory-manage-o365-subscription).

1. In Azure AD, search for the app registration by using the application ID you copied. You might need to switch from **My apps** to **All apps**.

1. Add users or groups as owners of this app registration. More information: [Managing access to apps](/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > This task can be performed either by a global administrator of your organization or the existing owner of this application.

1. After you've added yourself as an owner, reopen the site details page from the Power Platform admin center.

## See also
- [Power Pages admin APIs](admin-api.md)
