---
title: FAQ for Copilot for design studio
description: This FAQ discusses natural language to page and the key considerations for making use of this technology responsibly.
ms.date: 02/05/2025
ms.custom: responsible-ai-faqs
ms.topic: article
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - sandhangitmsft
    - DanaMartens
---

# FAQ for Copilot for design studio

These frequently asked questions (FAQ) describe the AI impact of natural language to page feature in Power Pages, and the key considerations for making use of this technology responsibly.

## What is Copilot for design studio?

Copilot for Power Pages design studio is available via Pages workspace and helps you jumpstart your site making journey by allowing you to add new pages, update existing pages with sections or forms, and apply new site themes by describing them using natural language, and by asking questions to get help or unblock yourself while creating sites with Power Pages.

## What can Copilot for design studio do?

The system allows you to customize pages and ask questions by describing your requirements in natural language. Use the following prompts to generate the following outcomes:

- **Add a page**: The system creates a new page with AI generated layout and content with rich text and images. The system also allows creation of a page with FAQs from a document on Sharepoint.
- **Add a section**: The system updates an existing page with a new section where the content is AI generated
- **Add a form**: The system creates a new AI generated form along with the underlying table and columns in Microsoft Dataverse. More information: [Create AI-generated form using Copilot](getting-started/add-form-copilot.md)
- **Create a theme**: The system creates a new AI generated theme for a brand that you can review and choose to apply to the site
- **How do I**: The system generates a summarized response to your question and might generate step-by-step instructions for you to follow.

With Copilot you can change AI-generated output by using regenerate, revising the prompt, or by using one of the out-of-box suggestions. You can also use the undo feature to revert the update done by Copilot. At any point, users can choose to use the existing standard capabilities of the Studio to change page elements.

## What is Copilot for design studio’s intended use?

The intended use case for Copilot for Design Studio is to aid users in creating and customizing web pages, especially when starting or prototyping a new Power Pages site. Copilot for design studio allows users to jumpstart the process of page creation and continuous editing by describing their needs using natural language. The system also allows makers to enhance their existing pages by updating the theme, styles, and content. The system also supports asking for information on how to use Power Pages, where to find a particular setting, or questions you would otherwise look up in help documentation.

## How was Copilot for design studio evaluated? What metrics are used to measure performance?

We conducted extensive testing before the feature release. Copilot for design studio relies on user feedback to report if the AI-generated text content isn't relevant or inappropriate. If you receive irrelevant or inappropriate responses, report it to Microsoft using the thumbs down gesture and include feedback in the form. We track the telemetry of thumbs up and thumbs down gestures present in the Copilot experiences for each AI-generated output. Your feedback helps improve the functionality moving forward.

## What are the limitations of Copilot for design studio? How can users minimize the impact of Copilot for design studio’s limitations when using the system?

- This feature doesn’t support non-English language input.
- See the [availability of Copilot in your geographical region](/power-platform/admin/geographical-availability-copilot).
- There's a limit on the number of tokens allowed in a query and response, so you might see corresponding limits on the number words that you can use in your prompt description, which might vary based on your use case.
- A FAQ page is created from a document on Sharepoint only if the prerequisites are met:
  - Document with sensitivity labels Public or General.
  - Documents max size is 28 MB, and only first 50k characters are used to generate FAQ content.
  - Only up to 12 questions and answers are generated in the page.
  - Additional instructions aren't supported, for example, **create a page with questions about company history using this Word doc..**.
  - To reduce the risk of generating harmful content, ensure documents are obtained from trusted sources.

## What operational factors and settings allow for effective and responsible use of Copilot for design studio?

Copilot for design studio is available when sites are in private mode so that users don't automatically publish AI generated content on their public sites. When Copilot generates a new page or updates an existing page, you can review the suggested updates and use options like undo to reject that change. Other options such suggested prompts, regenerate, or revising your prompt are options available for more attempts if the generated content isn't correct or appropriate for your requirements.

## See also

- [Add AI-generated text using Copilot](getting-started/add-text-copilot.md)
- [Add an AI-generated form using Copilot](getting-started/add-form-copilot.md)
- [Add an AI-generated multistep form using Copilot (preview)](getting-started/multistep-forms-copilot.md)
- [Create AI-generated theme using Copilot](getting-started/theme-copilot.md)
- [FAQ for Copilot data security and privacy in Microsoft Power Platform](/power-platform/faqs-copilot-data-security-privacy/)
