---
title: Data summarization API overview (preview)
description: Learn about the data summarization API in Microsoft Power Pages.
author: nageshbhat-msft
ms.topic: concept-article
ms.date: 08/28/2025
ms.update-cycle: 180-days
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# Data summarization API overview (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

Makers use the Power Pages summarization API to add page content summarization with generative AI. This feature lets site users get an overview of a page's content without reading the entire page. The API is built on the Power Pages Web API, which provides data summarization for Dataverse tables used on pages.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

- Enable the [site settings](/power-pages/configure/web-api-overview#site-settings-for-the-web-api) for the Web API.
- Only tables supported by the Power Pages Web API are available for summarization. Learn more about the Power Pages Web API in [Web API overview](/power-pages/configure/web-api-overview).
- This feature isn't available in Government Community Cloud (GCC), Government Community Cloud - High (GCC High), or Department of Defense (DoD) regions.

## Site settings

Enable pages in your web API and set the following site settings for the summarization API feature.

| Site setting name | Description |
|-------------------|-------------|
| Summarization/Data/Enable | Enable or disable the summarization feature.<br>**Default**: *false*<br>**Valid values**: *true*, *false* |
| Summarization/prompt/{any_identifier} | <p>Use these settings to provide instructions for summarization.<br>**Type**: *string*</p><p>Example:<br>**Name**: *Summarization/prompt/case_summary*<br>**Value**: *Summarize key details and critical information*</p> |
| Summarization/Data/ContentSizeLimit | Modify the input size limit for summarization content.<br>**Type**: *integer*<br>**Default**: *100,000* charecters |

## API schema

| Method | URI | JSON Sample |
|--------|-----|-------------|
| POST   | *[Site URI]/_api/summarization/data/v1.0/tablesetname* | `{ "InstructionIdentifier":"", "RecommendationConfig":"" }` |

| Property name | Description |
|---------------|-------------|
| InstructionIdentifier | This property is optional. To pass extra instructions for summarization, use the site settings to add the prompt. Always provide the site setting name as it was previously defined. |
| RecommendationConfig | This property is optional. Use this property to pass the prompt recommended by the summarization API. The value must be hashed and remain unmodified. |

> [!NOTE]
> The API follows the standard Open Data Protocol (OData) specifications supported by the Power Pages Web API. The summarization API supports all [read operations](/power-pages/configure/read-operations) available in the Power Pages Web API.

## Sample

Summarize the case type, subject, description, and case history by focusing on key details and important information.

### Request

```http
POST [Power Pages URL]/_api/summarization/data/v1.0/incidents(aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb)?$select=description,title&$expand=incident_adx_portalcomments($select=description)
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

Body:
{
"InstructionIdentifier": "Summarization/prompt/case_summary"
}
```

### Response

```http
HTTP/1.1 200 OK
OData-Version: 4.0
{
  "Summary": "The data results provide information…",
  "Recommendations": [
    {
      "Text": "would you like to know about…?",
      "Config": "HSYmaicakjvIwTFYeCIjKOyC7nQ4RTSiDJ+/LBK56r4="
    }
  ]
}
```

The summarization response provides recommended prompts for fine-tuning the summary. To use these recommendations, pass the configuration value in the request body without the `InstructionIdentifier` property.

## Security

The summarization API respects role-based security configured for table and column permissions. It only considers records the user can access for summarization.

## Authenticating the summarization API

You don't need to include an authentication code because the application session manages authentication and authorization. All Web API calls must include a [cross-site request forgery (CSRF) token](/power-pages/configure/web-api-http-requests-handle-errors#example-wrapper-ajax-function-for-the-csrf-token).

## Error codes and messages

The following table describes the different error codes and messages that you might encounter when you use the summarization API.

| Status code | Error code | Error message |
|-------------|------------|---------------|
| 400 | 90041001 | Generative AI features are disabled |
| 400 | 90041003 | Data summarization disabled for this site. Enable using the site setting. |
| 400 | 90041004 | Content length exceeds the limit |
| 400 | 90041005 | No records found to summarize |
| 400 | 90041006 | Error occurred while summarizing the content. |

## Related information

[FAQ for data summarization API](..\faqs-data-summarization.md)
