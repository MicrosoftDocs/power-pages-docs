---
title:  Use governance controls to disable anonymous access
description: Learn how you can disable site-level anonymous access.
author: nageshbhat-msft
ms.topic: how-to
ms.custom: 
ms.date: 10/15/2026
ms.author: bipuldeora
ms.reviewer: smurkute
ai-usage: ai-assisted
contributors:
    - nageshbhat-msft
---

# Use governance controls to disable anonymous access

As an administrator, you can disable anonymous access. This setting prohibits unauthenticated users from accessing Dataverse data displayed on websites in your tenant, preventing accidental exposure of sensitive data.

## Admin experience

You can disable and enable anonymous access to your websites using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

2. In the left navigation pane, select **Manage**.

3. Under **Products**, select **Power Pages**.

4. Select the **Settings** tab.

    <!-- SCREENSHOT PLACEHOLDER: Show the anonymous-access governance setting under Security on the Power Pages Settings tab. Use generic environment and site names without sensitive information. -->

5. Under **Security**, select **Anonymous access to Dataverse**.

6. A slide-out panel appears. Configure anonymous access for the following options:

    | Option | Description |
    |---------|---------|
    | None of the sites | Selecting **None of the sites** disables anonymous access in none of the sites, meaning anonymous access is allowed to view data when corresponding table permissions are configured for anonymous users. This configuration is the default behavior. |
    | Specific sites | Selecting **Specific sites** allows you to block anonymous access in specific sites that you choose in the tenant. Select the option overrides any maker configurations and prevents end users from accessing Dataverse data anonymously even if corresponding table permissions are configured for anonymous users. |
    | All sites except specific sites | Selecting **All sites except specific sites** blocks anonymous access in all the websites in the tenant EXCEPT the sites that you choose. This selection also overrides any maker configurations and prevents end users from accessing Dataverse data anonymously even if corresponding table permissions are configured for anonymous users. |
    | All sites | Selecting **All sites** blocks anonymous access in all the websites in the tenant, overriding any maker configurations that provide access to anonymous users. |

    > [!NOTE]
    > If admins block external authentication providers, anonymous access is automatically disabled.
    
7. Select the sites and choose **OK**.

8. Select **Save**. A message confirms that your changes are saved.

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
