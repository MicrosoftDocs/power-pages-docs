---
title: Set up Power BI integration
description: Learn how to set up Power BI integration with your website. View and embed dashboards and reports by enabling Power BI visualization and Power BI Embedded.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/20/2023
ms.subservice:
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
---

# Set up Power BI integration

Power BI is one of the best tools to deliver insights with simple and interactive visualization. To view dashboards and reports from Power BI on webpages on a website, you must enable Power BI visualization from the Power Platform admin center. You can also embed dashboards and reports created in the new workspace of Power BI by enabling the Power BI Embedded service integration.

> [!NOTE]
> - You must have an appropriate Power BI license.
> - To use Power BI Embedded service, you must have an appropriate Power BI Embedded license. Ensure you review [capacity planning](/power-bi/developer/embedded/embedded-capacity-planning), and [pricing](https://azure.microsoft.com/pricing/details/power-bi-embedded/) for Power BI Embedded. More information: [Power BI Embedded Licensing FAQs](/power-bi/developer/embedded-faq#licensing).
> - Ensure that **Embed content in apps** is *Enabled* in your Power BI tenant [Developer settings](/power-bi/guidance/admin-tenant-settings#developer-settings). When disabled, a portal can't render embedded Power BI dashboards or reports.

## Enable Power BI visualization

Enabling Power BI visualization allows you to embed dashboards and reports on webpages in a website by using the *powerbi* [Liquid](../configure/liquid-overview.md) tag.

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to enable Power BI visualization. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable Power BI visualization.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to enable Power BI visualization. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select **Power BI Visualization** link.

    :::image type="content" source="media/enable-power-bi/admin-center-enable-powerbi.png" alt-text="Enable Power BI.":::

1. The legacy Power Apps portals admin center will open. Select **Enable Power BI visualization**.

1.	Select **Enable** in the confirmation message. While Power BI visualization is being enabled, the website will restart and be unavailable for a few minutes. A message will appear when Power BI visualization has been enabled.

1. Select **Close**.

Customizers can now use the [powerbi Liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi) to embed Power BI dashboards and reports on webpages in a website. While embedding the Power BI content, customizers can use [filter parameters](/power-bi/service-url-filters) to create personalized views. For more information, see [powerbi Liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi).

### Disable Power BI visualization

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to disable Power BI visualization. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable Power BI visualization.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to disable Power BI visualization. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select **Power BI Visualization** link.

1. The legacy Power Apps portals admin center will open. Select **Disable Power BI visualization**.

1.	Select **Disable** in the confirmation message. While Power BI visualization is being disabled, the website will restart and be unavailable for a few minutes. A message will appear when Power BI visualization has been enabled.

1. Select **Close**.

## Enable Power BI Embedded service

Enabling the Power BI Embedded service allows you to embed dashboards and reports created in the new workspace of Power BI. The dashboards and reports are embedded on webpages in a portal by using the *powerbi* [Liquid](../configure/liquid-overview.md) tag.

**Prerequisites**: Before enabling the Power BI Embedded service, ensure that you've created your dashboards and reports in the new workspace in Power BI. After creating the workspace, provide admin access to the global administrator (by directly adding global administrator user to the workspace instead of via group membership) so the workspaces are displayed in the Power Platform admin center. For more information on creating new workspaces and adding access to them, see [Create the new workspaces in Power BI](/power-bi/service-create-the-new-workspaces).

> [!NOTE]
> Ensure that Power BI visualization is enabled for the *powerbi* Liquid tag to work.

**To enable Power BI Embedded service:**

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to enable Power BI Embedded service. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable Power BI Embedded.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to enable Power BI Embedded. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select **Power BI Embedded** link.

    :::image type="content" source="media/enable-power-bi/enable-power-bi-embedded.png" alt-text="Enable Power BI Embedded.":::

1. The legacy Power Apps portals admin center will open. Select **Enable Power BI Embedded**.

1. In the **Enable Power BI Embedded service integration** window, select the available workspaces from which you want dashboards and reports to be displayed in your portal. Move these workspaces to the **Selected Workspaces** list.

    :::image type="content" source="media/enable-power-bi/enable-powerbi-embedded-window.png" alt-text="Select Power BI workspaces.":::
    
    > [!NOTE]
    > After you add workspaces to the **Selected Workspaces** list, the databases and reports are rendered after a few minutes.
    
1. Select **Enable**. While Power BI Embedded service is being enabled, the website restarts and is unavailable for a few minutes. A message appears when Power BI Embedded service is enabled.

After enabling the Power BI Embedded service, you must create a security group, and add it to your Power BI account. For more information, see [Create security group and add to Power BI account](#create-security-group-and-add-to-power-bi-account).

### Create security group and add to Power BI account

After enabling the Power BI Embedded service integration, you must create a security group in Azure Active Directory, add a member to it, and then add the security group in Power BI through the Power BI admin portal. This configuration allows the dashboards and reports created in new Power BI workspaces to be displayed in the portal.

> [!NOTE]
> You must sign in with the same Global administrator account that you used to enable the Power BI Embedded service.

**Step 1: Create a security group**

1. Sign in to the [Azure portal](https://portal.azure.com) using a Global administrator account for the directory.

1. Select **Azure Active Directory**, **Groups**, and then select **New group**.

1. On the **Group** page, enter the following information:

    - **Group type**: Security

    - **Group name**: Power Pages Power BI Embedded service

    - **Group description**: This security group is used for Power Pages and Power BI Embedded service integration.

    - **Membership type**: Assigned

      :::image type="content" source="media/enable-power-bi/powerbi-embed-security-group.png" alt-text="Create security group for Power BI Embedded service.":::
  
1. Select **Create**.

**Step 2: Add a group member**

**Prerequisite**: Before adding a member to the security group, you must have the website's application ID. The ID is available on the **Site Details** section for the selected website in the [Power Platform admin center](admin-overview.md).

1. Sign in to the [Azure portal](https://portal.azure.com) using a Global administrator account for the directory.

1. Select **Azure Active Directory**, and then select **Groups**.

1. From the **Groups - All groups** page, search for and select the **Power Pages Power BI Embedded service** group.

1. From the **Power Pages Power BI Embedded service Overview** page, select **Members** from the **Manage** area.

1. Select **Add members**, and enter the website's application ID in the text box.

1. Select the member from the search result, and then choose **Select**.

**Step 3: Power BI setup**

1. Sign in to [Power BI](https://powerbi.microsoft.com) using a Global administrator account for the directory.

1. Select the **Settings** icon in the top right of the Power BI service, and choose **Admin portal**.

    :::image type="content" source="media/enable-power-bi/select-admin-portal.png" alt-text="Select Admin portal in Power BI service.":::

1. Select **Tenant settings**.

1. Under the **Developer settings** section, select **Allow service principals to use Power BI APIs**.

1. In the **Specific security groups** field, search for and select the **Portal Power BI Embedded service** group.

    :::image type="content" source="media/enable-power-bi/add-sg-powerbi.png" alt-text="Add security group in Power BI Admin portal.":::

1. Select **Apply**.

Customizers can now use the [powerbi Liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi) to embed Power BI dashboards and reports from new Power BI workspaces onto webpages in a website. To use Power BI Embedded service, the authentication type must be specified as **powerbiembedded**. While embedding the Power BI content, customizers can use [filter parameters](/power-bi/service-url-filters) to create personalized views. For more information, see [powerbi Liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi).

### Manage the Power BI Embedded service

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to manage the Power BI Embedded service. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable Power BI Embedded.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to manage Power BI Embedded. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select **Power BI Embedded** link.

    :::image type="content" source="media/enable-power-bi/enable-power-bi-embedded.png" alt-text="Enable Power BI Embedded.":::

1. The legacy Power Apps portals admin center will open. Select **Manage Power BI Embedded**.

1. In the **Manage Power BI Embedded service integration** window, select the available workspaces from which you want dashboards and reports to be displayed on your website. Move these workspaces to the **Selected Workspaces** list. You can also remove currently used workspaces by moving them back to **Available Workspaces**.
  
    :::image type="content" source="media/enable-power-bi/manage-powerbi-embedded-window.png" alt-text="Manage Power BI Embedded service integration.":::

    > [!NOTE]
    > After removing workspaces from the **Selected Workspaces** list, it can take up to 1 hour to reflect the changes. Until then, the databases and reports are rendered on the portal without any issues.

1. Select **Save**.

### Disable the Power BI Embedded service

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to manage the Power BI Embedded service. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to enable Power BI Embedded.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to manage Power BI Embedded. Select **Manage** from the main menu.

1. On the site information page, in the **Services** section, select **Power BI Embedded** link.

    :::image type="content" source="media/enable-power-bi/enable-power-bi-embedded.png" alt-text="Enable Power BI Embedded.":::

1. The legacy Power Apps portals admin center will open. Select **Manage Power BI Embedded**.

1. In the **Manage Power BI Embedded service integration** window, select **Disable Power BI Embedded service integration**.

    :::image type="content" source="media/enable-power-bi/disable-powerbi-embedded-window.png" alt-text="Disable Power BI Embedded service integration.":::

1. Select **Save**.

1. Select **OK** in the confirmation message. While Power BI Embedded service is being disabled, the website will restart and be unavailable for a few minutes. A message will appear when Power BI Embedded service has been disabled.

## Considerations and limitations

- Portals with version [9.3.4.x](/power-apps/maker/portals/versions/version-9.3.4.x) or later supports the following capabilities:
    - Dashboards and report from Azure Analysis Services using [live connections](/azure/analysis-services/analysis-services-connect-pbi). Azure Analysis Services on-premises configurations are not supported.
    - Dashboards with [role-based security](/power-bi/admin/service-admin-rls).
    - Single tile with role-based security.
- Power BI visualization functionality is not available in the China region for Azure Active Directory authentication.
- For more information about Power BI Embedded service limitations, see [Considerations and limitations](/power-bi/developer/embed-service-principal#considerations-and-limitations).

### Rendering a Power BI report on a webpage fails with the following error:

*A configuration error occurred while rendering your report.*

This problem can happen because of multiple reasons such as:

- Your [Power BI Embedded configuration](#enable-power-bi-embedded-service) is incorrect.
- [Row-level security](/power-bi/admin/service-admin-rls) in Power BI is enabled but you didn't pass roles in [Power BI component configuration](../getting-started/add-power-bi.md) (Advanced settings), or *roles* parameter in the [powerbi liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi).
- **Embed content in apps** in Power BI [Developer Settings](/power-bi/admin/service-admin-portal#developer-settings) isn't enabled.

## Privacy notice  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../includes/cc-privacy-powerbi-tiles-dashboards.md)]

## Next steps

[Add a Power BI component to a webpage](../getting-started/add-power-bi.md)

### See also

- [Add a Power BI report or dashboard to a webpage using liquid tag](/power-apps/maker/portals/admin/add-powerbi-report)
- [powerbi Liquid tag](../configure/liquid/dataverse-liquid-tags.md#powerbi)
- [Integration with Power BI](/training/modules/portals-integration/3-power-bi)


