---
title: "Tutorial: Configure authorized access to your site"
description: Learn how to configure Azure AD B2C authentication provider to your Power Pages site.
author: nickdoelman
ms.topic: tutorial
ms.custom: template-tutorial
ms.date: 04/21/2022
ms.subservice:
ms.author: ndoelman 
ms.reviewer: 
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Tutorial: Configure authorized access to your site

Power Pages provides a way to allow your external stakeholders to get self-service access to information and data from your business systems.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Provide user access to your Power Pages sites using an identity provider.

## Prerequisites

- A Power Pages subscription or trial. [Get a Power Pages trial here](trial-signup.md).
- A Power Pages site created. [Create a Power Pages site](create-manage.md).

## [Section 1 heading]
<!-- Introduction paragraph -->

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).
1. In design studio, select **Setup**.  
1. Under **Authentication**, choose **Identity Providers**.
1. Select **Configure**.
1. Ensure **Azure Active Directory B2C** is selected and then choose **Next**.
1. Choose a subscription.
1. Create a resource group.
1. Select a country.
1. Select next.
1. Confirm the defaults and then select **Next**.
1. Select defaults (new policy) and then select **Create**.
1. Select **Close**.
1. Select the ellipses next to **Local Sign In**.
1. Choose **Disable**.

Now your users can sign in, register, or redeem an invitation to your site using the configured identity provider.  

You can preview this functionality by visiting a portal and selecting **Sign In**, then select **Azure AD B2C**.  The default Azure AD B2C sign-in screen will appear.

## Next steps

Advance to the next article to learn how to upload your own custom CSS file to your site.
> [!div class="nextstepaction"]
> [Next steps](tutorial-add-custom-style.md)

