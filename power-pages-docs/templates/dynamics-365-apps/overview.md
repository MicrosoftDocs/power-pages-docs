---
title: Dynamics 365 templates
description: Learn how to use Dynamics 365 templates to create or enhance your Power Pages sites.
author: sampatn
ms.topic: conceptual
ms.custom: 
ms.date: 04/10/2023
ms.subservice:
ms.author: sampatn
ms.reviewer: danamartens
contributors:
    - sampatn
---

# Dynamics 365 templates

Dynamics 365 templates are available for your Power Pages sites in environments containing Dynamics 365 applications, including:

- Dynamics 365 Sales
- Dynamics 365 Customer Service
- Dynamics 365 Field Service
- Dynamics 365 Marketing
- Dynamics 365 Project Operations
- Dynamics 365 Supply Chain Management
- Dynamics 365 Intelligent Order Management

>[!IMPORTANT]
> Dynamics 365 templates are not available during the first run experience for site creation, but may be used for subsequent site creation.

## Customer self-service

The customer self-service site gives customers access to self-service knowledge and support resources.  Customers can also view the progress of their cases and provide feedback.

:::image type="content" source="media/dynamics365-templates/customer-self-service.png" alt-text="Customer self-service template landing page.":::

More information: [Manage knowledge categories](configure-knowledge-categories-articles.md)

## Partner

The partner site template allows organizations with resellers, distributors, suppliers, or partners to have real-time access to every stage of shared activities.

>[!NOTE]
>Field Service and Project Operations packages must be installed in your Dynamics 365 environment to enable respective options. For more information, see [Integrate Project Service Automation](integrate-project-service-automation.md) and [Integrate Field Service](integrate-field-service.md).

:::image type="content" source="media/dynamics365-templates/partner.png" alt-text="Partner template landing page.":::

>[!IMPORTANT]
> There's a limit of only one site for this type of template that can be created per Dynamics 365 environment. 

More information:

- [Site limits for site template type](/power-apps/maker/portals/create-additional-portals)
- [Use Opportunity record in Partner site](create-edit-and-distribute-opportunities-in-dynamics-365.md)
- [Configure web roles for a Partner site](configure-web-roles-partner-portal.md)
- [Field Service integration](integrate-field-service.md)
- [Project Service Automation integration](integrate-project-service-automation.md)

## Employee self-service

An employee self-service site creates an efficient and well-informed workforce by streamlining common tasks and empowering employees with a definitive source of knowledge.

:::image type="content" source="media/dynamics365-templates/employee-self-service.png" alt-text="Employee self-service template landing page.":::

## Event portal with Customer Insights Journeys

Customers with Customer Insights - Journeys can create a customizable event portal where clients access event details, session specifics, and speaker schedules, and register using the event registration form.

A centralized location is essential for clients to discover and learn about your events. The event portal allows swift creation of a comprehensive hub where customers access event details and register for multiple events at the same time.

This template includes:

- Customizable event template
- List of events
- Event detail page with information about the location, agenda, speakers, and sponsors
- Event registration page

Learn more about setting up and using this template in [Build an event registration website using Power Pages](/dynamics365/customer-insights/journeys/event-portal-template).

## Community

The community site template uses peer-to-peer interactions between customers and experts.  Use this template to organically grow the catalog of available knowledge via knowledge base articles, forums, and blogs, and the feedback provided through comments and ratings.

:::image type="content" source="media/dynamics365-templates/community.png" alt-text="Community template landing page.":::

More information:

- [Engage with Community](engage-with-communities.md)
- [Manage forums with Community](setup-manage-forums.md)
- [Manage blogs with Community](manage-blogs.md)
- [Manage ideas with Community](crowdsource-ideas.md)

## Supply chain management customer site

The supply chain management customer site template lets you build externally facing business-to-business (B2B) websites for sales order processing. Your customers can create and view orders to the associated Dynamics 365 for Supply Chain Management environment. You can modify this template to represent the company's brand, add more functionality, and change the user experience. 

:::image type="content" source="media/dynamics365-templates/scm.png" alt-text="Supply chain management template landing page.":::  

>[!IMPORTANT]
> There's a limit of only one site for this type of template that can be created per Dynamics 365 environment. 

More information:

- [Customer site for Dynamics 365 Supply Chain Management application](/dynamics365/supply-chain/sales-marketing/customer-portal-overview).
- [Site limits for site template type](/power-apps/maker/portals/create-additional-portals)

## Modern community

The modern community site template invites customers to provide suggestions, creating crowd sourced portfolios of outside-in ideas. Customers can collaborate on a social scale, rallying behind suggestions from others to shape the future of the products they use. 

:::image type="content" source="media/dynamics365-templates/modern-community.png" alt-text="Modern community template landing page.":::

More information: [Customer Service Community](/dynamics365/customer-service/community-get-started)

## Field service customer

The field service customer site template allows your customers to book new appointments, manage existing appointments, track their technician, and provide feedback.

:::image type="content" source="media/dynamics365-templates/field-service.png" alt-text="Field Service template landing page.":::

This template provides your customers with automated service reminders and notifications that include estimated technician arrival times, so that customers can better plan for their time around service visits.  

>[!IMPORTANT]
> There's a limit of only one site for this type of template that can be created per Dynamics 365 environment.

More information: [Field Service customer site](/dynamics365/field-service/field-service-portal-homepage)

## Order returns

> [!NOTE]
> This template is a preview offering.

This template integrates with the Dynamics 365 Intelligent Order Management application. Add this template to an existing customer website or use it to create a new site. Customers can return their orders, view the status of their return request, view return history, and monitor their refund status. 

:::image type="content" source="media/dynamics365-templates/order-returns.png" alt-text="Order returns template landing page.":::

More information: [Dynamics 365 Intelligent Order Management](/dynamics365/intelligent-order-management/overview)

## Limitations

While using [Power Pages design studio](../../configure/design-build-overview.md) to customize Dynamics 365 templates, consider the following limitations.

- Existing Dynamics 365 templates are not completely editable inside [Pages workspace](../../getting-started/first-page.md). Use [Portal Management app](../../configure/portal-management-app.md) or [Visual Studio Code](../../configure/power-platform-cli-tutorial.md) instead.
- [Styling workspace](../../getting-started/style-site.md) is not available for Dynamics 365 templates. Instead, use out of the box CSS files or custom CSS files as webfiles for styling. More information: [Create and manage web files](../../configure/web-files.md)
