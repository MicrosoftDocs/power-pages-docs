---
title: Customize Power Automate flows for Book a Meeting
description: template
author: nickdoelman
ms.topic: conceptual
ms.custom: 
ms.date: 04/08/2022
ms.subservice:
ms.author: ndoelman
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - ProfessorKendrick
---

# Customize Power Automate flows for Book a Meeting

This template comes with a rich set of flows that are built in as part of the template and will get triggered and emails sent depending on the user flow.

There are four emails being sent out:

Four types of emails are sent out:

- Scheduling appointment

- Rescheduling appointment

- Cancelling appointment

- Appointment reminder

You can edit the emails by heading to the solution explorer -&gt; navigate to the book a meeting solution and select the cloud flow to view the available flow and available for you to customize.

![List of cloud flows used in Book a Meeting portal app ](media/image46.png)

The email notifications will have hyperlinks embedded to allow recipients to navigate back to the portal.

To ensure the email notifications have the correct domain embedded, add the website ID to the flows that have been configured as part of the solution.

Grab the website ID from the URL – in this case **c7be234f-d856-ec11-8f8e-002248233fb1** is the website ID that we have.

![Show where the GUID can be extracted from the URL](media/image47.png)

Alternatively, you can also copy the website ID from the website table created within the solution.

![Power Apps solution explorer showing list of website GUIDs ](media/image48.png)

Select the flow you'd like edit.

![Power Automate command bar](media/image49.png)

Sign in and update the information within "Get the website" section.

![Updating the Website action step in Power Automate](media/image50.png)

Save the changes and you should start receiving email notifications with the correct embedded links as expected from the solution.