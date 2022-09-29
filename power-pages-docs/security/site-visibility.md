---
title: Site visibility in Power Pages
description: Learn how to secure your Power Pages site by using site visibility and easily switch site visibility between private and public options.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 10/03/2022
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Site visibility in Power Pages

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Power Pages site visibility feature enables you to manage who has access to your website. You can make your site **Private** to restrict access to specific people in your organization, or **Public** so that anyone with the link has access.

> [!IMPORTANT]
> - All new sites created in Power Pages are **Private** by default. When the website is ready to go live, you can change the site visibility to **Public**.
> - Site visibility feature is only available for websites with version [9.4.9.x](/power-platform/released-versions/portals/portalupdate949x) or later.

:::image type="content" source="media/site-visibility/site-visibility-preview.gif" alt-text="Animation that shows site visibility setting change from private to public.":::

## Difference between a private site and a public site

When a site is **Private**, only the site makers and organization users whom the maker granted access can view it. Website visitors need to authenticate using the organization's [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) identity provider to open the site. This can be helpful if your site is in development and only certain people should access it during the design phase.

When a site is **Public**, the site is available on the internet for everyone to access and interact with it. The website is now regarded to be in production and fully operational for the customer to use. You'll see a notification when you're editing a public site using [design studio](../getting-started/use-design-studio.md), [Portal Management app](../configure/portal-management-app.md), [Visual Studio code editor](../configure/cli-tutorial.md) and [Microsoft Power Platform CLI](../configure/cli-tutorial.md).

> [!IMPORTANT]
> - All websites created before October 12, 2022 are **Public** by default. To change the site to **Private**, go to Set up workspace in design studio and change the site visibility. More information: [Set up workspace](../configure/setup-workspace.md)
> - Be cautious when editing a public site because the changes are visible to external users immediately.

## Change site visibility

When a site is ready to go live, you can change the site visibility state to **Public** making the site accessible over internet to everyone anonymously or authenticated with configured identity. Also, you can change the Site visibility state back to private any time so that only makers of the site and selected users have access.

To change site visibility:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/)
1. Edit the site that you want to change site visibility for.
1. Select **Set up** from the list of workspaces on the left-side of the screen.
1. Select **Site visibility** tab under **Security** section.
1. Select **Public** to make the site public, or **Private** to make the site private.

> [!NOTE]
> Changing site visibility restarts your website causing a few minutes of delay to reflect the latest state change.

## Grant access to a private site

You can grant website access to other organization users using the Site Visibility page when the site is private.

To grant website access:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/)
1. Edit the site that you want to change site visibility for.
1. Select **Set up** from the list of workspaces on the left-side of the screen.
1. Select **Site visibility** tab under **Security** section.
1. Choose the users that you want to grant the website access to.
1. Select **Share**.

    :::image type="content" source="media/site-visibility/grant-site-access.png" alt-text="Grant site access for a private site.":::

> [!NOTE]
> - Granting website access is limited to **50 users**.
> - Organization users that are part of [System administrator](/power-platform/admin/security-roles-privileges) role in the Power Platform environment where the website is created have permissions to view the website by default.

## Permissions required to change site visibility

The ability to change site visibility is determined by the following factors:

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Azure Active Directory roles can change the site visibility:
    - [Global administrator](/power-apps/maker/portals/admin/portal-admin-roles#global-administrator)
    - [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
    - [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

Members of [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role can also change the site visibility when the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `true`.

If the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `false`, the members of [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role must also be a member of an exclusive security group in Azure Active Directory that has the permissions to **Manage site visibility**.
......


By default, the Site visibility option is only enabled if you're a member of one of the built-in service admin roles listed above.

However, service admins can configure the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` 

For more information about service admin roles in Power Platform, see [service admin roles](/power-platform/admin/use-service-admin-role-manage-tenant).
<br> For more information about built-in roles in Azure AD, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference).
<br> For more information about how to see the role assignments and assign roles in Azure AD, see [View and assign roles in Azure AD](/azure/active-directory/roles/manage-roles-portal#assign-a-role).

## Governance control for site visibility

Power Platform [service administrators](/power-platform/admin/use-service-admin-role-manage-tenant) (Global administrator, Dynamics 365 administrator and Power platform administrator) can control who can change site visibility. Service administrators can also change the site visibility by default.

Additionally, service administrators can also delegate the ability to change site visibility at the user-level using the tenant-level setting of `enableSystemAdminsToChangeSiteVisibility`.

enableSystemAdminsToChangeSiteVisibility = true; All System admins can change the site visibility (make a site public)

enableSystemAdminsToChangeSiteVisibility = false \[Recommended\]; Only the System admins who are added to a Security Group by the service administrator can change the site visibility (make a site public)

## How to change the tenant level setting enableSystemAdminsToChangeSiteVisibility?

The tenant level setting can be updated using PowerShell script.

To get the current value for the tenant setting, you can use the Get-TenantSettings command. Refer - [Get-TenantSettings (Microsoft.PowerApps.Administration.PowerShell) \| Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings?view=pa-ps-latest)

For e.g.,

$myTenantSettings = Get-TenantSettings

$ myTenantSettings.powerPlatform.powerPages

To set a value for the tenant setting (true or false), you can use the Set-TenantSettings command. Refer - [Set-TenantSettings (Microsoft.PowerApps.Administration.PowerShell) \| Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings?view=pa-ps-latest)

For e.g.,

$requestBody = @{

powerPlatform = @{

powerPages = @{

enableSystemAdminsToChangeSiteVisibility = $false

}

}

}

Set-TenantSettings -RequestBody $requestBody

## How to delegate site visibility controls to a select set of system administrators? 

When you do not want all system administrators to be able to change site visibility, then set enableSystemAdminsToChangeSiteVisibility = false

Now you can delegate site visibility controls to a select set of system administrators by adding them to a Security Group and giving site visibility permissions to the Security Group.

This can be done by:

1.  Open Power Platform Admin Center and click on 'Manage' for the desired website (Power Platform Admin Center à Resources à Portals à Right click on target website and 'Manage')

2.  In the website details view, click on Manage site visibility permissions under 'Security'  
    ![Graphical user interface Description automatically generated](media/image10.png)

3.  Select the Security Group  
    ![Graphical user interface Description automatically generated](media/image11.png)

Please note that there can only be one security group added to the site. Please ensure that all system administrators who should be able to change site visibility for that site are part of the security group.

## Creating a Security Group: 

(Existing article: [How to manage groups - Azure Active Directory - Microsoft Entra \| Microsoft Learn](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/how-to-manage-groups))

1.  Go to [Home - Microsoft Azure](https://portal.azure.com/#home)

2.  Click on Azure Active Directory  
    ![Graphical user interface  application Description automatically generated](media/image12.png)

3.  On the left panel, select Groups

![Graphical user interface  text  application  email Description automatically generated](media/image13.png)

4.  Select 'New Group' on the top left  
    ![Graphical user interface  text  application  email  website Description automatically generated](media/image14.png)

5.  Select Group type as 'Security' from the drop down  
    ![Graphical user interface  text  application  email Description automatically generated](media/image15.png)

6.  Click under 'Members' and add the users whom you want to enable making changes to site visibility (e.g., makers in your organization whom you want to make sites public). Click Create at the bottom right to create the Security Group  
    ![](media/image16.png)
