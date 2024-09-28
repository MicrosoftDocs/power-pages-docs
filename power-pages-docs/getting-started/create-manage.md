---
title: Create a site with Power Pages
description: Learn how to create a site with Power Pages.
author: danamartens
ms.topic: conceptual
ms.custom: 
ms.date: 07/09/2024
ms.subservice:
ms.author: tbhagwat
ms.reviewer: danamartens
contributors:
    - DanaMartens
---

# Create a site with Power Pages

Customize and design your site using the Power Pages design studio. 

> [!TIP]
> 
> - You can [use Copilot to help you create your site in Power Pages](create-site-copilot.md). For more information, see [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md).
> - We've created a series of tutorials and videos for you to learn to use Power Pages. You'll start with a simple site and progressively add components and features as your business requires. For more information, go to [Power Pages tutorials](tutorial-overview.md).

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

    The first time you visit the site, select the **Try it for free** button to [sign up for a free, 30-day trial](trial-signup.md).

1. Select the [Microsoft Dataverse environment](/power-platform/admin/environments-overview) where you'd like to create a site.

    :::image type="content" source="media/default-template/choose-environment.png" alt-text="Selecting a Microsoft Dataverse environment.":::

    > [!NOTE]
    > It is not recommended to create a site in the [*default* environment](/power-platform/admin/environments-overview#the-default-environment). This environment is shared across all the users in the tenant and creating your site here risks sharing data with other users unintentionally.

1. On the home page, select **+ Create a site**.

1. Review the available templates. For more details about each template, hover over the template and choose **Preview template**. Follow the different views across devices to preview the template experience.

    :::image type="content" source="media/default-template/default-template.png" alt-text="The design studio GUI with default template selected.":::

    > [!TIP]
    > If none of the business need templates match what you're looking for, choose one of the **Starter layout** templates with cross-industry solutions, or choose **Blank page** to customize the website from scratch. More information: [Power Pages templates](../templates/index.md)

1. After you've found the best template for your business needs, select **Choose this template**.

1. Validate the default site name and web address, then select **Done**.

    :::image type="content" source="media/default-template/provision-site.png" alt-text="The design studio with site provisioning options displayed.":::

    > [!NOTE]
    > It might take a few moments for your new site to be provisioned. You'll be able to modify the name and web address later.

1. After the site is created, you can begin to edit or preview your site.

    :::image type="content" source="media/default-template/manage-site.png" alt-text="Power Pages home page with site created.":::

## Roles and permissions
 There are several required roles and permissions in Microsoft Power Platform. You'll need:
 
 - A user account with [Read-Write Access Mode](/power-pages/admin/admin-roles#read-write-access-mode)
 - [System administrator](/power-pages/admin/admin-roles#system-administrator) role
 - [Permissions to register an app](/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) in Microsoft Entra

If [website creation is disabled in the tenant](/power-apps/maker/portals/control-portal-creation), users will also need at least one of the following roles to create a website:

 - [Dynamics 365 administrator](/power-pages/admin/admin-roles#dynamics-365-administrator)
 - [Power Platform administrator](/power-pages/admin/admin-roles#power-platform-administrator)

## Additional information

When you create a site with a new trial environment, the site metadata for all the [templates](../templates/index.md) is preloaded. It appears as website records in the [Portal Management app](../configure/portal-management-app.md).

:::image type="content" source="media/default-template/websites.png" alt-text="Website records in Portal Management app.":::

## Discover Power Pages for website creation

The following video is an overview of using Power Pages to create websites.<br />

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE557dn]

## Next steps

[Use design studio](use-design-studio.md)

