---
title: Plan your Power Pages project
description: Learn how to plan for a Power Pages project.
author: NikitaPolyakovMSFT
ms.topic: conceptual
ms.custom: 
ms.date: 05/13/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - NikitaPolyakovMSFT
    - ProfessorKendrick
---

# Plan your Power Pages project

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)] 

This article serves as guidance for enterprise teams working on projects that may go beyond the scope of a maker creating a site for a specific business need. Creating a plan with clear outcomes and expectations is always good practice regarding the size of your project.

> [!NOTE]
> Power Pages is built on a foundation of Power Apps portals. Many of the tools and methods used to configure Power Pages utilize the functionality of Power Apps portals. For more information, see [Introduction: Planning a Power Apps project](/power-apps/guidance/planning/introduction).

As you begin to plan your first Power Pages project, consider the following questions:

- Who will use my site?
- What will my users do?
- What text and content the site will have?
- What is shown publicly and what is secured?
- What will users use to sign in or register?
- How the data will be segmented after users sign in?
- How will my users find my site?

Answering these questions will help guide discussions as you embark on your project. Each project has unique needs and not all elements discussed will be required in every use case. 

## Audience

Our default template has basic web pages configured to help you get started. These template pages aren't secured and contain sample text and images for inspiration only. As you develop content and data experiences, you may wish to require authentication to access certain pages. Customize your Power Pages site to meet your organization's unique needs.

### Anonymous users
Pages that don't require a sign-in are referred to as anonymous or unauthenticated. 

### Authenticated users
Authenticated pages allow you to specify the exact data your customer sees or modifies. To make a site Authenticated-only, set page permissions on the home page properties.  This setting will require users to register and sign in before seeing content on any page of the site. For more information, see [Page permissions](../security/page-security.md). 

Any authenticated user on your site is tied to a contact record in Dataverse. Remember, your site authentication doesn't dictate your authorization.  Your authentication is simply a digital identifier, which grants access to specific pages.

## Access 

Many sites today include a sign- in or register experience where users either create a new sign-in profile or use an existing sign-in to access site pages.  These sign-in credentials could be tied to their social accounts or their corporate credentials.  These credentials are examples of Identity Providers(IdP). Power Pages works with many industry standard Identity Providers. 

View the full list here: [Overview of authentication in Power Apps portals - Power Apps | Microsoft Docs](/portals/configure/configure-portal-authentication)

### Internal users

Users within your organization should use **Azure AD**.Using Azure AD provides a seamless sign-in experience via use of an active session.  Using Azure AD also aids in site security.  When a user leaves the organization, their Azure AD account is disabled and they can no longer access the protected pages on your site. For your convenience, all Power Pages sites come with Azure AD pre-configured.

> [!TIP] 
> Rename the login button from Azure AD to something more friendly like "Contoso Employees" or "Contoso Work Account" Simply create a Site Setting named "Authentication/OpenIdConnect/AzureAD/Caption" and specify the value you wish to display. For more information, see [Portal Management App](portal-management-app.md).

### External users

External users should be using an external identity provider. Having a single external identity provider can help onboard users consistently across multiple sites or apps.  Your users can access these using a single set of credentials for their convenience. Power Pages offers several options.

[Azure Active Directory B2C](/azure/active-directory-b2c/overview) is one option you might consider for an identity provider. Integrate your custom or corporate identity systems.  You can enable the use of existing social accounts like Microsoft Account, LinkedIn, Google, including an option you set to allow a sign-in profile based on an email address.

You can also customize the look and feel to match your needs, see more in: [Customize the Azure AD B2C user interface](/power-apps/maker/portals/configure/azure-ad-b2c)

> [!NOTE] 
> We strongly recommend that you Disable Local sign-in providers.  For more information, see [Get started with configuring your authentication](/power-apps/maker/portals/configure/use-simplified-authentication-configuration#add-configure-or-delete-an-identity-provider)

## Security

Power Pages allows you to create secure sites.  

You can protect any page and data on your site. For more information, see [Power Pages Security](../security/power-pages-security.md).

You can set table permissions to configure web roles for authenticated and unauthenticated audiences. For more information, see [Assign table permissions](../security/assign-table-permissions.md).

> [!NOTE]
> Avoid setting global scope for table permissions. Doing so may leave more data exposed than you intended.

You can allow open registration or use identity providers to validate email addresses. For more information, see [Provide access to external audiences](../security/external-access.md).

## Data modeling

The Data workspace allows you to interact directly with data stored in Dataverse. Once you enable permissions, anonymous users can create records by interacting with a form on a public page. 

### Anonymous users data design

You don't need to do anything specific in the data design to grant read access. If you assign global table permissions for the anonymous web role, all the data will display in a list or form when they access the page.

### Contextual authentication users data design

Authenticated users on your site are represented by a corresponding contact record once they sign in. There's a native, built-in relationship between the Accounts table and each contact record.  You can make modifications to this association if you choose.  For more information about contextual data security, see [Power Pages security](../security/power-pages-security.md).

## Recommendations for your first project

### Separate development from production

While Power Pages offers the ability to install more than one site in each Environment, we recommend creating an area separate from production to create and test new features.  For more information, see [Go live checklist](../go-live/checklist.md).

### Conduct user testing

We strongly recommend creating a stable test site for internal stakeholders and early external testers.  A test site will allow you to fine tune your Development environment.  

### Secure a custom domain

Creating a custom domain for your go live is recommended. Reach out to your internal IT team to secure one in advance of your go live date.

Requirements for the SSL Certificate that will be required in order to set up your Custom Domain are specified in our documentation. For more information, see [Custom Domains](/power-apps/maker/portals/admin/add-custom-domain).

### Use our Go Live Checklist

We've created a [Go live checklist](../go-live/checklist.md) for you to use to ensure a successful go live.  

## See also
[Introduction: Planning a Power Apps project](/power-apps/guidance/planning/introduction)
