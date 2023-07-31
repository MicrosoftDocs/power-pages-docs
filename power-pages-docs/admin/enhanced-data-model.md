---
title: Enhanced data model
description: Learn how to use the enhanced data model in Power Pages site.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 06/07/2023
ms.subservice:
ms.author: nenandw 
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - neerajnandwana-msft
    - gitanjalisingh33msft
---

# Enhanced data model (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The standard data model was built with custom tables and was optimized for configuration of each website component stored as a record in a dedicated table in Microsoft Dataverse. The standard model requires other time to load the various solutions, tables, and metadata while provisioning a new site. Updates to website tables on the standard model require manual and time consuming application of package updates. 

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

The enhanced data model for Power Pages provides the following benefits:

- faster provisioning of websites
- faster design studio experiences
- allow website configuration to be contained in solutions to provide smoother ALM experiences
- improved updates of Power Pages enhancements and bug fixes

The enhanced data model is combination of system tables, a collection of nonconfiguration tables, and a set of virtual tables.

### Determine if your site is using standard or enhanced data model

You can see which data model your site is using by going to the [Power Platform admin center](https://aka.ms/ppac), go to **Resources** > **Power Pages sites**, select your site, select **Manage** and the **Data Model** value in the **Site Details** indicate what data model the site is using.

:::image type="content" source="media/enhanced-data-model/site-details.png" alt-text="Site details.":::

You'll also be able to view the data model being used from with the **Setup** workspace in the design studio.

You can also identify the data model used by opening the **Portal Management app** application as the new data model application name will be **Power Pages Management** instead of **Portal Management** application. 

:::image type="content" source="media/enhanced-data-model/power-pages-management.png" alt-text="Power Pages Management app.":::

When using the [Power Platform CLI](../configure/power-platform-cli.md), you're able to view which data model is being used by site with the following command:

`pac paportal list -v`

> [!NOTE]
> This parameter is supported from Power Platform CLI version 1.22.4 onwards.

### System tables

The system tables are Power Pages specific solution aware tables present in all Dataverse environments. These system tables can't be modified.

- Site
- Site Component
- Site Language

### Nonconfiguration tables

Nonconfiguration tables are feature specific tables that contain transactional business data. Data in these tables don't participate in ALM processes.

- Ad
- Poll
- Poll Option
- Poll Submission
- External Identity
- Portal comment
- Invitation
- Invitation Redemption
- Setting
- WebFormSession

### Virtual tables

The Power Pages virtual tables represent and contain the metadata of the specific website components. The virtual tables point to the system tables that contain the website metadata in JSON format. The content in the virtual tables can be updated and configured through the [Power Pages management app](#edit-site-using-the-power-pages-management-app) which has the identical look and feel of the legacy [Portal Management app](../configure/portal-management-app.md).

> [!NOTE]
> - If you have developed any custom code or tools that utilizes any of the standard data model tables, you will need to update the code to use the enhanced data model tables.
> - These tables cannot be modified.

| System table | Enhanced data model virtual table | Standard data model table |
| - | - | - |
|powerpagesite|mspp_website|adx_website|
|powerpagesitelanguage|mspp_websitelanguage|adx_websitelanguage|
| powerpagecomponent | mspp_columnpermission</br>mspp_columnpermissionprofile</br>mspp_contentsnippet</br>mspp_entityform</br>mspp_entityformmetadata</br>mspp_entitylist</br>mspp_entitypermission</br>mspp_pagetemplate</br>mspp_pollplacement</br>mspp_publishingstate</br>mspp_publishingstatetransitionrule</br>mspp_redirect</br>mspp_shortcut</br>mspp_sitemarker</br>mspp_sitesetting</br>mspp_webfile</br>mspp_webform</br>mspp_webformmetadata</br>mspp_webformstep</br>mspp_weblink</br>mspp_weblinkset</br>mspp_webpage</br>mspp_webpageaccesscontrolrule</br>mspp_webrole</br>mspp_websiteaccess</br>mspp_websitelanguage</br>mspp_webtemplate</br>|adx_columnpermission</br>adx_columnpermissionprofile</br>adx_contentsnippet</br>adx_entityform</br>adx_entityformmetadata</br>adx_entitylist</br>adx_entitypermission</br>adx_pagetemplate</br>adx_pollplacement</br>adx_publishingstate</br>adx_publishingstatetransitionrule</br>adx_redirect</br>adx_shortcut</br>adx_sitemarker</br>adx_sitesetting</br>adx_webfile</br>adx_webform</br>adx_webformmetadata</br>adx_webformstep</br>adx_weblink</br>adx_weblinkset</br>adx_webpage</br>adx_webpageaccesscontrolrule</br>adx_webrole</br>adx_websiteaccess</br>adx_websitelanguage</br>adx_webtemplate</br>|

## ​​Enable environment for enhanced data model  

You'll first need to enable the enhanced data model on your Power Platform environment before being able to provision a website utilizing the enhanced data model.

> [!NOTE]
> This will add solutions packages to support the enhanced data model on your Power Platform environment.  

Once the enhanced data model is enabled, when you provision a new website using one of the following templates, they utilize the enhanced data model;

- Starter layout 1-5
- Application processing
- Blank page
- Program registration
- Schedule meetings
 
The following templates use the standard data model even if the enhanced data model is enabled on the environment:

- FAQ (preview)
- Community (Dynamics 365)
- Customer Portal (Dynamics 365)
- Customer Self Service Portal (Dynamics 365)
- Employee Self Service Portal (Dynamics 365)
- Field Service (Dynamics 365)
- Modern Community (Dynamics 365)
- Order Returns (Dynamics 365)
- Partner Portal (Dynamics 365)

Follow these steps to enable the new data model for a specific environment.

1. Open the [Power Platform admin center](https://aka.ms/ppac)

1. Select **Environments**

1. Select the environment that you want to enable the new data model. 

1. Select **Power Pages sites** under the **Resources** tile. 

1. Select the **Switch to enhanced data model (preview)** switch from the tool bar.  

    :::image type="content" source="media/enhanced-data-model/switch-to-enhanced-data-model.png" alt-text="Switch to enhanced data model.":::

    This starts installation of the **Power Pages Core** package. You see a message once completed.

    :::image type="content" source="media/enhanced-data-model/packages-installed.png" alt-text="Updated packages installed.":::

You can opt out from new data model site creation by disabling the **Switch to enhanced data model (preview)** option from top tool bar. Disabling the enhanced data model won't remove the solution packages or delete any websites. 

Existing websites created using the enhanced data model continues to operate. Any new website created will use the standard data model.

## Create a website with an enhanced data model 

You can create a new site using Power Pages home page with the new data model once it's enabled for an environment.

> [!NOTE]
> The new site will be created using the new enhanced data model only if it is supported by the selected template. 

Create site using a template of your choice using the new data model:

1. Navigate to the [Power Pages](https://aka.ms/mpp) home page.

1. Select the **Create a site** button.  

1. Select the template and select **Choose this template** to create your site.

1. Fill in the required information and select **Done**.  

You're redirected to the Power pages home page, and the new site appears in the **My sites** list. You can edit the site using Power Pages design studio when the site is ready.

## See list of new data model sites 

You can see the newly created site from the Power Pages home.

The new data model sites are at functional parity, see [Determine if your site is using standard or enhanced data model](#determine-if-your-site-is-using-standard-or-enhanced-data-model) to see which data model your website is using.

All of the available sites in the Power Pages home page **Active sites** section. This list shows sites that are created on the new data model and the existing data model, whether the environment has been enabled for the new data model or not.

## Editing newly created site on new data model  

Site that is created on new data model has functional parity with classic data model and users can use [Power Pages design studio](../getting-started/use-design-studio.md) or [Power Pages management application](../configure/portal-management-app.md) for customization.  

## Edit site using the Power Pages design studio

Users can select **Edit** option from the Power Pages home page site card to open the design studio and edit the site.

> [!NOTE]
> Editing new data model site using design studio will work same as existing data model site without any functionality gaps.  

## Edit site using the Power Pages Management app

Users can select the **Portal management app** option from the Power Pages home site card to open the **Power Pages management** application.  Select the ellipse **…** followed by **Portal management**.

> [!NOTE]
> The new data model comes with new UCI model-driven Power App application with name **Power Pages management.** You will need to use this application for advanced customizations which are not available using the Power Pages design studio.  

You can also open the **Power Pages Management** application from Power Pages design studio. Select the ellipse **…** followed by **Portal management**. 

The **Power Pages Management** application allows you to make advance customizations unavailable in the design studio.

:::image type="content" source="media/enhanced-data-model/edit-site-power-pages-management.png" alt-text="Edit website using Power Pages Management app.":::

## Data model Power Platform CLI parameters

You need to use the `modelVersion` parameter when uploading or downloading enhanced data model website configuration data using the Power Platform CLI. The value of `2` indicates to use the enhanced data model. 

Download
`pac paportal download --path <path> --webSiteId <siteId> --modelVersion 2`

Upload
`pac paportal upload --path <path> --modelVersion 2`

> [!NOTE]
> This parameter is supported from Power Platform CLI version 1.22.4 onwards.

See [Power Platform CLI parameters](../configure/power-platform-cli.md#parameters) for more information.

## Frequently asked questions: 

### How can I update a website from the standard data model to the enhanced data model?

Guidance and tooling support to update from the standard data model to enhanced data model will be delivered in a later update.

### Can I edit new sites based on enhanced data model configurations in the Portal management app? 

New websites created using the enhanced data model can be edited using the new Power Pages Management app.

## Known issues

1. A logged website user sees a list of all supported languages instead of just the website enabled languages on the language selection on the user profile page.

1. The search feature won't return any web page results.

1. Follow the steps in [Set up telemetry monitoring](../go-live/telemetry-monitoring.md) to enable traffic analysis for websites using the enhanced data model.

1. The **Account** table isn't part of the Power Pages management app. This limits adding a parent account record to a contact. As a workaround, [manually add the account table](/power-apps/maker/model-driven-apps/add-edit-app-components#add-a-table) to Power Pages management app.

1. Configuring [list actions](../getting-started/add-list.md#choose-list-actions) on websites with the enhanced data model currently doesn't save the configuration. As a workaround, configure the list using the [Power Pages management app](../configure/list-configuration.md).  

1. You will need to assign contacts to web roles using the **Portal Contact (Enhanced Form)** on the contact record using the Power Pages management app. See [Configure web roles](../security/create-web-roles.md#from-the-contact-with-site-using-enhanced-data-model) for more information.

## See also

- [Using solutions with Power Pages](../configure/power-pages-solutions.md)
- [Power Platform CLI solution management](../configure/power-platform-cli-solution-management.md)