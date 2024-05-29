---
title: Customize content by using content snippets
description: Learn how to customize content by using content snippets.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 04/13/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - sandhangitmsft
---

# Customize content by using content snippets

Content snippets are small chunks of editable content that can be placed by a developer in a header, footer, web page or a web template, allowing for customizable content to populate any portion of a webpage's layout easily. 

A developer can place a snippet using Liquid: `{{ snippets["<<snippet name>>"] }}`, `{% editable snippets '<<snippet name>>' %}`, or `{% include 'snippet' snippet_name:'<<snippet name>>' %}`.

## Edit snippets

Snippets can be created and edited through the Portal Management app. The main power of the snippet is the fact that you can abstract a bit of content (other than the main copy of the page) and edit it separately, allowing essentially any static content on your site to be fully content-managed and editable.

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Content** > **Content Snippets**.

1. To create a new snippet, select **New**.

1. To edit an existing snippet, select an existing **Content Snippet** in the grid.

Enter values for the following fields:

| Name    | Description                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| Name    | The name can be used by a developer to place the snippet value into website code. |
| Website | The website that is associated with the snippet.                                                              |
| Display Name | Display name for the content snippet. |
| Type | Type of content snippet, Text, or HTML.
| Content Snippet Language | Select a language for the content snippet. To add more languages, go to [enable multiple language support](enable-multiple-language-support.md).
| Value   | The content of the snippet to be displayed in the website. You can enter plain text or HTML markup. You can also use [liquid objects](liquid/liquid-objects.md) with both text or HTML markup values.    |

## Use snippet

You can use snippets to show text or HTML. The content snippets can also use [liquid objects](liquid/liquid-objects.md), and reference other content such as [entities](liquid/liquid-objects.md#entities).

For example, you can use the steps explained earlier in this article to create/edit a content snippet. While editing the snippet, you can include sample code to [a record](liquid/liquid-objects.md#entities). Ensure you replace the ID of the **Account** table record with the correct ID from your environment. You can also use another table instead of **Account**.

After you create a snippet with text, HTML, or liquid objects shown in the example above, you can use it in a webpage.

To do add snippet on a webpage:

1. Create a [web template](web-templates.md) and use [snippets liquid object](liquid/liquid-objects.md#snippets) to call the snippet you created.

2. Create a [page template](page-templates.md) using the web template created earlier.

3. Use the design studio to create a new page using the page layout created earlier.

## Example

The following example uses a Microsoft Dataverse database with [sample data](/power-platform/admin/add-remove-sample-data).

> [!NOTE]
> You will need to configure [table permissions](../security/table-permissions.md) for the **Account** table (or whatever table you will use).

1. Open the [Portal Management app](./portal-management-app.md).

1. Go to **Content** > **Content Snippets**.

1. To create a new snippet, select **New**.

1. Enter name. For example, **AccountData**.

1. Select your website.

1. Enter Display Name. For example, **AccountData**.

1. Select type as HTML for this example. You can also select text instead.

1. Select a language.

1. Copy and paste sample value:

    ```
    {% assign account = entities.account['f4f25307-d284-ea11-a816-000d3a36ff29'] %}
    {% if account %}
    <b> Account Name is: </b> {{ account.name }} <br>
    <i> Account State: </i> {{ account.statecode.label }})
    {% endif %}
    ```

    Replace the GUID of the record with an account table record from your Dataverse database.

    :::image type="content" source="media/customize-content-snippets/new-content-snippet-html-liquid.png" alt-text="Create content snippet..":::

1. Save content snippet.

1. In the Power Pages design studio, create a new webpage or choose an existing webpage.

1. Select **Edit code**.

1. In between existing `<div></div>` tags, copy and paste the following source value:

    ```{% include 'snippet' snippet_name:'AccountData' %}```

    If different, update the value for *snippet_name* with your snippet name.

    :::image type="content" source="media/customize-content-snippets/vs-code-snippet.png" alt-text="Adding snippet to code.":::

1. Select **CTRL-S**.

1. In the design studio select **Sync**

1. Select **Preview**.

You will see the account information rendered as part of the snippet:

:::image type="content" source="media/customize-content-snippets/browse-portal.png" alt-text="Text used by screen readers.":::

You can follow the same steps with content snippet of **Text** type instead of HTML, for example:

```
{% assign account = entities.account['f4f25307-d284-ea11-a816-000d3a36ff29'] %}
{% if account %}
Account Name is: {{ account.name }} 
Account State: {{ account.statecode.label }}
{% endif %}
```
Replace the GUID of the record with an account table record from your Dataverse database.

When you browse the page with this content snippet, the table information is displayed using liquid object along with text instead of HTML. Likewise, you can also use only HTML to display content without using liquid objects.

## See also

[Work with liquid templates](liquid/liquid-overview.md)

