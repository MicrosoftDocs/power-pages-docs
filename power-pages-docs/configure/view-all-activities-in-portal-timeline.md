---
title: View activities in a web page timeline
description: Learn how to view all activities in a timeline on Power Pages.
author: DanaMartens

ms.topic: conceptual
ms.custom: 
ms.date: 04/13/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# View activities in a web page timeline

While working on a support case using the [Dynamics 365 Customer Self-support website](../templates/dynamics-365-apps/overview.md) or interacting with a customer, you might create an activity such as an appointment, an email, or a phone call. When you navigate to a web page with a form with the timeline control enabled, you might not find this activity because by default all activities aren't displayed in the timeline. 

> [!NOTE]
> The ability to display both [notes](configure-notes.md) and activities on the same form for a custom table is currently not supported with configuration.

To view all activities in a website timeline: 

1. Set the **CustomerSupport/DisplayAllUserActivitiesOnTimeline** site setting to true.  
    
    > [!NOTE]
    > If **DisplayAllUserActivitiesOnTimeline** site setting does not exist, you can create a new setting with this name.

1. If not present, add the activity type to include in the view filter:  
    1. Go to the [Data workspace](../getting-started/use-data-workspace.md).    
    1. Select **Activity** table and expand **Views**.
    1. Edit the **Portal Timeline View**.
    1. Update the **Edit Filter Criteria** and add the required activity type such as **Appointment, Email, or Phone Call**.
    1. **Save** and **Publish** the customizations. 

    > [!IMPORTANT]
    > Preparing customizations may take some time. If you see a message that the browser page has become unresponsive, wait for the page to become responsive, and don't close it.

1. Make sure the timeline control is enabled to show activities.
    1. From the Data workspace, select the form where the timeline control is enabled.
    1. From the main menu, select the ellipses **...** and then select **Switch to classic**.
    1. On the classic form designer, select the timeline control and choose **Change properties** from the main menu.
    1. On the **Web Client Properties** tab, ensure that **Activities** are selected in the **Default tab** section.
        :::image type="content" source="media/timeline/timeline-config.png" alt-text="Classic editor timeline configuration.":::
    1. Select **OK**, followed by **Publish**, and then **Save and Close**.

1. Since this change is a website metadata change, [clear the server-side cache](../admin/clear-server-side-cache.md) to ensure the updated data is displayed on the website.

> [!NOTE]
> The website timeline doesn't show inline images in the timeline control. For example, images embedded within emails don't appear on the timeline.