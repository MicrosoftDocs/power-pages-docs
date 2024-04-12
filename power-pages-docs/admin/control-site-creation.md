---
title: Control site creation in a tenant
description: Instructions to control site creation in a tenant.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/12/2024
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
    - sampatn
---

# Control site creation in a tenant

As a global administrator, if you want to disable site creation in a tenant by non-administrators, you can do it by enabling the `disablePortalsCreationByNonAdminUsers` tenant level setting through PowerShell. To run PowerShell cmdlets, you must first install the required modules. For information on installing the required PowerShell modules, see [Installation](/power-platform/admin/powerapps-powershell#installation).

After installing the modules, run the following command in a PowerShell window (run PowerShell as an administrator).

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

Administrators are the users having one of the following Azure roles:

- [Global administrator](admin-roles.md#global-administrator)
- [Dynamics 365 administrator](admin-roles.md#dynamics-365-administrator)
- [Power Platform administrator](admin-roles.md#power-platform-administrator)

Users without these Azure roles are considered non-administrators.

When the site creation is disabled in a tenant, non-administrators see an error&mdash;`You don't have permissions to create a site in this environment. Choose another one or contact your administrator to request access.`

To enable site creation in a tenant, change the settings value from `$true` to `$false`.

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

For more details about the required roles, and permissions to create a site, see [Roles required for website administration](admin-roles.md).

## Next steps

[Manage sites](manage-sites.md)

### See also

[Create additional sites in an environment](create-additional-sites.md) <br />
