---
title: Create a site with Power Pages
description: Learn how to create a site with Power Pages using the design studio and customize it to meet your business needs.
author: dmartens
ms.topic: conceptual
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/21/2025
ms.date: 04/21/2025
ms.subservice: null
ms.author: tbhagwat
ms.reviewer: danamartens
contributors:
  - DanaMartens
---

# Create a site with Power Pages

Use the Power Pages design studio to customize and design your site. 

> [!TIP]
>
> - [Use Copilot to help you create your site in Power Pages](create-site-copilot.md). For more information, see [Overview of AI-powered and Copilot features in Power Pages](../configure/ai-copilot-overview.md).
> - We created a series of tutorials and videos for you to learn to use Power Pages. You start with a simple site and progressively add components and features as your business requires. For more information, go to [Power Pages tutorials](tutorial-overview.md).

1. Go to [Power Pages](https://make.powerpages.microsoft.com/).

    When you visit the site for the first time, select the **Try it for free** button to [sign up for a free, 30-day trial](trial-signup.md).

1. Select the [Microsoft Dataverse environment](/power-platform/admin/environments-overview) where you'd like to create a site.

    :::image type="content" source="media/default-template/choose-environment.png" alt-text="Selecting a Microsoft Dataverse environment.":::

    > [!NOTE]
    > It isn't recommended to create a site in the [*default* environment](/power-platform/admin/environments-overview#the-default-environment). This environment is shared across all the users in the tenant and creating your site here risks sharing data with other users unintentionally.

1. On the home page, select **Start with a template**.

1. Review the available templates. For more details about each template, hover over the template and choose **Preview template**. Follow the different views across devices to preview the template experience.

    :::image type="content" source="media/default-template/default-template.png" alt-text="The design studio GUI with default template selected.":::

    > [!TIP]
    > If none of the business need templates match what you're looking for, choose one of the **Starter layout** templates with cross-industry solutions, or choose **Blank page** to customize the website from scratch. More information: [Power Pages templates](../templates/index.md)

1. After you find the best template for your business needs, select **Choose this template**.

    > [!TIP]
    > If you encounter an error message that reads "Sorry, there's been a disconnect", navigate to Power Pages in your environment via `https://make.powerpages.microsoft.com/environments/{environment_id}/portals/home`, replacing `{environment_id}` with your environment ID. From there, you can choose "Start with a template" or "Start from blank" to create your site.
  
1. Check the default site name and web address, and then select **Done**.

    :::image type="content" source="media/default-template/provision-site.png" alt-text="The design studio with site provisioning options displayed.":::

    > [!NOTE]
    > It might take a few moments for your new site to be provisioned. You're able to modify the name and web address later.

1. After the site is created, start editing or previewing your site.

## Roles and permissions

There are some required roles and permissions in Microsoft Power Platform. You need:

 - A user account with [Read-Write Access Mode](/power-pages/admin/admin-roles#read-write-access-mode)
 - [System administrator](/power-pages/admin/admin-roles#system-administrator) role
 - [Permissions to register an app](/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) in Microsoft Entra

If [website creation is disabled in the tenant](/power-apps/maker/portals/control-portal-creation), users need at least one of the following roles to create a website:

 - [Dynamics 365 administrator](/power-pages/admin/admin-roles#dynamics-365-administrator)
 - [Power Platform administrator](/power-pages/admin/admin-roles#power-platform-administrator)

## Additional information

When you create a site with a new trial environment, the site metadata for all the [templates](../templates/index.md) is preloaded. It appears as website records in the [Portal Management app](../configure/portal-management-app.md).

:::image type="content" source="media/default-template/websites.png" alt-text="Website records in Portal Management app.":::

## Discover Power Pages for website creation

This video provides an overview of how to use Power Pages to create websites.<br />

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=5a509a83-addc-4851-ab2b-58c24ebe0cef]

## Next steps

[Use design studio](use-design-studio.md)
