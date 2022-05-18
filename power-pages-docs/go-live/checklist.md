---
title: Go live checklist for Power Pages
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

As you prepare and consider going live with your project on Power Pages, there are many items to consider and plan for. Here are a few areas to keep in mind:

 - Tidy up your site
 - Develop an environment strategy
 - Set up monitoring 
 - Do performance testing
 - Set up a custom domain 
 - Complete authentication setup
 - Assign licensing 
 - Set up telemetry monitoring
 - Announce and invite users

We'll go over several of them in this article, and update this article over time as we head towards general availability of Power Pages.

## Tidy up your site

Users of your site should find it in neat and clean. This is the time to remove any sample webpages or stock text, and hide any other unfinished work.

Delete or deactivate any unused pages. Just because it's not in the menu doesn't mean it's gone.

Set your browser suffix "Home page - Starter Portal". You can find the content snippet "BrowserSuffix" in the **Content Snippets** area of the [Portal Management app](../configure/portal-management-app.md)

Set your specific copyright text, and add any privacy or other links in the "Footer" web template. Find it in the **Web templates** area of the [Portal Management app](../configure/portal-management-app.md).

Secure any unfinished functionality behind a separate web role. Learn more about [Page permissions](../security/page-security.md).

## Separate dev, test, production

You want a working area to create and test new features away from your live production site. Although Power Pages lets you install more than one site in each environment, it's almost always impractical to actually accomplish the proper separation you need while working in just one environment.

### Development environment 

We encourage you to convert your site from a trial type to a production type as soon as possible, so you don't lose time setting up your site host again. Your site is safely kept inside Dataverse.

Rename your website record to best represent your project and distinguish it from others—for example, "Contoso Student Portal" or "Student Site", but not "Student Dev"

### Testing environment 

New Environment

This is where you do your user testing.

### Production environment 

This is the environment your live customers will use.

This is where any invitation workflows with emails will have the final, custom domain URLs. 

This is where your identity options are finalized and unused ones are removed.

Consider environment strategy suggestions from Microsoft Power Platform guidance: [Establishing an environment strategy](/power-platform/guidance/adoption/environment-strategy).

## When and why to do performance testing

If you have high scalability needs (think thousands of users a month or a very critical workload), consider performing load testing to understand the type of performance you'll get and troubleshoot any problem areas. 

Consider reviewing with your Microsoft customer service account manager whether a Microsoft customer engineer can help you. Take a look at this post about some ways they can help: [Power Apps portal: How a Customer Engineer can help - Microsoft Dynamics CRM Community](https://community.dynamics.com/crm/b/crminthefield/posts/power-apps-portal-how-a-customer-engineer-can-help).

## Set up a custom domain 

Most users would prefer to visit your site and have greater confidence in it if it had a custom domain name. Although Microsoft is fine with your using our domain (so it would look like contosositeprod.powerpages.com, for example), you likely want your users to see your own URL listed, so it would look like customercenter.contso.com.

You can read more about setting up [custom domains](/power-apps/maker/portals/admin/add-custom-domain). 

Remember that this process takes time on your end to find and get approval from your internal team, get the right SSL certificate, set up this up and test it. You'll want this domain name working for most external identity providers, so it becomes a dependency to go live.

## Complete authentication setup

This is the time to turn off local authentication and only provide the ways you want users to be able to sign in or sign up for your site. 

Set up an external identity provider. Turn off local authentication. 

> [!TIP]
> - You want to finish setting up your custom domain because the redirect URL should be the new fancy one. 
> - If you're using the **Azure AD** sign-in button, rename it to something like **Contoso Employees**. To do so, create the site setting "Authentication/OpenIdConnect/AzureAD/Caption" for your specific website and set the name you want. Find it in the **Site Settings** area of the [Portal Management app](../configure/portal-management-app.md).

More information: [Configure authentication](../security/configure-portal-authentication.md)

## Assign licensing 

Power Pages is a cloud service, and thus automatically scales to global user demands and needs. One signal for our back-end system to use to auto-scale is looking at your assigned licensing capacity. It's critical that this be assigned, especially if you anticipate a significant load, so be sure to:

- Convert from trial if you haven't already done so. <!--link-->

- Assign capacity to the environment the site is in. <!--link-->

At the time, of writing the Power Pages capacity would be using Power Apps portals constructs of Page View and Portal sign in. <!--link-->

## Set up telemetry monitoring

To understand statistics for your users, you want to capture them right at site launch. Remember, in the future you can't go back to measure something you didn't start to track. Microsoft doesn't provide an out-of-the-box feature as part of Power Pages at this time. 

You can use any vendor who can do front-end web application telemetry, tracking, and monitoring. 

You can place the telemetry tracking HTML/JS snippet of code in the **Enable Traffic Analytics** area in the Portal Management app. <!--link-->

Consider Azure Monitor - Application Insights. Our Microsoft Customer Engineers team wrote this blog post with some tips and other suggestions. <!--link-->

## Announce and invite users

You want the world to know about your project, or maybe not. But you certainly do. If you have passive use-case or self-registration. Consider sending a newsletter inviting your customer user base to the site, and let them know what they can expect to do and the value it serves to them.

If you know your customers already, bring them in and use the invitation process. <!--link-->

Format the email to include the final production custom domain URL. Be sure to provide guidance on what they should expect in terms of identity providers. They might be able to use an existing one, or perhaps they'd also need to create a sign-in profile inside of your identity provider during the invitation redemption or self-registration process on your site. 


