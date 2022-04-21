---
title: Planning your Power Pages project
description: Learn how to use the Portal Management app.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 03/17/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - NikitaPolyakovMSFT
---

# Planning Power Pages project

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]


## Who is this article for

We all have various experiences and expertise in building apps or sites. Each project might have unique needs. Purpose of this article is to bring up a few areas to keep in mind as you embark on a new or maybe revisit a previous project.

## Set clear goals for your project

Building sites is exciting and could be overwhelming especially your first time. Consider coming up with a few simple goals to keep you focused and on track. Allow yourself to be iterative and involve others for feedback; even consider a pilot program with a few close real end-users of your site, they will provide the best feedback. Ship in smaller iterations but more often, if applicable. 

## Anonymous vs Authenticated 

Your site comes with sample web pages to get you inspired, those pages are not secured as they contain sample text and images for inspiration only. As you develop content and data experiences you want to consider if you want those pages secured behind a login - that would mean Authenticated user context.

## Users Identity

Many sites you and your end-users navigate today have a Login or Register experience where users either create a new login profile or use an existing login. That login part itself could be their personal and social accounts, corporate credentials or custom login systems - all of those are various identity providers or IdP for short. Power Pages can use many industry standards based Identity Providers. Yon can view the fill list here: <link>

Any authenticated user on your site after they register or login get a Contact record that represents them. Remember that how (Authentication) your login to your site does not dictate what you do (Authorization). Think of identity as a key or a digital key card. 

### Internal Users

Internal users withing your organization should use Azure AD that should include you, your project team working on this site, and your testers. This is the same login provider as your users use to access Power Platform, Microsoft 365 and likely their Windows machines too. This is great option because in case user is removed from the organization, so is their access to your sites. Great news is that all sites you create with Power Pages start with Azure AD pre-configured. Only remove this option if you do not plan to have your employees use your portal. We suggest you rename the login button from Azure AD to something more friendly like "Contoso Employees" or "Contoso Work Account"

### External Users

External users should be using an external identity provider. Let's go over a few options.

### Local Login

Local Login provider is our legacy option and is not recommend, use it only for quick casual testing early in your project. It's important to know that we are no longer investing in this feature so you would not want to use it in production on a new project. Because this login provider is local to just this specific site, you cannot re-use it across another site, this is frustrating for your end-users. We recommend you Disable Local Login provider especially in Production. See how: Setting up Identity Providers : Setting Default <link>

### Recommendation

Consider Azure AD B2C you might qualify for sizable initial set of users (50,000 monthly logins free at time of writing) <link>

### Why have an external identity provider?
Having a single external identity provider would help you onboard users consistently across multiple future sites, other web sites or web or mobile apps in the future. This way your external users have one login they can use without creating yet another login and password. It’s a good idea to spearhead that as long as you are careful to name and brand your identity provider more generic. Consider something simple like "Contoso Login" or "Contoso Student Login" over hyper specific ones like "Contoso EDU Student Meal Plan Portal Login"  

## Users Security

Any authenticated user on your site after they register or login get a Contact record that represents them. Remember that how (Authentication) your login to your site does not dictate what you do (Authorization). Think of identity as a key or a digital key card. We'll now talk about the what a user gets to do once they are authenticated. 

Remember you are in control of what is shared. Do be aware that there are default settings that make your site easy to demo and experience as you get started that might not be best for all real projects. 

Default Web Roles Explained

Default Settings / Open Registration

<link to Profile Authentication article>
	
## Data Modeling Considerations

Any authenticated user on your site after they register or login get a Contact record that represents them. 

There is a native built-in relationship to Accounts table in Dataverse that each Contact record has. You have to intentionally make this association yourself or via automation or data job you design. Again you are in control of this field. If you have another relationship you rather create to a custom table in Dataverse, you are free to do so, you are not limited.

Knowing this now if we wanted to segment data for users and their organizations, we have the right tools already waiting for us.

Review Doc for Table Permission to learn more about Contact, Account scope. <link>

Let's say we have orders we want suppliers to review when they login, we would want to add a Lookup field for Account table. We want to select a few Accounts on each Order record. We then want to setup just the right Contacts to such Accounts. Then when those contacts login to the portal they will only see the orders intended for them. Even if another supplier sends them a link or savvy users tries to use the Portal Web API they will not be able to touch data not linked to them.

What if you wanted to allow read so anonymous users can see data?

What if you wanted to allow creation of records for anonymous users?

## Onboard User Invitation Strategy 

Now that we have started to consider how we will model any data,

## Portal Project Team Helpful Skills to go Next Level

Everyone brings different skill sets to each project. Power Pages make is easy for just about anyone to get started and launch a site. However there are some skills or experience in building sites that would enable your project to accelerate. 

## Consider separate Dev, Test, Production

You want a working area to create and test new features away from live production site. While Power Pages offers ability to install more than one site in each Environment, it's almost always impractical to actually accomplish the needed proper separation working in just one Environment.

### Development Environment 

We encourage you to convert from Trial type to Production type as soon as possible, so you do not lose time resetting up your site host again. Your site is safely kept inside Dataverse

Rename your Website record to best represent your project and tell it apart when moving up.

"Contoso Student Portal" or "Student Site"  but not "Student Dev"

### Testing Environment 

New Environment

Add new Portal

Moving your relevant Dataverse tables in a Solution 

Move your Portal configuration

Update Portal configuration to use your Portal "Student Site" not "Default Template"
	
### Production Environment 

This is the environment your live customers will use

Repeat same as Testing

If you have any invitation workflows with emails - here is where you setup final production URLs 

Follow more guidance in setting up in Go Live Check link <link>

Here are some other tips from across the Power Platform about good ALM practices.

## User Testing

You want to have a stable test site for your internal stakeholders and any early external testers. This will allow you to have a stable place where users can test while you work on more features and fine tuning in your Development environment. 

You want to list out core outcomes and ensure you have full complete test scenarios documented somewhere for yourself and shared with testers. 

You want your testers to report and take screenshots or recording of what happened. Doing this in a Test Environment would allow you to re-test this, then Development address the issue, move the fix to Test Environment to confirm it's addressed before moving the change up to Production.

## Load Testing

If you have high scalability needs (think 1000s of users a month or any critical workload)
Link to How Microsoft Customer Engineer 
Power Apps portal: How a Customer Engineer can help - Microsoft Dynamics CRM Community
	
## Custom Domain

Review with IT dept requirement from the SSL Cert you will need that, <link>

## Consider good strategies from Power Apps 

https://docs.microsoft.com/en-us/power-apps/guidance/planning/introduction

## See Also Go Live Checklist

