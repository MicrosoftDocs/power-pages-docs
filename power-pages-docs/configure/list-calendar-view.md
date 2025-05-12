---
title: List calendar view
description: Learn how to enable a list to render as a calendar view on a website.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 02/07/2025
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# List calendar view

You can enable a list to render as a calendar view, with each individual record configured to act as a single event.

The required settings are available in the [Portal Management app](portal-management-app.md). Once you have the view open in the management app, select the **Calendar View** tab. The following field mappings can be configured to display list records as dated events on the calendar. The records need to include at least one date field.

> [!Tip]
> See [date and time](behavior-format-date-time-field.md#date-and-time) field behaviors for information on formatting date and time fields on webpages.

| Entity Field Mappings | Details |
| - | - |
| Start Date Field Name | A datetime column representing the start date of a calendar event. |
| End Date Field Name | A datetime column representing the end date of a calendar event. |
| Summary Field Name | A text column that shows the summary of a calendar event. |
| Description Field Name | A text column that displays a description of the calendar event. |
| Organizer Field Name | A text or lookup column that displays the organizer of the calendar event. |
| Location Field Name | A text column describing the location of the calendar event.|
| Is All Day Field Name | A yes/no column indicating if the calendar event is all day. |

| Setting | Details |
| - | - |
| Initial View | Initial view of the calendar; year, month, week, or day. Default value is month. |
| Initial Date | The initial start date when the calendar is rendered. Default (blank) is the current date. |
| Time Zone Display Mode | The time zone the calendar is displayed in. No option selected displays the events based on how the date column is configured in Dataverse. The *User Local Time Zone* displays events in the calendar using the time zone of the user viewing the portal. *Specific Time Zone* displays the calendar events with a specified time zone. |
| Display Time Zone | If the **Time Zone Display Mode** is set to *Specific Time Zone* this value determines the time zone the calendar events are displayed. |
| Style | The setting displays the calendar in either a *Full Calendar* format or as an *Event List* |

Once the specific fields are configured, a list calendar view appears on the portal page.

:::image type="content" source="media/lists/calendar-list.png" alt-text="List displayed as a calendar on a web page.":::

### See also

- [Lists overview](lists.md)
- [Portal Management app](portal-management-app.md)  
- [Redirect to a new URL](add-redirect-url.md)
