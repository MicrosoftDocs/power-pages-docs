---
title: Power Pages governance
description: Manage and administer your Power Pages sites.
author: donovangoode
ms.topic: conceptual
ms.custom: 
ms.date: 06/15/2022
ms.author: dgoode
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
    - donovangoode
---

# Power Pages governance



Power Pages provides some helpful tools for administrators to manage their sites and environments.

Administrators can use the [Power Platform admin center](admin-overview.md) to:

- Configure vanity domains
- Manage lifecycle operations
    - Create
    - Delete
    - Convert to Production
    - License assignments
- Restrict IP addresses
- Change Microsoft Dataverse environments
- Upload and manage custom certificates
- Enable integrations

The [Power Platform Center of Excellence toolkit](/power-platform/guidance/coe/starter-kit) provides tools and guidance to help you manage your Power Pages sites.

## Power Pages inventory components

The inventory components are core to Power Pages governance within the Center of Excellence (COE) Starter Kit. The Power Pages resources are synced to the  respective inventory items tables and can be viewed in the ***Power Platform Admin View*** app and in the ***COE Power BI*** report.

|Component  |Description |
|---------|---------|
|[Sync flows](/power-platform/guidance/coe/core-components#flows) of the CoE Starter Kit    |Syncs your tenant resources to the Dataverse tables.         |
|Admin Sync Template v3 (Portals)     |The Power Pages specific cloud flow that handles the Power Pages inventory telemetry         |
|Power Pages table   |Provides information about created by/on and modified by/on, in addition to resource-specific information.         |
|Power Pages site |Represents a portal website. | 

The following information is available for each app:
	
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
	- Table Permissions Enabled All Advanced Form Steps

- System Created and Orphan Details
	- App Owner Display Name
	- Power Pages is Orphaned
    	
## Power Platform admin view

Use the Power Platform admin view to:

- Get a quick overview of resources in your tenant.
- Learn about your makers, connectors, Power Apps, Power Pages sites, and Power Automate cloud flows.
- Find out who apps are shared with.
- Add additional information, such as notes and risk assessments, to your resources.
- Set approved capacity for environments, and see capacity and add-on information for each environment.
- Complete [app audits](/power-platform/guidance/coe/example-processes).
- Manage capacity alerts.

> [!NOTE]
> The permission app is intended to be used only by admins. Power Platform Service Admin permission is required. Share this app with your CoE admins.

:::image type="content" source="media/coe-admin-app.png" alt-text="COE admin app dashboard.":::

View Power Pages sites data by selecting **Power Pages Sites** in the left pane. This view shows all sites in the organization's tenant, allowing admins to govern data security and authentication across environments.

:::image type="content" source="media/coe-admin-app-power-pages-list.png" alt-text="COE admin Power Pages list.":::

Admins are able view more details about a Power Pages Site by selecting an inventory record row from the list. This action displays the Power Pages details form.  Admins can investigate and govern Power Pages sites to ensure they're up to their organization's security and DLP standards.

:::image type="content" source="media/coe-power-pages-inventory-record.png" alt-text="COE Power Pages inventory record.":::

## CoE Power BI report

The CoE Dashboard  Power BI report provides a holistic view of inventory items in Dataverse with rich visualizations and insights for Environment and Power Pages sites information. 

Follow the set up [instructions](/power-platform/guidance/coe/setup-powerbi) to set up the Power BI dashboard. More information: [Gain deep insights into your Microsoft Power Platform adoption with the CoE Power BI dashboard](/power-platform/guidance/coe/power-bi)

:::image type="content" source="media/coe-power-bi-dashboard.png" alt-text="COE Power BI dashboard.":::


## Further resources

- [Power Pages admin center](/power-apps/maker/portals/admin/admin-overview) Allows you to perform advanced administrative actions on portals. The admin center is available when a portal is provisioned successfully.
- Explore the [Power Apps admin documentation](/power-platform/admin/admin-documentation). As an admin looking after the CoE, you should be familiar with the administration and governance of Microsoft Power Platform. We recommend the following white paper as a resource: [Power Apps admin whitepaper](https://aka.ms/powerappsadminwhitepaper)
- Find training resources, including guided learning and step-by-step guides, at [Power Platform labs](https://aka.ms/powerplatformlabs).

