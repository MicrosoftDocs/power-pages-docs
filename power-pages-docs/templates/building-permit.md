---
title: Building permit application template
description: Learn about the building permit application template.
author: deepa88 
ms.topic: conceptual
ms.custom: 
ms.date: 09/22/2022
ms.subservice:
ms.author: deepabansal 
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Building permit application template

The building permit application template is designed to show you the capabilities of an application submission site. We've chosen the example of a building permit application site. This template might be useful for any industry or organization wishing to create an application submission portal.

:::image type="content" source="media/permit.png" alt-text="The Building Permit Application template landing page in the design studio.":::

## Users

The template is designed for two key users:

- The resident customer who wants to view the permit types and requirements and potentially apply for and track the status of their permit(s).

- The government permits administrator who is responsible for managing the status of submitted building permits.

### Resident customers

Resident customers' capabilities vary based on whether or not they've created a user profile. Residents without a user profile are unauthenticated users and residents who have created user profiles are authenticated users.

#### Unauthenticated

As an unauthenticated resident, you can:

- View the different permit types.

- View the description and timeline for each permit type.

- View the application process information​.

#### Authenticated

As an authenticated resident, you can:

- View the detailed requirements for submitting the application online.

- Submit a permit application online.

- Track the status of a submitted application.

- View (read-only) submitted permits.

- Withdraw submitted permits.

- Receive email notifications.

### Government permit administrators 

As a Government permit administrator, you can:

- View the submitted applications.

- View a snapshot that summarizes the statuses of the submitted applications.

- Edit the status of the submitted applications.

- Provide status updates to residents on the status of their application via an automatic email that gets triggered when the application status changes.

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md) to modify the template for specific needs.

The following are the pages, basic forms, and customizable tables provided in the template. These components can be modified to align with your specific project needs.

## Pages

### Customer pages

The following pages are used by resident customers.

| **Page**        | **Description**                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
| Home            | Resident homepage. Contains links to common permits and the associated permit application.<br />Contains the resident sign-in.                                                                                |
| Default Permit  | Contains the application steps for a permit.                                               |
| Summary         | Contains the sections of the permit application.                                           |
| View My Permits | Contains a summary of applications submitted by a resident and the associated status.<br />Contains the ability for a resident to view their permit application or withdraw their submitted application. |

### Admin pages

The following pages are used by the government permit administrators.

| **Page**            | **Description**                                                          |
|---------------------|--------------------------------------------------------------------------|
| \[Admin\] Home Page | Contains a snapshot summarizing the status of each submitted application.<br />Contains a table view of the submitted applications so the administrator can edit the statuses accordingly. |
| Access Denied       | Displayed when an administrator doesn't have access.                     |
| Page Not Found      | Displayed when the user's search criteria isn't matched.                 |

### Forms and tables

The template uses the following forms linked to Dataverse tables.

| Table        | Table form name\*    | Page form name\*\*                                 |
|--------------|----------------------|----------------------------------------------------|
| Application  | Default Permit       | \[Building Permit\] Default - View Permit          |
| Application  | View Permit          | \[Building Permit\] C1 Admin - View Default Permit |
| Application  | Permit Status Update | \[Building Permit\] C1 Admin - Update Status       |
| Permit       | Information          | N/A                                                |
| Permit Steps | Information          | N/A                                                |

*\* The form name as it appears associated to the table in data workspace.*

*\*\* The form name as it appears when added to a page as a component.*

### Table information

| Table name   | Schema name            | Description                                                     |
|--------------|------------------------|-----------------------------------------------------------------|
| Application  | bp\_DefaultApplication | Contains the application steps for the default permit.          |
| Permit       | bp\_Permit             | Contains the list of common permits.                            |
| Permit Steps | bp\_PermitSteps        | Contains an overview of the sections of the permit application. |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.
