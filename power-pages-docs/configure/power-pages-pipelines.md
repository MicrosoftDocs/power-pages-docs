---
title: Use Power Platform pipelines with Power Pages
description: Learn how to use Power Platform pipelines with Power Pages
author: gitanjalisingh33msft

ms.topic: conceptual
ms.custom: 
ms.date: 06/14/2023
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - gitanjalisingh33msft
    - nickdoelman
---

# Use Power Platform pipelines with Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Using Power Platform pipelines with Power Pages solutions allows you to automate the deployment of websites from development environments to target environments like test and production.  

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

To try this feature, you require at minimum two Power Platform environments that have the enhanced data model enabled, one designated as the source and the other as the target. See [Power Pages enhanced data model](../admin/enhanced-data-model.md) to enable the enhanced data model for an environment.

You can have multiple target environments depending on your setup. For example, a testing, staging, and production environments.

Each environment requires a site that is created using the new data model. See [create a website with an enhanced data model](../admin/enhanced-data-model.md#create-a-website-with-an-enhanced-data-model).

You also need to set up and configure a pipeline from your development environment to corresponding target environments. See [Power Platform pipelines](/power-platform/alm/pipelines) for details on how to configure pipelines.

## Deploy solutions using pipelines

1. In your development environment, create and configure your website and add the website to a solution, see [Use solutions with Power Pages](power-pages-solutions.md) for details on how to add website configuration data to a solution.

1. In the solution, select the **Pipelines** icon on the side toolbar.

1. Select a pipeline from the dropdown list.

1. Select **Deploy here**.

1. Choose whether you wish to deploy immediately or schedule the deployment for a later time.

1. Select **Next**.

1. Verify the summary, modify the version number and deployment notes and select **Deploy**.

Watch this video to see how to deploy a solution using pipelines:
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW15YVG]

## Activate on the target environment

The first time you deploy a website to a destination environment, you need to reactivate the site. See [Reactivating site on target environment](/admin/migrate-site-configuration.md?tabs=sol#reactivating-site-on-target-environment) for information on how to reactivate a website that has been deployed to the destination environment.

When the site has been deployed, you can continue to deploy more configuration changes using the same pipeline process. You need to [clear the cache](../admin/clear-server-side-cache.md) on the destination website to see the changes.

### See also

- [Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm)
- [Overview of pipelines in Power Platform](/power-platform/alm/pipelines)