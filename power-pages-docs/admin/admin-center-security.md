---
title: Manage website security from the Power Platform admin center (preview)
description: Learn how to manage website security in the Power Platform admin center.
author: vamseedillimsft
ms.topic: conceptual
ms.custom: 
ms.date: 09/28/2023
ms.subservice: 
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - vamseedillimsft
    - professorkendrick
---

# Manage website security from the Power Platform admin center (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use the Power Platform admin center to monitor the security status of the websites in your tenant. You can also see key information such as how many sites have Web Application Firewall (WAF) disabled or how many sites have external authentication enabled.

> [!IMPORTANT]
>
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To monitor website security for all websites in your tenant:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. On the left pane, select **Resources**, and then select **Power Pages sites**.

1. Select **Security (preview)** tab.

    :::image type="content" source="media/admin-center-security/security-admin-center.png" alt-text="A screenshot of Power Platform admin center security tab.":::

## Anonymous access enabled

**Anonymous access enabled** shows the number of websites where anonymous access is allowed for certain tables in Microsoft Dataverse. It means that these sites have at least one table permission that allows anonymous users to have access to the data. For more information, go to [Table permissions](../security/assign-table-permissions.md).

Select **View details** to review the anonymous access setting for each website.

### Web Application Firewall disabled

**Web Application Firewall disabled** shows the number of production websites where [Web Application Firewall (WAF)](../security/web-application-firewall.md) is disabled.

Enabling WAF improves the security of your website and Microsoft recommends enabling WAF. For more information, go to [Enable Web Application Firewall for a website](../security/configure-web-application-firewall.md).

Select **View details** to review the WAF setting for each website.

### External authentication enabled

**External authentication enabled** shows the number of websites where there is at least one authentication provider enabled which isn't Microsoft Entra ID allowing access to Dataverse data. for more information, go to [Authentication providers](../security/authentication/index.md).

Select **View details** to review the external authentication configuration for each website.

### Site security health

**Site security health** dashboard gives you a summary of the websites in your organization related to security status. The security status of a website is determined based on certain security checks that are run for each website. For more information, go to [Security site checker](../security/site-checker-security.md).

The security health is calculated by looking at various configuration parameters and identifying common issues. These checks aren't exhaustive and we recommend you continue following website security best practices.

The criteria for classifying security health into Standard, Enhanced and Advanced is outlined in the table provided. This criteria might change during the feature preview and before the feature is generally available.

| Health status | Description |
| - | - |
| Standard | This status means that less than 33% of the security checks for this website are in **Pass** state. |
| Enhanced | This status means that more than 33% of the security checks for this website are in **Pass** state. |
| Advanced | This status means that more than 66% of the security checks for this website are in **Pass** state. |
| No results | This status means that security checker isn't being run, or the site configurations don't allow checks to be run. Such as, a site that has an IP restriction setup, or a site that is stopped. To resolve, run the site checker from Power Platform Admin Center. Site checker doesn't work if a website has IP address restrictions. |

Select **View** to review the security checker results.

The checks are flagged as **Warning** when the configurations aren't the same as what Microsoft recommends. There can be cases where your business needs demand the sites to be configured in a way that isn't in the **Recommended** state.

**Note:** You can also get a security check level view under 'Site security checks'. This view shows every security check along with the number of sites for which the check result is - passed, failed, warning or not run. 

## Authentication providers

**Authentication providers** shows the list of all authentication providers that are used across the websites in your tenant, along with the count of all websites in which they're used.

Select **Review** to see the list of websites where the specific authentication provider is used.

## Sites with integrations

**Sites with integrations** shows the list of all integrations with other services that are configured across the websites in your tenant, along with the count of all websites in which they're enabled. Currently, this view shows sites with the following integrations: i) Power BI visulaization ii) Power BI embedded service iii) SharePoint iv) CloudFlows

Select **Review** to see the list of websites where the specific integration has been enabled. If you find a site where the integration should not have been enabled, please work with the site maker and remove it or disable it.

## Frequently Asked Questions

In this section, find answers to frequently asked questions related to managing website security using Power Platform admin center.

### How frequently is the data refreshed?

Security checks are run against all websites in your tenant, once every day automatically. The insights and security status are refreshed after every run. The most current update for the results can be seen on the top right corner of the page.

You can also manually refresh the security status on-demand by selecting **Refresh**.

### Who can view the security dashboard?

You must have one of the following roles to view website security using Power Platform admin center:

- Global administrator
- Dynamics 365 administrator
- Power Platform administrator
- System administrator (can only see websites for the environments of which they're a system administrator)

## Next steps

[Configure site details](admin-overview.md#site-details)

### See also

- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)
