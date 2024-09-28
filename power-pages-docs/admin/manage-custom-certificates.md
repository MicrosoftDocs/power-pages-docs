---
title: Add custom certificates
description: When extending portals functionality using a client-side API call with OAuth 2.0 implicit grant flow, configure custom certificates for added security.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 08/28/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Manage custom certificates

When extending Power Pages functionality using a client-side API call with [OAuth 2.0 implicit grant flow](/power-apps/maker/portals/oauth-implicit-grant-flow), it's best practice to use custom certificates to provide an additional level of security. You can upload you own custom certificates using the Power Platform admin center.

> [!IMPORTANT]
> You cannot re-use the same custom certificate to set up a [custom host name](/power-apps/maker/portals/admin/add-custom-domain). See [SSL Certificates](/power-apps/maker/portals/admin/manage-ssl-certificates).

## Add new certificate

1. Open the [Power Platform admin center](admin-overview.md).

    1. Under **Resources** choose **Power Pages sites**.

    1. Select the site where you want to manage custom certificates. Select **Manage** from the main menu.

    **Or**

    1. In the **Environments** section, select the environment that contains the site you want to manage custom certificates.

    1. In the **Resources** area, choose **Power Pages sites**.

    1. Select the site where you want to manage custom certificates. Select **Manage** from the main menu.

1. On the site information page, in the **Security** section, select **Custom Certificates**.

    :::image type="content" source="media/manage-custom-certificate/manage-custom-certificate.svg" alt-text="Manage custom certificates.":::

1. Select **+ New** to upload a new certificate.

1. Select the upload button underneath **File** to select a .pfx certificate file. After selecting the file, enter the password for your SSL certificate in the **Password** field.

1. Select **OK** to upload the certificate.

     > [!NOTE]
     > The SSL certificate must meet all of the following requirements:
     > - Signed by a trusted certificate authority
     > - [Exported](/powershell/module/pki/export-pfxcertificate) as a password-protected PFX file.
     > - Contains private key at least 2048 bits long
     > - Contains all intermediate certificates in the certificate chain
     > - Must be SHA2 enabled; SHA1 support is being removed from popular browsers
     > - PFX file must be encrypted with TripleDES encryption; Power Pages doesn't support AES-256 encryption
     > - Contains an [Extended Key Usage](https://en.wikipedia.org/w/index.php?title=X.509&section=4#Extensions_informing_a_specific_usage_of_a_certificate) for server authentication (OID = 1.3.6.1.5.5.7.3.1).
     > 
     > The steps to export SSL certificate as a password-protected PFX file may vary depending on your certificate provider. Check with your certificate provider for recommendation. For example, certain providers may suggest using an OpenSSL third-party tool from [OpenSSL](https://www.openssl.org/) or [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) sites. 


