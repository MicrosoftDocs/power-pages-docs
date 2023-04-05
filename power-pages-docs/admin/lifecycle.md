---
title: Power Pages lifecycle
description: Information about Power Pages lifecycle and converting it from trial to production.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 04/03/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Power Pages lifecycle

A Power Pages website is always created as a trial. A trial website, which expires after 30 days, is useful for trying out its capabilities at no cost. After it expires, the website is suspended and shut down. Seven days after it's suspended, the trial website host is deleted. You'll be notified at every stage of the website lifecycle; nearing suspension, suspended, deleted, and converted from trial to production; through toast notifications and email.

As an administrator, you can convert a trial or suspended website to a production website. When converting a website from trial to production, you must ensure that the Dataverse environment is also a production or a sandbox environment. You can't convert a trial website to production in a trial Dataverse environment. If you delete the Dataverse environment in which a trial website is created, the website is also deleted.

| Dataverse Environment Type  | Convert website to production |
|---------|---------|
| Trial | No |
| Developer | No |
| Sandbox | Yes |
| Production | Yes |

### Understanding website lifecycle stages

The following diagram explains various stages that a Power Pages website goes through, from creation until deletion.

:::image type="content" source="media/lifecycle/portal-lifecycle.png" alt-text="Power Pages lifecycle stages.":::

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

- [Power Pages templates](../templates/)
- [Create a site](/getting-started/create-manage.md)

### See also

- [Convert a website from trial to production](convert-site.md#convert-a-website-from-trial-to-production)
- [Convert an existing website to capacity-based model](convert-site.md#convert-an-existing-website-to-capacity-based-model)