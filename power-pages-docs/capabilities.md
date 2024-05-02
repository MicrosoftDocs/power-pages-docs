---
title: Power Pages capabilities
description: Learn about Power Pages capabilities.
author: dileepsinghmicrosoft
ms.topic: conceptual
ms.custom: 
ms.date: 05/01/2024
ms.subservice:
ms.author: dileeps
ms.reviewer: kkendrick
contributors:
    - nickdoelman
    - ProfessorKendrick
    - KumarVivek
    - dileepsinghmicrosoft
---

# Power Pages capabilities

You can quickly create and design professional and secure sites for your business with Power Pages. This article provides an overview of key Power Pages capabilities. 

## Simplified authoring experience for makers

Quickly create new sites directly from the Power Pages home page by using the default template, or choose from existing industry-based starter templates.

:::image type="content" source="media/overview/create-a-site.png" alt-text="Create a Power Pages site.":::

More information: [Create a site](getting-started/create-manage.md)

### Design studio

Build powerful and engaging sites without writing a single line of code.

:::image type="content" source="media/overview/design-studio.png" alt-text="Design studio.":::

The new and enhanced [design studio](getting-started/use-design-studio.md) provides five workspaces:

- [Pages workspace](getting-started/first-page.md) for creating, designing, and arranging webpages
- [Styling workspace](getting-started/style-site.md) for applying styles and themes to your site
- [Data workspace](getting-started/use-data-workspace.md) for creating and modifying Microsoft Dataverse tables used in data-driven web applications
- [Set up workspace](configure/setup-workspace.md) for administration and site management
- [Security workspace](getting-started/use-security-workspace.md) for identifying and addressing vulnerabilities

## Responsive rendering

Power Pages is based on Bootstrap, which natively provides support for building websites that are responsive, mobile-friendly, and available in various form factors.

:::image type="content" source="media/overview/form-factors.png" alt-text="Power Pages form factors.":::

## Advanced development capabilities for pro developers 

Makers can work with pro developers in fusion teams to extend the functionality using Visual Studio Code and the Microsoft Power Platform CLI to create powerful business application websites.

:::image type="content" source="media/overview/vs-code-pac-cli.png" alt-text="Visual Studio Code.":::

Read more: 
- [Using Visual Studio Code and Power Platform CLI](configure/power-platform-cli-tutorial.md)
- [Use the code editor](getting-started/code-editor.md)
- [Add code components](configure/component-framework.md)

## Security and governance

Power Pages' inbuilt security is its core. It allows organizations to securely enable access of their business data to their users (internal or external) through Power Pages authorization rules. More information: [Power Pages security](security/power-pages-security.md)

- Organizations using Power Pages can choose from various authentication providers or allow access to site content anonymously. More information: [Configure Power Pages site authentication](security/authentication/configure-site.md)

- Power Pages is hosted as Azure App Service, which has International Organization for Standardization (ISO), System and Organization Controls (SOC), and Payment Card Industry Data Security Standards (PCI DSS) compliance. More information: [Microsoft Trust Center](https://www.microsoft.com/trust-center/product-overview)

 - Power Pages supports modern TLS crypto standards (TLS 1.2) and has built-in Azure DDoS protection. It also supports dynamic IP restriction to limit traffic from bad actors and provides secure, configuration-driven mechanisms for admins to address top web security vulnerabilities such as injection attacks, cross-site request forgery, and server-side request forgery.

- You can also configure Power Pages to use edge caching and web application firewall (WAF) capabilities. More information: [Set up Azure Front Door with Power Pages sites](configure/azure-front-door.md)

Power Pages provides helpful tools for administrators to manage the administration and lifecycle of their sites and environments. More information: [Power Pages governance](admin/coe-portals.md) 

## Integration with other Microsoft Power Platform components

Power Pages provides deep integration with other [Microsoft Power Platform](/power-platform) components.

- **Dataverse** allows you to securely store and manage data used by business applications and your Power Pages sites. Use model-driven app constructs like forms, views, charts, and dashboards to easily surface Dataverse data. 

- **Power Apps** empowers anyone to create no-code/low-code custom mobile and web apps to share and collect data and streamline business processes. Using Power Apps to create an app that uses SharePoint to store content is a popular way to quickly build basic intranet sites. Power Pages is ideal for websites focused on external audiences that require more secure access to your business information.  

- **Power Automate** simplifies the creation of automated workflows. You can use Power Automate for plug-ins, workflows, automated cloud flows, or to extend business logic. You can also interact with data and events coming and going in and out of Dataverse. 

- **Power BI** allows anyone to access visually immersive and interactive insights from business data. With Power Pages, integrate with Power BI to access components like reports, dashboards, and tiles. Use the embed capability to surface data that sits outside of Dataverse. 

- **Microsoft Copilot Studio** enables teams to easily create and publish AI-driven chatbot experiences. With Power Pages, add chatbots to your external-facing websites for a myriad of business purposes.
