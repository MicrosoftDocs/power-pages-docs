---
title: FAQ for Power Pages data summarization API
description: "Look up frequently asked questions (FAQ) for the data summarization API of Microsoft Power Pages."
author: danamartens
ms.topic: conceptual
ms.date: 09/05/2024
ms.author: dmartens
ms.reviewer: dmartens
contributors:
    - dmartens
    - tapanm
---

# FAQ for Power Pages data summarization API

## What is data summarization API in Power Pages?

The summarization API for Dataverse records provides summaries for records used in web pages. Only users with access to the record can retrieve the summary. The API is secured using the Power Pages Auth model, protected by a CSRF token, and cannot be used outside the pages site. The Power Pages maker can provide the summarization prompt using site settings, end user cannot modify or pass any prompt.

## What are the system capabilities?

- It gives the makers more flexibility and control over the data summarization, by allowing them to configure UI component using the API.

- It reduces the cognitive load and effort on the part of the site users, by providing them with concise and informative summaries of the complex and multi-page content.

- It brings focus to the value and quality of the content on the pages, by highlighting the most relevant and important information.

## What is the system's intended use?

The system aims to deliver concise and relevant page summaries by the prompt configured by C1 maker. The summary is grounded in the website's content passed using the Power Pages API that is secured using the table permission.

## How was the data summarization feature evaluated? What metrics are used to measure performance?

The capability was evaluated over custom datasets for offensive and malicious prompts and responses, through both automated and dedicated manual sessions designed to expand the test suite.

## What are the limitations of this feature? How can users minimize the impact of the copilot limitations when using the system?

- The feature will provide summarization for the content passed using the dataverse tables and columns used in pages using the web API.

- This feature will support only English language.

- This capability may be subject to usage limits or capacity throttling.

- Summaries generated are not always perfect and content may have inaccuracies.

## What operational factors and settings allow for effective and responsible use of the system?

- Before deploying capability into the production system, it's crucial to thoroughly test and review its functionality. This includes assessing its capacity to provide accurate, relevant, and free of offensive language responses to user prompts on the site.
