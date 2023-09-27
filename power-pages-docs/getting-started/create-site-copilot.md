---
title: Create an AI-generated site using Copilot (preview)
description: Learn how to create an AI-generated site using Copilot in Power Pages.
author: sampatn
ms.topic: conceptual
ms.custom: 
ms.date: 09/26/2023
ms.subservice:
ms.author: sampatn
ms.reviewer: tapanm
contributors:
    - tapanm
    - sampatn
---
# Create an AI-generated site using Copilot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

You can create a new site by describing the type of site. Copilot generates the contextual site name, site address, Home page layout, and additional pages with HTML for each page with relevant text copy and images from the description. The site is created with the Home page and additional pages selected, with the pages added to the sitemap. Once the site is created, these pages can be refined and edited using Copilot and the WYSIWYG editor.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature doesn't support non-English language input.
> - This feature will be available for preview in the Dataverse environments located in the United States only.
> - To understand capabilities and limitations of AI-powered Copilot features in Power Pages, see [FAQ for Copilot to generate site](../faqs-generate-site.md).

## Prerequisites

- Maker Copilot features are only available for sites in US-based dataverse environments. 

## Generate a site

To use Copilot to generate a webpage:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Type a description of the site you want to build or select a suggested description of the site, and click **Submit** button or hit Enter on keyboard.

    :::image type="content" source="media/common/copilot/home-copilot-create-site-input.png" alt-text="The Copilot on Power Pages home with to input a description of the site.":::

    Sample descriptions:

     - Build a website for Public transportation. 
     - Create a site to find a financial advisor for a bank that offers loans.
       
1. Copilot generates a site name and a web address based on your description. You can edit these suggestions as needed for your site and click **Next**

    :::image type="content" source="media/common/copilot/copilot-create-site-site-details.png" alt-text="Copilot generated site details.":::

1. Copilot generates a home page layout, which you can scroll through and browse the page generated. You can select **Try again** to generate a new layout or click **Next** to accept the suggested layout.

    :::image type="content" source="media/common/copilot/copilot-create-site-home-layout.png" alt-text="Copilot generated home page layout.":::

1. Copilot generates additional pages that could be used in the site based on the description. You can one or more pages and click **Done** to complete the site creation. You can always iterate on these pages from the Power Pages Design Studio editing capabilities and Copilot capabilities.

    :::image type="content" source="media/common/copilot/copilot-create-site-common-pages.png" alt-text="Copilot generated common pages.":::

Site creation may take up to 120 seconds, and upon completion, you will be re-directed to the Site opened in the Power Pages Design Studio, where you can continue to leverage the Copilot capabilites and the WYSIWYG editor to make changes, create forms, sections, pages, etc. 
   
## Discard a Copilot-generated home page layout

If you don't want to keep the home page layout that Copilot generated, you can:

- Select **Try again** and Copilot generates another layout based on your last input.

    
    >[!NOTE] 
    > - Copilot-generated pages will reference images that are saved as web files.
    > - Web files can only be deleted through the Power Pages management app. More information: [Create and manage web files](../configure/web-files.md)
