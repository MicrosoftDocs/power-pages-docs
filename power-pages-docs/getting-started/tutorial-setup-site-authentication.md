---
title: "Tutorial: Configure authorized access to your site"
description: Learn how to configure Azure AD B2C authentication provider to your Power Pages site.
author: dmartens
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 06/02/2022
ms.subservice:
ms.author: dmartens 
ms.reviewer: 
contributors:
---

# Tutorial: Configure authorized access to your site

Power Pages provides integration to multiple authentication providers to allow secure access to external users to your site. In this tutorial, you'll see how to use the Setup workspace to configure Azure Active Directory Business-to-Consumer (Azure AD B2C) as an authentication provider.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Provide user access to your Power Pages sites using Azure AD B2C as an identity provider.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).
- An Azure subscription and administrative rights to configure Azure AD B2C

## Configure authorized access to your site

Setting up an external authentication provider will allow you to provide access to your site and provide the mechanism for end users to be able to reset their passwords and other information without administrator intervention.

This video provides an overview of authentication in Power Pages.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=93986f06-7a78-4fcd-8a30-57d849557c04]

This video provides an overview of the steps to configure authentication providers.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=8f3f4cd7-ef83-41f2-b637-2029e60d61bf]

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

1. In design studio, select **Security**.  
    - Under **Manage**, select **Identity Providers**.
    :::image type="content" source="media/tutorial/setup.png" alt-text="Choose an identity provider from the Setup menu.":::

1. Select **Configure**.

    - Ensure **Azure Active Directory B2C** is selected and then choose **Next**.
    :::image type="content" source="media/tutorial/azure-b2c.png" alt-text="Select a login provider.":::

1. Fill in the details.

    - Choose an Azure subscription.
    - Create an Azure resource group.
    - Select a country.
    - Select **Next**.
    :::image type="content" source="media/tutorial/resource-group.png" alt-text="Enter details to configure identity provider.":::

1. Confirm the defaults and then select **Next**.

1. Select defaults (new policy) and then select **Create**.

    :::image type="content" source="media/tutorial/create-button.png" alt-text="The create button.":::

1. Select **Close**.

1. Select the ellipses next to **Local Sign In**.

1. Choose **Disable**.

Now your users can sign in, register, or redeem an invitation to your site using Azure AD B2C.  

You can preview this functionality by visiting a portal and selecting **Sign In**, then select **Azure AD B2C**.  The default Azure AD B2C sign-in screen will appear.

:::image type="content" source="media/tutorial/azure-ad-b2c.png" alt-text="Azure AD B2C.":::

## Next steps

Learn how to protect your pages using page permissions in the next tutorial
> [!div class="nextstepaction"]
> [Set up page permissions](tutorial-setup-page-permissions.md)
