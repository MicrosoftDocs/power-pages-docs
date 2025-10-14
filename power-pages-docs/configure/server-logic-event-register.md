---
title: Create an event registration page
description: Create an event registration page that automates attendee validation, calendar bookings, and confirmation emails with this comprehensive guide.
#customer intent: As a developer, I want to use the Microsoft Graph API to book events in a shared Outlook calendar so that scheduling is automated.
author: shwetamurkute
ms.author: nabha
ms.reviewer: smurkute
ms.date: 09/30/2025
ms.topic: concept-article
---

# How to create an event registration page

## Step 1: Visitor fills event registration form

- Name, Email, Phone
- Event (dropdown from Dataverse: “Product Launch”, “Training Session”, “Webinar”)
- Preferred Date

## Step 2: On Submit (Server Logic runs)

- Validates attendee info (Dataverse Read)
- Creates an “Event Registration” record in **Dataverse**
- Calls **Microsoft Graph API**:
  - Books the event into a shared Outlook calendar
  - Generates a **Teams meeting link** for virtual event
  - Stores Teams link + registration ID back in Dataverse

## Step 3: Confirmation

- Page shows “Registration Confirmed” with Teams meeting link and calendar invite download.
- Good to have: Email confirmation sent via server logic SMTP.

### Related information

[Server logic overview](server-logic-overview.md)  
[Author server logic](author-server-logic.md)  
[Server objects](server-objects.md)   
[How to interact with Dataverse tables using Server logic](server-logic-operations.md)  
