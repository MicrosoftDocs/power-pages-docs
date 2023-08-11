---
title: Create AI-generated form using Copilot (preview)
description: Learn how to create AI-generated form using Copilot to a page in your Power Pages site.
author: pranita225
ms.topic: conceptual
ms.custom: 
ms.date: 05/23/2022
ms.subservice:
ms.author: prpadalw
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Create AI-generated form using Copilot (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

You can start the form creation process by describing the type of form you're looking to create. Copilot suggests a form based on the description and offers a preview of the AI-generated form derived from your descriptions. You can refine and edit this form or completely start over with a different description.

:::image type="content" source="media/add-form-copilot/describe-form.png" alt-text="A screenshot of preview screen where you can describe the form." border="true":::

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature doesn't support non-English language input.
> - This feature will be available for preview in the United States only.
> - To understand capabilities and limitations of AI-powered and Copilot features in Power Pages, see [Transparency notes for Power Pages](../transparency-note.md).

To use Copilot for forms:

1. Go to [Pages workspace](first-page.md).
1. [Add a form](add-form.md).
1. Start typing the description of your form inside the text box under **Describe a form to create it**.

As the preview gets generated for the form, you can perform quick actions by selecting the AI-generated actions. The history shows you the descriptions you've used in the current attempt, and you can also start over.

After reviewing the AI-generated form, you can add it to the page. In the background, Power Pages creates the following for you:

- A [table](../configure/data-workspace-tables.md) in Microsoft Dataverse.
- A [Dataverse form](../configure/data-workspace-forms.md).
- A [basic form](../configure/basic-forms.md) in Power Pages.

The Dataverse table is created with the solution publisher's prefix selected in the Data workspace. The names of tables and forms created by Power Pages for Copilot start with `Copilot [Table name]` format to simplify and streamline your form creation process.

Once the form is added to the page, you can continue to edit the form with the in-context [editing experiences](customize-pages.md).

For example, here's how the preview might look like when describing the form as "Scholarship application form".

:::image type="content" source="media/add-form-copilot/scholarship-application-form.png" alt-text="A screenshot of generated preview for a scholarship form." border="false":::

Likewise, here's an example of an AI-generated preview of a "Product customer support form".

:::image type="content" source="media/add-form-copilot/customer-support-form.png" alt-text="A screenshot of generated preview for a customer support form." border="false":::

### See also

- [Overview of AI-powered and Copilot features in Power Pages (preview)](../configure/ai-copilot-overview.md)
- [Enable chatbot in Power Pages site (preview)](enable-chatbot.md)
- [Force Bing webmaster to index your site (preview)](force-bing-index.md)
- [Use Copilot to generate text and it to a webpage (preview)](add-text-copilot.md)