---
title: Power Pages lifecycle
description: Learn about the Power Pages lifecycle, including trial, production, suspended, and deleted stages, and how to convert a trial site to production.
author: neerajnandwana-msft
ms.topic: concept-article
ms.custom:
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:02/20/2025
ms.date: 04/23/2026
ms.subservice: null
ms.author: nenandw
ms.reviewer: danamartens
contributors:
  - neerajnandwana-msft
ms.collection:
  - ai-assisted
---

# Power Pages lifecycle

A Power Pages site is always created as a trial, in a production, sandbox, developer, or trial environment. A trial site is useful for trying out its capabilities at no cost. If the trial site is created in a trial environment, the trial site expires after 30 days or when your trial environment expires, whichever is earlier. If the trial site is created in a nonexpiring environment (for example, production or sandbox), your trial site expires after 90 days.

After it expires, the site is suspended and shut down. Seven days after suspension, the trial site host is deleted. You're notified at every stage of the site lifecycle (nearing suspension, suspended, deleted, and converted from trial to production) through email and toast notifications.

> [!NOTE]
> - The process of [converting](convert-site.md) a website is a different process than [migrating](migrate-site-configuration.md) a website.
> - Note the difference between developer, trial, and production **websites** and developer, trial, sandbox, and production **environments**.

As an administrator, you can **convert** a trial or suspended site to a production site. When converting a site from trial to production, you must ensure that the Power Platform environment is also a production or sandbox environment. You can't convert a trial site to production in a trial or developer Power Platform environment. If you delete the Power Platform environment in which a trial site is created, the site is also deleted.

You can't [convert](convert-site.md) a developer site to a production site, but you can [migrate](migrate-site-configuration.md) a trial, developer, or production site to another site on the same or another environment. A production site needs to be provisioned on a sandbox or production environment.

### Understanding site lifecycle stages

The following diagram explains various stages that a Power Pages site goes through, from creation until deletion.

:::image type="content" source="media/lifecycle/lifecycle.png" alt-text="Power Pages lifecycle stages.":::

## Trial site

Every site begins as a trial site that eventually expires based on the type of environment it was created in. You can convert it to a production site from the Power Platform admin center if you have the required licenses. More information: [Convert a website from trial to production](convert-site.md#convert-a-website-from-trial-to-production)

> [!NOTE]
> - When a trial site is created in a trial environment, it expires after 30 days or when the trial environment expires, whichever is earlier. If your environment expires before the trial site expires, you lose access to your trial site.
> - When a trial site is created in a non-expiring environment like production or sandbox, the trial site expires after 90 days, giving you more time to build your site in a non-expiring environment.

To convert a trial website to a production website, the environment needs the required licensing for external users or a license for internal users. More information: [Power Apps and Power Automate licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) and [Power Pages licensing](/power-platform/admin/powerapps-flow-licensing-faq#power-pages).

> [!IMPORTANT]
> Once the website is converted to production, you should ensure that the website is appropriately licensed with authenticated or anonymous user capacity corresponding to the expected user volume or enabled for pay-as-you-go. Scaling of the website resources is done automatically based on the Power Pages licensing capacity assigned to the environment. Not having appropriate licenses assigned can result in degraded performance. For information on how to allocate authenticated or anonymous user capacity, see [Allocate or change capacity in an environment](/power-platform/admin/capacity-add-on#allocate-or-change-capacity-in-an-environment).

## Suspended site

You see notifications in the Power Platform admin center about your trial site's expiration. Trial sites expire after 30 days (in trial environments) or 90 days (in production or sandbox environments). If you don't convert your site to production during the trial period, the site is shut down and suspended. Similarly, if you don't edit your developer site or it's inactive for 90 days, it's suspended.

You can't access your site after it expires. However, you can still convert the suspended site to production within seven days of suspension.

## Deleted site

If you don't convert your site to production within the seven-day suspension period, the site host is deleted. Similarly, if you don't reactivate your developer site within the seven-day suspension period, the site host is deleted. The site data isn't deleted from the environment; however, the space used by the site in the environment is released, and you can create a new site.

## Next steps

- [Power Pages templates](../templates/index.md)
- [Create a site](../getting-started/create-manage.md)

### See also

- [Use developer websites](../getting-started/developer-sites.md)
- [Migrate website configuration](migrate-site-configuration.md)
- [Convert a website from trial to production](convert-site.md#convert-a-website-from-trial-to-production)
- [Convert an existing website to capacity-based model](convert-site.md#convert-an-existing-website-to-capacity-based-model)
- [Power Pages connectivity to a Microsoft Dataverse](connectivity.md)
- [Power Pages architecture](architecture.md)
- [Reactivate sites](reactivate-website.md)
