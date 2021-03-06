---
title: Go live checklist for Power Pages
description: Learn how to go live.
author: NikitaPolyakovMSFT
ms.topic: conceptual
ms.custom: 
ms.date: 06/07/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Go live checklist

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

This checklist is guidance to help you plan your Power Pages and Power Apps portals projects.

> [!IMPORTANT]
> - Power Pages is an evolution of Power Apps portals, and the new features introduced by Power Pages such as the new design studio and templates are in preview for users to try and provide feedback. We recommend that you wait until the general availability of Power Pages later this year to use sites created using the new Power Pages design studio in production scenarios.
> - All the platform, site admin, and pro 
developer capabilities inherited by Power Pages from Power Apps portals are generally available and can be used in production scenarios. More information: [Power Pages and Power Apps portals](../difference-portals.md)

As you prepare and consider going live with your project, here are a few areas to keep in mind:

> [!div class="checklist"]
> * Finalize your site
> * Create separate development, testing, and production sites
> * Test your site performance
> * Set up a custom domain
> * Configure authentication set up
> * Set up telemetry monitoring
> * Provide access to users

## Finalize your site

Clean up your site and remove any sample webpages, sample text, and placeholder images.

Delete or deactivate any unused pages. 

Change your browser suffix from "Home page - Starter Portal" to a meaningful name. You can find the content snippet "BrowserSuffix" in the **Content Snippets** area of the [Portal Management app](../configure/portal-management-app.md)

Set your specific copyright text, and add any privacy or other links in the "Footer" web template. Find it in the **Web templates** area of the [Portal Management app](../configure/portal-management-app.md).

Protect any unfinished page by using [Page permissions](../security/page-security.md).

## Create separate development, testing, and production sites

To continue to make updates to your site without breaking functionality for existing users of your site, we recommend three separate environments to manage the application development lifecycle. 

More information: [Power Platform application lifecycle management](/power-platform/alm/basics-alm) for more information. 

## Test your site performance

Optimize your site's performance by enabling a content delivery network (CDN).

More information: [Configure CDN](/power-apps/maker/portals/configure/configure-cdn).

If you have high scalability needs (thousands of users a month or a critical workload), consider performing load testing to understand the type of performance you'll get and troubleshoot any problem areas. 

Areas to consider:
- Number of visitors to your site on a daily basis.
- Traffic volumes at different times.
- High traffic pages linked to Dataverse.
- Volume of data stored in Dataverse.

## Set up a custom domain 

Your site should align with your corporate domain name whenever possible. By default, Power Pages create a URL using the powerappsportals.com domain.

You can read more about setting up your own [custom domains](/power-apps/maker/portals/admin/add-custom-domain) in the Power Apps documentation.

You may need to get approval from your internal team to get the right SSL certificate, configure, and test it. You'll want this domain name working for most external identity providers, so it becomes a dependency to go live.

## Configure authentication set-up

By default Power Pages sets local authentication as your identity provider. We recommend using one of the supported identity providers as your default and disabling local authentication.

For example, [Azure Active Directory B2C](../getting-started/tutorial-setup-site-authentication.md).

> [!TIP]
> - Finish setting up your custom domain to utilize the redirect URL for the authentication provider. 
> - If you're using the **Azure AD** sign-in button, you can rename it to reflect meaningful label. Using the [Portal Management app](../configure/portal-management-app.md), create the site setting **Authentication/OpenIdConnect/AzureAD/Caption** for your specific website and set the name you want.  

More information: [Configure authentication](../security/configure-portal-authentication.md)

## Set up telemetry monitoring

You can place the telemetry tracking HTML/JS snippet of code in the **Enable Traffic Analytics** area in the Portal Management app. 

Open the [Portal Management app](../configure/portal-management-app.md) and navigate to the **Enable Traffic Analysis** section. Enter the snippet from your analytics provider.

:::image type="content" source="media/portal-analytics.png" alt-text="Portal analytics.":::

## Provide access to users

For information on adding users to your site, see [Provide access to external audiences](../security/external-access.md)
