---
title: Book a Meeting template
description: Learn about the Book a Meeting template
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

# Book a Meeting template

Book a meeting is designed to show you the capabilities of a scheduling template. We've chosen the example of scheduling with a bank representative.  The scheduling principle will apply to any industry or organization looking to stand up a scheduling portal.

:::image type="content" source="media/meeting.png" alt-text="The Book a Meeting landing page in design studio."::: 

## Users

There are two key users that the template is designed for:

- The banking customer is trying to book an appointment with the bank representative.

- The bank representative who is looking at the list of appointments and managing their calendars and appointments.

### Bank customers

As a customer of a bank, you can do the following seamlessly:

- Book an appointment with a specific bank representative at a specific bank branch and select your preferred time.

- Cancel and reschedule your appointments via links provided in the email booking confirmation.

### Bank representatives

As a bank representative, you can do the following seamlessly:

- Manage your schedule.
- Create, update, and manage appointments.
- Block your schedule to indicate time away and other commitments.
- Receive email notifications for appointment changes.

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md)  to modify the template for specific needs.

The following are the basic forms, lists, code components, and customizable tables provided in the template.

### Customer pages

The following pages are utilized by **Bank Customers**:


| **Pages** | **Tables** | **Forms** | **Lists** | **Description** |
|-----------|------------|-----------|-----------|-----------------|
| Home |||
| Book an appointment| | | Advanced/multi-step form <br>There's a calendar picker within the form. | Customer inputs services interested in, location (virtual or bank branch), availability, schedules appointment, etc. |
| Cancel appointment | | | Basic form | Customer cancels an appointment that was booked. |
| Reschedule appointment | | |Advanced/multi-step form | Customer reschedules an appointment that was booked. |

### Admin pages

The following pages are utilized by **Bank Representatives**:

| **Pages** | **Tables** | **Forms** | **Lists** | **Description** |
|-----------|------------|-----------|-----------|-----------------|
| Home | | | List styled as a calendar | |
| Specialties | | | List styled as subgrids | |
| Cancel appointment| | Basic form | | Bank representative cancels an appointment that was booked. |
| Edit appointment | | Basic form | | Bank representative edits an appointment that was booked. | 
| Edit unavailability | | Basic form | | Bank representative edits availability. | 
| Reschedule appointment | |Advanced/multi-step form  | | Bank representative schedules an appointment that was booked. |
| Create unavailability | | Basic form | | Bank representative creates unavailability. |


## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns.  For custom code editing, use the [**Power Platform CLI**](../configure/cli-tutorial.md) to download the site metadata and **VS Code** to view and modify the source code.