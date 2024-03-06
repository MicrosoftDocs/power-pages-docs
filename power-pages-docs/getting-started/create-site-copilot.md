---
title: Copilot for site creation (preview)
description: Learn how to create an AI-generated site using Copilot in Power Pages.
author: sampatn
ms.topic: conceptual
ms.custom: 
ms.date: 09/26/2023
ms.subservice:
ms.author: sampatn
ms.reviewer: kkendrick
ms.collection: 
    - bap-ai-copilot
contributors:
    - tapanm-msft
    - ProfessorKendrick
---

# Create an AI-generated site using Copilot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

With the Copilot for site creation, you can create Power Pages sites with the help of AI. Describe the site that you want to create, and AI designs it for you. Use natural language processing to help you build your site by describing the type of site, intended users of the site, and type of information you want the site to process.

Copilot generates the contextual site name, site address, home page layout, and more pages with HTML for each page with relevant text copy and images from the description. The site is created with the home page and more pages as selected, with the pages added to the sitemap. Once the site is created, these pages can be refined and edited using Copilot and the WYSIWYG editor.

For this preview, Copilot in Power Pages is enabled by default.

:::image type="content" source="media/create-site-copilot/copilot-create-site.png" alt-text="The Copilot on Power Pages home with an input field for users to enter a description of the site emphasized.":::

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This preview feature doesn't support non-English language input.
> - Please see the availability of Copilot in your geographical region [here](/power-platform/admin/geographical-availability-copilot). 
> - To understand the capabilities and limitations of this feature, see [FAQ for Copilot for site creation](../faqs-generate-site.md).

## Create a site with the help of AI

To use Copilot for site creation:

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. Enter a description of the site you want to build or select a suggested description of the site. Then press the Enter key or select the paper airplane icon in the lower-right corner of the text box.

    Example descriptions:

     - Build a website for public transportation for residents of city, to view routes and fares.
     - Create a site for customers to find financial advisors at a bank based on their qualifications, and areas of expertise.

1. Copilot generates a site name and a web address based on your description. Edit these suggestions as needed for your site, and select **Next**.

1. Copilot generates a home page layout, which you can scroll through and browse the page generated. Select **Try again** to generate a new layout or select **Next** to accept the suggested layout.

1. Copilot generates more pages that could be used in the site based on the description. Describe one or more pages and select **Done** to complete the site creation.

Site creation can take a few minutes. When finished, you're redirected to the site opened in the [design studio](use-design-studio.md) that you can customize further.

>[!NOTE]
> - If the enhanced data model is disabled, Copilot for site creation is also disabled. Be sure to enable the [Enhanced data model](../admin/enhanced-data-model.md). 
> - Copilot-generated pages will reference images that are saved as web files.
> - Web files can only be deleted through the Power Pages management app. More information: [Create and manage web files](../configure/web-files.md)

## Next steps

[Style your pages site](style-site.md)

### See also

- [Overview of AI-powered and Copilot features in Power Pages (preview)](../configure/ai-copilot-overview.md)
- [FAQ for Copilot for site creation](../faqs-generate-site.md)
