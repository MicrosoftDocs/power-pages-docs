﻿---
title: Configure Power Automate cloud flows in Power Pages (preview)
description: Learn how to add and configure Power Automate cloud flows on Power Pages.
author: nageshbhat-msft

ms.topic: conceptual
ms.custom: 
ms.date: 06/15/2023
ms.subservice: 
ms.author: nabha
ms.reviewer: ndoelman
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick
---

# Configure Power Automate cloud flows in Power Pages (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Power Automate cloud flow allows users to create automated workflows between different applications and services. You can use a Power Automate cloud flow to create logic that performs one or more tasks when an event occurs. For example, configure a button so that when a user selects it, send an email or meeting request, update a record, collect data, synchronize files, and other tasks.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

Now, you can securely invoke Power Automate cloud flows from Power Pages to interact with 900+ external data sources and integrate it into your business site.

> [!NOTE]
> Your Power Pages site version must be 9.5.4.xx or later for this feature to work.
> Your starter site package version must be 9.3.2304.x or higher.

## Prerequisites

You need a Power Automate per flow license to integrate with Power Pages.

## Steps to integrate cloud flow

1. Create a cloud flow.

1. Add the flow to your site.

1. Invoke a flow from your website.

## Create a flow

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. On the left pane, select **Solutions**.

1. Either [create a new solution](/power-apps/maker/data-platform/create-solution) or select an existing solution.

1. Select **+New**, **Automation**, **Cloud flow**, and then **Instant**.

1. Select **Skip**.

1. Search for **Power Pages** Select **When Power Pages calls a flow** trigger.

    :::image type="content" source="media/cloud-flow/power-automate-power-pages.png" alt-text="Selecting Power Pages options in Power Automate.":::

1. Define your flow steps and return values and select **Save**.

> [!NOTE]
> Only [solution-aware](/power-automate/overview-solution-flows) flows can be attached to the Power Pages site.

## Add a flow to your Site

After you create an instant cloud flow, it needs to be associated with the Power Pages site and secured with a web role.

1. Sign into [Power Pages](https://make.powerpages.microsoft.com/).

1. Select site **+ Edit**.

1. Navigate to the **Set up** workspace, then select **Cloud flows (preview)** under **App integrations**.

1. Select **+ Add cloud flow**.

1. Search for the recently created flow.

1. Select **+ Add roles** under **Roles**.

1. Select roles that should have access to the flow.

1. Select **Save**.

    :::image type="content" source="media/cloud-flow/add-to-website.png" alt-text="Add cloud flow to website.":::

> [!NOTE]
> When you add a flow to your site, a unique URL is generated that allows you to invoke the cloud from your site.

## Invoke a flow from web page

Use Power Pages cloud flow API to interact with Power Automate to perform external service integration. Cloud flow API operations consist of HTTP requests and responses.

| Operation         | Method | URI                                                    |
|-------------------|--------|--------------------------------------------------------|
| Invoke cloud flow | POST   | \[Site URI\]\_/api/cloudflow/v1.0/trigger/&lt;guid&gt; |

Example:

Request

```html
POST https://contoso.powerappsportals.com/_api/cloudflow/v1.0/trigger/4d22a1a2-8a67-e681-9985-3f36acfb8ed4
{
    "text":"abc@contoso.com"
}
``` 

Response

Cloud flow without response action

```html
HTTP/1.1 Accepted
Content-Type: application/json
```

Cloud flow with response action

```html
HTTP/1.1 200 OK
Content-Type: application/json
Body
{
    "name":"Sample Account",
    "credit_on_hold":false,
    "description":"This is a sample account",
    "revenue":50000000
}
```

## Authenticating cloud flow API requests

You don't need to include an authentication code, because the application session manages authentication and authorization. All API calls must include a Cross-Site Request Forgery (CSRF) token.

## Passing parameter to cloud flow

In a cloud flow, you can define input parameters of type **Text**, **Boolean**, and **Number**. The parameter name you define in the request body should match the parameter name defined in the cloud flow trigger.

>[!IMPORTANT]
> You must pass the request parameters in the same order they are defined in the cloud flow.

### Sample JavaScript to call a flow

This sample demonstrates how to call a flow using Asynchronous JavaScript and XML (AJAX).
 
```
    shell.ajaxSafePost({
        type: "POST",
        contentType: "application/json",
        url: _api/cloudflow/v1.0/trigger/44a4b2f2-0d1a-4820-bf93-9376278d49c4,
        data: JSON.stringify({"eventData":JSON.stringify({"Email": "abc@contoso.com" }),
        processData: false,
        global: false
    })
    .done(function (response) {
    
    })
    .fail(function(){
    
    });
```
>[!NOTE] 
> If no input parameter is defined in the trigger, pass an empty payload in the request.
