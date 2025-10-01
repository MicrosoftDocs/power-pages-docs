---
title: Power Pages server logic overview (preview)
description: Learn how to configure and secure Power Pages server logic, including governance settings, API authentication, and site-specific configurations.
#customer intent: As a developer, I want to securely run JavaScript on the server so that I can extend site functionality without exposing code in the browser.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# Server logic overview (preview)

[!INCLUDE[cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Power Pages server logic lets makers run JavaScript securely on the server, adding extensibility directly to the site runtime.  
   
Because server logic runs on the server, it's hidden from the browser and protected by web roles and table permissions. You add logic in Power Pages Studio and author it using Visual Studio Code, which provides IntelliSense and compile-time validation.  

Dataverse stores code and configuration, so server logic benefits from the same lifecycle management and deployment pipelines as other Power Pages components.  

> [!IMPORTANT]
>
> - This feature is a preview feature.
> - Preview features aren’t meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2189520), and are available before an official release so that customers can get early access and provide feedback. 

## Features

Server logic lets developers write native JavaScript code compliant with the [ECMAScript 2023](https://tc39.es/ecma262/2023/) standard. This environment doesn't provide access to browser-specific APIs or libraries, like `fetch`, `XMLHttpRequest`, or other DOM-related features typically available in client-side JavaScript.  

This feature is available only for Enhanced Data Model.

## Securing the Server logic 

To run code in server logic, users need the right permissions set by the maker. Web roles and table permissions control access.

### Authenticating server logic API 

You don't need to include custom authentication code. Authentication and authorization are managed by the application session. All web API calls must include a Cross-Site Request Forgery (CSRF) token.  

## Governance setting for anonymous access 

Server logic integrates with Dataverse and external services to perform complex computations that might use data from external systems. When administrators enforce the governance control, any integration initiated by anonymous users, especially those involving external systems, is blocked.  

## Site settings

The following optional site settings help configure server logic: 

| Name                | Description             | Default                |
|---------------------|-------------------------|------------------------|
| ServerLogic/Enabled | Enable / Disable feature                 | true  |
| ServerLogic/AllowedDomains    | Restrict which external domains can be called | All domains allowed |
| ServerLogic/TimeoutInSeconds        | Maximum execution time (in seconds)      | 120    |
| ServerLogic/MaxMemoryUsageInBytes   | Maximum memory per function              | 10 MB  |
| ServerLogic/AllowNetworkingToAllDomains | Allow networking across domains         | True   |

## Server logic API URL 

Construct the API URL using this format:   
https://\<site-url\>/\_api/serverlogics/\<server-logic-name\>   
   
Example:   
https://contoso.powerappsportals.com/\_api/serverlogics/exchangerate 

 

## Supported HTTP methods 

Each method maps to a function you define in server logic: 

| Method  | Function signature    | Usage                              |
|---------|-----------------------|------------------------------------|
| GET     | function get() { }    | Retrieve data.                     |
| POST    | function post() { }   | Create records or send new data.   |
| PATCH   | function patch() { }  | Update part of a record (upsert).  |
| PUT     | function put() { }    | Replace or update records.         |
| DELETE  | function del() { }    | Delete records or fields.          |

Next steps

Author server logic