---
title: Provision a site using the older add-on
description: Instructions to provision a site using the older site add-on.
author: neerajnandwana-msft
ms.topic: conceptual
ms.collection: get-started
ms.date: 04/12/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Provision a site using the older add-on

If you have purchased an older site add-on, and want to provision a site using the add-on, you must go to the **Dynamics 365 Administration Center** page and provision the site.

> [!NOTE]
> - To provision a site, you must be assigned either System Administrator or System Customizer role of the Microsoft Dataverse environment selected for the site. You must also have the [required permissions](/azure/active-directory/develop/howto-create-service-principal-site#required-permissions) to create and register an application in Microsoft Entra ID. If you don't have the required permissions, contact the Global Administrator to update your permissions or ask the Global Administrator to provision the site.
> - There can be only one site of each type and for a language created in an environment. For more information, see [Create additional sites in an environment](create-additional-sites.md).
> - To learn about the roles required to create add-on sites, read [Roles required for website administration](admin-roles.md).

## Provision add-on site

To provision an add-on site:

1. Create a [Power Pages website](/power-pages/getting-started/create-manage).
1. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), select **Convert to Production**. The Convert trial to production window will appear.
1. Choose the **Add-on** option and select the **Confirm** button.

The table below summarizes the features associated with each site option:

| Feature                                | Customer Self-Service site | Partner site | Employee Self-Service site | Community site | Custom site |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| World Ready                            | *                            | *              | *                            | *                | *             |
| Multi-Language Support                 | *                            | *              | *                            | *                | *             |
| Site Administration                    | *                            | *              | *                            | *                | *             |
| Customization and Extensibility        | *                            | *              | *                            | *                | *             |
| Theming                                | *                            | *              | *                            | *                | *             |
| Content Management                     | *                            |                | *                            | *                |               |
| Knowledge Management                   | *                            | *              | *                            | *                |               |
| Support/Case Management                | *                            |                | *                            | *                |               |
| Forums                                 | *                            |                | *                            | *                |               |
| Faceted Search                         | *                            |                | *                            |                  |               |
| Profile Management                     | *                            |                | *                            |                  |               |
| Subscribe to Forum Thread              | *                            |                | *                            |                  |               |
| Comments                               | *                            |                | *                            | *                |               |
| Azure AD Authentication                |                              |                | *                            |                  |               |
| Ideas                                  |                              |                |                              | *                |               |
| Blogs                                  |                              |                |                              | *                |               |
| Project Service Automation Integration |                              | *              |                              |                  |               |
| Field Service Integration              |                              | *              |                              |                  |               |
| Partner Onboarding                     |                              | *              |                              |                  |               |
| Site   Base                            |  *                           | *              |  *                           | *                | *             |
| Site Workflows                         |  *                           | *              |  *                           | *                | *             |
| Web Notifications                      |  *                           | *              |  *                           | *                | *             |
| Microsoft Identity                     |     *                         |  *              |     *                         |   *               | *             |
| Identity Workflows                     | *                            |  *             |     *                         |   *               | *             |
| Multistep Forms                              |  *                            | *               |    *                          | *                 | *             |
| Feedback                               |   *                           |  *              |  *                            | *                 | *             |
||

## Troubleshoot provisioning

Sometimes the package installation process or URL creation process can error out. In these cases, the processes can be restarted.

If *Name*-Configuring changes to *Name*-Provisioning Failed, you need to restart the provisioning process.

1. Go to the **Applications** page, and select the site.
2. Select the blue pencil button labeled **Manage**.
3. Choose one of the following options:

   - **Restart Provisioning**: Restarts the installation process with the configuration that was previously defined.

   - **Change Values and Restart Provisioning**: Lets you change some of the values before restarting the provisioning process.

If the package installation has failed, the site administrator page will open without any issues, but navigating to the actual site URL will show a message Getting set up. To confirm this:

1. Go to the Solution Management page of the **Dynamics 365 Administration Center** page and check that the package status is **Install Failed**. 

2. If the package status is **Install Failed**, try retrying the installation from the solution page. Also, be sure to check that a system administrator is installing the solution with the default language in Dataverse set to the language the site should be installed in.

> [!NOTE]
> Some solutions have prerequisites for their installation, so an installation will fail if the prerequisites are not met. For example, to install the Partner Field Service for a partner site, the Partner Site and Field Service solutions must have already been installed. If you attempt to install the Partner Field Service first, the installation will fail and give you an error message.

## Change site type and audience

After you've provisioned a site, the option to change the site audience is disabled.

> [!NOTE]
> 
> - It's recommended to reset and provision your site again to change the audience, type of site, organization, and so on. More information: [Delete a website](delete-website.md)
> - The changing of Dynamics 365 instance is applicable only to the sites provisioned using the older site add-ons.

## Next steps

[Manage sites](manage-sites.md)
