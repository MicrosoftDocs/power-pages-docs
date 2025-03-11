---
title: Responding to Data Subject Rights (DSR) requests to delete Power Pages customer data
description: Walkthrough of how to respond to Data Subject Rights (DSR) requests to delete Power Pages customer data.
ms.reviewer: dmartens
ms.topic: overview
ms.date: 10/08/2024
ms.author: pudupa
search.audienceType: 
  - admin
contributors:
- DanaMartens 
---

# Responding to Data Subject Rights (DSR) requests to delete Power Pages customer data

This article discusses the experiences that Power Pages offers when deleting personal data for a specific user.

## Maker/Admin

1. **System generated telemetry logs:**

    Learn how to delete this data in [Responding to DSR requests for system-generated logs in Power Apps, Power Automate, and Microsoft Dataverse](/power-platform/admin/powerapps-privacy-dsr-guide-systemlogs).

1. **Environment:**

    All the data stored in environments are stored within Dataverse. Learn more about how to respond to DSR requests for this data in [Responding to DSR requests for Microsoft Dataverse customer data](/power-platform/admin/dataverse-privacy-dsr-guide).

1. **Power Pages Maker/Admin settings:**

    To delete these settings, you can delete the user from Microsoft Entra. Learn more in [Responding to Data Subject Rights (DSR) requests to delete customer data](/power-platform/admin/powerapps-privacy-delete-dsr).

## Website user/visitor

1. **System generated telemetry logs:**

    Learn how to delete this data in [Responding to DSR requests for system-generated logs in Power Apps, Power Automate, and Microsoft Dataverse](/power-platform/admin/powerapps-privacy-dsr-guide-systemlogs).

    All system generated telemetry logs are automatically deleted after 29 days.

1. **Environment:**

    All the data stored in environments are stored within Dataverse. By default, all Power Pages customer data is stored in the following tables in Dataverse:

    - Contact
    - Account
    - Web Form Sessions (or Advanced Form Sessions)
    - Power Pages log (if Web Application Firewall logs are enabled)

    However, you can extend this configuration. It's essential to establish policies and procedures for tracking where each individual's personal data is stored, ensuring you're ready to handle DSR requests.

    Learn more about how to respond to DSR requests for this data in [Responding to DSR requests for Microsoft Dataverse customer data](/power-platform/admin/dataverse-privacy-dsr-guide).
