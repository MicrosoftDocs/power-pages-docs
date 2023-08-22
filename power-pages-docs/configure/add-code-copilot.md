---
title: Add AI-generated code using Copilot
description: Add AI-generated code using Copilot.
author: neerajnandwana-msft
ms.topic: conceptual
ms.custom: 
ms.date: 08/22/2023
ms.subservice:
ms.author: nenandw 
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
    - ProfessorKendrick
---

# Add AI-generated code using Copilot (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Add AI-generated code using Copilot in Visual Studio Code helps you create code using natural language chat interaction. In Power Pages, you work with site code that includes HTML, JS, or CSS code to make site customizations that aren't currently supported in the Power Pages low-code design studio. This Copilot chat experience assists Power Pages developers like you to write code by describing your expected code behavior using natural language. You can then refine the generated code and use it when customizing your site.

:::image type="content" source="media/add-ai-generated-code/power-pages-code-copilot.png" alt-text="Visual Studio Code with Power Pages Copilot.":::


> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

Review the [terms](https://go.microsoft.com/fwlink/?linkid=2189520) and [Responsible AI FAQ](../responsible-ai-overview.md) documents to understand usage and limitations of Copilot. Check the following requirements to start using Copilot in Power Pages: 

- Ensure you have installed the latest Power Platform Tools extension. 
- Open site root folder in Visual Studio Code. 
  :::image type="content" source="media/add-ai-generated-code/explorer.png" alt-text="Visual Studio Code explorer.":::

- Sign in to Power Pages Copilot with your Dataverse Environment credentials. 
	
## How to use Copilot to generate code

> [!IMPORTANT] 
> Copilot in Visual Studio Code is tuned to generate code for Power Pages sites, so its **functionalities are limited to Power Pages site supported languages like HTML, JavaScript, and CSS**. The generated code from Copilot makes use of supported frameworks like bootstrap and jQuery. 

1. In the Copilot chat, describe the code behavior you want using natural language. For example, code for form validation or Ajax calls using the Power Pages Web API. 
1. Continue to rephrase your questions in the Copilot chat and iterate them until you’ve got what you need.  
1. Once you're happy with the generated code, you can easily copy and paste the code snippet or insert the code to Power Pages site and modify the code further.
1. Use the **up/down** arrow key to navigate between recently entered prompts.  

Examples
- `Write code for Web API to fetch active contacts`
- `Write code in JavaScript to make sure that submitted value for phone number field is in valid format`

> [!NOTE]
> - Copilot generated code might not have the correct names for tables or columns, so it’s recommended to verify these details before using the code. 
> - To generate more **accurate** code, make sure you open the file where you want to use the code. For example, open a **web template** where you want to add Web API code or open a custom JavaScript file for forms where you want to add field validation. 
	
:::image type="content" source="media/add-ai-generated-code/ai-generated-code.png" alt-text="Add AI generated code.":::

## Known issues

In some instances, a prompt is classified incorrectly as malicious code.

## Help us in improving this feature
In every response of the Copilot chat, select the feedback options, a thumb up (👍) if you like the response or thumb down (👎) if you didn’t like it. Your feedback greatly helps improve the capabilities of this feature.

:::image type="content" source="media/add-ai-generated-code/evaluate-ai.png" alt-text="Text used by screen readers.":::

## See also

- [FAQ for AI-generated code using Copilot](../faqs-pro-developer.md)
