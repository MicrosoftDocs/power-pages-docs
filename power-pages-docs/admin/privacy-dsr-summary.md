---
title: Respond to Data Subject Rights (DSR) requests for Power Pages customer data
description: Review personal data request information for Microsoft Power Pages.
author: PramithaU
ms.reviewer: dmartens
ms.topic: overview
ms.date: 10/08/2024
ms.author: pudupa
search.audienceType: 
  - admin
contributors:
- DanaMartens 
---

# Respond to Data Subject Rights (DSR) requests for Power Pages customer data

The European Union (EU) General Data Protection Regulation (GDPR) gives significant rights to individuals regarding their data. Learn more about GDPR in [General Data Protection Regulation Summary](/compliance/regulatory/gdpr). This resource includes an overview, key terms, an action plan, and a readiness checklist to help you meet your obligations under GDPR when using Microsoft products and services.

Learn more about GDPR and how Microsoft supports it and our customers affected by it:

- The [Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy/gdpr-overview) provides general information, compliance best practices, and documentation helpful to GDPR accountability, such as Data Protection Impact Assessments, Data Subject Requests, and data breach notification.

- The [Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) provides information about how Microsoft services help support compliance with GDPR.

This article provides examples of steps you can take to support privacy compliance when using Power Pages. You learn how to use Microsoft products, services, and administrative tools to help controller customers find, access, and act on personal data in the Microsoft cloud in response to DSR requests.

The following actions are covered in this article:

| Action   | Description |
|----------|-------------|
| **Discover** | Use search and discovery tools to more easily find customer data that might be the subject of a DSR request. Once potentially responsive documents are collected, you can perform one or more of the following DSR actions to respond to the request. Alternatively, you might determine that the request doesn't meet your organization's guidelines for responding to DSR requests. |
| **Access** | Retrieve personal data that resides in the Microsoft cloud and, if requested, make a copy of that data available to the data subject. |
| **Rectify** | Make changes or implement other requested actions on the personal data, where applicable. |
| **Restrict** | Restrict the processing of personal data, either by removing licenses for various online services or turning off the desired services where possible. You can also remove data from the Microsoft cloud and retain it on-premises or at another location. |
| **Delete** | Permanently remove personal data that resides in the Microsoft cloud. |
| **Export** | Provide an electronic copy (in a machine-readable format) of personal data to the data subject. |

## Discover

The first step in responding to a DSR request is to find the personal data that is the subject of the request. You need to first determine the type of user for which the request is made.

The step of finding and reviewing the personal data at issue helps you determine whether a DSR request meets your organization's requirements for honoring or declining a DSR request. For example, after reviewing the personal data in question, you might determine that the request doesn't meet your organization's requirements because it could negatively affect the rights and freedoms of others.

### Step 1: Identify the type of user for which data is requested

Power Pages has two types of users accessing its services:

| Type of User | Experience used to access Power Pages service |
|--------------|----------------------------------------------|
| Maker/Admin  | Power Pages Maker Studio, Power Platform Admin Center, Power Pages Portal Management App, Power Pages Management App, Power Pages VS Code Extensions, Power Pages Admin API’s, Dataverse API |
| Website user/visitor     | Website hosted using Power Pages Service     |

### Step 2: Find personal data for the user in Power Pages

Once you identify the type of user, review the types of Power Pages resources that contain personal data for a specific user type:

#### Maker/Admin

| Resources containing personal data | Purpose |
|------------------------------------|---------|
| System Generated Telemetry logs    | Logging that captures historical events within the service. |
| Environment                        | An environment is a space to store, manage, and share your organization's business data, apps, and flows. Learn more in [Power Platform environments overview](/power-platform/admin/environments-overview). |
| Power Pages Maker/Admin Settings   | Power Pages stores several user preferences and settings that are used to deliver the Maker Portal and Admin Portal experience. |

#### User

| Resources containing personal data | Purpose |
|------------------------------------|---------|
| System Generated Telemetry logs    | Logging that captures historical events within the service. |
| Environment                        | An environment is a space to store, manage, and share your organization's business data, apps, and flows. Learn more in [Power Platform environments overview](/power-platform/admin/environments-overview). |

Learn more about how you can use these experiences to find personal data for a specific user for each of these types of resources in [Responding to Data Subject Rights (DSR) requests to export Power Pages customer data](privacy-dsr-export.md).

After you find the data, you can then perform the specific action to satisfy the request by the data subject.

## Rectify

If a data subject asks you to rectify the personal data that resides in your organization's data, you and your organization must determine whether it's appropriate to honor the request. Rectifying data might include editing, redacting, or removing personal data from a document or other type of item.

You can use Microsoft Entra to manage the identities (personal data) of your users within Power Apps. Enterprise customers can manage DSR rectify requests by using the limited editing features within a given Microsoft service. As a data processor, Microsoft doesn't offer the ability to correct system-generated logs, because they reflect factual activities and constitute a historical record of events within Microsoft services.

## Restrict

Data subjects might request that you restrict processing of their personal data. Microsoft provides both preexisting application programming interfaces (APIs) and user interfaces (UIs). These experiences provide the enterprise customer's Power Platform admin the capability to manage such DSRs through a combination of data export and data deletion. A customer might request:

- Export an electronic copy of the personal data of the user, including:
  - accounts
  - system-generated logs
  - associated logs
- Delete the account and associated data residing within Microsoft systems.

## Export

The "right of data portability" allows a data subject to request a copy of their personal data in an electronic format (structured, commonly used, machine-readable, and interoperable) that can be transmitted to another data controller.

Learn more in [Responding to Data Subject Rights (DSR) requests to export Power Pages customer data](privacy-dsr-export.md).

## Delete

The "right to erasure" by the removal of personal data from an organization's customer data is a key privacy protection. Removing personal data includes system-generated logs but not audit-log information.

Power Apps allows users to build line-of-business applications that are a critical part of your organization's day-to-day operations. When a user leaves your organization, you need to manually review and determine whether to delete certain data and resources that they created. Other customer data is automatically deleted whenever the user's account is deleted from Microsoft Entra ID.

Learn more in [Responding to Data Subject Rights (DSR) requests to delete Power Pages customer data](privacy-dsr-delete.md).
