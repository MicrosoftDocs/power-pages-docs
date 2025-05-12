---
title: Frequently Asked Questions template (preview)
description: Learn about the Frequently Asked Questions template in Power Pages.
ms.topic: faq
ms.custom: bap-template
ms.date: 4/14/2023
ms.subservice:
author: murugesh1985 
ms.author: murugeshs 
ms.reviewer: danamartens
contributors:
---

# Frequently Asked Questions template (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

The Frequently Asked Questions (FAQ) template gives you an easy way to add an FAQ page to your Power Pages site. The FAQ template organizes information around a topic, subtopic, and article framework. A no-code administrator experience makes it easy to update and organize content.

:::image type="content" source="media/faq.png" alt-text="Screenshot of the FAQ template user interface.":::

> [!IMPORTANT]
> This is a preview feature. [!INCLUDE [cc-preview-features-definition](../includes/cc-preview-features-definition.md)]

## Users

The template is designed for two key users:

- A customer who wants to search for and view answers to commonly asked questions

- A content administrator who's responsible for updating and organizing content

### Customer

As an unauthenticated customer, you can:

- Search for articles and topics.

- View articles in topics and subtopics; for example:

  - Topic: Getting started
    - Subtopic: Onboarding
      - Article: How do I submit an issue or inquiry?

- Use a Contact Us form to provide feedback.

- Receive an automated email confirmation of your feedback.

### Content administrator

As a content administrator, you can:

- Create and update topics, subtopics, and articles. Articles can be related to topics or subtopics.

- Determine when to publish updated or new articles, subtopics, and topics.

    Published subtopics of updated and unpublished topics aren't shown. You must publish a topic for its subtopics to be visible on your site. The system doesn't warn you if you edit a topic that has published subtopics and forget to publish it.

- Enter richly formatted article content.

- Determine how featured articles are ordered.

    The system doesn't warn you if you assign the same order number to more than one article. Articles still appear in chronological order; for example: 1, 2, 2, 3.

## Makers

Makers can use the [design studio](../getting-started/use-design-studio.md) to modify the FAQ template. Only makers, not admins, can delete topics, subtopics, and articles.

You must connect the Power Automate email flow to an account you want customer feedback sent to. If you want an admin to have access to "Contact Us" messages, add the admin's email address to the Power Automate email flow. The admin can also create a data table that displays the messages.

## Pages

The template provides the following pages, forms, and tables. Modify them as needed.

### Customer pages

The following pages are used by customers.

| **Page**             | **Description**                                                                         |
|----------------------|-----------------------------------------------------------------------------------------|
| Home                 | Customer homepage; contains topics, featured articles, and the sign-in for administrators |
| Topics               | Customer view of the articles associated with the topics and subtopics                  |
| Article              | Content of the selected article                                                         |
| Search Results       | List of results when a customer searches for an article, topic, or subtopic             |
| Contact Us Submitted | Confirmation page after a customer submits feedback                                     |
| Page not found       | Displayed when the user's search criteria isn't matched                                 |
| Access denied        | Displayed if the content administrator doesn't have access                              |

### Admin pages

The following pages are used by the content administrator.

| **Page**                  | **Description**                                                   |
|---------------------------|-------------------------------------------------------------------|
| \[Admin\] Articles        | List of articles                                                  |
| \[Admin\] Topics          | List of topics                                                    |
| Contact Us                | Form for a customer to offer feedback on article content          |
| \[Admin\] Article Details | Provides functionality to create an article                       |
| \[Admin\] Create Subtopic | Provides functionality to create a subtopic                       |
| \[Admin\] Edit Article    | Provides functionality to edit an article                         |
| \[Admin\] Edit Subtopic   | Provides functionality to edit a subtopic                         |
| \[Admin\] Edit Topic      | Provides functionality to edit a topic                            |
| \[Admin\] Topic Details   | Provides functionality to create a topic and upload a topic icon  |
| \[Admin\] View Article    | Preview of the selected article                                   |

### Forms and tables

The template uses the following forms, which are linked to Dataverse tables.

| **Table**  | **Table form name\*** | **Page form name\*\*** | **Form Description** |
|------------|-----------------------|------------------------|----------------------|
| Faq\_topic | \[Admin\] New Topic, Edit Topic | \[Admin\] Create/Edit Topic | Create and edit topics |
| Faq\_topic | \[Admin\] Create/Edit Subtopic, Create Subtopic, Edit Subtopic | \[Admin\] Create/Edit Subtopic | Create and edit subtopics |
| Faq\_article | Create Article, Edit Article | \[Admin\] Create/Edit Article | Create and edit articles |
| Feedback | Contact Us | Feedback main form | Capture feedback from customer |

*\* The form name as it appears in the data workspace.*

*\*\* The form name as it appears when it's added to a page as a component.*

### Table information

| Table name | Schema name  | Description                             |
|------------|--------------|-----------------------------------------|
| Article    | faq\_Article | Article content and associated metadata |
| Topic      | faq\_Topic   | Topics, subtopics, and topic details    |
| Feedback   | Feedback     | Customer feedback                       |

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.

### See also

[Tutorial: Add a page to your Power Pages site](../getting-started/tutorial-add-webpage.md)  
[Create and design pages](../getting-started/first-page.md)
