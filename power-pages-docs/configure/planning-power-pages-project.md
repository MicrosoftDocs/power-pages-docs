---
title: Plan your Power Pages project
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

# Plan your Power Pages project

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

## Summary 

### Who is this article for

Anyone can benefit from bit of help in planning. 

Everyone has various background and diverse expertise in building apps or sites from none to many. Power Pages is built on the foundation of Power Apps portals. Many of the tools and methods used to configure Power Pages utilize the functionality of Power Apps portals. This also means that we have years of experience and guidance to share with you when you are ready to get started on a project.

Each project might have unique needs and not all elements might be required for all use-cases. Purpose of this article is to bring up a few areas to keep in mind as you embark on your project. We'll cover subjects in more details that are most new, rushed or often missed and will evolve other areas of this material over time. And these subjects are not exclusive to your actual visual design, styling or content and other creative and fun work we know you will already enjoy working on in the Power Pages Studio. Power Pages is a lot of fun so don’t stop exploring and creating. 

### High-level considerations for a site

At high level you want to think about 

- Who will use my site
- What will my users do
- What text and content the site will have
- What is shown publicly and what is secured
- What will users use to sign in or register
- How the data will be segmented after users sign in
- How will my users find my site

## Learn from Microsoft Power Apps strategies 

Because Power Pages is part of Microsoft Power Platform, specifically Microsoft Dataverse and Microsoft Power Apps - there is very good relevant materials available here : [Introduction: Planning a Power Apps project](https://docs.microsoft.com/power-apps/guidance/planning/introduction)

## Audience : anonymous, authenticated, or both

As you might notice when you start to explore your site it's available online to anyone who knows the URL. Our basic starting template has sample web pages to get you inspired, those pages are not secured as they contain sample text and images for inspiration only. As you develop content and data experiences you want to consider if you want those pages secured behind a login - that would mean Authenticated user context. Any pages that do not require a login are referred to as Anonymous or Unauthenticated. 

Your sites can be both, and many of our customers have it this way. For example if you want to have a few pages that do not require login that have helpful information or explain the program, who and how should register, and so on. Then users can register and sign-in to do more granular work with pages and data that you want to secure. Also being Authenticated means you can then specify the exact data your customer sees or modifies about themselves, their parent organization, and any other related records. You can do it all and nothing is defaulted or presumed so you are in control. You also get to control how open you have the registration process, or if you want users to be invited first, it's up to you. 

Remember the default sites out of the box might be setup for easiest but might not represent your unique needs and you can change them.

To make a site Authenticated-only you simply set Page Permissions on the Home page properties, this way any page on the site would require the users to register and sign-in. Learn more here: <Do page for Pages workspace>

## Identity : how will my users sing in 

Many sites you and your end-users navigate today have a Login or Register experience where users either create a new login profile or use an existing login. That login part itself could be their personal and social accounts, corporate credentials or custom login systems - all of those are various **Identity Providers or IdP** for short. 

Power Pages can use many industry standards based Identity Providers. Yon can view the fill list here: [Overview of authentication in Power Apps portals - Power Apps | Microsoft Docs](https://docs.microsoft.com/power-apps/maker/portals/configure/configure-portal-authentication)

Any authenticated user on your site after they register or sign in get a Contact record that represents them. Remember that how you login (Authentication) to a site does not dictate the security of what you do (Authorization). Think of identity as a digital key card in an office building - it's just a digital identifier, which doors the key card opens is stored separately. We'll go over security in the next section, let's dive deeper into identity options first.  

### Internal users

Internal users withing your organization should use **Azure AD**, this also includes you and your project team working on this site, and your internal testers. This is the same login provider as your users use to access Power Platform, Microsoft 365 and likely even their Windows machines too. In many organization this also means very smooth sign-in experience without having to remember your password, since you are already in an active logged in session, including in your web browser where they will use to open your sites. This is great option also because in case user is removed from the organization, so is their Azure AD account - meaning they can't login to Azure AD and they can’t login to your site too. 

Also great news for you is that all sites you create with Power Pages start with Azure AD pre-configured out of the box. That's the Azure AD button you see on the singin page of your site, try it out for yourself! 

Only remove this option if you do not plan to have your internal users or employees use your portal. 

> TIP: We suggest you rename the login button from Azure AD to something more friendly like "Contoso Employees" or "Contoso Work Account" Simply create a Site Setting named "Authentication/OpenIdConnect/AzureAD/Caption" with value of your choice specific to your site. Find Site Settings area in [Portal Management App](https://docs.microsoft.com/power-pages/configure/portal-management-app)

### External users

External users should be using an external identity provider. Let's go over a few options.

**External users : Local Login**

Local Login provider is our legacy option and is not recommend, use it only for quick casual testing early in your project. It's important to know that we are no longer investing in this feature so you would not want to use it in production on a new project. Because this login provider is local to just this specific site, you cannot re-use it across another site, this is frustrating for your end-users. We recommend you Disable Local Login provider especially in Production. See how: [Get started with configuring your authentication](https://docs.microsoft.com/power-apps/maker/portals/configure/use-simplified-authentication-configuration#add-configure-or-delete-an-identity-provider)

**External users : External Identity Provider**

External users are best served by an External Identity Provider.

**Why have an external identity provider?**

Having a single external identity provider would help you onboard users consistently across multiple future sites, other web sites or web or mobile apps in the future. This way your external users have one login they can use without creating yet another login and password. It’s a good idea to spearhead that as long as you are careful to name and brand your identity provider more generic. Consider something simple like "Contoso Login" or "Contoso Student Login" over hyper specific ones like "Contoso EDU Student Meal Plan Portal Login"  

**External users : consider Azure Active Directory B2C**

Consider [Azure Active Directory B2C](https://docs.microsoft.com/azure/active-directory-b2c/overview) - this is external identity provider. You can integrate your custom or corporate identity systems, and enable use of existing social accounts like Microsoft Account, LinkedIn, Google, etc. including an option you set to allow a login profile based on email address to be used.

To look like part of your brand and experience we also support customization of the look and feel to match your needs, see more in: [Customize the Azure AD B2C user interface](https://docs.microsoft.com/en-us/power-apps/maker/portals/configure/azure-ad-b2c)

## Security : what will users get to see and do 

Any authenticated user on your site after they register or login get a Contact record that represents them. Remember that how (Authentication) your login to your site does not dictate what you do (Authorization). Let's talk about what security options you have.

Read about all of the Security features here : [Power Pages Security](https://docs.microsoft.com/power-pages/security/power-pages-security)

Here are a few tips to keep in mind:

- You can protect any page on your site to require authentication via Web Roles. Including your root home page which can make your entire site, authenticated audience only.

- You must make it a habit to think about a table permission for any table used for either your web roles for either authenticated or unauthenticated audiences. 

- Avoid, as in a hurry as you might be to, setting up global scope for your table permissions just to get a form or a list to work. It might be harder to remember to accurately scope it later. You might be leaving more data exposed then you intended. See more in the next section about data modeling.

- Consider if you want features like open registration based on your intended audience.

- Check the default settings like open registration and what does the default web role is setup for all authenticated users allows such users to do and if that fits your security requirements. Be aware that there are default settings that make your site easy to demo and experience as you first get started that might not be best for your specific projects. 

- Consider if your identity provider(s) are setup to validate email addresses. Can you trust the user based on their email address? 

Remember you are in control of what is shared. Test your site to see what various audiences see what users get to do and adjust accordingly. 
	
## Data modeling : how will users interact with data 

Here we are talking about Data workspace and Tables you build there and what design considerations you should think about. Let’s break it down into two - users are either authenticated and we can get very specific or they are anonymous.

### Anonymous users data design

This one is most simple because you do not have an option to get granular nor you would do anything specific in the data design. 

What if you wanted to allow read so anonymous users can see data? You won’t need anything special in the data model, but consider that you will either show all or no records because if you assign global permission for all anonymous users the entire table you setup that way is shown in a list or form that you will surface on the public page.

What if you wanted to allow creation of records for anonymous users? Same here, any users without login can create a number of records after you enable create and global for a table permission on such table and put a create form on a public page. 

### Contextual authentication users data design

Any authenticated user on your site after they register or login get a Contact record that represents them. 

There is a native built-in relationship to Accounts table in Dataverse that each Contact record has. You have to intentionally make this association yourself or via automation or data job you design. Again you are in control of this field. If you have another relationship you rather create to a custom table in Dataverse, you are free to do so, you are not limited.

Knowing this now if we wanted to segment data for users and their organizations, we have the right tools already waiting for us.

Review documentation Table Permission to learn more about Contact, Account scope as those are the important building blocks if you want contextual data security.  Read more: [Power Pages Security](https://docs.microsoft.com/power-pages/security/power-pages-security)

Let's say we have orders we want suppliers to review when they login, we would want to add a Lookup field for Account table. We want to select a few Accounts on each Order record. We then want to setup just the right Contacts to such Accounts. Then when those contacts login to the portal they will only see the orders intended for them. Even if another supplier sends them a link or savvy users tries to use any of our APIs they will not be able to touch data not linked to them, it's protected at platform level no matter how the users ask for the data. 

## Consider separating development from production

You want a working area to create and test new features away from live production site. While Power Pages offers ability to install more than one site in each Environment, it's almost always impractical to actually accomplish the needed proper separation working in just one Environment. 

In short you should not go live on the same site you are working on right now. If you invite users to the site you are working on, it's hard to get them to stop coming here and go to your intended final one. 

We will go into this deeper in [Go live checklist](https://docs.microsoft.com/power-pages/go-live/checklists)

## Case for user testing

You want to have a stable test site for your internal stakeholders and any early external testers. This will allow you to have a stable place where users can test while you work on more features and fine tuning in your Development environment. You want to list out core outcomes and ensure you have full complete test scenarios documented somewhere for yourself and shared with testers. 

## Why you will want a custom domain

As you start to look towards your own Preview or Go Live you will want want a custom domain like ContosoPartnerRegistration.com or Students.Contoso.edu While Power Pages comes with subdomain URLs for your convenience under the .PowerPages.com domain (Ex: ContosoPartners.PowerPages.com), that is unlikely how you'd want to present your site to your users. Maybe your internal users would not need a flashy URL, but anyone external you really should invest in getting a custom domain. 

This is where you need your own internal IT team to help you get one because Power Pages does not own those. As you start to look towards your own Preview or Go Live be sure to reach out and start this discussion internally so everyone has ample time to get ready. Remember your production setup for external identity provider would want the final URLs and your invitations and confirmation emails and anything else user-facing would like to have the final URLs. 

To save time please send this helpful information to your IT team as they need to know our requirements for the SSL Certificate that will be required in order to setup your Custom Domain. You can read more about setting up [Custom Domains](https://docs.microsoft.com/en-us/power-apps/maker/portals/admin/add-custom-domain) 

## Check out our Go Live Checklist

If you want to peak ahead be sure to check out [Go live checklist](https://docs.microsoft.com/power-pages/go-live/checklist)
