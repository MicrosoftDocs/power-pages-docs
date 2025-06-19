---
title: Manage agent provisioning
description: Learn how to manage default agent provisioning in Microsoft Power Pages by using PowerShell scripts.
ms.topic: how-to
ms.date: 06/17/2025
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
  - bap-ai-copilot
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-desc
  - ai-seo-date:09/07/2023
  - bap-template
---

# Manage agent provisioning

This article explains how to manage agent provisioning in Microsoft Power Pages. It shows how service admins use PowerShell scripts to disable default agent provisioning. By following these steps, admins ensure agents are created only when needed.

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) in the following Microsoft Entra roles can use a PowerShell script to change the tenant-level `enableChatbotOnWebsiteCreation` setting:

- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

The default value of the tenant-level setting is `null`, which is equivalent to `true` and creates a bot during site creation. Admins can set the value to `true` or `false`.

## Get the current value of the setting

To get the current value of the tenant-level setting, run the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. Here's an example:

```powershell
$myTenantSettings = Get-TenantSettings
$myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The `Get-TenantSettings` command doesn't list tenant settings where the value is `null`. Because the default value of the tenant-level `enableChatbotOnWebsiteCreation` setting is `null`, this setting doesn't appear in the list the first time you run the script. After you set its value to `true` or `false`, the setting appears in the list.

## Set the value

Set a value for `enableChatbotOnWebsiteCreation` by using the [Set-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings) command. This example sets the value to `false`:

```powershell
$requestBody = @{
    powerPlatform = @{
        powerPages = @{
            enableChatbotOnWebsiteCreation = $false
        }
    }
}
Set-TenantSettings -RequestBody $requestBody
```

## Related information

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Add an agent to your Power Pages site](../getting-started/enable-agent.md)
- [Responsible AI: FAQ for site agent](../faq-site-agent.md)
