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

**LANDING PAGE PHOTO GOES HERE**

## Users and administrators

There are two key users that the template is designed for:

- The banking customer is trying to book an appointment with the bank representative.

- The bank representative who is looking at the list of appointments and managing their calendars and appointments.

### Bank customers

As a customer of a bank, you can do the following seamlessly:

- Book an appointment with a certain bank representative, in a certain bank branch and the time that best suits the customer.

- The customer can also cancel and reschedule the appointments via links present in the email that they receive upon booking confirmation.

### Bank representatives

As a bank representative, you can do the following seamlessly:

NEED CONTENT FOR THIS SECTION

## Makers

This template includes basic forms, lists, code components, and customizable tables.

### Tables

#### Bank Customer

| **Page** | **Components** | **Description** | 
|-------------------------|---------------|----------------------|
| Home |||
| Book an appointment| Advanced/multi-step form <br>There's a calendar picker within the form. | Customer inputs services interested in, location (virtual or bank branch), availability, schedules appointment, etc. |
| Cancel appointment | Basic form | Cancel appointment | Customer cancels an appointment that was booked. |
| Reschedule appointment | Advanced/multi-step form | C2 Reschedule appointment | Customer reschedules an appointment that was booked. |

#### Bank Representative

| **Page** | **Components** | **Description** | 
|-------------------------|---------------|----------------------|
| Home | List styled as a calendar | |
| Specialties | List styled as subgrids | |
| Cancel appointment| Basic form | Appointment | Bank representative cancels an appointment that was booked. |
| Edit appointment | Basic form | Bank representative edits an appointment that was booked. | 
| Edit unavailability | Basic form | Bank representative edits availability. | 
| Reschedule appointment | Advanced/multi-step form | Bank representative schedules an appointment that was booked. |
| Create unavailability | Basic form | Calendar block | Bank representative creates unavailability. |


## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns.  For custom code editing, use the [**Power Platform CLI**](../configure/cli-tutorial.md) to download the site metadata and **VS Code** to view and modify the source code.