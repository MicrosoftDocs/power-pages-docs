---
title: Change the base URL of a Power Pages site
description: Learn how to change the base URL of a website.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/16/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Change the base URL of a website

You can change the base URL of a website after it is provisioned. For example, if you choose `contosocommunity.powerappsportals.com` as the base URL when provisioning the website, you can later change it to `contosocommunityportal.powerappsportals.com` to meet your requirements.

> [!NOTE]
> Once you change the base URL of your website, the older URL will no longer be accessible and it will become available for other customers to use for their websites.

:::image type="content" source="media/change-base-url/change-base-url.png" alt-text="Change base URL.":::

1. Open up the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site for which you want to change the URL, select **Manage** from the main menu.

1. Select the pencil icon.

1. In the side panel, enter in your new URL prefix, tab off the field to see if the value is available.

1. Select **Update**.

1. The site will restart and the new URL will be available.

## Troubleshooting

If changing the base URL of a website fails, an error is displayed. Typically, these are transient errors and you can retry changing the base URL. 

If the issue persists, contact Microsoft support.


