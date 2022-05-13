---
title: Power Pages governance
description: Manage and administer your Power Pages sites.
author: donovangoode
ms.topic: conceptual
ms.custom: 
ms.date: 04/15/2022
ms.author: dgoode
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
    - donovangoode
---

# Power Pages governance

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE[powerapps-info](../includes/cc-powerapps-info.md)]

Power Pages provides some helpful tools for administrators to manage their sites and environments.

The [Power Pages admin center](admin-overview.md) allows administrators various capabilities:
- Configure vanity domains
- Manage lifecycle operations:
    - Create
    - Delete
    - Convert to Production
    - License assignments.
- Restrict IP addresses
- Change Dataverse environments
- Upload and manage custom certificates
- Enable integrations

The [Power Platform Center of Excellence toolkit](power-platform/guidance/coe/starter-kit) provides tools and guidance on managing your Power Pages sites.

<!--TO DO-->
## Power Pages Inventory Components

The inventory components are core to Power Pages governance within the Center of Excellence (COE) Starter Kit. The Power Pages resources are synced to the  respective inventory items tables and can be viewed in the ***'Power Platform Admin View*** app and in the ***'COE Power BI'*** report.

### Tables
The [sync flows](https://docs.microsoft.com/en-us/power-platform/guidance/coe/core-components#flows) of the CoE Starter Kit syncs your tenant resources to the Dataverse tables. The 'Admin | Sync Template v3 (Portals)'  is the Power Pages specific cloud flow that handles the Power Pages inventory telemetry. The Power Pages table provides information about created by/on and modified by/on, in addition to resource-specific information.
- Power Pages Sites (Portals) represents an portal website. The following information is available for each app:
	
    - Details
    	- Power Pages Owner
    	- Power Pages Display Name
    	- Power Pages Environment
    	- Power Pages Website Name
    	- Power Pages Created On
    	- Power Pages Modified On
    	- Power Pages Website ID
    	- Power Pages Unique ID
    	- Power Pages Website Record Status

    - Inventory Details
        - COE Inventory Record Created On
        - COE Inventory Record Modified On
			
    - Identity and Authentication
    	- Auth Open Registration Enabled
    	- Auth Local Registration Enabled
    	- Auth Local Authentication Enabled
    	- Auth Invitation Enabled
        - Auth External Identities Enabled
	
    - Data Security
    	- Table Permissions Enabled Across Portal
    	- Table Permissions Enabled All Lists
    	- Table Permissions Enabled All Basic Forms
    	- Table Permissions Enabled All Adv Form Steps
	
    - System Created and Orphan Details
    	- App Owner Display Name
    	- Power Pages is Orphaned
	
	
## Power Platform Admin View
Use this app to:
- Get a quick overview of resources in your tenant.
- Learn about your makers, connectors, Power Apps, Power Pages sites, and Power Automate cloud flows.
- Find out who apps are shared with.
- Add additional information, such as notes and risk assessments, to your resources.
- Set approved capacity for environments, and see capacity and add-on information per environment.
- Complete [app audits](https://docs.microsoft.com/en-us/power-platform/guidance/coe/example-processes).
- Manage capacity alerts.

**Permission:** This app is intended to be used only by admins. Power Platform Service Admin or Global Admin permission is required. Share this app with your CoE admins.


From the CoE Dashboard, Power Platform resources can be viewed through chart visualizations and lists.

:::image type="content" source="media/coe-admin-app.png" alt-text="COE Admin App Dashboard":::

Admins can view Power Pages sites data by navigating to the Power Pages Icon in the left navigation and select it. This will load a view in the app. This view will show a list of all the Power Pages websites  that have been created various makers across the entire tenant. This provides admins with a normalized view of all Power Pages websites in their organization's tenant. This provides ease of use for admins to govern data security and authentication across environments.

:::image type="content" source="media/coe-admin-app-power-pages-list.png" alt-text="COE Admin Power Pages List":::

Admins are able view even more details about a Power Pages Site by selecting  an inventory record row from the list. This displays the Power Pages details form, enabling admins to further investigate and govern Power Pages sites to ensure they are up to their organization's security and DLP standards.

:::image type="content" source="media/coe-power-pages-inventory-record.png" alt-text="COE Power Pages Inventory Record":::

## CoE Power BI report

Additionally, admins can leverage the CoE Dashboard  Power BI report. This enables admins with a holistic view of inventory items in Dataverse with rich visualizations and insights for Environment and Power Pages sites information. 
Follow the setup [instructions](https://docs.microsoft.com/en-us/power-platform/guidance/coe/setup-powerbi) to set up the Power BI dashboard. More information: [Gain deep insights into your Microsoft Power Platform adoption with the CoE Power BI dashboard](https://docs.microsoft.com/en-us/power-platform/guidance/coe/power-bi)

:::image type="content" source="media/coe-power-bi-dashboard.png" alt-text="COE Power Pages Inventory Record":::


## Further resources
- [Power Pages Admin Center](https://docs.microsoft.com/en-us/power-apps/maker/portals/admin/admin-overview) Allows you to perform advanced administrative actions on portals. The admin center is available when a portal is provisioned successfully.
- Explore the [Power Apps admin documentation](https://docs.microsoft.com/en-us/power-platform/admin/admin-documentation).As an admin looking after the CoE, you should be familiar with the administration and governance of Microsoft Power Platform. We recommend the following white paper as a resource: [aka.ms/PowerAppsAdminWhitepaper](https://aka.ms/powerappsadminwhitepaper)
- Find training resources, including guided learning and step-by-step guides, at [aka.ms/PowerPlatformLabs](https://aka.ms/powerplatformlabs).
