---  
title: Copilot hub for Power Pages (preview)
description: Learn about the Copilot hub in Power Platform admin center, offering analytics and governance controls for AI features in Power Pages.  
author: PramithaU  
ms.topic: concept-article  
ms.date: 05/15/2025  
ms.author: pudupa  
ms.reviewer: smurkute  
contributors:  
  - shwetamurkute  
  - PramithaU  
---  

# Copilot hub for Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Copilot hub in the Power Platform admin center provides a centralized dashboard for admins to monitor and manage usage of AI capabilities across Power Platform products. Power Pages integrates into this hub to offer detailed visibility into the usage of AI-powered features and give admins the tools they need to govern them effectively.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature is gradually being rolled out across regions and might not be available yet in your region.

> [!NOTE]  
> Before you begin, ensure the site runs on runtime version 9.7.4.xx or later.

## Access Copilot insights and settings for Power Pages

To access Copilot insights and settings for Power Pages, follow these steps:

1. Visit the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left navigation, select **Copilot Hub**.
1. Select the **Power Pages** tab to:
    - Explore product-specific insights for Copilot usage.  
    - Navigate to the **Settings** page to view or configure AI feature settings for your environments.

## Capabilities

Copilot hub enables makers and end users to monitor, analyze, and manage AI-powered functionalities in Power Pages. The following capabilities provide insights into AI usage, helping organizations optimize their adoption of AI technologies:

