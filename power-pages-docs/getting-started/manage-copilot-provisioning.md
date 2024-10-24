---
title: Manage copilot provisioning
description: Learn how to manage default copilot provisioning in Microsoft Power Pages by using PowerShell scripts.
ms.topic: how-to
ms.date: 10/22/2024
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

# Manage copilot provisioning

This article explains how to manage the provisioning of copilot features in Microsoft Power Pages. Specifically, it provides instructions that show how service administrators can use PowerShell scripts to disable the default copilot provisioning. By following the steps, admins can ensure that copilots are created only when they are wanted.

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Microsoft Entra roles can use a PowerShell script to change the tenant-level `enableChatbotOnWebsiteCreation` setting:

- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

The default value of the tenant-level setting is `null`. This value is equivalent to a value of `true` and creates a bot during site creation. An admin can set the value to `true` or `false`.

## Get the current value of the setting

To get the current value of the tenant-level setting, use the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. Here is an example:

```powershell
$myTenantSettings = Get-TenantSettings
$myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The `Get-TenantSettings` command doesn't list tenant settings where the value is `null`. Because the default value of the tenant-level `enableChatbotOnWebsiteCreation` setting is `null`, this setting doesn't appear in the list the first time that you run the script. However, after you set its value to `true` or `false`, the setting appears in the list.

## Set the value

To set a value for `enableChatbotOnWebsiteCreation`, use the [Set-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/set-tenantsettings) command. The following example sets the value to `false`:

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
- [Add a copilot to your Power Pages site](../getting-started/enable-chatbot.md)
- [Responsible AI: FAQ for site copilot](../faqs-chatbot.md)
