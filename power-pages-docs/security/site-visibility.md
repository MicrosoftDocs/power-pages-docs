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

:::image type="content" source="media/site-visibility/site-visibility.gif" alt-text="Animation that shows site visibility setting change from private to public.":::

> [!IMPORTANT]
> - All new sites created in Power Pages are **Private** by default. When the website is ready to go live, you can change the site visibility to **Public**.
> - Site visibility feature is only available for websites with version [9.4.9.x](/power-platform/released-versions/portals/portalupdate949x) or later.
> - All websites created before October 12, 2022 are **Public** by default. To change the site to **Private**, go to Set up workspace in design studio and change the site visibility. More information: [Set up workspace](../configure/setup-workspace.md)
> - Be cautious when editing a public site because the changes are visible to external users immediately.

## Difference between a private site and a public site

When a site is **Private**, only the site makers and organization users whom the maker granted access can view it. Website visitors need to authenticate using the organization's [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) identity provider to open the site. Having a site private can be helpful if your site is in development and only certain people should access it during the design phase.

When a site is **Public**, the site is available on the internet for everyone to access and interact with it. The website is now regarded to be in production and fully operational for the customer to use. You'll see a notification when you're editing a public site using [design studio](../getting-started/use-design-studio.md), [Portal Management app](../configure/portal-management-app.md), [Visual Studio code editor](../configure/cli-tutorial.md) and [Microsoft Power Platform CLI](../configure/cli-tutorial.md).

## Change site visibility

When a site is ready to go-live, you can change the site visibility state to **Public** making the site accessible over internet to everyone anonymously or authenticated with configured identity. Also, you can change the Site visibility state back to **Private** any time so that only makers of the site and selected users have access.

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

### Change tenant-level setting

The tenant level setting can be updated using a PowerShell script.

To get the current value for the tenant setting, use the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command.

For example:

```powershell
$myTenantSettings = Get-TenantSettings
$ myTenantSettings.powerPlatform.powerPages
```

To set a value for the tenant setting (`true` or `false`), use [Set-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings) command.

For example:

```powershell
$requestBody = @{
    powerPlatform = @{
        powerPages = @{
            enableSystemAdminsToChangeSiteVisibility = $false
        }
    }
}
Set-TenantSettings -RequestBody $requestBody
```

### Delegate site visibility control

When you don't want all system administrators to be able to change site visibility, then set the tenant-level setting of `enableSystemAdminsToChangeSiteVisibility` to `false`.

Now, you can delegate site visibility controls to a select set of users by adding them to a [security group in Azure AD](/azure/active-directory/fundamentals/how-to-manage-groups), and giving site visibility permissions to that security group.

To delegate site visibility to specific system administrators:

1. Go to [Power Platform admin center](https://admin.powerplatform.com).
1. Select **Portals**.
1. Select your website, and then select **Manage**.
1. In the **Security** section, select **Manage site visibility permissions**.

    :::image type="content" source="media/site-visibility/manage-site-visibility.png" alt-text="Manage site visibility permission.":::

1. Add the security group that contains the specific system administrators that you want to delegate managing site visibility to.

    :::image type="content" source="media/site-visibility/add-security-group.png" alt-text="Add security group.":::

After you add the security group, all system administrators that are part of the added security group can manage site visibility. System administrators that aren't part of this security group will have the site visibility section disabled.

### See also

[Configure authentication](configure-portal-authentication.md)
