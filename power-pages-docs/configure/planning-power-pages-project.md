---
title: Planning your Power Pages project
description: Learn how to plan for a Power Pages project.
author: NikitaPolyakovMSFT
ms.topic: conceptual
ms.custom: 
ms.date: 04/27/2022
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

This article is not about mechanics or detailed how to building sites with Power Pages but what you should consider and think about the overall project.

## What does this article cover

This article will cover topics like:

- Audiences of users of my site
- Options for how users can login to my site
- Options you have for securing your pages and data
- Learn about data modeling considerations for your sites 
- Why you should test and have separate test and live production site
- What and why you will need a custom domain URL for your site

## Set clear goals for your project

Building sites is exciting and could be overwhelming especially your first time. Consider coming up with a few simple goals to keep you focused and on track. Allow yourself to be iterative and involve others for feedback; even consider a pilot program with a few close real end-users of your site, they will provide the best feedback. Ship in smaller iterations but more often, if applicable. 

## Anonymous, Authenticated, or both

As you might notice when you start to explore your site it's available online to anyone who knows the URL. Our basic starting template has sample web pages to get you inspired, those pages are not secured as they contain sample text and images for inspiration only. As you develop content and data experiences you want to consider if you want those pages secured behind a login - that would mean Authenticated user context. Any pages that do not require a login are referred to as Anonymous or Unauthenticated. 

Your sites can be both, and many of our customers have it this way. For example if you want to have a few pages that do not require login that have helpful information or explain the program, who and how should register, and so on. Then users can register and sign-in to do more granular work with pages and data that you want to secure. Also being Authenticated means you can then specify the exact data your customer sees or modifies about themselves, their parent organization, and any other related records. You can do it all and nothing is defaulted or presumed so you are in control. You also get to control how open you have the registration process, or if you want users to be invited first, it's up to you. 

Remember the default sites out of the box might be setup for easiest but might not represent your unique needs and you can change them.

To make a site Authenticated-only you simply set Page Permissions on the Home page properties, this way any page on the site would require the users to register and sign-in. Learn more here: <Do page for Pages workspace>

## Users Identity

Many sites you and your end-users navigate today have a Login or Register experience where users either create a new login profile or use an existing login. That login part itself could be their personal and social accounts, corporate credentials or custom login systems - all of those are various identity providers or IdP for short. Power Pages can use many industry standards based Identity Providers. Yon can view the fill list here: <link>

Any authenticated user on your site after they register or login get a Contact record that represents them. Remember that how (Authentication) your login to your site does not dictate what you do (Authorization). Think of identity as a key or a digital key card. 

### Internal users

Internal users withing your organization should use Azure AD, this also includes you and your project team working on this site, and your internal testers. This is the same login provider as your users use to access Power Platform, Microsoft 365 and likely even their Windows machines too. In many organization this also means very smooth sign-in experience without having to remember your password, since you are already in an active logged in session. This is great option also because in case user is removed from the organization, so is their Azure AD account - meaning they can't login to Azure AD and they can’t login to your site too. Great news is that all sites you create with Power Pages start with Azure AD pre-configured out of the box. Only remove this option if you do not plan to have your internal users or employees use your portal. We suggest you rename the login button from Azure AD to something more friendly like "Contoso Employees" or "Contoso Work Account"

### External users

External users should be using an external identity provider. Let's go over a few options.

### External users : Local Login

Local Login provider is our legacy option and is not recommend, use it only for quick casual testing early in your project. It's important to know that we are no longer investing in this feature so you would not want to use it in production on a new project. Because this login provider is local to just this specific site, you cannot re-use it across another site, this is frustrating for your end-users. We recommend you Disable Local Login provider especially in Production. See how: Setting up Identity Providers : Setting Default <link>

### External users : External Identity Provider 

External users are best served by an External Identity Provider>

### External users : Our Recommendation

Consider Azure AD B2C you might qualify for sizable initial set of users (50,000 monthly logins free at time of writing) <link>

### Why have an external identity provider?
Having a single external identity provider would help you onboard users consistently across multiple future sites, other web sites or web or mobile apps in the future. This way your external users have one login they can use without creating yet another login and password. It’s a good idea to spearhead that as long as you are careful to name and brand your identity provider more generic. Consider something simple like "Contoso Login" or "Contoso Student Login" over hyper specific ones like "Contoso EDU Student Meal Plan Portal Login"  

## Security

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

## Onboard Users via Invitation 

Now that we have started to consider how we will model any data, you know that users are Contact records and we store their idenitty in External Identity rows related to each Contact. If you are migrating from another web experience and you already know all your users - you can do a data job and pre-load all the contacts, their user identity information and they can login seamlessly into your new portal and have an expected experience of you knowing exactly who they are.

So what is Invitation process? If you will have a scenario where you know your customers or customers come in via other systems and you need to invite them to a portal and link them to the Contact record you already have in Dataverse.


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

If you have high scalability needs (think 1000s of users a month or a very critical workload) consider performing load testing to know the type of performance you will get and troubleshoot any problem areas. 

Consider reviewing with your Microsoft Customer Service Account Manager if a Microsoft Customer Engineer can help you, take a look at this post about some ways they can help you: Power Apps portal: How a Customer Engineer can help - Microsoft Dynamics CRM Community
	
## Custom Domain

Microsoft offers you the URLs for your convenience under our PowerPages.com domain, but that is unlikely how you'd want to present your site to your users. You want a customer domain like ContosoStudents.com or Students.Contoso.edu - this is where you need your own IT team to help you. Be sure to reach out and start this discussion as you start to look towards your own Preview or Go Live. 

You can read more about setting up Custom Domains here: 

Please send this helpful information to your IT team as they need to know our requirements for the SSL Cert that will be needed to setup a Custom Domain <link> 

## Also consider good strategies from Microsoft Power Apps 

https://docs.microsoft.com/power-apps/guidance/planning/introduction

## See Also Go Live Checklist
<>


