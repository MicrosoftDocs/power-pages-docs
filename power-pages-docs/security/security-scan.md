---
title: Run security scan (preview)
description: Learn how to identify and address security vulnerabilities in Power Pages with security scan.
author: ProfessorKendrick
ms.topic: how-to
ms.custom: 
ms.date: 05/28/2024
ms.subservice:
ms.author: avishwakarma
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Run security scan (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Use Power Pages security scan to enhance your site's resilience by identifying and addressing vulnerabilities, safeguarding it against potential threats and ensuring a secure online environment for users.

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

## Prerequisites

- Power Pages Core version 1.0.2403.2 or later.

## Run a security scan

Use the [Security workspace](../getting-started/use-security-workspace.md) to run the scan. You can also review the [third party notice](https://go.microsoft.com/fwlink/?linkid=2271056) prior to running the security scan.

To run a security scan:

1. Select the **Run Deep Scan** button.  

    > [!NOTE]
    > By default, security scan only scans anonymous pages. To include authenticated pages in the scan: 
    > 1. Select the check box next to **Include authenticated pages in scan**. A notification window appears in the workspace.
    > 2. Enter your user name and password, then select **Continue**.

1. Select the **Continue** button to begin the scan.

    You can cancel the scan at any time by returning to the Security workspace and selecting the **Cancel scan** button.

Once the scan is completed, you receive an email. After you receive the email confirmation, you can view the scan report summary by returning to the **Run scan** section of the Security workspace.

## Review the summary report 

The summary report includes a list of failed checks and corresponding alerts, and a description of how to fix the alerts. You can optionally download the report as a PDF. Report summaries for security scan are only supported in English-US language.

