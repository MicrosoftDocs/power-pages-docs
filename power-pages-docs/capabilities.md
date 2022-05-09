---
title: Power Pages capabilities
description: Learn about Power Pages capabilities.
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 05/09/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
    - KumarVivek
---

# Power Pages capabilities

[!INCLUDE[cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

You can quickly create and design professional and secure sites for your business using Power Pages. This topic provides you an overview of key Power Pages capabilities. 

## Simplified authoring experience for makers

Quickly create new site directly from the Power Pages home page using the default template or choose existing industry-based starter templates.

:::image type="content" source="media/overview/create-a-site.png" alt-text="Create a Power Pages site.":::

See more: [Create a site](getting-started/create-manage.md)

### Design studio

Makers can build powerful and engaging sites without writing a single line of code.

:::image type="content" source="media/overview/design-studio.png" alt-text="Design studio.":::

The new and enhanced [design studio](getting-started/use-design-studio.md) provides the following workspaces:

- [Pages workspace](getting-started/first-page.md) for creating, designing and arranging web pages.
- [Style workspace](getting-started/style-site.md) for applying styles and themes to your site.
- [Data workspace](getting-started/use-data-workspace.md) for creating and modifying Microsoft Dataverse tables used in data-driven web applications.
- [Setup workspace](configure/setup-workspace.md) for administration and site management

## Responsive Rendering

Power Pages is based on Bootstrap which natively provides support for building websites that are responsive, mobile friendly, and available in various form factors.

<!--image-->
**CONTENT NOTE:  BETTER IMAGE SHOWING SAME SCREEN DIFFERENT FORM FACTORS**

:::image type="content" source="media/overview/form-factors.png" alt-text="Power Pages form factors.":::

## Advanced development capabilities for professional developers 

Makers can work with pro-developers in fusion teams to extend the functionality using Visual Studio Code and the Power Platform CLI to create powerful business application web sites.

:::image type="content" source="media/overview/vs-code-pac-cli.png" alt-text="Visual Studio Code.":::

See more: 
- [Using Visual Studio Code and Power Platform CLI](configure/cli-tutorial.md)
- [Use the code editor](getting-started/code-editor.md)
- [Add code components](configure/component-framework.md)

## Robust security and governance capabilities

### Security

<!--image-->
**CONTENT NOTE: IMAGE CONVEYING SECURITY HERE**

Power Pages inbuilt security is its core which allows organizations to securely enable access of their business data to their users (internal or external) via Power Page’s authorization rules. For more information, go to [Power Pages Security](security/power-pages-security.md)

Organizations using Power Pages can choose from a variety of authentication providers or allow access to site content anonymously. For more information, go to [Configure Authentication](security/configure-portal-authentication.md)

Power Pages is hosted as Azure App Service, which has International Organization for Standardization (ISO), System and Organization Controls (SOC), and Payment cards Industry Data Security Standards (PCI DSS) compliance. For more information, go to [Microsoft Trust Center](https://www.microsoft.com/trust-center/product-overview)

Power Pages support modern TLS crypto standards (TLS 1.2) and has inbuilt DDOS protection. Power Pages supports dynamic IP restriction to rate limit traffic from bad actors and provide secure configuration driven mechanisms for admins to address top web security vulnerabilities such as injection attacks, cross site request forgery, and server-side request forgery.

You can also configure Power Pages to use edge caching and Web Application Firewall (WAF) capabilities.  For more information, go to [Set up Azure Front Door with portals](/power-apps/maker/portals/azure-front-door).

### Governance

Power Pages and provides some helpful tools for administrators to manage the administration and lifecycle of their sites and environments.

For more information, go to [Power Pages Governance](admin/coe-portals.md)

## Integration with other Power Platform components

Power Pages provides deep integration with other Power Platform components, such as you can:
- Embed Power BI reports in sites configured with row-level security so that authenticated users can only view data that they have access to.
- Configure intelligent bots created using Power Virtual Agents on your site pages.
- Trigger Power Automate flows to automate business tasks.
- Build Power Apps to access information collected and transacted from Power Pages.
- Extend Dynamics 365 business applications using Power Pages.