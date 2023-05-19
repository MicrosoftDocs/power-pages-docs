---
title: Transparency note for chatbot
description: The transparency note to add chatbot and the key considerations for making use of this technology responsibly.
ms.date: 5/23/2023
ms.custom: transparency-note
ms.topic: article
author: pranita225
ms.author: prpadalw
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Transparency note for chatbot

This transparency note describes the AI impact of chatbot feature in Power Pages.

## What is chatbot in Power Pages?

The chatbot feature in Power Pages provides you with an easy way to configure a GPT-powered Power Virtual Agents chatbot for your public website. The bot enhances the interaction experience for the website users by enabling them to ask natural language (NL) questions and receive summarized responses with relevant links. This experience allows site users to get the necessary information available on the website - for example, through FAQs or knowledge articles easily using the bot without the need to search and locate the information manually.

## What are the system’s capabilities?

A chatbot for public sites created in Power Pages for providing generative answers to customer queries. The public site needs to be indexed by Bing as a pre-requisite for enabling the chatbot on the site as it allows the search engine to index the site's content. This indexing enables web users to ask natural language questions and receive summarized responses. You can test the bot before publishing it to ensure that it provides appropriate summaries. Service administrators can also turn off the publishing of the bot at the tenant level to prevent accidental or unintended exposure of AI capabilities on the public site. Additionally, you can navigate to the associated Power Virtual Agents chatbot for advanced configuration and customization.

## What is the system’s intended use?

Chatbot on Power Pages site enhances the conversational capabilities by enabling site users to ask queries in natural language and receive summarized responses. Bot has the ability to add more complex conversational features, such as contextual understanding, entity recognition, and sentiment analysis. These capabilities allow the bot to better understand user inputs and provide more accurate and helpful responses.

## How was chatbot feature evaluated? What metrics are used to measure performance?

The capability was evaluated on a collection of manually curated question-and-answer datasets, covering multiple industries.

More evaluation was performed over custom datasets for offensive and malicious prompts and responses.

## What are the limitations of this feature? How can users minimize the impact of the chatbot limitations when using the system?

- This feature can't take the content from a private or an authenticated site for summarizing the search results.
- This feature doesn't include a mitigation for checking for correctness of responses returned by the bot. Nonfactual responses might be generated if the URL from the information is gathered (and what the maker provided) contains incorrect information.
- This feature only supports English language.
- This feature is available for preview only in the United States region.
- GPT answers don't support websites that sell prohibitive products or services, as these terms get intentionally blocked by content moderation. An exception to this exclusion is if the content moderation slider gets set to **Low**.
- That the bot sometimes returns misguiding responses for high-risk domains that include healthcare finance, communications, and legal.

## What operational factors and settings allow for effective and responsible use of the system?

You're able to test the bot before making it available to your site users. Evaluate bot's performance&mdash;that is, the ability of bot to return relevant, accurate, and offensive-language-free responses to site user's inquiries, or force Bing to rebuild index for a supplied URL.

When a feature is enabled, the bot is created with a content moderation set to **High** by default. This setting filters the offensive content by using Azure Open AI’s content filtering and Azure Content Moderator.

## See also

- [Enable chatbot in a Power Pages site (preview)](getting-started/enable-chatbot.md)
- [Force Bing webmaster to index your site (preview)](getting-started/force-bing-index.md)