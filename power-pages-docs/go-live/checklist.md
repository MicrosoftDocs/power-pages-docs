---
title: Go live checklist
description: Learn how to go live.
author: NikitaPolyakovMSFT
ms.topic: conceptual
ms.custom: 
ms.date: 03/17/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Go live checklist

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

## Summary

Summary text here

## Tidy up your site

Set your browser suffix "Home page - Starter Portal"

Set your Copyright text in the Footer Web Template

Delete or Deactivate any unused pages - just because it's not in the menu does not mean it's gone

Secure any unfinished functionality behind a separate Web Role 

## Separate Dev, Test, Production

You want a working area to create and test new features away from live production site. While Power Pages offers ability to install more than one site in each Environment, it's almost always impractical to actually accomplish the needed proper separation working in just one Environment.

### Development Environment 

We encourage you to convert from Trial type to Production type as soon as possible, so you do not lose time resetting up your site host again. Your site is safely kept inside Dataverse

Rename your Website record to best represent your project and tell it apart when moving up.

"Contoso Student Portal" or "Student Site"  but not "Student Dev"

### Testing Environment 

New Environment

This is where you do your user testing

### Production Environment 

This is the environment your live customers will use

This is where any invitation workflows with emails - would have final custom domain URLs 

This is where your identity options are finalized and unused ones are removed


## When and why to do performance testing

If you have high scalability needs (think 1000s of users a month or a very critical workload) consider performing load testing to know the type of performance you will get and troubleshoot any problem areas. 

Consider reviewing with your Microsoft Customer Service Account Manager if a Microsoft Customer Engineer can help you, take a look at this post about some ways they can help you: [Power Apps portal: How a Customer Engineer can help - Microsoft Dynamics CRM Community] (https://community.dynamics.com/crm/b/crminthefield/posts/power-apps-portal-how-a-customer-engineer-can-help)


# Get a Custom Domain 
	
Setup custom domain - while we are fine with you using our domain like contosositeprod.powerpages.com - you might really want your users to see your own URL listed like customercenter.contso.com and use that in your invitations

You can read more about setting up [Custom Domains](https://docs.microsoft.com/en-us/power-apps/maker/portals/admin/add-custom-domain) 

# Complete Identity Setup

If you are using it, rename "Azure AD" login button to something like "Contoso Employees". To do so by providing a text value this Site Setting "" for your specific Website. Find it in Site Settings area of Portal Management App <link>

Setup external identity provider. Set this up in Setting up IDPs <link>

Turn off Local Authentication. Set this up in Setting up IDPs <link>

Tip: You would want to finish setup of the custom domain because the redirect URL should be the new fancy one 

# Announce Portal & Invite Users

You want the world to know about your project, or maybe not. But you certainly do If you have passive use-case or self-registration. Consider sending a newsletter and inviting your end-customer user base to the site and let them know what they can expect to do and the value it serves to them.

If you know your end-customers already - bring them in and use the invitation process <link>

Format the Email to include final production custom domain URL and be sure to provide guidance on what they should expect in terms of identity provider as they could mean they can use an existing on or they would need to also create a login profile inside of your identity provider during invitation redemption or self-registration process on your site. 

# Assign Licensing Capacity

Power Pages is cloud service and thus automatically scales to global user demands and needs, one signal for our back-end system to use to auto-scale is looking at your assigned licensing capacity. It's critical this is assigned especially if you anticipate a significant load, so be sure to:

Convert from Trial if not already done so <link>

Assign capacity to Environment the site is in <link>

At the time of writing the Power Pages capacity would be using Power Apps portals constructs of Page View and Portal Login. <link>

# Setup Monitoring

In order to understand statistics for your users you want to capture them right at the launch. Remember you can't in future go back to measure something you did not start to track. Microsoft does not provide an out of the box feature as part of Power Pages at this time. 

You can use any vendor who can do font-end web application telemetry and tracking and monitoring. 

You can place the telemetry tracking HTML/JS snippet of code in the "Enable Traffic Analytics" area inside of Portal Management App <link>

Consider Azure Monitor - Application Insights. Our Microsoft Customer Engineers team wrong this blog post with some tips and other suggestions <link>
