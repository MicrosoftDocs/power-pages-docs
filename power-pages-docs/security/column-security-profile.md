---
title: Column security profile (preview)
description: Column security profile in Power Pages controls access to sensitive columns within records. Learn how to configure security profiles to protect your site data.
author: nageshbhat-msft
ms.author: nabha
ms.reviewer: smurkute
ms.date: 07/09/2026
ms.topic: concept-article
---

# Column security profile (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

After you configure the web role to set up the tables and record level permission, you might need to control the access to sensitive columns within the record. **Column security profile** is a feature that lets you control access to sensitive columns within records on your Power Pages site.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

Before you can use column security profiles, your site must be enabled for the enhanced authorization model. For more information, see [Enable enhanced authorization](unify-pages-security-with-dataverse.md#enable-enhanced-authorization).


> [!IMPORTANT]
> - Column security profiles are supported only on sites that use the enhanced authorization model.
> - When you enable enhanced authorization for a site, manage the profile at [Power Platform Admin Center](/power-platform/admin/field-level-security).
> - Column security applies to all components and APIs used in Power Pages, including but not limited to Web API, forms, and list components.

## Assign column security profiles to site users

You can assign one or more security profiles to site users from the security workspace as follows:

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) and open the site for edit in studio.

1. Navigate to the **Security** workspace and then to **Column Security Profile**.

1. Select the profile.

   Select the appropriate button to add or remove users from the profile.
:::image type="content" source="Media/unify-pages/column-security.png" alt-text="Screenshot of powere pages studio showing column security profiles":::

> [!NOTE]
> Anonymous users represents all users accessing the site without authentication.

### See also

[Enable enhanced authorization (preview)](unify-pages-security-with-dataverse.md)  
[Implement privacy protections](../configure/implement-privacy.md)  
[Configuring table permissions](table-permissions.md)
