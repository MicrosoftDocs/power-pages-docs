---
title: Generate answers from public data using Bing search
description: Learn how to trigger Microsoft Bing to index the content of your Power Pages site immediately after you add a copilot.
ms.topic: how-to
ms.date: 04/29/2025
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
  - bap-ai-copilot
contributors:
  - nageshbhat-msft
  - DanaMartens
ms.custom: bap-template
---

# Generate answers from public data using Bing search

You can generate answers from publicly available data by utilizing Bing search. Configuring Bing search enables the generation of answers from external sources beyond the Power Pages site built on the Dataverse instance.

To use Bing search:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select the site, then select **+ Edit**.
1. Go to the **Set up** workspace and select **Add copilot** under **Copilot**.
1. Select **View copilot analytics**.
1. Select **Topics**.
1. Select the **System** tab.
1. Select the **Conversational boosting** topic.
1. Update the **Create generative answers** node to include the public websites you want to index. For more details, go to [Search public data or use a Bing Custom Search for generative answers](/microsoft-copilot-studio/nlu-generative-answers-bing).
1. Select **Save** and then select **Publish**.

    Check if your public site is indexed by searching for its content using Bing search. If no results from your site appear, it might not be indexed. You can either wait for indexing or prompt Bing Webmaster to index your site immediately.

> [!IMPORTANT]
>
> If you configure copilot for generative answers from public data using Bing search, the use of Bing search is governed by the [Microsoft Services Agreement](https://go.microsoft.com/fwlink/?linkid=2178408) and [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Force Bing Webmaster Tools to index your site (optional)

When you add a site to Copilot, Bing might not index your site immediately. Indexing can take several hours to a day. To expedite indexing, use Bing Webmaster Tools to index your site's content immediately.

### Add your site to your Bing Webmaster Tools account

1. Open [Webmaster Tools](https://www.bing.com/webmasters).
1. [Create a Bing Webmaster Tools account](https://www.bing.com/webmasters/help/getting-started-checklist-66a806de) if you don't have one yet.
1. [Add your site to your account](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b).

    - If your site is already verified on Google Search Console, you can import it to Bing Webmaster Tools.
    - If your site isn't verified on Google Search Console, you can add your site manually.

### Verify your ownership

Verify that you're the site owner using one of the following methods, also described in [Bing Webmaster Tools help](https://www.bing.com/webmasters/help/add-and-verify-site-12184f8b).

### XML file authentication

With this method, you upload an XML file to your site's root folder. In Power Pages, it's as simple as adding the file to a note on the site's home page.

1. On the **Add & verify site** page in [Webmaster Tools](https://www.bing.com/webmasters), select **XML File**.
1. Select **BingSiteAuth.xml** to download the file to your local drive.

    :::image type="content" source="media/force-bing-index/xml-verification.png" alt-text="Screenshot of the XML File option in Bing Webmaster Tools.":::

1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Web Files**.
1. Select **+ New**.
1. In **Name**, enter: *BingSiteAuth.xml*
1. In **Website**, search for and select your site.
1. In **Parent Page**, search for and select your site's home page.
1. In **Partial Url**, enter: *BingSiteAuth.xml*
1. In **Publishing State**, search for and select **Published**.
1. Select **Save**.
1. Select the **Notes** tab.
1. Upload the `BingSiteAuth.xml` file.
1. Select **Save & Close**.

### Meta tag authentication

With this method, you add a metadata tag to your site's header HTML. In Power Pages, it's as simple as adding a content snippet.

1. On the **Add & verify site** page in [Webmaster Tools](https://www.bing.com/webmasters), select **HTML Meta Tag**.
1. Select **Copy**.

    :::image type="content" source="media/force-bing-index/meta-content.png" alt-text="Screenshot of the HTML Meta Tag option in Bing Webmaster Tools.":::

1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Content Snippets**.
1. Select **+ New**.
1. In **Name**, enter: *Head/Bottom*
1. In **Website**, search for and select your site.
1. In **Display Name**, enter: *Head/Bottom*
1. Leave **Type** set to **Text**.
1. In **Content Snippet Language**, search for and select **English**.
1. In the **Value** box, paste the metadata you copied in step 2.
1. Select **Save & Close**.

### Add a Robots.txt file

Add a file to your site to tell Bing, Google, and other search engines (or *robots*) how much of its content to index. This Robots.txt file lets search engines index the entire site, but you can control which pages they index. Use Bing Webmaster Tools to easily [edit and test your Robots.txt file](https://blogs.bing.com/webmaster/september-2020/Bing-Webmaster-Tools-makes-it-easy-to-edit-and-verify-your-robots-txt).

1. On your local drive, create a text file and name it **Robots.txt**.
1. Enter the following content in the file:

    ```txt
    User-agent: *
    Disallow:
    ```

1. Save and close the file.
1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Web Files**.
1. Select **+ New**.
1. In **Name**, enter: *Robots.txt*
1. In **Website**, search for and select your site.
1. In **Parent Page**, search for and select your site's home page.
1. In **Partial Url**, enter: *Robots.txt*
1. In **Publishing State**, search for and select **Published**.
1. Select **Save**.
1. Select the **Notes** tab.
1. Upload the `Robots.txt` file.
1. Select **Save & Close**.

### Add a meta description to pages to index

A *meta description* tells search engines what text to display with the page title. It's an important part of making your site easy to find, so put thought into the description of each page you plan to index. To find guidance for creating effective meta descriptions, enter the key phrase "meta description" in your favorite search engine.

1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Web Pages**.
1. Open a page that you want to force Bing to index.
1. Enter or update the **Description** on both the **Information** form and the **Content Page** form.

    :::image type="content" source="media/force-bing-index/meta-description-example.png" alt-text="Screenshot of a web page's Information form, with the Description highlighted.":::

1. Select **Save & Close**.
1. Repeat for all pages to be indexed.

### Run an SEO scan and fix issues

Scan for common search engine optimization (SEO) issues that make your site harder to find.

1. Open [Webmaster Tools Site Scan](https://www.bing.com/webmasters/sitescan).
1. Select **Start new scan**.
1. [Follow the instructions](https://www.bing.com/webmasters/help/site-scan-623520c9) to analyze your site and view the report.
1. Fix as many of the issues the scan discovered as you reasonably can.

### Submit URLs

As the final step, index individual page URLs directly. It's a good idea to submit the URLs of any important new pages or pages with new content to get them indexed faster. You can submit up to 100 URLs per day.

1. Open [Webmaster Tools URL Submission](https://www.bing.com/webmasters/submiturl).
1. Select **Submit URLs**.
1. Enter the URLs to index, one per line.
1. Select **Submit**.

To verify the indexing status, select **URL Inspection** in the left side panel. Enter a URL, and then select **Inspect**.

Indexing usually completes within a few minutes, but it can take up to an hour to see results.

### See also

- [Create an AI-generated webpage using Copilot](../getting-started/create-page-copilot.md)
- [Create a form in a webpage using a Copilot](../getting-started/add-form-copilot.md)
- [Use Copilot to generate text and it to a webpage](../getting-started/add-text-copilot.md)
- [Add a copilot to your Power Pages site](../getting-started/enable-chatbot.md)
- [Add AI-generated code using Copilot (preview)](../configure/add-code-copilot.md)
