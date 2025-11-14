---
title: Power Pages server logic overview (preview)
description: Learn how to configure and secure Power Pages server logic, including governance settings, API authentication, and site-specific configurations.
#customer intent: As a developer, I want to securely run JavaScript on the server so that I can extend site functionality without exposing code in the browser.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 11/12/2025
ms.topic: concept-article
---

# Server logic overview (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Power Pages server logic lets makers run JavaScript securely on the server, adding extensibility directly to the site runtime.  
   
Because server logic runs on the server, it's hidden from the browser and protected by web roles and table permissions. You add logic in Power Pages Studio and author it using Visual Studio Code, which provides IntelliSense and compile-time validation.  

Dataverse stores code and configuration, so server logic benefits from the same lifecycle management and deployment pipelines as other Power Pages components.  

:::image type="content" source="media/server-logic-overview/server-logic-flow.png" alt-text="Server logic flow":::

> [!IMPORTANT]
>
> - This feature is a preview feature.
> - Preview features aren’t meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2189520), and are available before an official release so that customers can get early access and provide feedback.
> - This feature is available only for site running on [Enhanced Data Model](../admin/enhanced-data-model.md).

## Language support

Server logic lets developers write native JavaScript code compliant with the [ECMAScript 2023](https://tc39.es/ecma262/2023/) standard. Hosting environment doesn't provide access to browser-specific APIs or libraries, like `fetch`, `XMLHttpRequest`, or other DOM-related features typically available in client-side JavaScript.  

## What you can do with server logic

Server logic in Power Pages allows makers and developers to move critical operations from the browser to the server for improved control, scalability, and security. It enables your site to perform complex tasks and integrations without exposing sensitive logic or data on the client side.

With Server logic, you can:
- Connect to external services and APIs: Integrate securely with REST APIs, Azure Functions, or other business systems to exchange data, trigger actions, or retrieve dynamic information.
- Perform secure data operations : Execute Dataverse operations—such as querying, updating, or deleting records—on the server, applying business logic and validation consistently.
- Run custom logic and transformations: Process or manipulate data before returning it to the client. For example, calculate totals, validate business rules, or enrich data using external lookups.
- Return processed responses to pages: Send only the required and filtered data to client pages, ensuring faster rendering and reduced payloads.
- Simplify secure authentication: Manage service credentials and API keys on the server rather than in client code, maintaining secure and compliant integration practices.

## Benefits of using server logic

Server logic brings enterprise-grade extensibility to Power Pages, helping organizations build more secure, scalable, and maintainable web experiences.

Key benefits include:
-	Enhanced security: Business logic, secrets, and API keys are executed and stored on the server—never exposed in the browser or to end users.
-	Integration flexibility: Connect Power Pages seamlessly with external systems, including Azure Functions, REST APIs, Dataverse actions, and business services.
-	Improved performance and efficiency: Offload heavy computations, validations, and data processing to the server, reducing client-side workload and improving page responsiveness.
-	Consistency across channels: Apply the same logic across web pages, forms, and integrations, ensuring uniform data validation and behavior throughout the application.
-	Centralized maintenance: Update or refine logic in one place without redeploying or editing multiple client scripts or pages.


## Secure the server logic 

To execute code in server logic, users must have the appropriate permissions configured by the maker. Access is governed by web roles and table permissions, which also determine whether server logic can access specific tables.

### Authenticate server logic API 

You don't need to include custom authentication code. Authentication and authorization are managed by the application session. All server logic API calls must include a Cross-Site Request Forgery (CSRF) token.  

## Governance setting for anonymous access 

Server logic integrates with Dataverse and external services to perform complex computations that might use data from external systems. When administrators enforce the [governance control](../security/disable-anonymous-access.md), any integration initiated by anonymous users, especially those involving external systems, is blocked.  

## Site settings

The following optional site settings help configure server logic: 

| Name                | Description             | Default                |
|---------------------|-------------------------|------------------------|
| ServerLogic/Enabled | Enable / Disable feature                 | true  |
| ServerLogic/AllowedDomains    | Restrict which external domains can be called | All domains allowed |
| ServerLogic/TimeoutInSeconds        | Maximum execution time (in seconds). Time out can be increased up to 240 seconds     | 120    |
| ServerLogic/AllowNetworkingToAllDomains | Allow networking across domains         | True   |

## Server logic API URL 

Construct the API URL using this format:
  
`https://<site-url>/_api/serverlogics/<server-logic-name>`
   
Example:   

`https://contoso.powerappsportals.com/_api/serverlogics/exchangerate`

 
## Supported HTTP methods 

Server logic supports standard HTTP methods to perform operations on data or interact with external services.
Each method maps to a function you define in your server logic code.

| Method  | Function signature    | Usage                              | Description   |
|---------|-----------------------|------------------------------------|---------------|
| GET     | function get() { }    | Retrieve data.                     | Used to fetch data from Dataverse, external APIs, or custom business logic. Ideal for read-only operations where no data changes are made. |
| POST    | function post() { }   | Create records or send new data.   | Commonly used to insert new records into Dataverse or send data to external systems. Suitable for form submissions or workflows that need to create or trigger actions. |
| PUT     | function put() { }    | Replace or update records.         | Updates or replaces an entire record or dataset. Typically used for full updates or synchronization scenarios. |
| DELETE  | function del() { }    | Delete records or fields.          | Removes records or data from Dataverse or an external system. Should be used cautiously to prevent unintended data loss. |

## Next step

[Author server logic](author-server-logic.md)

### Related information

[Server objects](server-objects.md)  
[How to interact with Dataverse tables using server logic](server-logic-operations.md)   

