---
title: Set up DocuSign integration
description: Learn how to set up DocuSign integration with your website. Include document generation and e-signature functionality in multi-step forms using DocuSign in Power Pages.
author: meeramahabala

ms.topic: conceptual
ms.custom: 
ms.date: 08/28/2023
ms.subservice:
ms.author: meeram 
ms.reviewer: kkendrick
contributors:
    - meeramahabala
    - ProfessorKendrick
---
# Set up DocuSign integration (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Power Pages and DocuSign integration offer an efficient workflow for incorporating e-signatures into multi-step forms through a low-code Studio experience. This integration uses the DocuSign connector-based Microsoft Power Automate Flow to enable an end user to view and sign documents. The configuration of these components is through a newly introduced **Integrations > External Apps** tab in the Set up workspace and allows you to map to your specific Dataverse tables to DocuSign. With this integration, you can add an e-signature step to your multi-step forms, enabling a streamlined process for capturing digital signatures.

> [!IMPORTANT]
> - This feature is a preview feature.
> - [!INCLUDE [preview-tags](../includes/cc-preview-features-definition.md)]

Integrating DocuSign into your application requires three steps:

[Step 1: Install DocuSign](#step-1-install-docusign) - In this step, the Site Admin installs the DocuSign package consisting of required tables, flows, Dataverse plugin, and PCF control for the environment.

[Step 2: Configure DocuSign](#step-2-configure-docusign) - In this step, the Site Admin or maker configures specific DocuSign credentials and templates.

[Step 3: Enable DocuSign](#step-3-enable-docusign) - In this step, the maker includes the form and enables e-signature on the required step for the multi-step form.

## Prerequisites

- Set up a template in DocuSign. The template can contain one or more documents for viewing and signing. The template is assigned a recipient role but doesn't need any name or email association—these fields are assigned from the Power Pages website. The document can include tabs or fields including the signature tab. See [DocuSign Template documentation](https://support.docusign.com/s/document-item?language=en_US&bundleId=xry1643227563338&topicId=uab1578456394214.html&_LANG=enus) for details or watch [this video](https://support.docusign.com/s/articles/Create-a-DocuSign-Template?language=en_US).

- You may wish to review how to [Configure Power Automate cloud flows in Power Pages (preview)](../configure/cloud-flow-integration.md) prior to integrating DocuSign with your Power Pages site.

## Step 1: Install DocuSign

1. In the design studio, choose **Set up > Integration > External Apps**.
1. Select the **Install** action for DocuSign. 
    :::image type="content" source="Media/docusign/install-docusign.png" alt-text="The Set up workspace in Power Pages design studio with the External Apps menu option selected and the install button for DocuSign emphasized.":::

The install action may take a few moments. The action will change to configure once the action is complete. This installs a solution, which contains tables, flows, a Dataverse plug-ins, and code components to render signed documents.

## Step 2: Configure DocuSign

Once you've installed the DocuSign package, you can begin to configure DocuSign for your Power Pages site.

1. In the design studio, choose **Set up > Integrations > External Apps**.
1. In the Integrations table, Select the **Configure** action for DocuSign.
The Enable integration menu displays.
:::image type="content" source="Media/docusign/enable-integrations.png" alt-text="The Enable integration options inside design studio.":::
1. Select the links to resolve the connection references and enable cloud flows in Power Automate, ensuring both cloud flows are turned **on**.
    > [!NOTE]
    >
    > - There are two flows, one that accesses DocuSign and one that accesses Dataverse.
    > - Use the appropriate credentials to access DocuSign and Dataverse.

1. Return to the Enable integration menu in design studio and select the **I have resolved the connection references checkbox**.
1. Select **Next**, then **Close** to exit the Enable integration menu.
1. In the **Set up workspace**, choose **Cloud Flows**.
1. Add the cloud flows from the previous step to this site.
1. Create a Dataverse table to capture the DocuSign instances.  This is the table that will render the subgrid for the documents to sign.  You'll use this table in the next step.
1. Enter the DocuSign template metadata in the fields provided, including *Template ID*, *Template Name*, *Role Name*, and *Table*.
1. Map the form table fields to the DocuSign tabs in the document.

## Step 3: Enable DocuSign

To enable DocuSign, complete the following steps:

1. Create a form for the table you created in Step 2 to represent the documents grid.
1. Add a form to the table you've mapped to your template in the previous step. More information: [Add a multistep form](../getting-started/multistep-forms.md)
1. Add table permissions for your table (minimum: create and write + authenticated or higher). More information: [Configuring table permissions](../security/table-permissions.md)
1. Add a child permission to that permission for the DocuSign Output table (minimum: AppendTo + match parent role).
1. Select the **Sync** button.

Next, add a new form step entitled Sign Document (or similar).

1. Proceed to Step settings.
1. Select **Integrations**.
    - Choose the correct Template to associate with the form.
    - Enable the form toggle for e-signature.

        > [!NOTE] 
        > You must open the form to give permission to authenticated users.

1. Preview and test your webpage.

### See also

- [Add a multistep form](../getting-started/multistep-forms.md)
- [Use Dataverse low-code plug-ins (experimental)](/power-apps/maker/data-platform/low-code-plug-ins)
- [Use code components in Power Pages](../configure/component-framework.md)