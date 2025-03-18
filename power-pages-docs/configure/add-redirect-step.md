---
title: Add a redirect step type
description: Learn how add and configure a redirect step for multistep forms in Power Pages.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 04/06/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
---

# Add a redirect step type

The **Redirect** step type allows for a redirect of the user's browser session to another webpage in the website or to an external URL. This is useful for seamlessly directing flow.

| Name                                                            | Description                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| External URL                                                    | Requires On Success set to Redirect. Specify a URL to an external resource on the web.                                                                                                       |
| or Web Page                                                     | Requires On Success set to Redirect. Select a Web Page from the current website.                                                                                                             |
| Append Existing Query String                                    | Requires On Success set to Redirect. When checked the existing query string parameters will be added to the target URL prior to redirection.                                                 |
| Append Record ID To Query String                                | Requires On Success set to Redirect. When checked the ID of the record created is appended to the query string of the URL being redirected to.                                               |
| Record ID Parameter Name                           | Requires On Success set to Redirect. The name of the ID parameter in the query string of the URL being redirected to.                                                                        |
| Append Custom Query String                                      | Requires On Success set to Redirect. A custom string that can be appended to the existing Query String of the redirect URL.                                                                  |
| Append Attribute Value to Query String - Parameter Name         | Requires On Success set to Redirect. A name to give to the parameter that correlates to the attribute value on the target table that gets appended to the Query String of the redirect URL. |
| Append Attribute Value to Query String - Attribute Logical Name | Requires On Success set to Redirect. A logical name of an attribute on the target table to get the value to be appended to the Query String of the redirect URL.                            |

### See also

- [Portals Management app](portal-management-app.md)  
- [Define basic forms](basic-forms.md)  
- [Multistep form steps](multistep-form-steps.md)  
- [Load form/load tab step type](load-form-step.md)  
- [Conditional step type](add-conditional-step.md)  
- [Add custom JavaScript](add-custom-javascript.md)  