- [Analytics & insights](#analytics-and-insights) 
- [Governance controls for AI features](#governance-controls-for-ai-features)

## Analytics and insights

The Copilot hub includes Power Pages specific usage metrics, enabling tenant admins to understand adoption and monitor how Copilot features are being used across their environments. Learn more about Copilot features in [Overview of AI-powered and Copilot features in Power Pages](/power-pages/configure/ai-copilot-overview).

Track how AI features are being used in Power Pages:

- **Maker Copilot**  
  Maker Copilot provides insights into how makers use AI for site creation, text generation, and page creation.

- **End user Copilot**  
  End user Copilot provides analytics on end user facing AI components, such as chatbot interactions and intelligent search.

### Switch between maker and end-user views

Admins can seamlessly toggle between maker and end-user Copilot analytics views at an environment level. This allows for a focused analysis depending on whether the Copilot features are used by site creators or by site visitors.

### Maker Copilot analytics

The **Maker Copilot** analytics view includes insights for both **Studio Copilot** (used by makers in the design studio) and **Prodev Copilot** (used by developers via the VS Code extension). Admins can view:

| **Metric**                     | **Description**                                                                 |
|---------------------------------|---------------------------------------------------------------------------------| 
| **Studio Copilot MAU**          | Monthly active makers using AI features in the design studio.                   |
| **Prodev Copilot MAU**         | Monthly active pro developers receiving AI responses.                           |
| **Sites with Copilot Enabled**  | Number of sites where Copilot features are turned on.                           |
| **Copilot Usage Trend**         | Time-based trend showing Copilot usage.                                         |
| **Most Used Copilot Features**  | Insights into which AI-powered capabilities are most frequently used by makers. |

:::image type="content" source="media/copilot-hub/maker_copilot.png" alt-text="Screenshot of Maker Copilot analytics view showing usage metrics and trends." lightbox="media/copilot-hub/maker_copilot.png":::

### End-user Copilot analytics

The **End-user Copilot** view provides insights into how end users interact with AI-powered features like chat agents, search summaries, and other Copilot functionalities. It includes metrics such as usage trends, active users, and feature adoption across sites.

| **Feature**                     | **Metric Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------------|
| [Chat agent or add a Copilot](../getting-started/faqs-site-agent.md)        | <ul><li> **Total Sites with Chat agent Enabled**: Total number of sites where the chat agent feature is enabled. </li><li> **Usage Table & Trend View**: Displays usage patterns over time and includes a detailed table with information such as site name, monthly active users (MAU), site type, and environment. </li><li> **Monthly Active Users (MAU)**: Number of end users who received at least one successful AI-generated response from the Site Copilot chatbot during the selected time period. </li></ul> |
| [Search summary](../configure/search/generative-AI.md)               | <ul><li> **Monthly Active Users (MAU)**: Number of users who received successful AI-generated summaries of their search results.  </li> <li> **Total sites with Search Summary enabled**: Total number of sites where the Search Summary feature is enabled.  </li><li> **Usage Table**: Includes details such as site name, usage metrics, site type, and environment for each site using the feature.  </li><li>   **Search Query Volume**: Indicates the number of search queries executed per website, helping assess user engagement and feature adoption. </li></ul>  |
| [Summarization API](../configure/data-summarization-api.md)            | <ul><li> **API Usage Volume**: Total number of successful summaries generated using API calls. </li> <li>   **Total Sites with Summarization API Enabled**: Total number of sites where the Summarization API feature is enabled. </li> <li>   **Usage Table**: Displays site-level usage insights, including site name, usage metrics, site type, and environment. </li></ul>  |
| [AI form fill assistance](../getting-started/add-form.md)      | <ul><li> **Monthly Active Users (MAU)**: Number of users who successfully used the form fill feature by uploading attachments, resulting in at least one form field being auto-filled. </li> <li>   **Total Sites with Intelligent Forms Enabled**: Number of sites where this AI-powered feature is in use. </li> <li>  **Usage Table**: Displays site-level usage details including site name, usage volume, site type, and environment. </li> <li>  **Fields Auto-Filled**: Total number of form fields auto-filled through AI assistance across all sites. </li> <li>   **Form Submission Rate**: Comparison of submission rates between users who used form fill assistance vs. those who didn't. </li></ul>  |
| [AI summary list](../getting-started/add-ai-summary-list.md)             | <ul><li> **Monthly Active Users (MAU)**: Number of users who successfully received a generative AI summary of the data. </li> <li>   **Total Sites with List Summary Enabled**: Number of sites where this feature is enabled. </li> <li>   **Usage Table**: Site-level breakdown showing usage details such as site name, volume of usage, site type, and environment. </li></ul> |

:::image type="content" source="media/copilot-hub/end_user_copilot.png" alt-text="Screenshot of End-User Copilot feature analytics showing usage metrics and trends." lightbox="media/copilot-hub/end_user_copilot.png":::

## Governance controls for AI features

Governance settings empower admins to manage AI feature exposure across the tenant. Admins can configure how AI features are used across environments or sites. Admins can:

- **Enable or disable AI features for makers**  
  Control whether makers in specific environments can use AI features.

- **Enable or disable AI features for end-user**  
  Manage exposure of AI-powered components (for example, chat or summaries) to external users.

 In the governance settings, for end user AI features, admins can apply controls at a feature-granular level, allowing them to enable or disable individual features based on their organization’s needs. Settings are applied at:

- Environment level
- Site level (for granular control)

:::image type="content" source="media/copilot-hub/governance-control.png" alt-text="Screenshot of governance controls for AI features in Power Pages." lightbox="media/copilot-hub/governance-control.png":::

### Considerations

When you manage AI-powered features in the Copilot hub, it's important to understand a few dependencies and restrictions at both the tenant and environment levels. Here are the details:

1. **Tenant-level control via PowerShell (enableGenerativeAIFeaturesForSiteUsers) and governance settings:**
   - Tenant-level Copilot settings can be configured using PowerShell.  
   - If AI features are disabled at the tenant level, they can't be configured at the environment level in the Copilot hub.  
   - In such cases, admins will see an error message in the Copilot hub indicating the need to enable settings at the tenant level.
   - [Service admins](/power-platform/admin/use-service-admin-role-manage-tenant) who are members of any of the following Azure Active Directory (AAD) roles can change the governance setting:
     - [Power Platform administrator](/power-platform/admin/use-service-admin-role-manage-tenant#power-platform-administrator)
     - [Dynamics 365 administrator](/power-platform/admin/use-service-admin-role-manage-tenant#dynamics-365-administrator)

2. **Access restrictions:**
    - Only [tenant-level admins](/power-pages/admin/admin-roles) can configure Copilot settings across environments.
    - Users without tenant-level admin privileges can't access or modify AI configuration settings in the Copilot hub.

3. **Chat agent (site Copilot) specific setting:**  
   If the setting for “Publish bots with AI” is disabled at the tenant level, admins are unable to configure site Copilot at the environment level.

4. **Bing search:**  
   If disabled at the environment level, no Copilot functionality that relies on Bing search will be available. Admins must enable this feature at the environment level to allow any Copilot features that depend on bing search to function.

5. **Move data across regions:**  
   This setting can be allowed or disallowed at the environment level. If disallowed, Copilot doesn't operate when there's insufficient Azure OpenAI (AOAI) capacity within the environment’s region to process queries. Admins aren't able to configure the settings in the Copilot hub. More information: [Move data across regions for Copilots and generative AI features](/power-platform/admin/geographical-availability-copilot)

## Admin experience

Admins manage AI-powered experiences for makers and site users through the Copilot hub in the Power Platform admin center. To configure settings:

1. Go to the [**Settings** page](#access-copilot-insights-and-settings-for-power-pages).
1. Use the product filter to select **Power Pages**.
1. From the list of AI features, select any feature to view and configure its settings.
1. On the selected feature’s settings page, a list of environments within the tenant is displayed, showing environment name, type, region, status (on/off), and more.
1. Admins can select a specific environment and select **Set up/Edit** to update the feature’s configuration.
1. Once the **Set up** page is displayed, admins can enable AI features in:

    | **Option**                  | **Description**                                                                                     |
    |-----------------------------|-----------------------------------------------------------------------------------------------------|
    | **All sites**               | Selecting the **On - All sites** option enables AI-powered experiences for all websites in the environment. |
    | **All sites except specific sites** | Enables AI-powered experiences in all websites except the sites that you choose. Overrides maker configurations. |
    | **Specific sites**          | Enables AI-powered experiences only in the websites that you choose. Prevents access in other sites. |
    | **None of the sites**       | Disables all AI-powered experiences across the environment. Overrides maker configurations.         |

1. Select **Save**.

> [!IMPORTANT]  
> The tenant-level [governance configuration feature](/power-pages/admin/copilot-governance) is now deprecated. While your existing settings will remain in place, we strongly recommend reviewing and validating them to ensure they still meet your requirements. Going forward,  all governance settings for Copilot features must be managed through the Copilot hub. To view or update these settings, navigate to **Copilot hub > Power Pages > Settings** in the Power Platform admin center.
> During the deprecation phase, ensure your configurations are aligned within the Copilot hub to maintain consistency with your intended governance setup.


## Maker Experience

Makers building sites in Power Pages can benefit from integrated AI-powered capabilities through Studio Copilot and Pro Dev Copilot features, helping accelerate site creation and improve productivity.

When AI features are disabled by tenant admins, the maker experience will reflect this status clearly:

- If a maker Copilot feature (for example, Studio Copilot or Pro Dev Copilot) is disabled, makers see an in-product message informing them that the feature has been turned off by an admin. The message prompts them to reach out to their administrator to request access.
    :::image type="content" source="media/copilot-hub/maker-setting.png" alt-text="Screenshot of maker scenario when AI is enabled." lightbox="media/copilot-hub/maker-setting.png":::

- If end user AI features (for example, chatbot, search summary, and AI form fill assistance) are disabled by admins, makers can’t configure these features for their sites. The configuration options in the studio appear greyed out, and a message indicates that the feature settings are managed by the admin. Makers are advised to contact their admin to enable or manage the settings.
    :::image type="content" source="media/copilot-hub/ai_feature_disable.png" alt-text="Screenshot showing grayed-out configuration options for disabled end user AI features." lightbox="media/copilot-hub/ai_feature_disable.png":::

This ensures alignment between governance policies and maker actions, preventing unauthorized use of AI features while maintaining transparency for site builders.

## User experience

When generative AI experiences are blocked in a site for users, they fall back to the standard experience. For example, users see a regular search and don't get a generative AI powered search summary. Users don't see any messaging about organizational policies or governance controls. 

### Related information

- [Overview of AI-powered and Copilot features in Power Pages](/power-pages/configure/ai-copilot-overview)    
- [Manage Copilot in Power Platform](/power-platform/admin/copilot/copilot-hub?wt.mc_id=ppac_inproduct_copilothub)   
- [Security FAQs in Copilot Studio](/microsoft-copilot-studio/security-faq?wt.mc_id=ppac_inproduct_copilothub)   
- [FAQ for Copilot data security and privacy for Dynamics 365 and Power Platform](/power-platform/faqs-copilot-data-security-privacy?wt.mc_id=ppac_inproduct_copilothub)   
- [Empowering responsible AI practices](https://www.microsoft.com/en-in/ai/responsible-ai)  
