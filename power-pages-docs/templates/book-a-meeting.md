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

The following are the pages, basic forms, and customizable tables provided in the template.

### Pages

#### Customer pages

The following pages are utilized by **Bank Customers**:

|Page|Description|
|---------|---------|
|Home|Customer homepage. Provides a link to book a meeting with a financial consultant.|
|C2 Book an Appointment|Book an appointment with a financial consultant using a multi-step process by inputting service(s) desired, location, and availability.|
|C2 Cancel Appointment|Cancel appointment with a financial consultant.|
|C2 Cancel Confirmation|Confirmation page for successfully canceled appointment(s).|
|C2 Reschedule Appointment|Reschedule a previously booked appointment with a financial consultant.|
|Search|Keyword-based search.|

#### Admin pages

The following pages are utilized by **Bank Representatives**:


|Page|Description|
|---------|---------|
|C1 Home|Sign in to view schedule of appointments by day or by week.|
|C1 Specialties|Select specialties that bank customers can schedule an appointment to discuss.|
|C1 Cancel Appointment|Cancel an appointment with a customer.|
|C1 Edit Appointment|Edit appointment with customer.|
|C1 Edit Unavailability|Edit availability to meet with customers.|
|C1 Reschedule Appointment|Reschedule a previously booked appointment with a customer.|
|Create Unavailability|Create unavailability via a calendar block.|
|Profile|Details about bank representative, such as specialties.|
|getAllAppointments|Query for a bank representative to retrieve all appointments.|
|Access Denied|Displays if bank representative doesn't have access.|
|Page Not Found|Displays if user's search criteria isn't matched.|


### Forms 

The following forms are included in this template:


|Column1  |Column2  |Column3  |
|---------|---------|---------|
|Row1     |         |         |
|Row2     |         |         |
|Row3     |         |         |
|Row4     |         |         |
|Row5     |         |         |
|Row6     |         |         |
|Row7     |         |         |
|Row8     |         |         |
|Row9     |         |         |
|Row10     |         |         |
|Row11     |         |         |
|Row12     |         |         |
|Row13     |         |         |
|Row14     |         |         |

### Tables

All data for this template is stored in these tables:

|**Table**|**Description**|
|---------|---------|
|Appointment    |         |
|AppointmentRequest     |         |
|Contact     |         |
|Location    |         |
|Service     |         |
|Website     |         |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns.  For custom code editing, use the [**Power Platform CLI**](../configure/cli-tutorial.md) to download the site metadata and **Visual Studio Code** to view and modify the source code.