---
title: Frequently Asked Questions template (preview)
description: Learn about the Frequently Asked Questions template.
author: deepa88 
ms.topic: conceptual
ms.custom: 
ms.date: 4/12/2023
ms.subservice:
ms.author: deepabansal 
ms.reviewer: kkendrick
contributors:
    - ProfessorKendrick
---

# Frequently Asked Questions template (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Frequently Asked Questions template provides your target audience with answers to commonly asked questions. The FAQ template organizes information with a topic, subtopic and article framework. There's a no-code administrator experience for updating and organizing content.

:::image type="content" source="media/faq.png" alt-text="The FAQ template user interface. The page header contains a search box and the body of the page contains six topic tiles, each displaying a title and icon.":::

> [!IMPORTANT]
> - This is a preview feature.
> - [!INCLUDE [cc-preview-features-definition](../includes/cc-preview-features-definition.md)]
> - This template is being rolled out across regions, and may not be available in your region yet.

## Users

The template is designed for two key users:

- The customer user who wants to view and search for FAQ content

- A content administrator who is responsible for updating and organizing content

### Customer

As an unauthenticated customer, you can:

- View articles to selected topics and subtopics. In this example, "Getting Started" is a Topic and "Onboarding" and "Account Management" are subtopics. The "How do I submit an issue or inquiry" Article is nested under the "Onboarding" topic.

- Search for articles and topics

- Ability to provide feedback if articles are missing via Contact Us form

- Receive an automated email after submitting feedback

### Content Administrator

As a Content Administrator, you can:

- Create and update articles, topics and subtopics. Articles can be related to either topics or subtopics.

- Determine whether to publish updates to existing or new articles, topics, subtopics. If a parent topic is in draft (not published) and subtopics are published, the subtopics won't be displayed. For all subtopics to show up, the parent topics must be published. An error message won't be returned to the Admin.

- Input rich text formatting for article content

- Manage ordering of featured articles via the Article Details page. If you select the same article or topic order number as another article/ topic, an error message isn't displayed. Articles are still ordered in chronological order. (for example: 1, 2, 2, 3)

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md) to modify the template for specific needs. As an added control, only Makers (not Admins) can delete topics, subtopics and articles.

Additionally, the Power Automate email flow must be connected to an email account that they want the Customer messages to be sent to. Also, for the Admin to have access to the "Contact Us" messages, the Admin can create a data table that displays the messages and/or add the Admin's email address to the Power Automate email flow.

## Pages

### Customer pages

The following pages are used by Customers:

| **Page**             | **Description**                                                                                    |
|----------------------|----------------------------------------------------------------------------------------------------|
| Homepage             | Customer homepage. Contains topics, featured articles. Also contains the login for Administrators. |
| Topics               | Customer view of the articles associated to the topics and subtopics                               |
| Article              | Contains the content of the selected article.                                                      |
| Search Results       | Displays the search results when a customer searches for an article, topic or subtopic             |
| Contact Us Submitted | Displays the confirmation page after the customer feedback is submitted                            |
| Page Not Found       | Displayed when the user's search criteria isn't matched                                           |
| Access Denied        | Displayed if content administrator doesn't have access                                            |

### Admin pages

The following pages are used by the Content Administrator

| **Page**                  | **Description**                                                                               |
|---------------------------|-----------------------------------------------------------------------------------------------|
| \[Admin\] Articles        | Displays the list of articles                                                                 |
| \[Admin\] Topics          | Displays the list of topics                                                                   |
| Contact Us                | Form for the customer to reach out to the Content Administrator with any feedback on content. |
| \[Admin\] Article Details | Provides functionality to create a new article                                                |
| \[Admin\] Create Subtopic | Provides functionality to create a subtopic                                                   |
| \[Admin\] Edit Subtopic   | Provides functionality to edit a subtopic                                                     |
| \[Admin\] Edit Article    | Provides functionality to edit a single article                                               |
| \[Admin\] Edit Topic      | Provides functionality to edit an existing topic                                              |
| \[Admin\] Topic Details   | Provides functionality to create new topic and upload topic icon                              |
| \[Admin\] View Article    | Preview of the selected article                                                               |

### Forms and tables

The template uses the following forms linked to Dataverse tables.

| **Table**    | **Table form name\***                                           | **Page form name\*\***          | **Form Description**                   |
|--------------|-----------------------------------------------------------------|---------------------------------|----------------------------------------|
| Faq\_topic   | \[Admin\] New Topic, Edit Topic                                 | \[Admin\] Create/ Edit Topic    | Create and edit topics                 |
| Faq\_article | Create an article, Edit Article                                 | \[Admin\] Create/ Edit Article  | Create and edit articles               |
| Faq\_topic   | \[Admin\] Create/ Edit Subtopic, Create Subtopic, Edit Subtopic | \[Admin\] Create/ Edit Subtopic | Create & edit Subtopics                |
| Feedback     | Contact Us                                                      | Feedback main form              | Capture feedback details from Customer |

*\* The form name as it appears associated to the table in data workspace.*

*\*\* The form name as it appears when added to a page as a component.*

### Table information

| Table name | Schema name  | Description                                             |
|------------|--------------|---------------------------------------------------------|
| Article    | faq\_Article | Capture article content and associated article metadata |
| Topic      | faq\_Topic   | Capture topics, subtopics and topic details             |
| Feedback   | Feedback     | Capture feedback from customer                          |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.

### See also

[Tutorial: Add a page to your Power Pages site](../getting-started/tutorial-add-webpage.md)  
[Create and design pages](../getting-started/first-page.md)
