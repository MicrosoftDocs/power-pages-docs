---
title: Provisioning issues
description: Learn about Site Checker diagnostics results for provisioning issues.
author: neerajnandwana-msft

ms.topic: concept-concept-article
ms.custom: 
ms.date: 03/03/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - dileepsinghmicrosoft
---

# Provisioning issues

In this article, you'll learn about Site Checker diagnostics results for site provisioning issues.

## Profile form isn't available for contact table

The profile page is one of the common pages used in your website for all profile-related issues. This page shows a form component that lets users update their profiles. The form on this page comes from the **Profile Web Page** main form available in the contact table. This form is created in your Microsoft Dataverse environment when the website is provisioned. This error is displayed when the **Profile** form is either deleted or disabled in your website. This form is mandatory and deleting or disabling this form can break the whole website, displaying a runtime error. This is an irreparable state and requires the website to be reinstalled in the environment.

### See also

[Run Site Checker](site-checker.md)


