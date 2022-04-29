---
title: After School template
description: Learn about the after school template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/28/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# After School template

The After School Program template is designed to show you the capabilities of a registration portal application.  We have chosen the example of registering for after school classes.  This template may be useful for any industry or organization wishing to create a registration portal.

:::image type="content" source="media/school.png" alt-text="The After School template landing page.":::

## Users

There are two key users that the template is designed for:

- The parent who is trying to register their children for after school classes.

- The school representative is looking to maintain a list of courses, edit existing courses, and add new courses to the catalog.

### Parents

As a parent who is looking to register for classes, you can:

- Register for an after-school class from the list of available classes.

- Modify the schedule.

- Add and edit attendee information.

- Receive emails with information about the class, which you can use to modify your registration.

### School representatives

As a representative of the school, you can:

- Maintain the course catalog.

- Add and modify existing classes.

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md)  to modify the template for specific needs.

The following are the basic forms, lists, code components, and customizable tables provided in the template.

### Customer pages

The following pages are utilized by **Parents**:

| **Pages** | **Components** | **Description** |
|-----------|----------------|-----------------|
| Home      | List view | Displays courses and key details about each course. |
| Unregister Attendee | Basic form | Ability to unregister children who are currently registered. |
| Add Attendee Profile | Basic form | Ability to add an attendee. | 
| Attendee Information | List view | View details of children who are registered. |
| Edit Attendee Profile | Basic form | Edit the information for children in "My Children." |
| My Registrations | List view | View courses that attendees are registered for. |
| Registration Success | | |
| View Course Details | | |

### Admin pages

The following pages are utilized by **School Representatives**:

| **Pages** | **Components** | **Description** |
|-----------|----------------|-----------------|
| Courses Home | List view | Displays the courses that are available. |
| Edit Course | Basic form | Ability to modify existing course(s). |
| Delete Course | Basic form | Ability to delete a course. |
| Create Course | Basic form | Ability to create a course. |
| Duplicate Course | Basic form | Ability to duplicate a course. |
| View Registrations | List view | View registrations for attendees. |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns.  For custom code editing, use the [**Power Platform CLI**](../configure/cli-tutorial.md) to download the site metadata and **VS Code** to view and modify the source code.