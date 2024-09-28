---
title: Application processing template
description: Learn about the application processing template.
author: deepa88 
ms.topic: conceptual
ms.custom: 
ms.date: 04/14/2023
ms.subservice:
ms.author: deepabansal 
ms.reviewer: danamartens
contributors:
    - nickdoelman
---

# Application processing template

The application processing template is designed to show you the capabilities of an application submission site. We've chosen the example of a building permit application site. This template might be useful for any industry or organization wishing to create an application submission portal.

:::image type="content" source="media/permit.png" alt-text="The application processing template landing page in the design studio.":::

## Users

The template is designed for three key users:

- A [resident customer](#resident-customer) user who wants to view the permit types and requirements.
- A [resident customer](#resident-customer) who has created a profile and wants to apply for a permit. [Web role](../security/create-web-roles.md) assigned to this user: "[Building Permit] C2 – User (Default)"
- A [government permit administrator](#government-permit-administrator) who is responsible for managing the status of the building permits. [Web role](../security/create-web-roles.md) assigned to this user: "[Building Permit] C1 - Admin Unauthenticated Resident"

### Resident customer

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

### Government permit administrator

As a government permit administrator, you can:

- View the submitted applications.
- View a snapshot that summarizes the statuses of the submitted applications.
- Edit the status of the submitted applications.
- Provide status updates to residents on the status of their application using an automatic email that gets triggered when the application status changes.

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md) to modify the template for specific needs.

The following are the pages, basic forms, and customizable tables provided in the template. These components can be modified to align with your specific project needs.

## Pages

### Customer pages

The following pages are used by resident customers.

| **Page**        | **Description**                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
| Home            | Resident homepage. Contains links to common permits, the associated permit application, and the option for the residents to sign-in.                                                                                |
| Default Permit  | Contains the application steps for a permit.                                               |
| Summary         | Contains the sections of the permit application.                                           |
| View My Permits | <ul> <li> Contains a summary of applications submitted by a resident and the associated status. </li> <li> Allows a resident to view their permit application or withdraw their submitted application. </li> </ul> |

### Admin pages

The following pages are used by the government permit administrators.

| **Page**            | **Description**                                                          |
|---------------------|--------------------------------------------------------------------------|
| \[Admin\] Home Page | <ul> <li> Contains a snapshot summarizing the status of each submitted application. </li> <li> Contains a table view of the submitted applications so the administrator can edit the statuses accordingly. </li> </ul>|
| Access Denied       | Displayed when an administrator doesn't have access.                     |
| Page Not Found      | Displayed when the user's search criteria isn't matched.                 |

### Forms and tables

The template uses the following forms linked to Dataverse tables.

| Table        | Table form name\*    | Page form name\*\*                                 | Form Description                                                                                                                                                 |
|--------------|----------------------|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Application  | Default Permit       | \[Building Permit\] Default - View Permit          | Contains the application questions of the permits that include: <ul> <li> User Information </li> <li> Permit Description </li> <li> Document Upload </li> <li> Acknowledgment </li> <li> Review Request </li> </ul> |
| Application  | View Permit          | \[Building Permit\] C1 Admin - View Default Permit | Submitted permit applications                                                                                                                                    |
| Application  | Permit Status Update | \[Building Permit\] C1 Admin - Update Status       | Status update of submitted applications                                                                                                                          |
| Permit       | Information          | N/A                                                | N/A                                                                                                                                                              |
| Permit Steps | Information          | N/A                                                | N/A                                                                                                                                                              |

*\* The form name as it appears associated to the table in data workspace.*

*\*\* The form name as it appears when added to a page as a component.*

### Table information

| Table name   | Schema name            | Description                                                    |
|--------------|------------------------|----------------------------------------------------------------|
| Application  | bp\_DefaultApplication | Contains the application steps for the default permit          |
| Permit       | bp\_Permit             | Contains the list of common permits                            |
| Permit Steps | bp\_PermitSteps        | Contains an overview of the sections of the permit application |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.

### See also

[Tutorial: Add a page to your Power Pages site](../getting-started/tutorial-add-webpage.md)  
[Create and design pages](../getting-started/first-page.md)
