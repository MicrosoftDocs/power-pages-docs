---
title: Add a custom domain name
description: Learn how to add a custom domain name to your Power Pages website.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 03/03/2023
ms.subservice: 
ms.author: nenandw
ms.reviewer: ndoelman
contributors:
    - neerajnandwana-msft
    - nickdoelman

---

# Add a custom domain name

A custom domain can enhance your brand and help your customers more easily find your support resources. Once you provision your website and acquire your domain name, you'll need an SSL certificate to set up a custom host name. After the SSL certificate is purchased, you can use a wizard to link your website to a custom domain. Only one custom domain name can be added to a website.

> [!IMPORTANT]
> - You can add a custom domain name to a website only when the website is in production state. For more information about website stages, go to [Power Pages lifecycle](/power-apps/maker/portals/admin/portal-lifecycle).

To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site to which you want to add a custom domain. Select **Manage** from the main menu. A page will open with details about your site.

1. In the **Site Details** section, select **Connect Custom Domain**.

1. A side panel will appear, on the **Choose a SSL certificate** section, select one of these options:
   - **Upload a new certificate**: Select this option to upload the .pfx file if you haven't yet uploaded it to the organization. Select the upload button underneath **File** to select the .pfx file. After selecting the file, enter the password for your SSL certificate in the **Password** field.
   - **Use an existing certificate**: Select this option to choose the correct certificate from the drop-down list.

     > [!NOTE]
     > The SSL certificate must meet all the following requirements:
     > - Signed by a trusted certificate authority.
     > - [Exported](/powershell/module/pki/export-pfxcertificate) as a password-protected PFX file.
     > - Contains private key at least 2048 bits long.
     > - Contains all intermediate certificates in the certificate chain.
     > - Must be SHA2 enabled; SHA1 support is being removed from popular browsers.
     > - PFX file must be encrypted with TripleDES encryption. Power Pages doesn't support AES-256 encryption.
     > - Contains an [Extended Key Usage](https://en.wikipedia.org/w/index.php?title=X.509&section=4#Extensions_informing_a_specific_usage_of_a_certificate) for server authentication (OID = 1.3.6.1.5.5.7.3.1).
     > 
     > The steps to export SSL certificate as a password-protected PFX file may vary depending on your certificate provider. Check with your certificate provider for recommendation. For example, certain providers may suggest to use OpenSSL 3rd party tool from [OpenSSL](https://www.openssl.org/) or [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) sites. 

    :::image type="content" source="media/add-custom-domain/add-ssl-certificate.png" alt-text="Upload an SSL certificate.":::

1. Select **Next**.

1. On the **Choose hostname** section, enter the CNAME you want in the **Domain Name** field (for example `www.contoso.com`).
   
   > [!NOTE]
   > - You can only have one custom domain name for a website. 
   > - To create a custom host name, you will need to create a CNAME with your domain provider that points your domain to the URL of your website.
   > - If you have just added a CNAME with your domain provider, it will take some time to propagate to all DNS servers. If the name is not propagated and you add it here, the following error message will appear: "Please add a CNAME record to this domain name. Retry after some time passes."

1. Select **Next**

1. This step is applicable for [Content Delivery Network](../configure/configure-cdn.md) enabled site. On the **Validate the domain** section, copy the **Record type**, **Record name**, and the **Record value** and create a **TXT** record with your domain provider.
   If you have just added the TXT entry with your domain provider, it will take some time to propagate to all DNS servers. Select **Refresh** to validate the custom domain. When information has been validated, the **Next** button will be activated. The TXT record must be created within 7 days after enabling the Content Delivery Network; otherwise, you will need to disable and re-enable the Content Delivery Network

1. Select **Next**

1. Review the information comparing the **Custom host name** and the **SSL certificate**, and then select **Next** to begin creating the SSL Binding. 

1. You should see the message **Custom Domain name has been successfully configured**.  You can now go to {Custom Domain Name} to access this website. 

1. Select **Close**.

## Change current custom domain name

To change your existing custom domain name:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site to which you want to change the a custom domain. Select **Manage** from the main menu. A page will open with details about your site.

1. In the **Site Details** section, select the pencil icon to the right of your custom URL.

1. A side panel will appear.

    1. Select and delete the current assigned hostname.
    1. Select and delete the current SSL certificate.
    1. Select and delete the current SSL binding.

    :::image type="content" source="media/add-custom-domain/change-ssl.png" alt-text="Change SSL certificate.":::

1. Follow the instructions outlined in [**Add a custom domain name**](#add-a-custom-domain-name) to configure you new domain.

> [!NOTE]
> When you add a custom domain name for a [Content Delivery Network](../configure/configure-cdn.md) enabled site, Power Pages uses Azure Front Door-managed TLS certificates to enforce HTTPS for custom domains. These certificates are created with a lifetime validity of 6 months and are auto-renewed 45 days prior to the expiry date. 

### See also

[Configure SSL certificates and custom domain names](/training/modules/portals-administration/2-custom-domain)


