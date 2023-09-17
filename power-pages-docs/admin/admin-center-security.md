---
title: Manage website security from the Power Platform admin center (preview)
description: Learn about the admin settings for website security in the Power Platform admin center.
author: vamseedillimsft
ms.topic: conceptual
ms.custom: 
ms.date: 10/03/2023
ms.subservice: 
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - vamseedillimsft
    - professorkendrick
---

# Manage website security from the Power Platform admin center (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use the Power Platform admin center to monitor the security status of the websites in your tenant. You can also see key information such as how many sites have Web Application Firewall disabled or how many sites have external authentication enabled.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

To monitor website security for all websites in your tenant:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

1. On the left pane, select **Resources**, and then select **Power Pages sites**.

1. Select **Security (preview)** tab.

    :::image type="content" source="media/admin-center-security/security-admin-center.png" alt-text="A screenshot of Power Platform admin center security tab.":::

## Anonymous access enabled

**Anonymous access enabled** shows the number of websites where anonymous access is allowed for certain tables in Microsoft Dataverse. It means that these sites have at least one table permission that allows anonymous users to have access to the data. More information: [Table permissions](../security/assign-table-permissions.md)

Select **View details** to see the review anonymous access setting for each website.

### Web Application Firewall disabled

**Web Application Firewall disabled** shows the number of production websites where [Web Application Firewall (WAF)](../security/web-application-firewall.md) is disabled.

Enabling WAF improves the security of your website and Microsoft recommends enabling WAF. More information: [Enable Web Application Firewall for a website](../security/configure-web-application-firewall.md)

Select **View details** to see the review anonymous access setting for each website.

### External authentication enabled

**External authentication enabled** shows the number of websites where there is at least one authentication provider enabled which isn't Azure Active Directory allowing access to Dataverse data. More information: [Authentication providers](../security/authentication/index.md).

Select **View details** to see the review anonymous access setting for each website.

### Site security health

**Site security health** dashboard gives you a summary of the websites in your organization related security status. The security status of a website is determined based on certain security checks that are run for each website. More information: [Security site checker](../security/site-checker-security.md)

| Health status | Description |
| - | - |
| Standard | This status means that less than 33% of the security checks for this website are in **Pass** state. |
| Enhanced | This status means that more than 33% of the security checks for this website are in **Pass** state. |
| Advanced | This status means that more than 66% of the security checks for this website are in **Pass** state. |
| No results | This status means that security checker hasn't been run or if the site configurations don't allow checks to be run. Examples: A site that has an IP restriction setup, or a site that is stopped. |

Select **View** to find out the security checker results.

> [!NOTE]
> The checks are flagged as **Warning** when the configurations are not the same as what Microsoft recommends. There can be cases where your business needs demand the sites to be configured in a way that is not the **Recommended** state.

The pie chart shows you the count of websites in each Security Status

## Authentication providers

**Authentication providers** shows the list of all authentication providers that are used across the websites in your tenant, along with the count of all websites in which they're used

Select **Review** to see the list of websites where the specific authentication provider is used.

## Frequently Asked Questions

In this section, find answers to frequently asked questions related to website security using Power Platform admin center.

### How frequently is the data refreshed?

The security checks are run against all websites in your tenant, once every day automatically. The insights and security status are refreshed after every such run. The last updated time for the results can be seen on the top right corner of the page.

You can also manually refresh the security status on-demand by selecting **Refresh**.

### Who can view the security dashboard?

You must be a member of one of the following roles to view website security using Power Platform admin center:

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
