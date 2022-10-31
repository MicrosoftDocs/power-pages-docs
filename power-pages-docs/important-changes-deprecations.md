---
title: Important upcoming changes and deprecations in Power Pages
description: Learn about the important changes, including deprecations, coming soon to Power Pages.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 09/09/2022
ms.subservice: 
ms.author: sandhan
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - sandhangitmsft
    - dileepsinghmicrosoft
    - nageshbhat-msft
    - ProfessorKendrick
---

# Important upcoming changes and deprecations in Power Pages

The announcements for changes and deprecations described in this article apply to Power Pages. Makers, developers, and IT pros can use this information to prepare for future releases.

> [!IMPORTANT]
> *Deprecated* means that we intend to remove the feature or capability from a future major release. The feature or capability will continue to work and is fully supported until it's officially removed. This deprecation notification can span a few months or years. After it's removal, the feature or capability no longer work. This notice is to allow you sufficient time to plan and update your code before the feature or capability is removed.

## Controlling site visibility changes in Power Pages

Starting October 2022 with website version 9.4.9.xx, any new site created in Power Pages or Power Apps portals will be private by default. Only makers or people in the organization granted permission by makers will have website access, making Power Pages sites secure. This feature will provide another layer of security using Azure Active Directory authentication to prevent accidental leaks of partially developed website data and design. When a website is ready to go-live, the site visibility can be changed to public making it accessible to everyone over the internet anonymously or secured with identity providers.  

At launch, users with the system administrator role along with [service admins](/power-platform/admin/use-service-admin-role-manage-tenant) will by default have privilege to change site visibility status (private to public or vice versa). 

> [!NOTE]
After February 1, 2023 system administrators will not be able to change site visibility when the tenant-level setting is null.  To prevent this, set the value for the tenant level setting to either TRUE or FALSE.

### See also

[Important changes (deprecations) coming in Power Apps, Power Automate, and customer engagement apps](/power-platform/important-changes-coming)

