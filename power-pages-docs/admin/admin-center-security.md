---
title: Manage website security from the Power Platform admin center
description: Learn how to manage website security in the Power Platform admin center.
ms.topic: conceptual
ms.custom: 
ms.date: 03/12/2025
ms.subservice: 
author: PramithaU
ms.author: pudupa
ms.reviewer: danamartens
contributors:
    - vamseedillimsft
    - DanaMartens
---

# Manage website security from the Power Platform admin center

Use the Power Platform admin center to monitor the security status of the websites in your tenant. You can also see key information such as how many sites have Web Application Firewall (WAF) disabled or how many sites have external authentication enabled.

To monitor website security for all websites in your tenant, access the Power Platform admin center. The steps differ slightly depending on whether you are using the [new admin center](new-admin-overview.md) or the [classic admin center](admin-overview.md):

# [Classic admin center](#tab/classic)

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Resources**, and then select **Power Pages sites**.
1. Select **Security** tab.

:::image type="content" source="media/admin-center-security/security-admin-center.png" alt-text="A screenshot of Power Platform admin center security tab.":::

# [New admin center](#tab/new)

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left pane, select **Security**.
1. Under **Products**, select **Power Pages**.

:::image type="content" source="Media/admin-center-security/security-dashboard.png" alt-text="Screenshot of the Power Pages security view in the new Power Platform admin center.":::

---

## Anonymous access to Dataverse tables

**Anonymous access to Dataverse tables** shows the number of websites where anonymous access is allowed for certain tables in Microsoft Dataverse. This means these sites have at least one table permission that allows anonymous users to access the data. For more information, go to [Table permissions](../security/assign-table-permissions.md).

Select **View details** to review the anonymous access setting for each website.

## Web Application Firewall disabled

**Web Application Firewall disabled** shows the number of production websites where [Web Application Firewall (WAF)](../security/web-application-firewall.md) is disabled.

Enabling WAF improves the security of your website and Microsoft recommends enabling WAF. For more information, go to [Enable Web Application Firewall for a website](../security/configure-web-application-firewall.md).

Select **View details** to review the WAF setting for each website.

## External authentication enabled

**External authentication enabled** shows the number of websites where there is at least one authentication provider enabled that isn't Microsoft Entra ID allowing access to Dataverse data. For more information, go to [Authentication providers](../security/authentication/index.md).

Select **View details** to review the external authentication configuration for each website.

## Renew Website authentication key

**Renew Website authentication key** shows the number of production websites where the [website authentication key](manage-auth-key.md) expired or expires within 90 days.

Website authentication key has a fixed validity period and requires timely renewal to continue providing the security benefits & ensure uninterrupted access. Failure to renew the website authentication key before it expires can lead to security vulnerabilities and make the website inaccessible to end users.

Learn more about how to update the website authentication key at [Renew website authentication key](manage-auth-key.md#renew-authentication-key).

Select **View details** to review the website authentication expiry details for each website.

## Renew SSL Certificate key

**Renew SSL Certificate key** shows the number of production websites where the [SSL certificate](add-custom-domain.md) expired or expires within 90 days.

SSL certificates have a fixed validity period and require timely renewal to continue providing the security benefits. Failure to renew SSL certificates before they expire can result in security vulnerabilities, and loss of user trust. Learn more about how to renew the certificate at [Renew SSL certificate](add-custom-domain.md#renew-or-reissue-ssltls-certificate-for-power-pages).

Select **View details** to review the SSL certificate expiry details for each website.

## Site health

The **Site health** section includes tabs to view the results of deep or quick scans:

### Deep scan

The [deep scan](../security/security-scan.md) feature is designed to strengthen your site's resilience by detecting and addressing vulnerabilities, protecting it from potential threats, and ensuring a secure online environment for users.

The dashboard offers a summary of:

- The count of sites within the tenant that were scanned and the count that weren't scanned.
- Site-specific details, including the scan status, scan score (number of passed/failed checks), if the scan is completed, a view of the scan results, and an option to initiate the scan.

Select **view** from the scan results column to open the summary report. The summary report includes a list of failed checks and corresponding alerts with descriptions of how to fix the alerts. You can optionally download the report as a PDF. Report summaries for security scans are only supported in English-US language.

### Quick scan

The quick scan tab gives you a summary of the websites in your organization related to security status. The security status of a website is determined based on certain security checks that are run for each website. For more information, go to [Security site checker](../security/site-checker-security.md).

The security health is calculated by looking at various configuration parameters and identifying common issues. These checks aren't exhaustive and we recommend you continue following website security best practices.

The criteria for classifying security health into Standard, Enhanced, and Advanced is outlined in the table provided.

| Health status | Description |
| - | - |
| Standard | This status means that less than 33% of the security checks for this website are in **Pass** state. |
| Enhanced | This status means that more than 33% of the security checks for this website are in **Pass** state. |
| Advanced | This status means that more than 66% of the security checks for this website are in **Pass** state. |
| No results | This status means that the security checker isn't being run, or the site configurations don't allow checks to be run. Such as a site that has an IP restriction setup, or a site that is stopped. To resolve this, run the site checker from Power Platform Admin Center. Site checker doesn't work if a website has IP address restrictions. |

Select **View** to review the security checker results.

The checks are flagged as **Warning** when the configurations aren't the same as what Microsoft recommends. There can be cases where your business needs demand the sites to be configured in a way that isn't in the **Recommended** state.

## Site security checks

**Site security checks** shows every security check along with the number of sites for which the check result is passed, failed, warning, or not run.

## Authentication providers

**Authentication providers** shows the list of all authentication providers that are used across the websites in your tenant, along with the count of all websites in which they're used.

Select **Review** to see the list of websites where the specific authentication provider is used.

## Sites with integrations

**Sites with integrations** shows the list of all integrations with other services that are configured across the websites in your tenant, along with the count of all websites in which they're enabled. Currently, this view shows sites with the following integrations:

- [Power BI visualization](set-up-power-bi-integration.md)
- [Power BI embedded service](set-up-power-bi-integration.md#enable-power-bi-embedded-service)
- [SharePoint](../configure/manage-sharepoint-documents.md)
- [Cloud flows](../configure/cloud-flow-integration.md)
- [Payment](set-up-payments-integration.md)

Select **Review** to see the list of websites where the specific integration is enabled. If you find a site where the integration shouldn't be enabled, work with the site maker to remove it or disable it.

## Frequently Asked Questions

In this section, find answers to frequently asked questions related to managing website security using Power Platform admin center.

### How frequently is the data refreshed?

Security checks are run against all websites in your tenant, once every day automatically. The insights and security status are refreshed after every run. The most current update for the results can be seen in the top right corner of the page.

You can also manually refresh the security status on-demand by selecting **Refresh**.

### Who can view the security dashboard?

You must have one of the following roles to view website security using Power Platform admin center:

- Dynamics 365 administrator
- Power Platform administrator
- System administrator (can only see websites for the environments of which they're a system administrator)

## Next steps

[Configure site details](admin-overview.md#site-details)

### See also

- [Administer Microsoft Power Platform](/power-platform/admin/admin-documentation)
- [Manage Dynamics 365 apps](/power-platform/admin/manage-apps)  
- [Upgrade a website](upgrade-site.md)  
- [Managing websites from the Power Platform Admin Center (video)](https://youtu.be/YuBlXVBlPVk?feature=shared)
