---
title: Use governance controls for external authentication in your websites
description: Learn how to use governance controls to enable or disable external authentication providers in your Power Pages websites.
author: DanaMartens
contributors:
ms.topic: how-to
ms.date: 02/21/2025
ms.author: bipuldeora
ms.reviewer: dmartens
---

# Use governance controls for external authentication in your websites

As an admin, you can enable or disable external authentication providers in your websites. Disabling them prevents users outside your organization from accessing Power Pages websites in your tenant, protecting your sites and data.

## Admin experience

Control external authentication providers in your websites using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).
1. In the left-side menu, select **Resources** > **Power Pages Sites**.
1. Select **Governance Controls** from the top ribbon menu.

    :::image type="content" source="media/external-auth-control/governance-controls.png" alt-text="Screenshot of the Governance Controls menu in the Power Platform admin center.":::

1. Select **Enable external authentication providers** from the list.
1. In the slide-out panel, control external authentication providers with the following options:

   | **Option** | **Description** |
   |----|----|
   | **All sites** | Allows external authentication providers to be enabled in all the websites in the tenant (if the makers choose to). This configuration is the default behavior. |
   | **All sites except specific sites** | Allows external authentication providers to be enabled in all websites in the tenant ***except*** the sites that you choose. Among the websites you choose, this selection overrides any maker configurations and prevents any user who is external to your organization from accessing your websites. |
   | **Specific sites** | Allows you to enable external authentication providers ***only*** in specific sites that you choose in the tenant. For all other sites in the tenant, this setting overrides any maker configurations and prevents any user who is external to your organization from accessing your websites. |
   | **None of the sites** | Enables external authentication providers in none of the sites, meaning users outside of your organization can't access any of your websites. This setting makes all websites in your tenant internal to your organization. |

1. Select the sites and choose **OK**.
1. Select **Save**. A success message appears in green below the Governance Controls ribbon menu.

## Maker experience

After an admin completes the steps, external authentication providers are disabled in your websites (shown as not available). Makers can't configure external authentication providers, and any existing ones aren't honored.

:::image type="content" source="media/external-auth-control/identity-providers.png" alt-text="Screenshot of the maker experience showing external authentication providers as not available.":::

For existing sites where external authentication providers are configured, a banner error message is displayed indicating a policy update is applied.

## User experience

When users try to access your website, they must sign in and authenticate with Microsoft Entra ID (your organization sign-in page). Users can access the website only after they authenticate.

:::image type="content" source="media/external-auth-control/sign-in.png" alt-text="Screenshot of the user sign-in page for Microsoft Entra ID.":::
