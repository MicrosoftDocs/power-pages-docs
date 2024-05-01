---
title: Gather feedback by using polls on Power Pages
description: Learn how to create polls on Power Pages and gather feedback by using them.
author: sandhangitmsft

ms.topic: conceptual
ms.custom: 
ms.date: 04/12/2023
ms.subservice: 
ms.author: sandhan
ms.reviewer: dmartens
contributors:
    - nickdoelman
    - sandhangitmsft
    - ProfessorKendrick
---

# Gather feedback by using polls on Power Pages

Polls give your web audiences a quick and easy way to voice their opinion on specific topics, and then immediately and automatically see feedback from their vote.

Use the polls capability of Power Pages to ask your audience about topics of interest and let them give single answers or let them submit the response from a list of options. Either way, their responses are instantly stored and associated with the applicable **Contact** record for immediate review or aggregate reporting. You can use polls as simple market research tools and, if you refresh or rotate the polls dynamically, you'll keep your website looking current and topical.

> [!Note]
> Users can vote anonymously. Duplicate votes are not permitted. Basic information about submissions can be tracked, and users who sign in to the website will have their submissions linked to the **Contact** table that tracks that user in Microsoft Dataverse.

## Add a poll to the page

Content managers can use [Template tags](liquid/liquid-overview.md) to add a poll to any editable content area:  

`{% include 'Random Poll' placement:polls.placements[Sidebar] %}`

or

`{% include 'Poll Template' ad:ads[Wireframe Development] %}`

> [!Note]
> Example web templates are configured in the starter websites. You can use the **Random Poll** template to display a random poll from a particular Poll Placement table, or you can use the Poll Template template to display a specific poll. You can edit these templates or follow their example and create your own by using [Polls](liquid/liquid-objects.md#polls). 

## Create a poll placement

To create a new poll placement region:

1. Open the [Portal Management app](portal-management-app.md).

1. Go to **Websites** > **Poll Placements**.

1. Select **New**.

1. Select the associated **Website**, give the placement a name, and&mdash;optionally&mdash;select the [web template](web-templates.md) that will control how it is rendered.

1. After the placement has been created, you must associate one or more polls with this placement. On the **Polls** tab of the Poll Placement table, select **Add Existing Poll**. 

1. In the resulting lookup box, select an existing poll record or create a new poll by selecting **New Poll**.
  
## Polls

A poll is a simple yes/no question that you can display on your website via poll placements. There are many customizable options for the display of polls available for developers, but for content managers, adding polls to your website is as easy as choosing a question and series of possible answers (poll options). A poll must have related options to function, and must be associated with a poll placement to be rendered on the website.

A new poll can be created in two ways: 
- By going to the **Polls** section.
- By selecting the **New** button on the **Look Up Records** window while adding a poll to a poll placement.

## Poll attributes

| Name                | Description                                                                                                                                                                                                                                                                                                                                  |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                | The descriptive name of the poll.                                                                                                                                                                                                                                                                                                            |
| Website             | The associated website.                                                                                                                                                                                                                                                                |  
| Web Template        | The associated [web templates](web-templates.md) that will be used by default to render the poll. This field is optional; if it is blank, the poll will be rendered by using a default template.                                                                                                                     |  
| Question            | This is the actual question that is being asked in the poll. The associated poll options are the possible answers that can be selected for this poll.                                                                                                                                                                                             |
| Submit Button Label | The text that is to be used for the submission button.                                                                                                                                                                                                                                                                                       |
| Release Date        | Controls the date and time after which the poll will be visible on the website. If the poll placement is rotating through multiple polls, an unreleased poll will not be shown. If no released polls are associated with a poll placement, nothing will appear. This is useful for controlling the release of time-sensitive content.         |
| Expiration Date     | Controls the date/time prior to which the poll will be visible on the website.                                                                                                                                                                                                                                                                  |
| Close Voting Date   | Until this date, users who have not yet voted on a poll can vote on the poll.|

> [!NOTE] 
> - When a user has voted on a poll, they will see a summary of current results for the poll. These results will also be displayed for a poll that is past its closed date, but for which the user has not yet voted. This allows you to continue to reveal the results of polls after you no longer want people to be able to vote on them. 
> - The difference between the **Close Voting Date** and **Expiration Date** is that after the expiration date has passed, the poll will no longer show up on the poll placement (it will not be cycled to). The **Close Voting Date** only determines the date past which users cannot vote on the poll.

Now that the poll has been created, you must associate one or more poll options with this poll. On the **Options** tab of the poll, select **New Poll Option**.

:::image type="content" source="media/polls/add-poll-options.png" alt-text="Add poll options.":::

## Poll options

A poll is a question that is being presented to the user. A poll has two or more possible answers as determined by the content author. These answers are represented by Poll Options, which must be associated with the poll in question. A new poll option is created via the **Look Up Records** window when adding poll options to a poll, as described above.

## Poll option attributes

| Name          | Description                                                                |
|---------------|----------------------------------------------------------------------------|
| Name          | The descriptive name for the poll option.                                  |
| Poll          | The poll that the option is associated with.                               |
| Answer        | The text to display as an available poll voting option.                    |
| Votes         | The number of votes the poll option has received (read-only).              |
| Display Order | A numeric value that will determine the display order of the poll options. |

## Poll submissions

When a user visits the website, they will be given the opportunity to vote on the poll displayed on the page.

:::image type="content" source="media/polls/submit-poll.png" alt-text="Submit a poll.":::
  
Users can vote only one time; after this, if the poll is displayed, they will see the results for that poll.

:::image type="content" source="media/polls/poll-votes.png" alt-text="Poll votes.":::

The details of the poll voting results are stored in Dataverse as **Poll Submission** records. The Poll Submission table contains the following information:

| Name        | Description                                                                                   |
|-------------|-----------------------------------------------------------------------------------------------|
| Name        | Displays the name of the voter if the user is signed in; otherwise, records the anonymous ID. |
| Poll        | The associated poll.                                                                          |
| Poll Option | The poll option that the user selected.                                                       |
| Contact     | The associated Contact record of the voter if the user is signed in.                          |
| Visitor ID  | The anonymous ID of the voter if the user is anonymous.                                       |

### See also

- [Portal Management app](portal-management-app.md)  
- [About lists](lists.md)  
- [Create and run advertisements](create-run-advertisement.md)  
- [Rate or vote on a webpage](rate-webpage.md)  
- [Redirect to a new URL](add-redirect-url.md)  


