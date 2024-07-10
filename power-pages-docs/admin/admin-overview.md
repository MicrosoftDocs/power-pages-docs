---
title: Use the admin center
description: Learn how to use the Power Pages admin center.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 05/07/2024
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
    - DanaMartens
---

# Use the admin center

Power Pages uses the Power Platform admin center to provide administrators with various site configuration capabilities.

> [!NOTE]
> You will need to be assigned certain roles to perform administrative tasks. For more information, see [Roles required for website administration](admin-roles.md).

1. To access the admin center, from the design studio, select the **Set up** workspace.

1. In the **Site Details** section, select **Open admin center**.

    :::image type="content" source="media/admin-center.png" alt-text="Navigating to the Power Platform admin center.":::

1. The **Power Platform admin center** opens allows you to configure your site.

    :::image type="content" source="media/power-platform-admin-center.png" alt-text="Power Platform admin center.":::

Alternatively, you can also access your site details directly from the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select site to which you view details or perform admin actions. 

The following capabilities are accessible from the admin center. More information on these features might be linked to the Power Apps documentation.

## Site Actions

Select **Site Actions** to perform the following actions on your site.

:::image type="content" source="media/site-actions.png" alt-text="Select site actions.":::

| Action | More Information |
| - | - |
| Restart site | Restart the site. |
| Shut down this site | Turn off the site. |
| Delete this site | See [Delete a portal](delete-website.md) |
| Disable custom errors | See [Disable custom errors](view-portal-error-log.md#disable-custom-error) |
| Enable diagnostic logs | See [Enable diagnostic logging](view-portal-error-log.md#enable-diagnostic-logging)
| Enable maintenance mode | See [Maintenance mode for a portal](enable-maintenance-mode.md) |

## Site Actions (...)

Select **...** to the left of **Site Actions** for more site actions.

:::image type="content" source="media/more-site-actions.png" alt-text="Selecting additional site actions.":::

| Action | More Information |
| - | - |
| Manage Dynamics 365 Instance | See [Update the Dynamics 365 instance for your portal](update-dynamics365-instance.md) |
| Update Dynamics 365 URL | If you updated your [environment URL](/power-platform/admin/edit-properties-environment#edit-an-environment), the **Update Dynamics 365 URL** action updates your site to point to the updated environment URL. |
| Metadata translations | See [Import metadata translation](import-metadata-translation.md)
| Install Field Service Extension | See [Integrate Field Service](../templates/dynamics-365-apps/integrate-field-service.md) |
| Install Project Service Extension | See [Integrate Project Service Automation](../templates/dynamics-365-apps/integrate-project-service-automation.md) |

## Switch to Classic
| Action | More Information |
| - | - |
| Switch to classic | Switch to the classic admin center [portals admin center](/powerapps/maker/portals/admin/admin-overview). The Power Apps portals admin center is now deprecated and no longer available as of August 2023. |

## Site Details

| Action | More Information |
| - | - |
| See All | Opens a side panel displaying all the attributes of the current site. |
| Edit | **Edit site details.**</br> A side panel opens allowing you to make the following updates to a site:<ul><li>Change the **Site Name**.</li><li>Change the **Website Record**, which associates the site to the corresponding site metadata stored in Microsoft Dataverse. This action updates the corresponding [website bindings](/power-apps/maker/portals/configure/website-bindings) record.</li><li>Selecting the **Enable Portal for Early Upgrade** allows you to specify that the site can be updated to the latest code. This setting is only recommended for development and testing sites.</li><li>You call also update the **Site URL** to a new unique URL using the **powerappsportals.com** domain.</li></ul>|
| Convert to Production | See [Convert a site](convert-site.md) |
| Connect Custom Domain | See [Add a custom domain name](add-custom-domain.md) |
| Application Type | Indicates the application status of the site (Trial or Production) |
| Early Upgrade | Indicates if site is enabled for an early upgrade. |
| Site Visibility | Indicates the visibility of the site. See [Site Visibility](../security/site-visibility.md). |
| Site State | Indicates the site's running state. |
| Application Id | The site's application ID. |
| Org URL | The organization URL of the Microsoft Dataverse instance the site is associated with. |

> [!NOTE]
> For certain attributes, you can view the date of the last modification and the person responsible for the change. These attributes are accompanied by an information icon. Click this icon to see the relevant details. For example, click the info icon next to Site Visibility to display when it was last modified and by whom.

## Security

| Action | More Information |
| - | - |
| IP Restrictions | See [Restrict website access by IP address](ip-address-restrict.md) |
| Custom Certificates | See [Manage custom certificates](manage-custom-certificates.md) |
| Website Authentication Key | See [Manage website authentication key](manage-auth-key.md) |
| Manage Site Visibility Permissions | See [Site visibility in Power Pages](../security/site-visibility.md) |

## Site Health

| Action | More Information |
| - | - |
| Site Checker | See [Run Site Checker](site-checker.md) |

## Performance & Protection

| Action | More Information |
| - | - |
| Content Delivery Network | See [Content Delivery Network](../configure/configure-cdn.md) |
| Web Application Firewall | |

## Services

| Action | More Information |
| - | - |
| Power BI Visualization | See [Enable Power BI visualization](set-up-power-bi-integration.md#enable-power-bi-visualization) |
| Power BI Embedded Service | See [Enable Power BI Embedded service](set-up-power-bi-integration.md#enable-power-bi-embedded-service) |
| SharePoint Integration | See [Manage SharePoint documents](../configure/manage-sharepoint-documents.md) |

## Add yourself as an owner of the Microsoft Entra application

To manage a website that is already provisioned or resubmit provisioning if it failed, you must be an owner of the Microsoft Entra application connected to your website.

To add yourself as an owner of the Microsoft Entra application:

1. Go to the Power Platform admin center following the steps above.

1. From the **Site Details** section, copy the value of the **Application Id** field.

1. Go to Microsoft Entra associated with your tenant. More information: [Take over an unmanaged directory as administrator in Microsoft Entra ID](/azure/active-directory/active-directory-manage-o365-subscription).

1. In Microsoft Entra ID, search for the app registration by using the application ID you copied. You might need to switch from **My apps** to **All apps**.

1. Add users or groups as owners of this app registration. More information: [Managing access to apps](/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > This task can be performed either by a global administrator of your organization or the existing owner of this application.

1. After you add yourself as an owner, reopen the site details page from the Power Platform admin center.

## See also

[Use Power Pages admin APIs](admin-api.md)
