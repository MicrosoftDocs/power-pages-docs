---
title: Site visibility in Power Pages
description: Learn how to use the site visibility setting to control who has access to sites you create with Microsoft Power Pages.
ms.date: 05/31/2024
ms.topic: how-to
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: kkendrick
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick
ms.custom: bap-template
---

# Site visibility in Power Pages

The Power Pages site visibility setting allows you to control who has access to your website. You can make the site private to restrict access to specific people in your organization. If you choose to make the site public, anyone with the link can access it.

:::image type="content" source="media/site-visibility/site-visibility.gif" alt-text="Animation that shows site visibility setting change from private to public.":::

> [!IMPORTANT]
>
> - All sites that you create in Power Pages are private by default.
> - Site visibility is only available for websites that were created with version [9.4.9.x](/power-platform/released-versions/portals/portalupdate949x) or later.
> - Be cautious when you edit a public site. Changes are visible to external users immediately.
> - Websites in developer environments can't be made public.

## Difference between a private site and a public site

Only site makers and organization users to whom the maker granted access can view private sites. Site visitors need to authenticate with the organization's [Microsoft Entra ID](/azure/active-directory/fundamentals/active-directory-whatis) identity provider before they can view site contents.

> [!TIP]
> Set visibility to private to limit access while your site is in development.

Anyone on the Internet can view public sites anonymously or if they're authenticated with an identity provider. Public websites are production sites, fully operational for customers to use. A notification reminds you when you edit a public site in the [design studio](../getting-started/use-design-studio.md), [Portal Management app](../configure/portal-management-app.md), [Visual Studio Code editor](../configure/vs-code-extension.md), and the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md).

## Change site visibility

When a site is ready to go live, you can set the site visibility to public. You can change the site visibility back to private at any time so that only the makers of the site and selected users have access.

When you change the site visibility, your website restarts. It may take a few minutes to reflect the last change.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and edit your site.
1. In the left side panel, select **Set up** in the list of workspaces.
1. In the **Security** section, select the **Site visibility** tab.
1. Select **Public** or **Private**.

If you [used Power Apps to create your site](/power-apps/maker/portals/create-portal), follow these steps instead:

1. Sign in to [Power Apps](https://make.powerapps.com)
1. Select **Apps**, and then select your site.
1. Select **More Commands** (**&hellip;**) > **Edit**.
1. Select **Open in Power Pages**.
1. In the left side panel, select **Set up** in the list of workspaces.
1. In the **Security** section, select the **Site visibility** tab.
1. Select **Public** or **Private**.

## Grant access to a private site

When your site is private, you can use the site visibility page to grant access to other organization users. You can grant access to up to 50 organization users. You don't need to grant access to users who have the [System administrator role](/power-platform/admin/security-roles-privileges) in your site's environment. They have permissions to view the site by default.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and edit your site.
1. In the left side panel, select **Set up** in the list of workspaces.
1. In the **Security** section, select the **Site visibility** tab.
1. Enter the names or email addresses of the users you want to grant access to.
1. Select **Share**.

    :::image type="content" source="media/site-visibility/grant-site-access.png" alt-text="Screenshot of the Site visibility page, with Grant site access options highlighted.":::

> [!NOTE]
> Users who are granted access to a private site aren't automatically authenticated on the site. [Learn how to provide access to external audiences](external-access.md).

## Permissions required to change site visibility

Your security role and tenant security settings determine whether you can change a site's visibility.

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Microsoft Entra roles can change the site visibility:

- [Global administrator](/power-apps/maker/portals/admin/portal-admin-roles#global-administrator)
- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

When the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `true`, members of the [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role can also change the site visibility.

If the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `false`, members of the [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role must be a member of an exclusive security group in Microsoft Entra that has the permissions to manage site visibility.

### Change the tenant-level setting

You can use a PowerShell script to change the tenant-level setting `enableSystemAdminsToChangeSiteVisibility`.


To get the current value of the tenant-level setting, use the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. For example:
>

```powershell
$myTenantSettings = Get-TenantSettings
$ myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The Get-TenantSettings command doesn't list tenant settings whose value is null. The default value of the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is null, so it doesn't appear the first time you run the script. After you set its value to `true` or `false`, the setting appears in the list. When the value of the tenant setting is null, System Administrators will be able to change the site visibility. 

To set a value for `enableSystemAdminsToChangeSiteVisibility`, use the [Set-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings) command. The following example sets the value to `false`:

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

When you don't want all system administrators to be able to change site visibility, set `enableSystemAdminsToChangeSiteVisibility` to `false`. Then delegate site visibility management to a select set of users.

1. Add system administrators to a [security group in Microsoft Entra ID](/azure/active-directory/fundamentals/how-to-manage-groups) and give the group site visibility permissions.
1. In the [Power Platform admin center](https://admin.powerplatform.com), select **Power Pages sites**.
1. Select your website, and then select **Manage**.
1. In the **Security** section, select **Manage site visibility permissions**.

    :::image type="content" source="media/site-visibility/manage-site-visibility.png" alt-text="Screenshot of a website settings page, with the Manage site visibility permissions option highlighted.":::

1. Add the security group that includes the specific system administrators you want to delegate site visibility control to.

    :::image type="content" source="media/site-visibility/add-security-group.png" alt-text="Screenshot of the Manage permissions for site visibility option page, with Choose a security group highlighted.":::

After you add the security group, all system administrators who are in the group can manage site visibility. System administrators who aren't members of the group see the site visibility section disabled.

## Known issues

Microsoft Entra authentication is turned on by default when a website is provisioned. A private Power Pages website doesn't work if you turn off Microsoft Entra authentication. Change the site visibility to public before you turn off Microsoft Entra authentication.

## See also

[Set up site authentication](authentication/configure-site.md)
