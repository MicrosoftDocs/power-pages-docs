---
title: Add an AI-generated form using Copilot
description: Learn how to create an AI-generated form using Copilot and add it to a page in your Power Pages site.
ms.topic: how-to
ms.date: 04/24/2024
author: pranita225
ms.author: prpadalw
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - nickdoelman
    - ProfessorKendrick
    - DanaMartens
ms.custom: bap-template
---

# Add an AI-generated form using Copilot

An easy way to add a form to your Power Pages website is to ask Copilot to create one for you. Describe the form you need. Copilot builds a form based on your description and offers a preview for you to check. You can [add the form](add-form.md) to your site as it is, edit it first, or start over with a different description.

:::image type="content" source="media/add-form-copilot/describe-form.svg" alt-text="Screenshot of the form creation page in the Copilot for Power Pages preview.":::

## Create a form with Copilot

1. Go to the [Pages workspace](first-page.md) and select a page for your form.
1. Select the **Form** component.
1. In the text box under **Describe a form to create it**, describe your form. You can use up to 250 characters in your description.
1. To send your description to Copilot, press the Enter key or select the paper airplane icon in the lower-right corner of the text box.
1. Check the preview to the right of your description and refine the form as needed.

    - To change the form, select a quick action or refine your description.
    - The history shows you the descriptions you've entered so far.
    - Select **Start over** to erase everything and start with a new description.

1. To add the form to the page, select **OK**.

    :::image type="content" source="media/add-form-copilot/generated-form.svg" alt-text="Screenshot of an AI-generated form in Power Pages, with the description, quick actions, and history highlighted.":::

    Legend:

    1. Refine description
    1. Quick actions
    1. History

When you add the form to the page, Power Pages creates the underlying form components for you in the background:

- A [table](../configure/data-workspace-tables.md) and [form](../configure/data-workspace-forms.md) in Microsoft Dataverse
- A [basic form](../configure/basic-forms.md) in Power Pages

The names of tables and forms that Copilot creates always begin with "Copilot." In the previous example, the Dataverse table that's associated with the Visitor Information form is named `Copilot Visitor Information`. It appears in the Data workspace.

After the form is added to the page, you can edit it the same way you [edit any page component](customize-pages.md).

## Start with a prebuilt form

You can start with a prebuilt form rather than enter your own description. Prebuilt forms that are appropriate for your website are listed on the form creation page.

:::image type="content" source="media/add-form-copilot/prebuilt-forms.svg" alt-text="Screenshot of the form generation page, with prebuilt forms highlighted.":::

For example, here's the preview when you select the prebuilt scholarship application form:

:::image type="content" source="media/add-form-copilot/scholarship-application-form.svg" alt-text="Screenshot of the generated preview of a prebuilt scholarship form.":::

Here's a preview of the prebuilt product customer support form:

:::image type="content" source="media/add-form-copilot/customer-support-form.svg" alt-text="Screenshot of the generated preview of a prebuilt customer support form.":::

## Delete an AI-generated form

If you remove an AI-generated form from the page it's on, it's still available for you to add to other pages. To delete an AI-generated form entirely, and the associated Dataverse table, you need to go into your site's advanced settings.

1. In the Power Pages design studio, select **More items** (**&vellip;**) > **Portal Management**.
1. In the sitemap under **Content**, select **Basic Forms**.
1. Find the form in the list. Remember, its name starts with "Copilot."
1. Select the space to the left of the form, and then select **Delete**.

### See also
- [Geographic and language availability for Copilot features](https://aka.ms/bapcopilot-intl-report-external)
- [FAQ for creating AI-generated form](../faqs-create-form.md)
- [Create an AI-generated webpage using Copilot](../getting-started/create-page-copilot.md)
- [Use Copilot to generate text and it to a webpage](../getting-started/add-text-copilot.md)

