---
title: Responding to Data Subject Rights (DSR) requests to export Power Pages customer data
description: Walkthrough of how to respond to Data Subject Rights (DSR) requests to export Power Pages customer data.
ms.reviewer: dmartens
ms.topic: overview
ms.date: 10/08/2024
ms.author: pudupa
search.audienceType: 
  - admin
contributors:
- DanaMartens 
---

# Responding to Data Subject Rights (DSR) requests to export Power Pages customer data

This article discusses the experiences that Power Pages offers when exporting personal data for a specific user.

## Maker/Admin

1. **System generated telemetry logs:**

    Learn how to get this data in [Responding to DSR requests for system-generated logs in Power Apps, Power Automate, and Microsoft Dataverse](/power-platform/admin/powerapps-privacy-dsr-guide-systemlogs).

1. **Environment:**

    All the data stored in environments are stored within Dataverse. Learn more about how to respond to DSR requests for this data in [Responding to Data Subject Rights (DSR) requests for Dataverse customer data](/power-platform/admin/dataverse-privacy-dsr-guide).

1. **Power Pages Maker/Admin settings:**

    Learn how to get this data in [Responding to Data Subject Rights (DSR) requests to export Power Apps customer data](/power-platform/admin/powerapps-privacy-export-dsr).

## Website user/visitor

1. **System generated telemetry logs:**

    Learn how to get this data in [Responding to DSR requests for system-generated logs in Power Apps, Power Automate, and Microsoft Dataverse](/power-platform/admin/powerapps-privacy-dsr-guide-systemlogs).

1. **Environment:**

    All the data stored in environments are stored within Dataverse. By default, all Power Pages customer data is stored in the following tables in Dataverse:

    - Contact
    - Account
    - Web Form Sessions (or Advanced Form Sessions)
    - Power Pages log (if Web Application Firewall logs are enabled)

    However, you can extend this configuration. It's essential to establish policies and procedures for tracking where each individual's personal data is stored, ensuring you're ready to handle DSR requests.

    Learn how to respond to DSR requests for this data in [Responding to DSR requests for Microsoft Dataverse customer data](/power-platform/admin/dataverse-privacy-dsr-guide).
