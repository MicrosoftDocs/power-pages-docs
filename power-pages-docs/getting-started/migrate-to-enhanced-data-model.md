---
title: Migrate to new enhanced data model
description: Learn how to migrate existing websites to teh new enhanced data model
author: gitanjalisingh33msft
ms.topic: conceptual
ms.custom: 
ms.date: 04/14/2023
ms.author: gisingh
ms.reviewer: ndoelman
contributors:
    - nickdoelman
    - gitanjalisingh33msft
    - neerajnandwana-msft
---

# Migrate to new enhanced data model

You can migrate existing websites to the new enhanced data model using the [Power Platform CLI](/power-platform/developer/cli/introduction).

## Follow below steps to migrate site configuration data from standard to enhanced data model 

Install the Power Platform CLI tools on your workstation. See [Microsoft Power Platform CLI support for Power Pages](../configure/power-platform-cli.md) for details.

> [!NOTE]
> Please do not modify records during migration.

1. Using the Power Platform CLI, connect to your org using the below command: 

    `pac auth create -u <<ORG URL>>` 

1. To list the websites in your org to get the `<<website-id>>` for downloading the data. Use the following command:  

    `pac paportal list -v` 

1. Use the `<<website-id>>` obtained above, and download the website's metadata by using the following command:

    `pac paportal download --path <<path to download>> --webSiteId <<website-id>>`

    > [!NOTE]
    > Make sure to download data from the correct org.

1. For uploading the data to new data model, use the following command:

    `pac paportal upload -p <<path-of-downloaded-data\website-name>> -mv 2` 

    > [!NOTE]
    > Make sure to upload data in the correct org.

If the data is not uploaded, there are two possible scenarios:

If you get the message `0 entities modified since download`, follow the below steps:  

1.  Go to `\<<path-of-downloaded-data>>\website-name>>.portalconfig` 

1. Rename `<<org-url>>-manifest.yaml` file to `temp.yaml` 

1. Retry uploading the data.

If you get the message `Some data are not uploading properly` then try re-running the **upload** command. It will correctly upload missing data. 

> [!NOTE]
> The Power Platform CLI can only download/upload the websites's metadata (mapped to core website tables), not the transactional table data such as contacts and invitation records. 

## Migrate standard data model site's non-configuration data to enhanced data model 

1. Navigate to the [Power apps](https://make.powerapps.com) home page.  

1. In the **Apps** section, open the **Power Pages Management app** 

1. Under **Website**, select **Websites** and open the website record for which the non-configuration data need to be migrated.  

1. Select the **Migrate relationships** option from the command bar. 

1. You'll see **App level migration in-progress** notification.  

1. You will see **App level notification** once the migration is successfully completed. 

1. In case failures select the command again. 

## What consists of configuration data for a website? 

Configuration data represents site data and is stored in the following tables. 

| Configuration tables in standard data model |  |
|-------------------------|-------------------------|
| adx_contentsnippet </br>adx_entitypermission </br>adx_pagetemplate </br>adx_portallanguage </br>adx_publishingstate </br>adx_publishingstatetransitionrule </br>adx_redirect </br>adx_setting </br>adx_shortcut </br>adx_sitemarker </br>adx_sitesetting </br>adx_tag </br>adx_webfile </br>adx_weblink </br>adx_weblinkset </br>adx_webpage </br>adx_webpageaccesscontrolrule  | adx_webrole </br>adx_webtemplate </br>adx_website </br>adx_websiteaccess </br>adx_websitelanguage </br>adx_entityform </br>adx_entityformmetadata </br>adx_webformmetadata </br>adx_entitylist </br>adx_webform </br>adx_webformstep </br>Annotation(webfiles) </br>adx_adplacement </br>adx_pollplacement </br>adx_botconsumer </br>adx_columnpermission </br>adx_columnpermissionprofile  |

## What consist of non-configuration data for a website? 

Records which are part of non-configuration tables. 

| Non-configuration tables |  |
|-------------------------|-------------------------|
| ad</br>poll</br>settings | Invitation</br>Portal comment |

Data stored as part of relationships between non metadata and metadata tables.

| Non-metadata table | Metadata table | Relationship Type |
|-------------------------|-------------------------|-------------------------|
| Contact | Web role  | N: N  |
| Account  | Web role  | N: N  |
| Ad  | Publishing state  </br>Webfile </br>Webpage  </br>Web template  </br>Website  | 1: N  |
| Invitation  | Website   | 1: N  |
| Invitation  | Web role  | N: N  |
| Poll  | Website  | 1: N  |
| Poll  | Poll Placement  | N: N  |
| Web form session  | Webform </br>Webform step  | 1: N  |


## Frequently asked questions: 

### With Power Pages solution awareness, when should I use solutions and when should I use the Power Platform CLI for migration?

You should use solutions.

### What is best practice when you are migrating a Power Pages website using solutions? 

Refer to [Overview of application lifecycle management with Microsoft Power Platform](/power-platform/alm/overview-alm) for best practices.

### After importing site configuration data in a managed solution I edited my website in the target environment. I don't see any new changes when I import managed solutions from my source environment.

Editing the site configuration data in the target environment is discouraged as it will result in the creation of an unmanaged layer and changes from the source will not reflect in the target. To fix it in the target environment user needs to remove the unmanaged solution layer. See [Solution layers](/power-platform/alm/solution-layers-alm) for more information.

### When we upgrade to the new data model, do we physically delete the tables at the end of the migration? 

The process migrates the data from the standard data model tables to the new enhanced model tables. Data is not deleted from the existing standard data model tables.  

Once the migration is completed and stable, you can remove legacy portal solutions manually after making a backup of your Power Platform environment. 

### Can I edit new sites based on enhanced data model configurations in the Portal management app? 

New websites created using the enhanced data model can be edited using the new Power Pages Management app. 

## Known issues

1. Editing of company logo and header from the design studio is not supported on new data model.

1. Dataverse dependency addition to solution is not available.

1. Enable traffic analysis is not available for websites using the enhanced data model.

1. You cannot configure canvas and model driven Power Apps on the Power Pages solution explorer.

1. The preview capabilities of the design studio may have some missing styling and images.

## Removed un-used tables in enhanced data model

The following Power Pages Dataverse tables are no longer used and not part of the enhanced data model:

`adx_webnotificationURL`
`adx_pagenotification`
`adx_pagealert`
`adx_pagetag`
`adx_portallanguage` (*merged with site language*)
`adx_tag`
`adx_urlhistory`
`adx_webfilelog`
`adx_webpagehistory`
`adx_websitebinding`
`adx_alertsubscription`
`adx_webpagelog`
`adx_webnotificationentity`