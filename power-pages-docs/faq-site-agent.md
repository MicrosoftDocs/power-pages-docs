---
title: FAQ for site agent
description: This FAQ to add agent and the key considerations for making use of this technology responsibly.
ms.date: 06/17/2025
ms.update-cycle: 180-days
ms.custom: responsible-ai-faqs
ms.topic: faq
author: pranita225
ms.author: prpadalw
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - nageshbhat-msft
    - DanaMartens
---

# FAQ for site agent

These frequently asked questions (FAQ) describe the AI impact of agent feature in Power Pages.

## What is agent in Power Pages?

The agent feature in Power Pages provides you with an easy way to configure a GPT-powered Microsoft Copilot Studio agent for your website. The agent enhances the interaction experience for the website users by enabling them to ask natural language (NL) questions and receive summarized responses with relevant links. This experience allows site users to get the necessary information available on the website - for example, through FAQs or knowledge articles easily using the agent without the need to search and locate the information manually.

## What are the system’s capabilities?

An agent for sites created in Power Pages for providing generative answers to customer queries. Bing indexing is used for unauthenticated public site content, while Dataverse Copilot handles the indexing of private and authenticated user-specific content. This enables web users to ask natural language questions and receive summarized responses. You can test the agent before publishing it to ensure that it provides appropriate summaries. Service administrators can also turn off the publishing of the agent at the tenant level to prevent accidental or unintended exposure of AI capabilities on the public site. Additionally, you can navigate to the associated Microsoft Copilot Studio agent for advanced configuration and customization.

## What is the system’s intended use?

Copilot on Power Pages site enhances the conversational capabilities by enabling site users to ask queries in natural language and receive summarized responses. Copilot has the ability to add more complex conversational features, such as contextual understanding, entity recognition, and sentiment analysis. These capabilities allow the agent to better understand user inputs and provide more accurate and helpful responses.

## How was agent feature evaluated? What metrics are used to measure performance?

The capability was evaluated on a collection of manually curated question-and-answer datasets, covering multiple industries.

More evaluation was performed over custom datasets for offensive and malicious prompts and responses.

## What are the limitations of this feature? How can users minimize the impact of the agent limitations when using the system?

- This feature doesn't check the correctness of responses returned by the agent.
- Nonfactual responses might be generated if the source information is incorrect.
- AI-generated responses might be inaccurate. Review content before using it.
- GPT answers don't support websites that sell prohibitive products or services, as these terms get intentionally blocked by content moderation. An exception to this exclusion is if the content moderation slider gets set to **Low**.
- That the agent sometimes returns misguiding responses for high-risk domains that include healthcare finance, communications, and legal.

## What operational factors and settings allow for effective and responsible use of the system?

You're able to test the agent before making it available to your site users. Evaluate agent's performance&mdash;that is, the ability of agent to return relevant, accurate, and offensive-language-free responses to site user's inquiries.

When a feature is enabled, the agent is created with a content moderation set to **High** by default. This setting filters the offensive content by using Azure Open AI’s content filtering and Azure Content Moderator.

## See also

- [Add an agent to your Power Pages site](getting-started/enable-agent.md)
- [Generate answers from public data using Bing search](getting-started/force-bing-index.md)
- [FAQ for Copilot data security and privacy in Microsoft Power Platform](/power-platform/faqs-copilot-data-security-privacy/)
