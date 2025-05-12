---
title: FAQ for data summarization API
description: Look up frequently asked questions (FAQ) for the data summarization API in Microsoft Power Pages.
author: nageshbhat-msft
ms.topic: faq
ms.date: 02/05/2025
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# FAQ for data summarization API

## What is the data summarization API in Power Pages?

The [data summarization API](configure/data-summarization-api.md) for Dataverse records provides summaries of records that are used on webpages. Only users who have access to a given record can retrieve the summary of it. The API is secured by using the Power Pages Auth model, it's protected by a cross-site request forgery (CSRF) token, and it can't be used outside the pages site.

The Power Pages maker can use site settings to provide the summarization prompt. Users can't modify or pass any prompt.

## What are the system capabilities?

- The feature gives makers more flexibility and control over data summarization, because they can use the API to configure UI components.
- The feature reduces the cognitive load and effort of site users by providing concise and informative summaries of complex and multipage content.
- The feature brings focus to the value and quality of page content by highlighting the most relevant and important information.

## What is the system's intended use?

The purpose of the system is to deliver concise and relevant page summaries by using the prompt that the maker configures. The summary is grounded in the website's content, which is passed by using the Power Pages API. That API is secured by using table permissions.

## How was the data summarization feature evaluated? What metrics are used to measure performance?

The capability was evaluated over custom datasets for offensive and malicious prompts and responses. The evaluation was done through both automated and dedicated manual sessions that were designed to expand the test suite.

## What are the limitations of this feature? How can users minimize the impact of those limitations when they use the system?

- The feature provides summarization for content that is passed by using the Dataverse tables and columns that are used on pages that use the Web API.
- The feature supports only the English language.
- The capability might be subject to usage limits or capacity throttling.
- The summaries that are generated aren't always perfect, and content might have inaccuracies.

## What operational factors and settings allow for effective and responsible use of the system?

Before you deploy the capability in a production system, it's crucial that you thoroughly test and review its functionality. This testing includes assessing the feature's capacity to provide responses that are accurate, relevant, and free of offensive language to user prompts on the site.
