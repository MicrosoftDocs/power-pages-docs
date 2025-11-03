---
title: Set up DocuSign integration
description: Learn how to set up DocuSign integration with your website. Include document generation and e-signature functionality in multistep forms using DocuSign in Power Pages.
author: PramithaU
ms.topic: how-to
ms.custom: 
ms.date: 08/14/2025
ms.subservice:
ms.author: pudupa 
ms.reviewer: dmartens
contributors:
    - meeramahabala
    - nageshbhat-msft
---
# Set up DocuSign integration

Power Pages and DocuSign integration offers an efficient workflow for incorporating e-signatures into multistep forms through a low-code Studio experience. This integration uses the DocuSign connector-based Microsoft Power Automate Flow to enable an end user to view and sign documents. The configuration of these components is through a newly introduced **Integrations** > **External Apps** tab in the Set up workspace and allows you to map your specific Dataverse tables to DocuSign. With this integration, you can add an e-signature step to your multistep forms, enabling a streamlined process for capturing digital signatures.

:::image type="content" source="media/docusign/multistep-form.png" alt-text="A signed document in a multistep form.":::


Integrating DocuSign into your application requires three steps:

[Step 1: Install DocuSign](#step-1-install-docusign). In this step, the site admin installs the DocuSign package consisting of required tables, flows, Dataverse plug-in, and PCF control for the environment.

[Step 2: Configure DocuSign](#step-2-configure-docusign). In this step, the site admin or maker configures specific DocuSign credentials and templates.

[Step 3: Enable DocuSign](#step-3-enable-docusign). In this step, the maker includes the form and enables e-signatures on the required step for the multistep form.

:::image type="content" source="media/docusign/docusign-architecture.png" alt-text="DocuSign architecture.":::

## Prerequisites

- Set up a template in DocuSign. The template can contain one or more documents for viewing and signing. The template is assigned a recipient role but doesn't need any name or email association—these fields are assigned from the Power Pages website. The document can include tabs or fields including the signature tab. See [DocuSign Template documentation](https://support.docusign.com/s/document-item?language=en_US&bundleId=xry1643227563338&topicId=uab1578456394214.html&_LANG=enus) for details or watch [this video](https://support.docusign.com/s/articles/Create-a-DocuSign-Template?language=en_US).
- You might wish to review how to [Configure Power Automate cloud flows in Power Pages](../configure/cloud-flow-integration.md) prior to integrating DocuSign with your Power Pages site.
- Create or identify a Microsoft Dataverse table to use in a multistep form. The table needs to be configured such that **Creating a new activity** needs to be selected in the **Make this table an option when** section. More information: [How to create and modify Dataverse tables by using the Data workspace](../configure/data-workspace-tables.md).
- Configure a [multistep form](../getting-started/multistep-forms.md) using the Dataverse table that has a step to allow users to sign documents. This step displays a subgrid displaying the documents requiring signature. This is configured in a later step. 
- The e-signature integration only works with authenticated users who must have their first name, last name, and email configured in their profile.

## Step 1: Install DocuSign

1. In the design studio, choose **Set up** > **Integrations** > **External apps**.
1. Select the **Install** action for DocuSign. 

   :::image type="content" source="media/docusign/install-docusign.png" alt-text="A screenshot of the Set up workspace in Power Pages design studio with the External Apps menu option selected and the install button for DocuSign emphasized.":::

The install action might take a few moments. The action changes to configure once the action is complete. This installs a solution, which contains tables, flows, Dataverse plug-ins, and code components to render signed documents.

## Step 2: Configure DocuSign

Once you install the DocuSign package, you can begin to configure DocuSign for your Power Pages site.

1. In the design studio, choose **Set up** > **Integrations** > **External Apps**.
1. In the Integrations table, select the **Configure** action for DocuSign.
The Enable integration menu displays.

   :::image type="content" source="media/docusign/enable-integrations.png" alt-text="A screenshot of the Enable integration options inside design studio.":::

1. Select the links to resolve the connection references and enable cloud flows in Power Automate, ensuring both cloud flows are turned **on**.
    > [!NOTE]
    > - There are two flows, one that accesses DocuSign and one that accesses Dataverse.
    > - Use the appropriate credentials to access DocuSign and Dataverse.
    > - For the **DocuSign Envelope completed trigger** flow, you'll need to select the appropriate DocuSign account ID for the **Account** setting on the **When an envelope status changes** trigger.

1. Return to the **Enable integration** menu in design studio and select the **I have resolved the connection references** checkbox.
1. Select **Next**, then **Close** to exit the Enable integration menu.
1. In the **Set up workspace**, choose **Cloud Flows**.
1. Add the **DocuSign Envelope Create and Sign** cloud flow from the previous step to this website.
1. Enter the DocuSign template metadata in the fields provided: 

   | Value | Source |
   |-|-|
   | Template ID | DocuSign eSignature website |
   | Template Name | DocuSign eSignature website |
   | Role Name | DocuSign eSignature website |
   | Table | Dataverse table used in the multistep form requiring e-signatures |

1. (Optional) Map the form table fields to the DocuSign tabs in the document.

    :::image type="content" source="media/docusign/add-template.png" alt-text="A screenshot of the Add a template option inside the Enable integration menu.":::

## Step 3: Enable DocuSign

To enable DocuSign, complete the following steps:

1. Create a multistep form step for the Dataverse table used in your multistep form process to represent the documents grid. 
1. Add table permissions for the Dataverse table used in the document signature multistep form process (you need at least **Create** and **Write**) and assign appropriate [web roles](../security/create-web-roles.md). More information: [Configuring table permissions](../security/table-permissions.md)
1. Select the **Sync** button.
1. On a webpage, add or edit the multistep form, and create a step entitled *Sign Document* (or similar). More information: [Add a multistep form](../getting-started/multistep-forms.md)
1. Proceed to **Step settings**.
1. Select **Integrations**.
    - Choose the correct template to associate with the form.
    - Enable the form toggle for e-signature.
    
        :::image type="content" source="media/docusign/step-settings.png" alt-text="The step settings options inside of the Set up workspace in Power Pages design studio.":::

        > [!NOTE] 
        > You must open the form to give permission to authenticated users.
    - A subgrid is automatically added to the form step that lists the documents that are to be signed.

1. Preview and test your webpage. You should be able to open the document, e-sign the appropriate fields, exit, and return to the multistep process.

### See also

- [Add a multistep form](../getting-started/multistep-forms.md)
- [Use Dataverse low-code plug-ins (experimental)](/power-apps/maker/data-platform/low-code-plug-ins)
- [Use code components in Power Pages](../configure/component-framework.md)  
- [Power Pages Docusign e-signature (video)](https://youtu.be/xvxspc-jLDE?feature=shared)
