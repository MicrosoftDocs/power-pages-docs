---
title:  Governance control to disable anonymous access
description: Learn how you can disable anonymous access at the site level.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 05/24/2023
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick
---

# Governance control to disable anonymous access (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

As an administrator, you can disable anonymous access to your websites in your tenant, preventing accidental exposure of sensitive data.

>[!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [cc-preview-features-definition](../includes/cc-preview-features-definition.md)]
> - This feature is being gradually rolled out across regions and may not be available yet in your region.

## Admin Experience

You can disable and enable anonymous access to your websites using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. From the left-hand menu, navigate to **Resources** and choose **Power Pages Sites**.

1. Select **Governance Controls** from the top ribbon menu.  

    :::image type="content" source="media/disable-anonymous-access/governance-controls.png" alt-text="Governance controls.":::

1. Choose **Disable anonymous access** from the list.  

1. A slide-out panel appears. You can configure anonymous access for the following options:

    | Option | Description |
    |---------|---------|
    | None of the sites | Selecting **None of the sites** disables anonymous access in none of the sites, meaning anonymous access is allowed to view data when corresponding table permissions are configured for anonymous users. This configuration is the default behavior. |
    | Specific sites | Selecting **Specific sites** allows you to block anonymous access in specific sites that you choose in the tenant. Select the option overrides any maker configurations and prevents end users from accessing Dataverse data anonymously even if corresponding table permissions are configured for anonymous users. |
    | All sites except specific sites | Selecting **All sites except specific sites** blocks anonymous access in all the websites in the tenant EXCEPT the sites that you choose. This selection also overrides any maker configurations and prevents end users from accessing Dataverse data anonymously even if corresponding table permissions are configured for anonymous users. |
    | All sites | Selecting **All sites** blocks anonymous access in all the websites in the tenant, overriding any maker configurations that provide access to anonymous users. |
    
1. Select the sites and choose **OK**.

1. Select **Save**. A message confirming success appears in green below the Governance Controls ribbon menu.  

## Maker experience

Once an admin completes the steps in the previous section, anonymous users are disabled for new table permissions.

:::image type="content" source="media/disable-anonymous-access/anonymous-access-disabled.png" alt-text="Disable anonymous access.":::

For existing sites where anonymous access is given, a banner error message is displayed indicating a **Data protection policy update** has been applied.

## End user experience

End users see a message explaining that they don't have permission to view records and prompting them to sign in.

