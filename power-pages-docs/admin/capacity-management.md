---
title: Power Pages capacity management 
description: Learn about capacity management in Power Pages.
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.custom: 
ms.date: 11/07/2023
ms.subservice: 
ms.author: dileeps
ms.reviewer: kkendrick
contributors:
    - dileepsinghmicrosoft
    - ProfessorKendrick
---

# Capacity management overview

Power Pages capacity management experience in the Power Platform Admin Center (PPAC) allows administrators to manage Power Pages capacity, monitor capacity consumption, and provides an overview of the different licensing models in use on the Power Pages websites on the tenant.

Capacity management features allow administrators to assign the prepurchased capacity between the environments in the tenant based on the expected usage of the websites in the environment. The capacity management panel provides daily consumption data at the environment level for up to three full months, which helps determining the required capacity for the environments.

Consumption monitoring views of the capacity management experience provide daily data for the month to date, the past two full months, and monthly data for past 12 months to help with the license budgeting and planning.

Finally, the licensing summary view includes information about production websites using legacy licensing models as well, which helps planning the licensing model migration from legacy to current licensing models.

Power Pages capacity management experience allows pivoting between the two supported capacity categories: Authenticated MAU and anonymous MAU. For more information on Power Pages licensing, see [Power Platform licensing FAQs - Power Platform \| Microsoft Learn](/power-platform/admin/powerapps-flow-licensing-faq#power-pages)

These views and features can be used in addition to the website consumption reports that are also available. For more information on the consumption reports, see [Website capacity consumption reports \| Microsoft Learn](/admin/website-consumption-reports?tabs=PPS)

## Licensing summary view

The licensing summary view is located under Billing (Preview) and Licenses (Preview). Once Power Pages is selected from the product selector, the tenant level licensing summary view is shown.

### Sections of the licensing summary view

*License type cards*

License type cards are shown at the top of the view. The cards provide information about different license types in use in production and relevant metrics such as capacity available ("Total") and capacity assigned ("Assigned"). For capacity-based licensing models, the card has a link to either the capacity management experience or the legacy capacity management panel, depending on the license type. For Dynamics 365 Portal Add-ons (legacy license type), "View details" shows the production websites that are using add-ons licensing model. And finally, "View details" for Pay as you go license type will show a list of websites in production using Pay as you go license model.

The license cards have information about the legacy licensing models as well to help administrator with licensing model migration planning. Rest of the views and features only support the current capacity based licensing model (Authenticated MAU and Anonymous MAU, for more information, please see [Power Platform licensing FAQs - Power Platform \| Microsoft Learn](/power-platform/admin/powerapps-flow-licensing-faq#power-pages))

*Capacity category pivot*

The capacity category pivot allows switching between Authenticated capacity and Anonymous capacity. This tab controls both the pie chart and graph.

*Assignments pie chart*

Assignments pie chart always shows the current data for total available prepurchased capacity, the amount of assigned capacity and the amount of unassigned capacity. Should the administrator perform any changes that have impact on the amounts, for example,  perform assignments or purchase more capacity, the change is reflected in this control without delay. The pie chart itself represents the top environments in the tenant by assigned capacity, including all other environments and unassigned capacity as well. Legend below the pie shows the top five environment names.

*Consumption history graph*

Consumption graph visualizes the data for assigned capacity, total available capacity, consumed capacity and overage at the tenant level, if any. Time ranges available are month to date, daily data for the past two full months and monthly data for the past 12 months. The licensing capacity consumption resets in the beginning of each month and grows as unique users access the websites and licensing capacity is consumed. The daily views are cumulative. There's a delay of up to 24 hours for the data shown in the graph.

*Notification cards*

Notification cards appear above the licensing summary view when something requires attention.

## Capacity management

To manage prepurchased authenticated and anonymous capacity, administrator should select "Manage capacity" in Licensing summary below "Capacity." This opens the capacity management pane on the right side of the view.

Capacity management pane allows the administrator to view and manage the environments that are either already using this licensing type (has been assigned either authenticated or anonymous capacity) or don't have any kind of license or capacity assigned.

On top of the capacity management pane the administrator can see the total capacity available for the tenant, assigned capacity and how much of the capacity is unassigned and available to be assigned to the environments. Capacity category (authenticated, anonymous) can be controlled with the tab control on the top.

Select an environment from the list to display details of the environment on the bottom part of the pane, such as region and the type of the environment. *Capacity assignment for the selected environment can be changed by entering the new amount in the "Assigned units" textbox and confirming with "Apply".*

If the environment is nearing or over its assigned capacity, icon is shown and status field is indicating that fact. Hover over the icon to see the consumption history from the past three months and can use that information when determining the amount of more capacity required.

## Legacy capacity and license management

Licensing summary view also shows any legacy capacity in use, Dynamics 365 Portals add-ons and pay-as-you-go sites. This information can be used for license model migration planning.

For legacy capacity, "Manage capacity"-link under the license type opens the legacy capacity management view to the right side of the screen. This view lists the environments and sites in this licensing model and "Manage capacity" action link next to the environment and site opens up the "Manage add-ons" view with the environment preselected. "Manage add-ons" view allows changes to be made to the legacy capacity (page views, logins).

For Dynamics 365 Portal Add-ons, list of sites is shown to help plan the migration to current licensing models.

For more information on how to convert existing website to capacity-based model, see [Convert an existing website to capacity-based model](convert-site.md#convert-an-existing-website-to-capacity-based-model).

For Pay as you go model, list of sites is shown. Usage tracking for these sites is available directly from the Azure portal.

For more information on how to track the usage of sites in pay as you go model, see  [View usage and billing information](/power-platform/admin/pay-as-you-go-usage-costs)

For more information on the website consumption reports, visit <https://learn.microsoft.com/power-pages/admin/website-consumption-reports>

For more information on Power Pages licensing, visit <https://learn.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#power-pages>
