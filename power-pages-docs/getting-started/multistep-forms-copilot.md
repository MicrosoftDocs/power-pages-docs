---
title: Add an AI-generated multistep form using Copilot
description: Learn how to add multistep forms to your Power Pages site using Copilot.
author: pranita225
ms.topic: how-to
ms.custom: 
ms.date: 02/05/2025
ms.subservice:
ms.author: prpadalw
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - pranita225
    - DanaMartens
---

# Add an AI-generated multistep form using Copilot (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

An easy way to add a multistep form to your Power Pages website is to ask Copilot to create one for you. In the copilot sidecar chat, describe the form you need. Copilot builds a multistep form with one or multiple steps based on your description and generates a preview. Review the form and its steps before adding it to your page.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]
> - This feature doesn't support non-English language input.

## **Prerequisites**

To use AI-powered Copilot features in Power Pages:

- Your browser language must be set to US-English.

## Create a multistep form

To use Copilot to generate a multistep form:

1. Go to the [Pages workspace](first-page.md) and choose a page for your form.

1. Select the **Copilot** button from the command bar.

1. Type a description of your form in the copilot text box. For example, you might ask Copilot to create a credit card application form.

    :::image type="content" source="media/multistep-form-copilot/multistep-form-copilot.png" alt-text="A screenshot of Power Pages' Copilot inside the design studio with the prompt text box emphasized.":::

    If there are existing tables relevant to the prompt, the system suggests the use of existing tables. You can choose to create the form using the suggested existing table or manually select another existing table. When you select an existing table, the form is generated using existing columns of the table.

    :::image type="content" source="media/multistep-form-copilot/multistep-form-copilot-table.svg" alt-text="A screenshot of Power Pages' Copilot inside the design studio with suggested tables emphasized.":::

    When there's no table suggestion, the form is generated, a preview of the form displays on the canvas, and the **Review this form**  toolbar displays at the bottom of the canvas. In this case, a new table is created for you automatically.  

    :::image type="content" source="media/multistep-form-copilot/copilot-review-form.png" alt-text="A screenshot of the AI-generated form in the design studio with review toolbar emphasized.":::

    Review each step. Then decide if you want to keep the form or discard it. If you choose to add the form to the page, you can edit it using design studio's existing functionality just as you would for other components.

### Related information

- [Add an AI-generated form using Copilot](add-form-copilot.md)
- [FAQ for creating AI-generated form or multistep form](../faqs-create-form.md)
