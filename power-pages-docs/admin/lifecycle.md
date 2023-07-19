---
title: Power Pages lifecycle
description: Information about Power Pages lifecycle and converting it from trial to production.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 05/15/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Power Pages lifecycle

A Power Pages website is always created as a trial. A trial website, which expires after 30 days, is useful for trying out its capabilities at no cost. After it expires, the website is suspended and shut down. Seven days after it's suspended, the trial website host is deleted. You'll be notified at every stage of the website lifecycle; nearing suspension, suspended, deleted, and converted from trial to production; through toast notifications and email.

> [!NOTE]
> - The process of [converting](convert-site.md) a website is a different process than [migrating](migrate-site-configuration.md) a website.
> - Note the difference between developer, trial, and production **websites** and developer, trial, sandbox, and production **environments**.

As an administrator, you can **convert** a trial or suspended website to a production website. When converting a website from trial to production, you must ensure that the Power Platform environment is also a production or a sandbox environment. You can't convert a trial website to production in a trial or developer Power Platform environment. If you delete the Power Platform environment in which a trial website is created, the website is also deleted.

You can't [convert](convert-site.md) a developer website to a production website, but you can [migrate](migrate-site-configuration.md) a trial, developer, production website to another trial, developer, or production website on the same or another environment. Note that a production website will need to be provisioned on a sandbox or production environment.

### Understanding website lifecycle stages

The following diagram explains various stages that a Power Pages website goes through, from creation until deletion.

:::image type="content" source="media/lifecycle/lifecycle.png" alt-text="Power Pages lifecycle stages.":::

Let's understand each website lifecycle stage.

## Trial website

Every website begins as a trial website that expires after 30 days. You can convert it to a production website from the Power Platform admin center if you have the required licenses. More information: [Convert a website from trial to production](convert-site.md#convert-a-website-from-trial-to-production)

To convert a trial website to a production website, the environment should have required licensing for external users or a license for internal users. More information: [Power Apps and Power Automate licensing FAQs](/power-platform/admin/powerapps-flow-licensing-faq) and [Power Pages licensing](/power-platform/admin/powerapps-flow-licensing-faq#power-pages).

> [!IMPORTANT]
> Once the website has been converted to production, you should ensure that the website is appropriately licensed with authenticated or anonymous user capacity corresponding to the expected user volume or enabled for pay-as-you-go. Scaling of the website resources is done automatically based on the Power Pages licensing capacity assigned to the environment. Not having appropriate licenses assigned can result in degraded performance. For information on how to allocate authenticated or anonymous user capacity, see [Allocate or change capacity in an environment](/power-platform/admin/capacity-add-on#allocate-or-change-capacity-in-an-environment).

## Suspended website

You'll continue to see notifications in the Power Platform admin center about the expiration of your trial website. Trial websites expire after 30 days. If you don't convert your website to production within the trial period, the website is shut down and placed in suspended status.

You can't access your website after it expires. However, you can still convert the suspended website to production within seven days of suspension.

## Deleted website

If you don't convert your website to production within the seven-day suspension period, the website host is deleted. The website data isn't deleted from the environment, but the space used by the website in the environment will be released, and you can create a new website.

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