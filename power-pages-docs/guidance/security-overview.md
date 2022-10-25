---
title: Security guidance overview
description: Learn about Power Pages' security capabilities.
author: kkendrick
ms.topic: guidance
ms.custom: 
ms.date: 10/25/2022
ms.author: kkendrick
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Security guidance overview

Power Pages offers enhanced control, protection, and security for administrators, website makers, and website visitors. It empowers makers to extend business data and processes to external users securely and helps ensure compliance. As a platform, it offers comprehensive compliance coverage across global, regional, government, and industry-specific compliance standards, making it a trusted Low code application platform. Business data which website users interact with is securely stored in [Microsoft Dataverse](https://docs.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-intro). Power Pages tightly integrates with products and capabilities such as Power Apps, Power Automate, Power Virtual Agents, Power BI, and Microsoft SharePoint.

> [!NOTE]
> Security is enabled by fundamental architectural building blocks that offer layers of protection. It is important to review the architecture of the Power Pages platform. The [Power Pages architecture white paper](https://aka.ms/PowerPagesArchitecture) describes the platform's capabilities, building blocks, and architecture.

## End-to-end protection

Power Pages delivers end-to-end protection designed to address our customers' biggest challenges across areas.

### Authentication

- How do I securely engage internal and external partners, customers, and community users?

- How do I extend business data and business processes externally?

### Authorization

- How do I control who has access to what level of business data?

- How do I control access to data securely and differently for anonymous and authenticated users?

How do I onboard external users to my application securely?

### Data Storage

- How do I ensure that business data is always protected & secured?

- How is the data stored? How is it encrypted? What controls do I have on my data?

#### Data location

For details on location of data, refer to data section in the [Microsoft Privacy and Security terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) and to the [Data Protection Addendum](https://aka.ms/DPA). 

### Application Security

- How can I restrict business data being accessed by geography, demography or by a set of users?

- How do I secure my application against vulnerabilities, attacks, and malicious actors?

- What security capabilities do I need to keep in mind when creating external facing applications?

### Governance

- What governance controls do I need to build to ensure that I can control what type of applications my organizational users can create? How do I control who can create these applications?

- How do I audit who conducts what operations? How do I react quickly if there's suspicious activity on the service?

## Enterprise security and compliance

Many national security agencies, community services, financial institutions, and health care providers entrust Power Pages with their most sensitive information. Enterprise security and compliance are at the core of Power Pages platform as it offers Secure by Design, Secure by Default, and Defense-in-Depth approaches to application building, deployment, and management.

The Power Pages service is governed by the [Commercial Licensing Terms (microsoft.com)](https://www.microsoft.com/licensing/terms/) and the [Microsoft Enterprise Privacy Statement](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). 

For compliance information, the [Microsoft Trust Center](https://www.microsoft.com/trustcenter) is the primary resource for Power Pages. Learn more about compliance in the [Microsoft compliance offerings](https://docs.microsoft.com/en-us/compliance/regulatory/offering-home).

### Zero Trust approach

Power Pages is built on a "Zero Trust" security approach- it assumes that activity on the platform, even by trusted users may be an attempted breach, hence activities/accesses are explicitly verified using a robust authorization model. Access to website data and website content honors the Least Privilege Access model. Security is a shared responsibility- Power Pages provides considerable advantages for organizational security and compliance efforts, and at the same time, the tools and capabilities must be used in a way that protects users and organizational data.

### The Security Development Lifecycle (SDL)

The Power Pages service follows the Security Development Lifecycle (SDL), strict security practices that support security assurance and compliance requirements. The SDL helps developers build more secure software by reducing the number and severity of vulnerabilities in software, while reducing development cost. Learn more at [Microsoft Security Development Lifecycle Practices](https://www.microsoft.com/securityengineering/sdl/practices).