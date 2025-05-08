---
title: Site visibility in Power Pages
description: Learn how to use the site visibility setting to control who has access to sites you create with Microsoft Power Pages.
ms.date: 05/08/2025
ms.topic: how-to
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
ms.custom: bap-template
---

# Site visibility in Power Pages

The Power Pages site visibility setting lets you control who can access your website. Make the site private to restrict access to specific people in your organization. If you make the site public, anyone with the link can access it.

> [!IMPORTANT]
>
> - All sites you create in Power Pages are private by default.
> - Be cautious when editing a public site. Changes are visible to external users immediately.
> - Websites in developer environments can't be made public.

## Difference between a private site and a public site

Only site makers and organization users who the maker granted access to can view private sites. Site visitors need to authenticate with the organization's [Microsoft Entra ID](/azure/active-directory/fundamentals/active-directory-whatis) identity provider to view site contents.

> [!TIP]
> Set the visibility to private to limit access while your site is in development.

Anyone on the Internet can view public sites anonymously or when they're authenticated with an identity provider. Public websites are production sites that are fully operational for customers to use. A notification reminds you when you edit a public site in the [design studio](../getting-started/use-design-studio.md), [Portal Management app](../configure/portal-management-app.md), [Visual Studio Code editor](../configure/vs-code-extension.md), or the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md).

## Change site visibility

When a site is ready to go live, set the site visibility to public. Change the site visibility back to private anytime so only the makers of the site and selected users have access.

When you change the site visibility, the website restarts. It can take a few minutes to reflect the change.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and edit your site.
1. In the left panel, select **Security**.
1. Under **Manage**, select **Site visibility**.
1. On the **This site is** card, select **Public** or **Private**.

## Grant access to a private site

If your site is private, use the site visibility page to grant access to up to 50 organization users. Users with the [System administrator role](/power-platform/admin/security-roles-privileges) in your site's environment already have permissions to view the site by default, so you don't need to grant them access.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and edit your site.
1. In the left side panel, select **Security**.
1. In the **Manage** section, select **Site visibility**.
1. In the **Grant site access** card, enter the names or email addresses of the users you want to grant access to.
1. Select **Share**.

> [!NOTE]
> - Users configured to access the private site are stored in an environment variable. Any Dataverse security role with permission to modify the environment variable can add or remove user access to the private site.
> - Users granted access to a private site aren't automatically authenticated. [Learn how to provide access to external audiences](external-access.md).

## Permissions required to change site visibility

Your security role and tenant security settings determine whether you can change a site's visibility.

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Microsoft Entra roles can change the site visibility:

- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

When the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `true`, members of the [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role can change the site visibility.

If the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is set to `false`, members of the [System administrator](/power-platform/admin/database-security#environments-with-a-dataverse-database) security role must be a member of an exclusive security group in Microsoft Entra that has the permissions to manage site visibility.

### Change the tenant-level setting

You can use a PowerShell script to change the tenant-level setting `enableSystemAdminsToChangeSiteVisibility`.

Get the current value of the tenant-level setting by using the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. For example:
>

```powershell
$myTenantSettings = Get-TenantSettings
$ myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The Get-TenantSettings command doesn't list tenant settings whose value is null. The default value of the tenant-level setting `enableSystemAdminsToChangeSiteVisibility` is null, so it doesn't appear the first time you run the script. After you set its value to `true` or `false`, the setting appears in the list. When the value of the tenant setting is null, system administrators can change the site visibility. 

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

1. Add system administrators to a [security group in Microsoft Entra ID](/azure/active-directory/fundamentals/how-to-manage-groups), and give the group site visibility permissions.
1. Manage site visibility permissions in the Power Platform admin center. Select the following tab based on which version of the admin center you're using:

# [New admin center](#tab/new)

1. In the [Power Platform admin center](https://admin.powerplatform.com), select **Manage**.
1. Select **Power Pages**.
1. Select your website, and then select **Manage**.
1. In the **Security** section, select **Manage site visibility permissions**.
1. Add the security group that includes the specific system administrators you want to delegate site visibility control to.

    :::image type="content" source="media/site-visibility/add-security-group.png" alt-text="Screenshot of the Manage permissions for site visibility option page, with Choose a security group highlighted.":::

After you add the security group, all system administrators in the group can manage site visibility. System administrators who aren't in the group see the site visibility section disabled.

# [Classic admin center](#tab/classic)

1. In the [Power Platform admin center](https://admin.powerplatform.com), select **Power Pages sites**.
1. Select your website, and then select **Manage**.
1. In the **Security** section, select **Manage site visibility permissions**.

    :::image type="content" source="media/site-visibility/manage-site-visibility.png" alt-text="Screenshot of a website settings page, with the Manage site visibility permissions option highlighted.":::

1. Add the security group that includes the specific system administrators you want to delegate site visibility control to.

    :::image type="content" source="media/site-visibility/add-security-group.png" alt-text="Screenshot of the Manage permissions for site visibility option page, with Choose a security group highlighted.":::

After you add the security group, all system administrators who are in the group can manage site visibility. System administrators who aren't members of the group see the site visibility section disabled.

---

## Known issues

Microsoft Entra authentication is on by default when a website is provisioned. A private Power Pages website doesn't work if you turn off Microsoft Entra authentication. Set the site visibility to public before turning off Microsoft Entra authentication.

## See also

[Set up site authentication](authentication/configure-site.md)
