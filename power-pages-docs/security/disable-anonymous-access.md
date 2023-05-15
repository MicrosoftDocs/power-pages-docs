---
title:  Governance control to disable anonymous access
description: Learn how you can disable anonymous access at the site level.
author: nageshbhat-msft
ms.topic: conceptual
ms.custom: 
ms.date: 05/15/2023
ms.author: vamseedilli
ms.reviewer: kkendrick
contributors:
    - nageshbhat-msft
    - nickdoelman
    - ProfessorKendrick
---

# Governance control to disable anonymous access

As an administrator, you can disable anonymous access to your websites in your tenant, preventing accidental exposure of sensitive data.

## Admin Experience

You can disable and enable anonymous access to your websites using the Power Platform admin center.

1. Go to the [Power Platform admin center](https://aka.ms/ppac).

1. From the left-hand menu, navigate to **Resources** and choose **Power Pages Sites**.

1. Select **Governance Controls** from the top ribbon menu.  

    :::image type="content" source="media/disable-anonymous-access/governance-controls.png" alt-text="Governance controls.":::

1. Choose **Disable anonymous access** from the list.  

1. A slide-out panel appears on the right. You can disable anonymous access for the following:

    - None of the sites
    - Specific sites
    - All sites except specific sites
    - All sites

1. Selecting **Specific sites** or **All sites except specific sites** a list of websites appear that you can select to be disabled or enabled. Select the sites and choose **OK**.

1. Select **Save**. A message confirming success appears in green below the Governance Controls ribbon menu.  

## Maker experience

Once an admin completes the steps in the previous section, anonymous users are disabled for new table permissions.

:::image type="content" source="media/disable-anonymous-access/anonymous-access-disabled.png" alt-text="Disable anonymous access.":::

For existing sites where anonymous access is given, a banner error message is displayed indicating a **Data protection policy update** has been applied.

## End user experience

End users see a message explaining that they don't have permission to view records and prompting them to sign in.

