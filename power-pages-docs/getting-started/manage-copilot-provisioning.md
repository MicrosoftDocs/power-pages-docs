---
title: Manage copilot provisioning
description: Learn how to manage default copilot provisioning in Microsoft Power Pages using PowerShell scripts.
ms.topic: how-to
ms.date: 10/17/2024
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

In this guide, you learn how to manage the provisioning of copilot features in Microsoft Power Pages. Specifically, this document provides instructions for service administrators on how to disable the default copilot provisioning using PowerShell scripts. By following these steps, administrators can ensure that copilots are only created when desired.

[Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Microsoft Entra roles can use a PowerShell script to change the tenant-level setting `enableChatbotOnWebsiteCreation`:

- [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
- [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

The default value of the tenant-level setting is `null`, which behaves as if the setting is set to `true` and creates the bot during site creation. The admin can set its value to `true` or `false`.

## Get the current value of the setting

To get the current value of the tenant-level setting, use the [Get-TenantSettings](/powershell/module/microsoft.powerapps.administration.powershell/get-tenantsettings) command. For example:
>

```powershell
$myTenantSettings = Get-TenantSettings
$myTenantSettings.powerPlatform.powerPages
```

> [!NOTE]
> The Get-TenantSettings command doesn't list tenant settings whose value is null. The default value of the tenant-level setting `enableChatbotOnWebsiteCreation` is null, so it doesn't appear the first time you run the script. After you set its value to `true` or `false`, the setting appears in the list.

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
