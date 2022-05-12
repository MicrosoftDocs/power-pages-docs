---
title: Go live checklist
description: Learn how to go live.
author: NikitaPolyakovMSFT
ms.topic: conceptual
ms.custom: 
ms.date: 05/06/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Go live checklist

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

## Summary

As you prepare and consider going live with your project on Power Pages there are many items to consider and plan for. 

Here are just a few areas to keep in mind:

 - Tidy up your site
 - Environment strategy
 - Performance testing
 - Set up custom domain 
 - Complete authentication setup
 - Assign licensing 
 - Set up telemetry monitoring
 - Announce and invite users

We will go over several of them in this article. We will evolve this article over time as we head towards General Availability of Power Pages.

## Tidy up your site

Users of your site should find it in neat clean. This is the time to remove any sample web pages, stock text and hide any other unfinished work.

Delete or Deactivate any unused pages - just because it's not in the menu does not mean it's gone

Set your browser suffix "Home page - Starter Portal" find the Content Snippet "BorwserSuffix" Find it in Content Snippets area of [Portal Management App](https://review.docs.microsoft.com/power-pages/configure/portal-management-app)

Set your specific Copyright text and add any Privacy and others links in the "Footer" Web Template. Find it in Web Templates area of [Portal Management App](https://review.docs.microsoft.com/power-pages/configure/portal-management-app)

Secure any unfinished functionality behind a separate Web Role. Learn more about [Page permissions](https://review.docs.microsoft.com/power-pages/security/page-security)

## Separate Dev, Test, Production

You want a working area to create and test new features away from live production site. While Power Pages offers ability to install more than one site in each Environment, it's almost always impractical to actually accomplish the needed proper separation working in just one Environment.

### Development Environment 

We encourage you to convert from Trial type to Production type as soon as possible, so you do not lose time resetting up your site host again. Your site is safely kept inside Dataverse

Rename your Website record to best represent your project and tell it apart when moving up. "Contoso Student Portal" or "Student Site"  but not "Student Dev"

### Testing Environment 

New Environment

This is where you do your user testing

### Production Environment 

This is the environment your live customers will use

This is where any invitation workflows with emails - would have final custom domain URLs 

This is where your identity options are finalized and unused ones are removed

Consider environment strategy suggestions from Power Platform guidance - [Establishing an Environment Strategy - Microsoft Power Platform - Power Platform | Microsoft Docs](https://docs.microsoft.com/power-platform/guidance/adoption/environment-strategy)


## When and why to do performance testing

If you have high scalability needs (think 1000s of users a month or a very critical workload) consider performing load testing to know the type of performance you will get and troubleshoot any problem areas. 

Consider reviewing with your Microsoft Customer Service Account Manager if a Microsoft Customer Engineer can help you, take a look at this post about some ways they can help you: [Power Apps portal: How a Customer Engineer can help - Microsoft Dynamics CRM Community](https://community.dynamics.com/crm/b/crminthefield/posts/power-apps-portal-how-a-customer-engineer-can-help)


# Setup custom domain 
	
Most users would prefer and have confidence in your site, if it had a custom domain name. While Microsoft is fine with you using our domain like contosositeprod.powerpages.com - you likely want your users to see your own URL listed like customercenter.contso.com 

You can read more about setting up [Custom Domains](https://docs.microsoft.com/en-us/power-apps/maker/portals/admin/add-custom-domain) 

Remember that this process takes time on your end to find and get approval from your internal team, get the right SSL Certificate, setup this up and test it. All before the real users get the domain name working. You'll want this domain name working for most external identity providers, so it's becoming a dependency to go live.

# Complete authentication setup

This is the time to turn off and only provide the final desired ways users can sing in or sing up to your site. 

Setup external identity provider. Turn off Local Authentication. 

> Tip: You would want to finish setup of the custom domain because the redirect URL should be the new fancy one 

> TIP: If you are using it, rename "Azure AD" login button to something like "Contoso Employees". To do so create Site Setting "Authentication/OpenIdConnect/AzureAD/Caption" for your specific Website and set a desired value. Find it in Site Settings area of [Portal Management App](https://review.docs.microsoft.com/power-pages/configure/portal-management-app)

Read more in [Configure authentication](https://review.docs.microsoft.com/power-pages/security/configure-portal-authentication)

# Assign licensing 

Power Pages is cloud service and thus automatically scales to global user demands and needs, one signal for our back-end system to use to auto-scale is looking at your assigned licensing capacity. It's critical this is assigned especially if you anticipate a significant load, so be sure to:

Convert from Trial if not already done so <link>

Assign capacity to Environment the site is in <link>

At the time of writing the Power Pages capacity would be using Power Apps portals constructs of Page View and Portal Login. <link>

# Set up telemetry monitoring

In order to understand statistics for your users you want to capture them right at the launch. Remember you can't in future go back to measure something you did not start to track. Microsoft does not provide an out of the box feature as part of Power Pages at this time. 

You can use any vendor who can do font-end web application telemetry and tracking and monitoring. 

You can place the telemetry tracking HTML/JS snippet of code in the "Enable Traffic Analytics" area inside of Portal Management App <link>

Consider Azure Monitor - Application Insights. Our Microsoft Customer Engineers team wrong this blog post with some tips and other suggestions <link>

# Announce and invite Users

You want the world to know about your project, or maybe not. But you certainly do If you have passive use-case or self-registration. Consider sending a newsletter and inviting your end-customer user base to the site and let them know what they can expect to do and the value it serves to them.

If you know your end-customers already - bring them in and use the invitation process <link>

Format the Email to include final production custom domain URL and be sure to provide guidance on what they should expect in terms of identity provider as they could mean they can use an existing on or they would need to also create a login profile inside of your identity provider during invitation redemption or self-registration process on your site. 

