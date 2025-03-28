---
title: Configure site settings for Power Pages sites.
description: Learn how to add and configure site settings for a Power Pages site and global settings for all sites in your organization.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 07/09/2024
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Configure site settings for websites

A site setting is a configurable, named value that is used by website code to modify the behavior or visual style of the site. Typically when a developer creates the website code, they reference site settings for various components to enable an end user to modify the setting values to alter the website without having to change the code, recompile, and redeploy the website.

The sample websites and templates that are provided with the installation of Power Pages contain several configurable site settings for various styles used to modify many visual elements within the site such as background style, text color, and layout width.
You can manage the following types of site settings:

- **Global settings**: These settings apply to all websites associated with the Microsoft Dataverse environment in which they're being added.
- **Website site settings**: These settings apply to specific websites that are associated with the Dataverse environment in which they're being added.

## Manage site settings

1. Using the [Portal Management app](portal-management-app.md), select **Site settings** under the **Website** section.

1. To create a new setting, select **New**.

1. To edit an existing setting, select the **Site Setting** listed in the grid.

1. Specify values for the fields provided: 

    - **Name**:  A label referenced by website code to retrieve the appropriate setting. The name should be unique for the associated website, because the code retrieving the setting takes the first record found with the matching name.
    
    - **Website**:  The associated website. 
    
    - **Value**: The setting
    
    - **Description**: The purpose of the setting or special instructions.

1. Select **Save & Close**.

> [!NOTE] 
> Bing Maps integration is not supported in the German Sovereign Cloud. If you try to create the Bingmaps/credentials setting in this environment, an error message will be displayed.

## Site settings

|Name|Value|Description|
|----|-----|-----------|
|Authentication/Registration/RequiresConfirmation|FALSE |A boolean value of true enables email confirmation and disables open registration. Default: False |
|Authentication/Registration/RequiresInvitation|FALSE |A boolean value of true enables invitation code feature and disables open registration. Default: False |
|HelpDesk/CaseEntitlementEnabled|TRUE|A Boolean value indicating if the Help Desk Case Entitlement is enabled. Default: false|
|HelpDesk/Deflection/DefaultSelectedProductName| |The name of a product record that is the default selected product in dropdown displayed on the Help Desk Case Deflection if there are more than one product where the producttypecode equals 100000001.|
|Profile/ForceSignUp|FALSE|A Boolean value when set to "True" forces the user to update their profile information before they have access to the website contents. Default: False|
|Profile/ShowMarketingOptionsPanel|TRUE|A Boolean value that indicates whether to show the panel that lists the fields to specify the marketing communication preferences on the profile. Default: False|
|Search/Enabled|TRUE|A Boolean value that indicates if search is enabled or not.|
|search/filters|Content:adx_webpage;Events:adx_event,adx_eventschedule;<br>Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;<br>Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;<br>Ideas:adx_ideaforum,adx_idea,adx_ideacomment;<br>Issues:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:incident|A collection of search logical name filter options. Defining a value here adds dropdown filter options to site-wide search. This value should be in the form of name/value pairs, with name and value separated by a colon, and pairs separated by a semicolon.<br>For example: "Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment".|
|Search/IndexQueryName|Portal Search|The name of the system view used by the website search query. Default: Portal Search|
|search/query|+(@Query) _title:(@Query) _logicalname:adx_webpage~0.9^0.2<br> -_logicalname:adx_webfile~0.9 adx_partialurl:(@Query)<br> _logicalname:adx_blogpost~0.9^0.1 -_logicalname:adx_communityforumthread~0.9|Override query for site search, to apply other weights and filters. @Query is the query text entered by a user. Lucene query syntax reference: [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|Search/Stemmer|English|The language used by the website search's stemming algorithm. Default: English|
|CustomerSupport/DisplayAllUserActivitiesOnTimeline|FALSE| |
|Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail| |Allow automatic association to a contact record based on email. </br>More information: [Allow contact mapping with email and require unique email general options](../security/authentication/configure-site.md#select-general-authentication-settings).</br> *Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail* isn't applicable for multitenant endpoints. Use [invitations](/power-apps/maker/portals/configure/invite-contacts) to allow users to authenticate to your website.|
| Site/EnableDefaultHtmlEncoding | True/False | Power Pages release version [9.3.8.x](/power-platform/released-versions/portals/portalupdate938x) or later by default have [escape](/power-apps/maker/portals/liquid/liquid-filters#escape) Liquid filter enforced for [user](/power-apps/maker/portals/liquid/liquid-objects#user) and [request](/power-apps/maker/portals/liquid/liquid-objects#request) Liquid objects. To disable this default configuration and allow these Liquid objects without escape Liquid filter, add this setting and set its value to **False**. |
| EnhancedFileUpload | True/False | Starting with Power Pages release version 9.3.2405.xx, new sites are automatically enabled with the enhanced file upload feature. To opt in for existing websites, add this setting and set its value to **True**. Learn more in [Enable attachments on a form](../getting-started/add-form.md#enable-attachments-on-a-form). |

> [!NOTE]
> *Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail* is not applicable for multi-tenant endpoints and [**Microsoft** identity provider](../security/authentication/oauth2-microsoft.md). Use [invitations](/power-apps/maker/portals/configure/invite-contacts) to allow users to authenticate to your website.

For site settings related to various website features, see:

- [Authentication identity](../security/authentication/set-authentication-identity.md)
- [Azure AD B2C provider](../security/authentication/azure-ad-b2c-provider.md)
- [OAuth 2.0](../security/authentication/oauth2-settings.md)
- [OpenID Connect](../security/authentication/openid-settings.md) 
- [WS-Federation](../security/authentication/ws-federation-provider.md) 
- [SAML 2.0](../security/authentication/saml2-settings.md)
- [Migrate identity providers to Azure AD B2C](../security/authentication/migrate-identity-providers.md)
- [Search within file attachment content](search/file-attachment.md)
- [Behavior and format of the date and time field](./behavior-format-date-time-field.md)
- [Add geolocation](add-geolocation.md)
- [Implementing General Data Protection Regulations](implement-gdpr.md)
- [Enable header and footer output caching](enable-header-footer-output-caching.md)

## Manage global settings

1. Open the [Portal Management app](portal-management-app.md).

1. Go to the **Website** section and select **Settings**.

1. To create a new setting, select **New**.

1. To edit an existing setting, select the **Setting** listed in the grid.

1. Specify values for the fields provided: 

    - **Name**:  A unique name referenced by code to retrieve the appropriate setting.

    - **Value**: The setting

    - **Description**: The purpose of the setting or special instructions.

1. Select **Save & Close**.
