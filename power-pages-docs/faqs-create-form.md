---
title: FAQ for creating AI-generated form or multistep form
description: This FAQ discusses natural language to forms and the key considerations for making use of this technology responsibly.
ms.date: 04/30/2024
ms.custom: responsible-ai-faqs
ms.topic: article
author: pranita225
ms.author: prpadalw
ms.reviewer: dmartens
ms.collection: 
    - bap-ai-copilot
contributors:
    - nickdoelman
    - ProfessorKendrick
    - DanaMartens
---

# FAQ for creating AI-generated form or multistep form

These frequently asked questions (FAQ) describe the AI impact of Power Pages' natural language to form or multistep form feature.

## What is natural language to form?

As you start design studio and add a form to the page, you're able to describe the form you want to create for your site. Once you describe the type of form you want to create, Power Pages Copilot will create a preview of the form with the questions and form fields for inputs.

You can continue to use natural language (NL) to make further revisions to the form, such as adding or removing questions, changing the type of response for a question. After you choose to create the form, a Microsoft Dataverse table is created to store the form data, and a Dataverse form is created with all required experiences to show the new form in your Power Pages site. After the form is created, you can see it on the page where the form is added. Set the permissions on the form as the next step to make it visible to the viewers of your website.

## What are the system’s capabilities?

The system will allow you to start from creation process by describing the type of form you're looking to create. Then, the system suggests possible questions and response fields as sample form, allowing you to preview the form. You can refine and edit the form, or completely start over if the form suggestions are not relevant to your requirement. When done generating the form, add it to the page in your website.

The form creation is now streamlined and reduces the tedious steps required to plan out the form questions and fields, mapping them to a table, creating the tables, columns and then Dataverse forms, and then be able to add it to the page. AI helps generate draft form for you to review and edit before adding to the site.

## What is the system’s intended use?

The goal of Copilot for form is to provide you with assistance in creating forms on a page in Power Pages.

## How was the feature evaluated? What metrics are used to measure performance?

This feature underwent substantial testing before the feature was released. AI-generated form relies on user feedback to report if the AI-generated form is not relevant or inappropriate. If you encounter irrelevant or inappropriate responses, report it to Microsoft using the thumbs down gesture and include feedback in the form. We track the telemetry of thumbs up and thumbs down gestures present in the Copilot experiences for each AI-generated output. Your feedback helps improve the functionality moving forward. In addition to this, we also track this feature's SLA to make sure it's always available to you.

## What are the limitations of natural language to form? How can users minimize the impact of the natural language to form limitations when using the system?

- This feature doesn’t support non-English language input.
- See the [availability of Copilot in your geographical region](/power-platform/admin/geographical-availability-copilot).
- There is a limit on the number of tokens allowed in a query and response.
- When a Maker edits a site with site visibility of Public, there is a risk that Copilot generated form, when added to the page, will be live for the end users of the site.

## What operational factors and settings allow for effective and responsible use of the system?

You can revise the form suggestion as needed. You can also review the form preview and decide if you want to add it to the page. Start over if the generated form doesn't fit your business requirements.

## See also

- [Add an AI-generated form using Copilot](getting-started/add-form-copilot.md)
- [FAQ for Copilot data security and privacy in Microsoft Power Platform](/power-platform/faqs-copilot-data-security-privacy/)
