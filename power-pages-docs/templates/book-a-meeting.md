---
title: Book a Meeting template
description: Learn about the Book a Meeting template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/08/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Book a Meeting template

Book a meeting is designed to show you the capabilities of a scheduling template. We've picked the example of scheduling with a bank representative; however, the scheduling principle will apply to any industry or organization looking to stand up a scheduling portal.

**LANDING PAGE PHOTO GOES HERE**

## Users and administrators

There are two key users that the template is designed for:

- The customer of the bank is trying to book an appointment with the bank representative.

- The bank representative who is looking at the list of appointments and managing their calendars and appointments.

### Bank customers

As a customer of a bank, you can do the following seamlessly:

- Book an appointment with a certain bank representative, in a certain bank branch and the time that best suits the customer.

- The customer can also cancel and reschedule the appointments via links present in the email that they receive upon booking confirmation.

### Bank representatives

As a bank representative, you can do the following seamlessly:

NEED CONTENT FOR THIS SECTION

## Makers

This template includes basic forms, lists, and code components, as well as the following customizable tables:

### Bank Customer

| **Page** | **Form name** | **Components in page** | **Form description** | 
|-------------------------|---------------|----------------------|-----------|
| Home | |||
| Book an appointment| Advanced/multi-step form <br>There is a calendar picker within the form. | C2 Book an appointment | Customer inputs services interested in, location (virtual or bankbranch), availability, schedules appointment, etc. |
| Cancel appointment | Basic form | Cancel appointment | Customer cancels an appointment that was booked. |
| Reschedule appointment | Advanced/multi-step form | C2 Reschedule appointment | Customer reschedules an appointment that was booked. |

### Bank Representative

| **Page** | **Form name** | **Components in page** | **Form description** | 
|-------------------------|---------------|----------------------|----------|
| Home | List styled as a calendar | |
| Specialties | List styled as subgrids | |
| Cancel appointment| Basic form | Appointment | Bank representative cancels an appointment that was booked. | |
| Edit appointment | Basic form | C1 Edit appointment | Bank representative edits an appointment that was booked. | 
| Edit unavailability | Basic form | C1 Create appointment | Bank representative edits availability. | 
| Reschedule appointment | Advanced/multi-step form | C1 Reschedule appointment | Bank representative schedules an appointment that was booked. |
| Create unavailability | Basic form | Calendar block | Bank representative creates unavilability. |


## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns.  For custom code editing, use the [**Power Platform CLI**](../configure/cli-tutorial.md) to download the site metadata and **VS Code** to view and modify the source code.