---
title: Import metadata translation
description: Instructions to import metadata translation.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 03/19/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
---

# Import metadata translation

When you provision a website, the Power Pages related solutions are installed on the environment. During the installation of solutions, the solution metadata translations (for example, field name, form name, and view name) are installed only for the languages currently activated in the organization. If you activate a new language in the future, the metadata will not be installed automatically for the newly activated language. To get the metadata translation for the newly activated language, you must import the metadata translation from the Power Platform admin center.

## To import metadata translation

> [!TIP]
> To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](admin-roles.md).

1. Open the [Power Platform admin center](admin-overview.md).

1. Under the **Resources** section, select **Power Pages sites**.

1. Select the site, and choose **Manage** from the main menu.

1. On the website details page, from the main menu, select the ellipse (**...**) and then choose **Metadata translations**.

1. A confirmation window is displayed asking whether to update the portal solutions.

1. Select **Update**. The solutions will be updated with the latest metadata translation.

> [!Note]
> - If the latest version of a Power Pages package is available, it isn't updated. The solutions are updated in the same version. To upgrade your solutions based on the latest available packages, see [Update solution](update-solution.md).
> - If a user has modified any data in Microsoft Dataverse, the existing data will not be overwritten during the update.
> - If the solutions are being installed, the solution update cannot be triggered.


