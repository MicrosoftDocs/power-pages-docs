---
title: FAQ for site search with generative AI
description: This FAQ discusses generative AI search and key considerations for making use of this technology responsibly.
ms.date: 02/05/2025
ms.update-cycle: 180-days
ms.custom: responsible-ai-faqs
ms.topic: faq
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - DanaMartens
---

# FAQ for site search with generative AI

These frequently asked questions (FAQ) detail how generative AI search functions in Power Pages.

## What is generative AI search in Power Pages?

The Power Pages Site Search with Generative AI provides site users with summarized responses to their natural language queries, utilizing generative AI technology. Additionally, it uses a semantic search approach in contrast to the traditional keyword-based methods, offering more relevant, and contextualized information. Summaries generated by site search with gen AI are directly extracted from the website content, ensuring alignment with user access permissions and enhancing the overall search experience.

## What are the system’s capabilities?

- It reduces the cognitive load and effort on the part of the site users, by providing them with concise and informative summaries that answer their queries.
- It gives the makers more flexibility and control over the search functionality, by allowing them to configure both the keyword-based and the generative AI based search options.
- It brings focus to the value and quality of the content on the pages and sites, by highlighting the most relevant and important information.

## What is the system’s intended use?

The system aims to deliver concise and relevant search results in response to user queries input in natural language. The search results are grounded in the website’s content and honor the user’s roles and permissions.

## How was the feature evaluated? What metrics are used to measure performance?

The capability was evaluated over custom datasets for offensive and malicious prompts and responses, through both automated and dedicated manual sessions designed to expand the test suite.

## What are the limitations of this feature? How can users minimize the effects of the copilot limitations when using the system?

- The feature provides summarized responses from only unstructured data used on the website, such as content stored as multiline columns or files in Dataverse. The keyword-based result includes both structured and unstructured content.
- Check the [availability of Copilot in your geographical region and language](https://aka.ms/bapcopilot-intl-report-external).
- This capability might be subject to usage limits or capacity throttling.
- Search responses generated aren't always perfect and content might have inaccuracies.  

## What operational factors and settings allow for effective and responsible use of the system?

- Before deploying capability into the production system, it's crucial to thoroughly test and review its functionality. This includes assessing its capacity to provide accurate, relevant, and free of offensive language responses to user prompts on the site.
- Use the **refine your data** option in Power Pages Studio to scope the search responses used to generate the answers.

## See also

- [FAQ for Copilot data security and privacy in Microsoft Power Platform](/power-platform/faqs-copilot-data-security-privacy/)
