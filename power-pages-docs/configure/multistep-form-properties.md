---
title: Define multistep form properties for Power Pages
description: Learn how to configure multistep form properties for a portal.
author: DanaMartens

ms.topic: concept-article
ms.custom: 
ms.date: 04/06/2023
ms.subservice: 
ms.author: bipuldeora
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
---

# Define multistep form properties

> [!NOTE]
> Multistep forms can be created using the Power Pages design studio. In addition, many of the multistep form properties can be configured in the design studio as well. See [Add a multistep form](../getting-started/multistep-forms.md) for more information.

The following information refers to configuration and management of multistep forms using the [Portal Management app](portal-management-app.md).

The multistep form contains relationships to webpages and a start step to control the initialization of the form within the website. The relationship to the webpage allows dynamic retrieval of the form definition for a given page node within the website.  

The other options on the multistep form record itself control top-level preferences for the multiple-step process as a whole, for example whether you'd like to display a progress bar.

To view existing multistep forms configuration or to create new multistep forms, open the [Portal Management app](portal-management-app.md) and go to **Content** > **Multistep Forms**.

> [!NOTE]
> Before you continue, ensure you review [considerations](#considerations) for multistep forms.

When creating or editing a webpage from the [Portal Management app](portal-management-app.md), an **Multistep Form** can be specified in the lookup field provided on the **New Web Page** form.

A multistep form can also be added to a web page, web template or content snippet using the Liquid tag `{% webform name: '<<My Multistep Form>>' %}`.

## Multistep form attributes

The following attributes and relationships determine the functionality of the multistep form.


|                Name                 |                                                                                                                                                                                        Description                                                                                                                                                                                         |
|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                Name                 |                                                                                                                                                                          A title of the form used for reference.                                                                                                                                                                           |
|             Start Step              |                                                                                The first step of the form. An Multistep Form will consist of one or more steps. For more information about these steps please refer to the section titled Multistep Form Step found below. The first step cannot be of type Condition.                                                                                |
|       Authentication Required       |                                                                              If checked, when a user who is not signed in visits the page that contains the form, they will be redirected to the sign-in page. Upon successful sign-in, the user will be redirected back to the page that contains the form.                                                                               |
|      Start New Session On Load      |              Selecting **Yes** indicates that if the user opens the form in a new browser or new tab, or closes the browser or page and returns, the form will start a completely new session and begin at the first step. Otherwise the session will be persisted and the user can close the browser or page and resume later exactly where they left off. Default: **No**.               |
| Multiple Records Per User Permitted |                                                                                                  Selecting **Yes** indicates that a user is permitted to create more than one submission. This assists the form in determining what to do when a user revisits a form. Default: **Yes**.                                                                                                   |
|       Edit Expired State Code       |                                                                                                                    The target entity's state code integer value that, when combined with the status reason, indicates when an existing record can no longer be edited.                                                                                                                     |
|     Edit Expired Status Reason      |                                                                       The target entity's status code integer value that, when combined with the state code, indicates that when an existing record has these values the record is not to be edited anymore&mdash;for example, when a record is updated as complete.                                                                       |
|        Edit Expired Message         | The message displayed when the existing record's state code and status reason match the values specified. For each language pack installed and enabled for the organization, a field will be available to enter the message in the associated language. Default message; You have already completed a submission. Thank you! |
|                                     |                                                                                                                                                                                                                                                                                                                                                                                            |

## Progress indicator settings

| Name                              | Description                                                                                          |
|-----------------------------------|------------------------------------------------------------------------------------------------------|
| Enabled                           | Check to display the progress indicator. Default: **Disabled**.                                      |
| Type                              | One of the following: Title, Numeric (Step x of n), and Progress Bar. Default: **Title**                                                                                    |
| Position                          | One of the following: Top, Bottom, Left, Right. Position is relative to the form. Default: **Top**.                                                   |
| Prepend Step Number to Step Title | Check to add the number of the step to the beginning of the title of the step. Default is unchecked. |
||

Example of the various progress indicator types:

**Title**

:::image type="content" source="media/multistep-forms/track-progress-title.png" alt-text="Track progress by using a title.":::

**Title with Step Number prepended**

:::image type="content" source="media/multistep-forms/track-progress-step-number.png" alt-text="Track progress by using a step number":::

**Numeric**

:::image type="content" source="media/multistep-forms/track-progress-numeral.png" alt-text="Track progress by using a numeral.":::

**Progress Bar**

:::image type="content" source="media/multistep-forms/track-progress-bar.png" alt-text="Track progress by using a bar.":::

## “Save changes” warning 

Because of the recent changes related to browsers support for custom text in beforeunload event, the ability to specify a custom message using "Save changes" warning in no longer functional. You can implement a save changes warning using [custom code](add-custom-javascript.md) methods.

## Geolocation configuration for multistep form

A managed form can be configured to display a map control to either display an existing location as a pin on a map or to provide the ability for the user to specify a location. See [Add Geolocation](add-geolocation.md).

The form's map control requires additional configuration to tell it what the IDs of the various location fields are, to assign values to them or retrieve values from them. The Multistep Form Step record has a section that defines these field mappings that you must assign values for. The field names will vary depending on the schema you have created.
:::image type="content" source="media/multistep-forms/geolocation-managed-form.png" alt-text="Geolocation data in multistep form.":::

> [!Note]
> The Geolocation section is not visible in the German Sovereign Cloud environment. If a user has enabled geolocation by using a different form, it will not be displayed during rendering on portal.

## Considerations

- An **Multistep Form** must be associated with a webpage for a given website for the form to be viewable within the site.
- Field level code components can be added to forms. More information: [Code components](component-framework.md).
- Rollup columns on Dataverse forms may sometimes show up as editable although they're intended to be read-only. To ensure that these columns remain read-only, mark the column as **Read-only**  on the model-driven app form or when configuring in [Data workspace](data-workspace-forms.md).

### See also

- [Configure a portal](portal-management-app.md)  
- [Define basic forms](basic-forms.md)  
- [Multistep Form steps](multistep-form-steps.md)  
- [Multistep Forms metadata](configure-multistep-form-metadata.md)  
- [Multistep Form subgrid configuration](configure-multistep-form-subgrid.md)  
- [Notes configuration](configure-notes.md)  



