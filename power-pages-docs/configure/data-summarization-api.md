---
title: Data summarization API overview (preview)
description: ""
author: danamartens
ms.topic: conceptual
ms.date: 09/05/2024
ms.author: dmartens
ms.reviewer: dmartens
contributors:
    - dmartens
    - tapanm
---

# Data summarization API overview (preview)

\[This topic is prerelease documentation and is subject to change.\]

Power Pages summarization API lets makers add a page content summarization using generative AI that helps site users to get overview without going over entire page. The API is built on top of the Power Pages Web API that provides data summarization on dataverse tables used in the pages.

> [!IMPORTANT]
>
> - This is a preview feature.
> - Preview features aren't meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

## Prerequisites

- You must enable the [site settings](https://learn.microsoft.com/en-us/power-pages/configure/web-api-overview#site-settings-for-the-web-api) needed for Web API to work summarization.

- Only tables supported for Pages Web API are available for summarization. Read [Web API overview](https://learn.microsoft.com/en-us/power-pages/configure/web-api-overview) for more details

- The feature is not available in UK, India, Australia, Government Community Cloud (GCC), Government Community Cloud - High (GCC High), or Department of Defense (DoD) regions

## Site settings

Apart from enabling pages web API you need to set below site settings for summarization API feature.

| **Site setting name** | **Description** |
|-----------------------|-----------------|
| Summarization/Data/Enable | Enables or disables the Summarization feature.</br>**Default:** False</br>**Valid values:** True, False |
| Summarization/prompt/{any_identifier} | Use these settings to provide any instruction for summarization</br>Type: string</br>Example:</br>Name: <em>Summarization/prompt/case_summary</em></br>Value: Summarize key details and critical information |
| Summarization/Data/ContentSizeLimit | Modify the input size limit for the summarization content</br>Type: integer</br>Default : 100K |

## API schema

| **Method** | **URI** |
|------------|---------|
| POST | `[Site URI]/_api/summarization/data/v1.0/tablename` |

{ "InstructionIdentifier":"", "RecommendationConfig":"" }

| **Name** | **Description** |
|-------------------------|-------------------------|
| InstructionIdentifier | This is an optional parameter. If you want to pass any addition instruction to summarization use the site settings to add the prompt and use here.</br>Note : you should always provide the sitesetting name as defined in above format |
| RecommendationConfig | This is optional, if you pass the recommended prompt provided by the summarization API, use this parameter to pass. Value should be hashed one and shouldn't be modified |

> [!NOTE]
>
> If both `InstructionIdentifier` and `RecommendationConfig` are provided, only `InstructionIdentifier` will be considered, and the other parameter will be ignored. Make sure to use only one of these input parameters.

The API follows the standard OData specifications supported by the Power Pages Web API. All [read operations](https://learn.microsoft.com/en-us/power-pages/configure/read-operations) supported by the Power Pages Web API will also be supported by the Summarization API.

## Sample

Summarize case type, subject, description and case history by focusing on key details and critical information.

Request

Method : POST

`<https://contoso.powerappsportals.com/>_api/summarization/data/v1.0/incidents(d2e11ba8-92f6-eb11-94ef-000d3a5aa607)?$select=description,title&$expand=incident_adx_portalcomments($select=description)`

{ "InstructionIdentifier": "Summarization/prompt/case_summary" }

Response

Status: 200

Content-Type: application/json

Body

{
  "Summary": "The data results provide information…...",
  "Recommendations": [
    {
      "Text": "would you like to know about…?",
      "Config": "HSYmaicakjvIwTFYeCIjKOyC7nQ4RTSiDJ+/LBK56r4="
    }
  ]
}

The summarization response provides recommended prompts for fine-tuning the summary. If you wish to use these recommendations, pass the configuration value in the request body without the InstructionIdentifier.

## Security

The role-based security configured for table and column permissions will be respected by the Summarization API. Only the records that the end user has access to will be considered for summarization.

## Authenticating summarization API

You don't need to include an authentication code, because authentication and authorization are managed by the application session. All Web API calls must include a Cross-Site Request Forgery (CSRF) token.

## Error codes and messages

The following table includes the different error codes and messages you might encounter when you use the summarization API:

| Status Code | Error Code | Error Message |
|-------------|------------|---------------|
| 400 | 90041001 | Generative AI Features are disabled |
| 400 | 90041003 | Data summarization disabled for this site. Please enable using site setting. |
| 400 | 90041004 | Content length exceeds the limit |
| 400 | 90041005 | No records found to summarize |
| 400 | 90041006 | Error occurred while summarizing the content. |

## Add Copilot summarization to case page

In this guide, you will set up the Copilot summarization section for the support case page, enabling users to quickly review the case and its timeline summary.

Prerequisite

Make sure you use the site created using [Community](https://learn.microsoft.com/en-gb/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#community) or [Customer self-service](https://learn.microsoft.com/en-gb/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#customer-self-service) portal template. These portals contain the support case page.

## Step 1. Create site settings

Before you can use the summarization API, you have to enable the required site settings with the Portal Management app.

1. Start the [Portal Management app](https://learn.microsoft.com/en-us/power-pages/configure/portal-management-app).

1. On the selected website record, select **Site Settings**.

1. Enter below site settings and value

   1. Enable Summarization API

      Name: Summarization/Data/Enable

      Value: true

   1. Set summarization prompt

      Name: Summarization/prompt/case_summary

      Value: "Summarize key details and critical information"

   1. Enable Web API for case table

      Name: Webapi/incident/enabled

      Value: true

   1. Enable description and title field of case table

      Name: Webapi/incident/fields

      Value: description,title

   1. Enable portal comments table for Web Api

      Name: Webapi/adx_portalcomment/enabled

      Value: true

   1. Enable description field of portal comments table

      Name : Webapi/adx_portalcomment/fields

      Value: description

## Step 2. Add Copilot summary section

In this step you will add summary section on top of the case page

1. Open Power Pages studio of the site
1. Select **Customer Service - Edit Case**

   This is the page where you will be adding summary section
1. Click on **Edit code** button to open **Visual studio code**
1. Copy below code and add beginning of the code block
1. Save the file
1. Click on Preview button to open site

## Step 3. Test the summarization

1. Click on **My support** tab
1. Create a new case and add case description
1. Add couple of comments
1. Click on down arrow button in copilot summary section to view the case summary
1. Try for other case records
