---
title: Add AI-generated text using Copilot (preview)
description: Learn how to add AI-generated text using Copilot to a page in your Power Pages site.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/23/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Add AI-generated text using Copilot (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Copilot for text allows you to create website copy within the context of design studio. After generating the text using Copilot, you can change the text to further customize your requirements.

:::image type="content" source="media/add-text-copilot/copilot-text.png" alt-text="A screenshot of the Copilot icon in text component." border="true":::

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - To understand capabilities and limitations of AI-powered and Copilot features in Power Pages, see [Responsible AI transparency notes for Power Pages](../transparency-note.md).

The text that you enter as description uses [Azure OpenAI](/azure/cognitive-services/openai/overview) to generate text and show a preview.

To use Copilot for text:

1. Go to [Pages workspace](first-page.md).
1. [Add a text component](add-text.md).
1. Select the **Copilot** icon.

    :::image type="content" source="media/add-text-copilot/copilot-icon.png" alt-text="A screenshot of copilot icon." border="true":::

1. Describe the text that you want to generate using AI. For example, "I want to describe the benefits of student loan options at Contoso university."

    :::image type="content" source="media/add-text-copilot/contoso-example-description.png" alt-text="A screenshot of the Contoso university student loan options." border="true":::

1. Generate text by pressing the **Enter** key on the keyboard, or using the generate text icon on the bottom-right side of the text box.

    :::image type="content" source="media/add-text-copilot/contoso-example-generated-text.png" alt-text="A screenshot of the Contoso university student loan options AI generated text." border="true":::

    To customize the text, you can choose the following options:
    
    - **Rewrite** - generates new text based on the already provided description.
    - **Change the tone** - changes the tone of the generated text to make it professional, conversational, friendly or educational.
    - **Adjust the length** - make the generated text shorter or longer.

1. Select **Add to page** to add the AI-generated text.

Once the text is added to the page, you can continue to edit the page with the in-context [editing experiences](customize-pages.md)

### See also

- [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md)
- [Enable chatbot in Power Pages site](enable-chatbot.md)
- [Force Bing webmaster to index your site](force-bing-index.md)
- [Create a form in a webpage using a Copilot](add-form-copilot.md)
