---
title: Force Bing webmaster to index your site (preview)
description: Learn how to force Bing webmaster to index your site.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/23/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Force Bing webmaster to index your site (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Power Pages chatbot is powered by Bing. When a chatbot is enabled for a site, the URL is shared with Bing to index the content. However, there's no guarantee that Bing immediately starts indexing. This process can take several hours to a day. To trigger Bing to index your site's content, you can use Bing Webmaster by following the steps explained in this article.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - To understand capabilities and limitations of AI-powered and Copilot features in Power Pages, see [Responsible AI transparency notes for Power Pages](../transparency-note.md).

## Add and verify site

Follow guidelines from [Webmaster tools help](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b) to add to your site. To verify your ownership to site, you can follow one of the two methods in Power Pages.

### Method 1. XML file authentication

1. Download **BingSiteAuth.xml** file from [Webmasters tools](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b)

    :::image type="content" source="media/force-bing-index/xml-verification.png" alt-text="A screenshot showing XML file verification." border="false":::

1. Open [Portal Management app](../configure/portal-management-app.md) of your site.

1. Go to **Web Files**.

1. Select **New Web File**.

1. Enter a name. For example, "Bing Site Auth".

1. Select your website.

1. Select **Home** in the **Parent Page** field.

1. Enter partial URL. For example, "BingSiteAuth.xml".

    > [!NOTE]
    > Partial URL must be same as the file name.

1. Select **Publishing state** as **Published**.

1. Select **Save**.

1. Under **Notes** tab, upload the file. In this example, "BingSiteAuth.xml".

    :::image type="content" source="media/force-bing-index/uploaded-file.png" alt-text="A screenshot showing the uploaded XML file." border="false":::

### Method 2. Meta tag authentication

1. Copy the meta content.

    :::image type="content" source="media/force-bing-index/meta-content.png" alt-text="A screenshot showing meta tag authentication." border="false":::

1. Open [Portal Management app](../configure/portal-management-app.md) of your site.

1. Go to **Content Snippets**.

1. Select **New Content Snippet**.

1. Enter the following values.

    1. Name - **Head/Bottom**
    1. Select your website.
    1. Display name - **Head/Bottom**
    1. Type - **Text**
    1. Content Snippet Language - **English**
    1. Value - paste the meta content.

1. Select **Save**.

## Add Robot.txt

1. Create a **Robots.txt** with the following content:

    ```
    **User-agent: ***
    **Disallow:**
    ```

    > [!NOTE]
    > The steps in this article use sample content that allows entire site to be indexed. However, you can change the content of Robot.txt as per the applicable standards and your business requirements.

1. Open [Portal Management app](../configure/portal-management-app.md) of your site.

1. Go to **Web Files**.

1. Select **New Web File**.

1. Enter a name. For example, "Robot.txt".

1. Select your website.

1. Select **Home** in the **Parent Page** field.

1. Enter partial URL. For example, "Robots.txt".

1. Select **Publishing state** as **Published**.

1. Select **Save**.

1. Under **Notes** tab, upload the file. In this example, "Robot.txt".

## Add meta description tag

1. Open [Portal Management app](../configure/portal-management-app.md) of your site.

1. Go to Web Pages.

1. Open the web page where you want to force Bing to index.

1. Update the **Description** field for both **Information form** and **Content Page form**.

    :::image type="content" source="media/force-bing-index/description.png" alt-text="A screenshot showing description tag." border="false":::

1. Save the record.

1. Repeat the steps for all pages to be indexed.

## Run SEO scan and fix issues

1. Open [Webmaster tools](https://www.bing.com/webmasters/sitescan)

1. Select **Site Scan** under **SEO**.

    :::image type="content" source="media/force-bing-index/site-scan.png" alt-text="A screenshot showing site scan." border="false":::

1. Select **Start New Scan**.

1. Enter a relevant name to scan name, URL of your website, and the total number of pages. And then, select **Start Scan**.

    After the scan is complete, the results are shown in the **Site Scan** dashboard.    

1. Open the scan to know the site related errors.

1. Resolve the errors related to the web page where you want to force Bing to index.

## Submit URLs

1. Open [Webmaster tools](https://www.bing.com/webmasters/sitescan)

1. Go to **URL Submission**.

1. Select **Submit URLs** button.

1. Enter all the URLs to that needs indexing.

1. Verify the indexing status by navigating to **URL inspection**.

Indexing might complete within a few minutes. However, it may take an hour to get the actual result on the bot.

### See also

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Enable chatbot in Power Pages site](enable-chatbot.md)
- [Create a form in a webpage using a Copilot](add-form-copilot.md)
- [Use Copilot to generate text and it to a webpage](add-text-copilot.md)