---
title:  Use governance controls to disable anonymous access
description: Learn how you can disable site-level anonymous access.
author: nageshbhat-msft
ms.topic: how-to
ms.custom: 
ms.date: 10/06/2025
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - nageshbhat-msft
---

# Use governance controls to disable anonymous access

As an administrator, you can disable anonymous access. This setting prohibits unauthenticated users from accessing Dataverse data displayed on websites in your tenant, preventing accidental exposure of sensitive data.

## Admin experience

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

    > [!NOTE]
    > If admins block external authentication providers, anonymous access is automatically disabled.
    
1. Select the sites and choose **OK**.

1. Select **Save**. A message confirming success appears in green below the Governance Controls ribbon menu.  

> [!NOTE]
> - While unauthenticated users will be prevented from viewing Dataverse data when this setting is enabled, these users can still write data to Dataverse. This is helpful in use cases where users wish to submit anonymous feedback.  

## Maker experience

Once an admin completes the steps in the previous section, anonymous users are disabled for new table permissions.

:::image type="content" source="media/disable-anonymous-access/anonymous-access-disabled.png" alt-text="Disable anonymous access.":::

For existing sites where anonymous access is given, a banner error message is displayed indicating a **Data protection policy update** has been applied.

## End user experience

End users see a message explaining that they don't have permission to view records and prompting them to sign in:

```You don't have permission to view these records. Please sign in to continue.```



## Related information

[Use governance controls to disable anonymous access (video)](https://youtu.be/F32I4P4HQNw?feature=shared)
