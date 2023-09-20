---
title: Enhanced data model
description: Learn how to use the enhanced data model in a Power Pages site.
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

# Enhanced data model 

The standard data model was built by using custom tables, and it was optimized for the configuration of each website component that is stored as a record in a dedicated table in Microsoft Dataverse. The standard model requires additional time to load the different solutions, tables, and metadata when a new site is provisioned. Updates to website tables in the standard model require manual and time-consuming application of package updates.

>[!NOTE]
> 
> - All new sites will be created by default using the enhanced data model.  
>- To use the standard data model, use the toggle switch in the top menu bar to disable the Enhanced Data Model.

The enhanced data model for Power Pages provides the following benefits:

- Provisioning of websites is faster.
- Design studio experiences are faster.
- Website configurations can be contained in solutions to provide smoother Application Lifecyle Management (ALM) experiences.
- Updates of Power Pages enhancements and bug fixes are improved.

The enhanced data model is a combination of system tables, nonconfiguration tables, and virtual tables.

## Determine whether your site is using the standard or enhanced data model

There are several ways to determine which data model your site is using:

- Open [Power Platform admin center](https://aka.ms/ppac), go to **Resources** \> **Power Pages sites**, select your site, and then select **Manage**. The **Data Model** field in the **Site Details** section indicates which data model is being used.

    :::image type="content" source="media/enhanced-data-model/site-details.png" alt-text="Screenshot that shows the Data Model field set to Enhanced in the Site Details section for a site.":::

- The **Setup** workspace in the Power Pages design studio shows which data model is being used.
- Open the Portal Management app. If the standard data model is being used, the application name is shown as **Portal Management**. If the enhanced data model is being used, the name is shown as **Power Pages Management**.

    :::image type="content" source="media/enhanced-data-model/power-pages-management.png" alt-text="Screenshot of the Power Pages Management app.":::

- If you're using the [Power Platform CLI](../configure/power-platform-cli.md), run the following command to view which data model is being used.

    `pac powerpages list -v`

    > [!NOTE]
    > This parameter is supported in Power Platform CLI version 1.22.4 and later.

## System tables

The system tables are Power Pages–specific solution-aware tables that are present in all Dataverse environments.

> [!NOTE]
> These tables can't be modified.

- Site
- Site Component
- Site Language

## Nonconfiguration tables

Nonconfiguration tables are feature-specific tables that contain transactional business data. Data in these tables doesn't participate in ALM processes.

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

## Virtual tables

The Power Pages virtual tables represent and contain the metadata of the specific website components. They point to the system tables that contain the website metadata in JavaScript Object Notation (JSON) format. You can update and configure the content of the virtual tables by using the [Power Pages Management app](#edit-a-site-by-using-the-power-pages-management-app). This app has the same look and feel as the older [Portal Management app](../configure/portal-management-app.md).

> [!NOTE]
> - If you've developed any custom code or tools that use any of the standard data model tables, you must update the code so that it uses the enhanced data model tables.
> - These tables can't be modified.

| System table | Enhanced data model virtual table | Standard data model table |
|---|---|---|
| powerpagesite | mspp\_website | adx\_website |
| powerpagesitelanguage | mspp\_websitelanguage | adx\_websitelanguage |
| powerpagecomponent | mspp\_columnpermission<br>mspp\_columnpermissionprofile<br>mspp\_contentsnippet<br>mspp\_entityform<br>mspp\_entityformmetadata<br>mspp\_entitylist<br>mspp\_entitypermission<br>mspp\_pagetemplate<br>mspp\_pollplacement<br>mspp\_publishingstate<br>mspp\_publishingstatetransitionrule<br>mspp\_redirect<br>mspp\_shortcut<br>mspp\_sitemarker<br>mspp\_sitesetting<br>mspp\_webfile<br>mspp\_webform<br>mspp\_webformmetadata<br>mspp\_webformstep<br>mspp\_weblink<br>mspp\_weblinkset<br>mspp\_webpage<br>mspp\_webpageaccesscontrolrule<br>mspp\_webrole<br>mspp\_websiteaccess<br>mspp\_websitelanguage<br>mspp\_webtemplate<br> | adx\_columnpermission<br>adx\_columnpermissionprofile<br>adx\_contentsnippet<br>adx\_entityform<br>adx\_entityformmetadata<br>adx\_entitylist<br>adx\_entitypermission<br>adx\_pagetemplate<br>adx\_pollplacement<br>adx\_publishingstate<br>adx\_publishingstatetransitionrule<br>adx\_redirect<br>adx\_shortcut<br>adx\_sitemarker<br>adx\_sitesetting<br>adx\_webfile<br>adx\_webform<br>adx\_webformmetadata<br>adx\_webformstep<br>adx\_weblink<br>adx\_weblinkset<br>adx\_webpage<br>adx\_webpageaccesscontrolrule<br>adx\_webrole<br>adx\_websiteaccess<br>adx\_websitelanguage<br>adx\_webtemplate<br> |

## Enable the enhanced data model in an environment

Before you can provision a website that uses the enhanced data model, you must enable the enhanced data model in your Microsoft Power Platform environment.

> [!NOTE]
> This process adds solutions packages to support the enhanced data model in your Microsoft Power Platform environment.

After you enable the enhanced data model, any new website that you provision by using one of the following templates uses the enhanced data model:

- Starter layout 1-5
- Application processing
- Blank page
- Program registration
- Schedule meetings

The following templates use the standard data model even if the enhanced data model is enabled in the environment:

- FAQ (preview)
- Community (Dynamics 365)
- Customer Portal (Dynamics 365)
- Customer Self Service Portal (Dynamics 365)
- Employee Self Service Portal (Dynamics 365)
- Field Service (Dynamics 365)
- Modern Community (Dynamics 365)
- Order Returns (Dynamics 365)
- Partner Portal (Dynamics 365)

Follow these steps to enable the enhanced data model in a specific environment:

1. Open [Power Platform admin center](https://aka.ms/ppac).
1. Select **Environments**.
1. Select the environment that you want to enable the enhanced data model in.
1. On the **Resources** tile, select **Power Pages sites**.
1. On the toolbar, enable the **Switch to enhanced data model (preview)** option.



    Installation of the **Power Pages Core** package begins. After installation is completed, you receive a message.

You can opt out of using the enhanced data model for site creation by disabling the **Switch to enhanced data model** option. If you disable the enhanced data model, you do **not** remove the solution packages or delete any websites. Existing websites that were created by using the enhanced data model continue to operate. Any new websites that are created use the standard data model.

## Create a website by using the enhanced data model

After the enhanced data model is enabled in an environment, you can create a new site from the Power Pages home page.

> [!NOTE]
> The enhanced data model is used to create the new site only if the selected template supports the enhanced data model.

Follow these steps to create a site by using a template that uses the new data model:

1. Open the [Power Pages home page](https://aka.ms/mpp).
1. Select **Create a site**.
1. Select a template, and then select **Choose this template** to create the site.
1. Fill in the required information, and then select **Done**.

You're redirected to the Power Pages home page, where the new site appears in the **My sites** list. When the new site is ready, you can edit it by using the Power Pages design studio.

## View the list of new data model sites

You can view newly created sites from the Power Pages home page.

Sites that use the enhanced data model have functional parity with sites that use the standard data model. To determine which data model your website is using, go to the [Determine whether your site is using the standard or enhanced data model](#determine-whether-your-site-is-using-the-standard-or-enhanced-data-model) section.

The **Active sites** section of the Power Pages home page lists all the available sites. The list shows both sites that use the standard data model and sites that use the enhanced data model, regardless of whether the enhanced data model has been enabled for the environment.

## Edit a new site that uses the enhanced data model

Sites that use the enhanced data model have functional parity with sites that use the standard data model. You can use either the [Power Pages design studio](../getting-started/use-design-studio.md) or the [Power Pages management app](../configure/portal-management-app.md) for customization.

### Edit a site by using the Power Pages design studio

On the Power Pages home page, on the site card, select **Edit** to open the Power Pages design studio and edit the site.

> [!NOTE]
> The editing process in the Power Pages design studio works the same, regardless of whether the site uses the enhanced data model or the standard data model. There are no functionality gaps.

### Edit a site by using the Power Pages Management app

On the Power Pages home page, on the site card, select the ellipsis (**…**), and then select **Portal management** to open the Power Pages Management app.

> [!NOTE]
> The enhanced data model includes a new UCI model-driven Power Apps application that is named **Power Pages Management**. You must use this app for advanced customizations that aren't available through the Power Pages design studio.

You can also open the Power Pages Management app from the Power Pages design studio. Select the ellipsis (**…**), and then select **Portal Management**.

You can use the Power Pages Management app to perform advanced customizations that are unavailable in the design studio.

:::image type="content" source="media/enhanced-data-model/edit-site-power-pages-management.png" alt-text="Screenshot that shows a website being edited in the Power Pages Management app.":::

## Data model Power Platform CLI parameters

When you use the Power Platform CLI to upload or download configuration data for a website that uses the enhanced data model, you must use the `modelVersion` parameter. A value of *2* indicates that the enhanced data model should be used.

**Download**

`pac powerpages download --path <path> --webSiteId <siteId> --modelVersion 2`

**Upload**

`pac powerpages upload --path <path> --modelVersion 2`

> [!NOTE]
> This parameter is supported in Power Platform CLI version 1.22.4 and later.

For more information, go to [Power Platform CLI parameters](../configure/power-platform-cli.md#parameters).

## Frequently asked questions

### How can I update a website from the standard data model to the enhanced data model?

Guidance and tooling support to help you update from the standard data model to the enhanced data model will be provided in a later update.

### Can I edit new sites that are based on enhanced data model configurations in the Portal Management app?

You can use the new Power Pages Management app to edit new websites that are created by using the enhanced data model.

## Known issues

- In the language selection on the user profile page, a signed-in website user is shown a list of all supported languages, not just the website-enabled languages.
- The search feature doesn't return any webpage results.
- To enable traffic analysis for websites that use the enhanced data model, follow the steps in [Set up telemetry monitoring](../go-live/telemetry-monitoring.md).
- The `Account` table isn't part of the Power Pages Management app. Therefore, the ability to add a parent account record to a contact is limited. As a workaround, [manually add the Account table](/power-apps/maker/model-driven-apps/add-edit-app-components#add-a-table) to the Power Pages Management app.
- If you configure [list actions](../getting-started/add-list.md#choose-list-actions) on websites that use the enhanced data model, the configuration isn't currently saved. As a workaround, configure the list by using the [Power Pages Management app](../configure/list-configuration.md).
- You must assign contacts to web roles by using **Portal Contact (Enhanced Form)** on the contact record in the Power Pages Management app. For more information, go to [Configure web roles](../security/create-web-roles.md#from-the-contact-enhanced-data-model).

## See also

- [Use solutions with Power Pages](../configure/power-pages-solutions.md)
- [Power Platform CLI solution support for Power Pages](../configure/power-platform-cli-solution-management.md)
