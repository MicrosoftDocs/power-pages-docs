---
title: How to run site checker
description: Learn how to run the Power Pages Site Checker to help you identify common problems within your website and get suggestions on how to fix them.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 03/03/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Run Site Checker

The **Site Checker** is a self-service diagnostic tool that can be used by administrators to identify common issues in their website. Site Checker helps to identify issues with a website by looking at various configuration parameters and provides suggestions on how to fix them.

When you run Site Checker, the results are displayed in the **Diagnostic Results** section in a grid format. The results grid has the following columns:

- **Issue**: Displays the top-level issue faced by a customer; for example, performance issue.
- **Category**: Displays the top-level area where issues can be categorized; for example, provisioning or solution upgrade.
- **Result**: Displays the status of the issue; for example, error or warning.

By default, information in the grid is sorted by the **Result** column in this order: error, warning, and pass.

:::image type="content" source="media/site-checker/site-checker-results.png" alt-text="site checker result grid.":::

You can expand an issue to view detailed information and mitigation steps. If the mitigation requires any action, you'll see a button that will perform the action. You can also provide feedback on whether the mitigation was useful.

:::image type="content" source="media/site-checker/site-checker-expand.png" alt-text="Expand an issue in diagnostic results":::

If required, you can rerun the diagnostic checks, which will refresh the results with updated data.

> [!NOTE]
> If the website is turned off or IP address filtering is enabled, certain diagnostic checks will not be run on your website.

For a list of common issues diagnosed by the Site Checker, see [Power Pages faq](../faq.yml).

To run Site Checker:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under the **Resources** section select **Power Pages sites**.

1. Select your website.

1. In the **Site Health** section, select **Run** in the **Site Checker** panel. 

    :::image type="content" source="media/site-checker/run-diagnostics.png" alt-text="Run diagnostics.":::


1. The diagnostic session will start and gather data about the customer issues. The results are displayed in the **Diagnostic Results** section.

    :::image type="content" source="media/site-checker/site-checker-results.png" alt-text="site checker result grid.":::

1. To rerun the diagnostic checks, select **Refresh results**.

## Identifying web pages listed in diagnostic results

The site checker diagnostic results could list web pages that have the same name as other pages in the website. If there are multiple web pages with the same name, you can identify the specific page affected using the unique guid of the page.

1. Open the [Portal Management app](../configure/portal-management-app.md).

1. In the left pane, select **Web Pages**.

1. Open any web page.

1. Replace the ID in the URL with the guid specified in the portal checker diagnostic results.

    :::image type="content" source="media/site-checker/webpage-by-id.png" alt-text="Replacing the web page ID the URL.":::

## Next steps

Analyze and resolve Site Checker diagnostics results:
- [Cache invalidation issues](site-checker-cache-invalidation.md)
- [Configuration issues](site-checker-configuration-issues.md)
- [Performance issues](site-checker-performance.md)
- [Website start-up issues](site-checker-startup-issue.md)
- [Provisioning issues](site-checker-provisioning-issues.md)

