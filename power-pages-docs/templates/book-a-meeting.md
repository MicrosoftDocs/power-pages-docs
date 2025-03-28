---
title: Schedule and manage meetings template
description: Learn about the schedule and manage meetings template.
author: murugesh1985
ms.topic: conceptual
ms.custom: 
ms.date: 04/14/2023
ms.subservice:
ms.author: murugeshs
ms.reviewer: danamartens
contributors:
    - meeramahabala
---

# Schedule and manage meetings template

Schedule and manage meetings is designed to show you the capabilities of a scheduling template. We've chosen the example of scheduling with a bank representative. The scheduling principle will apply to any industry or organization looking to stand up a scheduling website.

:::image type="content" source="media/meeting.png" alt-text="The Schedule and manage meetings landing page in the design studio."::: 

## Users

The template is designed for two key users:

- The banking customer who wants to book an appointment with the bank representative.

- The bank representative who's looking at the list of appointments and managing their calendars and appointments.

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

Makers are able to use the [design studio](../getting-started/use-design-studio.md) to modify the template for specific needs.

The following are the pages, basic forms, and customizable tables provided in the template. These components can be modified to align with your specific project needs.

### Pages

#### Customer pages

The following pages are used by bank customers.

|Page|Description|
|---------|---------|
|Home|Customer homepage. Provides a link to Schedule and manage meetings with a financial consultant.|
|C2 Book an Appointment|Book an appointment with a financial consultant using a multi-step process by inputting service(s) desired, location, and availability.|
|C2 Cancel Appointment|Cancel appointment with a financial consultant.|
|C2 Cancel Confirmation|Confirmation page for successfully canceled appointment(s).|
|C2 Reschedule Appointment|Reschedule a previously booked appointment with a financial consultant.|
|Search|Keyword-based search.|

#### Admin pages

The following pages are used by bank representatives.


|Page|Description|
|---------|---------|
|C1 Home|Sign in to view schedule of appointments by day or by week.|
|C1 Specialties|Select specialties that bank customers can schedule an appointment to discuss.|
|C1 Cancel Appointment|Cancel an appointment with a customer.|
|C1 Edit Appointment|Edit an appointment with a customer.|
|C1 Edit Unavailability|Edit availability to meet with customers.|
|C1 Reschedule Appointment|Reschedule a previously booked appointment with a customer.|
|Create Unavailability|Create unavailability via a calendar block.|
|Profile|Details about a bank representative, such as specialties.|
|getAllAppointments|Query for a bank representative to retrieve all appointments.|
|Access Denied|Displayed when a bank representative doesn't have access.|
|Page Not Found|Displayed when the user's search criteria isn't matched.|


### Forms and tables

The template uses the following forms linked to Dataverse tables.

| Table                 | Table form name*        | Page form name**        |
|---------------------------|----------------------------|---------------------------|
| contact                   | BAM C1 Specialties Subgrid | BAM C1 Select Specialties |
| appointment               | C1 Appointment Create      | C1 Appointment Create     |
| appointment               | Appointment                | C1 Cancel Appointment     |
| appointment               | C1 Appointment Create      | C1 Cancel Calendar Block  |
| msdyn\_appointmentrequest | Calendar Block             | C1 Create Calendar Block  |
| appointment               | Appointment                | C1 Edit Appointment       |
| appointment               | Appointment                | C1 Reschedule             |
| appointment               | Appointment                | C1 Reschedule Appointment |
| contact                   | BAM C1 Simple Specialties  | C1 Simple Specialties     |
| contact                   | BAM C1 Specialties Subgrid | C1 Specialties            |
| contact                   | BAM C1 Image Upload        | C1 UploadImage            |
| msdyn\_appointmentrequest | Cancel Appointment         | C2 Cancel Appointment     |
| feedback                  | simple contact us form     | simple contact us form    |
| account                   | Account                    | testform                  |

**The form name as it appears associated to the table in data workspace.*

***The form name as it appears when added to a page as a component.*

#### Table information

| **Table display name** | **Schema name**           | **Description**                                                                                 |
|------------------------|---------------------------|-------------------------------------------------------------------------------------------------|
| Appointment            | Appointment               | Scheduling for bank representatives.                                                            |
| AppointmentRequest     | msdyn\_appointmentrequest | Capture appointment request and actions (canceling, editing appointment) for customers.         |
| Contact                | contact                   | Capture contact information of bank representative.                                             |
| Feedback               | feedback                  | Capture feedback from customer.                                                                 |
| Account                | Account                   | Capture customer information.                                                                   |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.

### See also 

[Tutorial: Add a page to your Power Pages site](../getting-started/tutorial-add-webpage.md)  
[Create and design pages](../getting-started/first-page.md)
