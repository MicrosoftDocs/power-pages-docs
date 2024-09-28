---
title: Download public key of a website
description: Learn how to download public key of a website.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/16/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Download public key of website

The public key of a website is used to configure Live Assist for customer engagement apps (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, and Dynamics 365 Project Service Automation) to work with authenticated visitors for a website. [Live Assist](https://support.liveassistfor365.com/hc/articles/360006210033-What-is-Live-Assist-for-Microsoft-Dynamics-365-), provides a chat solution through which users can embed live chat assistance in their website. More information on how to use the public key to embed a chat on a website: [Setting up Authenticated Chats for Messaging](https://support.liveassistfor365.com/hc/en-us/articles/8684405210391-Setting-up-Authenticated-Chats-for-Messaging-Microsoft-Power-App-Portals-)

> [!TIP]
> To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](admin-roles.md).

1. Ensure you have installed a [custom certificate](/power-apps/maker/portals/admin/manage-custom-certificates).

1. Sign in to the website with a user that has been assigned the **Administrator** [webrole](../security/create-web-roles.md).

1. Get the public key by going to the URL: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> If the website is currently being provisioned or the package install is not finished in the organization, an error is displayed if you try to download the public key. You must wait until website provisioning is complete and the website is up and running.

