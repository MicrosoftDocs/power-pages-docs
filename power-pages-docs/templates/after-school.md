---
title: Program registration template
description: Learn about the program registration template.
author: meeramahabala
ms.topic: conceptual
ms.custom: 
ms.date: 4/14/2023
ms.subservice:
ms.author: meeram
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - meeramahabala
---

# Program registration template

The program registration template is designed to show you the capabilities of a registration site. We've chosen the example of registering for after school classes. This template might be useful for any industry or organization wishing to create a registration website.

:::image type="content" source="media/school.png" alt-text="The program registration template landing page.":::

## Users

The template is designed for two key users:

- The parent who wants to register their children for after-school classes.

- The school representative who's looking to maintain a list of courses, edit existing courses, and add new courses to the catalog.

### Parents

As a parent who is looking to register for classes, you can:

- Register for an after-school class from the list of available classes.

- Modify the schedule.

- Add and edit attendee information.

- Receive emails with information about the class, which you can use to modify your registration.

### School representatives

As a representative of the school, you can:

- Maintain the course catalog.

- Add and modify existing classes.

## Makers

Makers are able to use the [design studio](../getting-started/use-design-studio.md) to modify the template for specific needs.

The following are the pages, basic forms, and customizable tables provided in the template. These can be modified to align with your specific project needs.

### Pages

#### Customer pages

The following pages are used by parents.

| Page | Description |
|-----------|----------------|
|Home|Search for an event, and view courses and course details based on specified criteria.|
|Unregister Attendee |Unregister a previously registered child.|
|Add Attendee Profile|Set up a profile for a child.|
|Attendee Information|Input a child's information for the purposes of setting up an attendee profile.|
|My Registrations|View registration for an attendee profile.|
|Registration Success|Confirm that a child is successfully registered for a course.|
|View Course Details|View selected course details.|


#### Admin pages

The following pages are used by **School Representatives**:

|Page|Description|
|-----------|----------------|
|Courses Home|A list view of the courses based on the filters specified.|
|Create Course|Create a course.|
|Duplicate Course|Duplicate a course from an existing course.|
|Delete Course|Delete a course.|
|Edit Course|Edit a course.|


### Forms and tables

The template uses the following forms linked to Dataverse tables.

|Table|Table form name*|Page form name**|
|---------|---------|---------|
|contact|Add child profile|Add Attendee|
|msdynce_course|Portal Course Form|ASP Create Course|
|msdynce_course|Portal Course Form|ASP Edit Form|
|msdynce_course|Delete a course form|Delete Course Form|
|contact|Edit child profile|Edit Attendee|
|msdynce_registration|Registration unregister form|Unregister Attendee|

**The form name as it appears associated to the table in data workspace.*

***The form name as it appears when added to a page as a component.*

#### Table information

|Table name|Schema name|Description|
|---------|---------|---------|
|Contact|contact|Contact details for the child's profile.|
|Course|msdynce_course|Course details such as course name, description, type, instructor, category, grade level, start date, start time, end date, end time, registration deadline, capacity, % filled, status.|
|Registration|msdynce_registration|Course registration details.|

## Professional developers

This template includes custom code and has been styled to follow best-in-class UX patterns. For custom code editing, use the [Microsoft Power Platform CLI](../configure/power-platform-cli-tutorial.md) to download the site metadata, and use Visual Studio Code to view and modify the source code.
