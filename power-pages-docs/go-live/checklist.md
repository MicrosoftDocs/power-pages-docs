---
title: Go-live checklist for Power Pages
description: Learn how to go live.
author: NikitaPolyakovMSFT
ms.topic: checklist
ms.custom: 
ms.date: 05/28/2025
ms.author: nikpol
ms.reviewer: dmartens
contributors:
    - neerajnandwana-msft
---

# Go-live checklist

This checklist is guidance to help you plan your Power Pages projects.

The [Set up workspace](../configure/setup-workspace.md) inside the design studio includes a built-in go-live checklist that includes various interactive tasks that help you prepare your site to go live. These tasks include guided experiences to view and complete recommended actions.

Use the **Go-live checklist** guide to ensure you don't miss anything before your site is up and running. You can also go through additional recommendations in this article to help you extend your go-live preparations and improve the overall site experience when the site goes live.

> [!NOTE]
> The go-live checklist and the additional go-live guidance in this article are recommended actions. The checklist and actions explained in this article aren't mandatory for the site to be up and running.

## Go-live checklist in the Set up workspace

Making site live for production use is critical step, and the **Go-live checklist** section from **Set up workspace** integrates this process seamlessly with your site building activities.

The checklist includes various actions that you can follow up through a step-by-step exercise with a built-in experience that shows the step completion as you progress.

:::image type="content" source="media/go-live-checker.png" alt-text="Go-live checklist option in Set up workspace.":::

Here's the steps included in the go-live checklist:

| Number | Task | Success criteria |
|-------------------------|-------------------------|-------------------------|
| 1 | Run the site checker | 0 Errors in the [site checker](../admin/site-checker.md) last run results |
| 2 | Pick and allocate licenses | [Licenses](assign-licensing.md) are allocated, and acknowledgment in the form of marked as completed |
| 3 | Convert site to production | Site is converted to [production](/power-apps/maker/portals/admin/convert-portal) |
| 4 | Enable CDN to load site faster | [Content Delivery Network (CDN)](/power-apps/maker/portals/configure/configure-cdn) is enabled |
| 5 | Enable WAF to secure your site | [Web application firewall (WAF)](/power-apps/maker/portals/azure-front-door) is enabled |
| 6 | Connect custom domain | [Custom domain](/power-apps/maker/portals/admin/add-custom-domain) configured, is up and working (to check if the URL is accessible) |

Here's an example of how the checklist looks like as the steps progress:

:::image type="content" source="media/verified-checklist.png" alt-text="Go-live checklist once completed.":::

While completing the go-live checklist helps you better prepare and avoid any misses for considerations before the site is up and running, also consider the additional go-live guidance.

## Additional go-live guidance

Apart from the benefits of Go-live checklist, use the following additional guidance to help you plan your Power Pages projects.

### Create separate development, testing, and production sites

To continue to make updates to your site without breaking functionality for existing users of your site, we recommend three separate environments to manage the application development lifecycle. 

More information: [Power Platform application lifecycle management](/power-platform/alm/basics-alm) for more information. 

### Configure authentication set up

By default Power Pages sets local authentication as your identity provider. We recommend using one of the supported identity providers as your default and disabling local authentication.

For example, [Microsoft Entra External ID](../security/authentication/entra-external-id.md).

> [!TIP]
> - Finish setting up your custom domain to utilize the redirect URL for the authentication provider. 
> - If you're using the sign-in button, you can rename it to reflect meaningful label. Using the [Portal Management app](../configure/portal-management-app.md), create the site setting **Authentication/OpenIdConnect/AzureAD/Caption** for your specific website and set the name you want.  

More information: [Configure Power Pages site authentication](../security/authentication/configure-site.md)

### Test your site performance

Optimize your site's performance by enabling a content delivery network (CDN) through the Go-live checker explained earlier. Additionally, for high scalability needs (thousands of users a month or a critical workload), consider performing load testing to understand the type of performance you'll get and troubleshoot any problem areas.

Areas to consider:

- Number of visitors to your site on a daily basis.
- Traffic volumes at different times.
- High traffic pages linked to Microsoft Dataverse.
- Volume of data stored in Dataverse.

### Finalize your site

Clean up your site and remove any sample webpages, sample text, and placeholder images.

Delete or deactivate any unused pages. 

Change your browser suffix from "Home page - Starter Portal" to a meaningful name. You can find the content snippet "BrowserSuffix" in the **Content Snippets** area of the [Portal Management app](../configure/portal-management-app.md)

Set your specific copyright text, and add any privacy or other links in the "Footer" web template. Find it in the **Web templates** area of the [Portal Management app](../configure/portal-management-app.md).

Protect any unfinished page by using [Page permissions](../security/page-security.md).

### Manage site visibility

Configure site visibility after verifying the site is ready to be up and running. More information: [Site visibility](../security/site-visibility.md)

## See also
- [Set up telemetry monitoring](telemetry-monitoring.md)
