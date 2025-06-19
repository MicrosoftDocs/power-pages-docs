---
title: Add a custom domain name
description: Learn how to add a custom domain name to your Power Pages website.
author: neerajnandwana-msft

ms.topic: how-to
ms.custom: 
ms.date: 06/18/2025
ms.subservice: 
ms.author: nenandw
ms.reviewer: danamartens
contributors:
    - neerajnandwana-msft
    - nageshbhat-msft

---

# Add a custom domain name

A custom domain can enhance your brand and help your customers more easily find your support resources. Once you provision your website and acquire your domain name, you need an SSL certificate to set up a custom host name. After the SSL certificate is purchased, you can use a wizard to link your website to a custom domain. Only one custom domain name can be added to a website.

> [!IMPORTANT]
> - You can add a custom domain name to a website only when the website is in production state. For more information about website stages, go to [Power Pages lifecycle](/power-apps/maker/portals/admin/portal-lifecycle).

To learn about the roles required to perform this task, read [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site to which you want to add a custom domain. Select **Manage** from the main menu. A page opens with details about your site.

1. In the **Site Details** section, select **Connect Custom Domain**.

1. A side panel appears, on the **Choose a SSL certificate** section, select one of these options:
   - **Upload a new certificate**: Select this option to upload the .pfx file if you haven't uploaded it to the organization yet. Select the upload button underneath **File** to select the .pfx file. After selecting the file, enter the password for your SSL certificate in the **Password** field.
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

    :::image type="content" source="media/add-custom-domain/add-ssl-certificate.svg" alt-text="Upload an SSL certificate.":::

1. Select **Next**.

1. On the **Choose hostname** section, enter the CNAME you want in the **Domain Name** field (for example `www.contoso.com`).

   > [!NOTE]
   > - You can only have one custom domain name for a website.
   > - To create a custom host name, you will need to create a CNAME with your domain provider that points your domain to the URL of your website.
   > - If you have just added a CNAME with your domain provider, it will take some time to propagate to all DNS servers. If the name is not propagated and you add it here, the following error message will appear: "Please add a CNAME record to this domain name. Retry after some time passes."
   > - To successfully bind your custom domain, ensure there's no TXT record in your DNS named `asuid.{customDomain}`. If such a record exists, delete it and try binding the domain again. For example, if your domain is `www.contoso.com`, check for a TXT record named `asuid.www.contoso.com`. If found, remove it before retrying the domain configuration.

1. Select **Next**

1. This step is applicable for a [Content Delivery Network](../configure/configure-cdn.md) enabled site. On the **Validate the domain** section, copy the **Record type**, **Record name**, and the **Record value** and create a **TXT** record with your domain provider.

   When you add TXT entry with your domain provider, it takes some time to propagate to all DNS servers. Select **Refresh** to validate the custom domain. The TXT record must be created within seven days after enabling the Content Delivery Network; otherwise, you'll need to disable and re-enable the Content Delivery Network. When information has been validated, the **Next** button is activated.

1. Select **Next**

1. Review the information comparing the **Custom host name** and the **SSL certificate**, and then select **Next** to begin creating the SSL Binding.

1. You should see the message **Custom Domain name has been successfully configured**.  You can now go to {Custom Domain Name} to access this website.

1. Select **Close**.

## Change current custom domain name

To change your existing custom domain name:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site to which you want to change the custom domain. Select **Manage** from the main menu. A page opens with details about your site.

1. In the **Site Details** section, select the pencil icon to the right of your custom URL.

1. A side panel appears.

    1. Select and delete the current assigned hostname.
    1. Select and delete the current SSL certificate.
    1. Select and delete the current SSL binding.

1. Follow the instructions outlined in [**Add a custom domain name**](#add-a-custom-domain-name) to configure your new domain.

> [!NOTE]
> When you add a custom domain name for a [Content Delivery Network](../configure/configure-cdn.md) enabled site, Power Pages uses Azure Front Door-managed TLS certificates to enforce HTTPS for custom domains. These certificates are created with a lifetime validity of 6 months and are auto-renewed 45 days prior to the expiry date.

## Renew or reissue SSL/TLS certificate for Power Pages

Here are the high level steps for renewing or reissuing a SSL/TLS certificate covering your portals custom domain name.

>[!NOTE]
> 
> - Steps may slightly change based on your preferred Certificate Authority. The best practice is to refer to the CA website for the complete renewal process.
> - If you already have your new certificate .PFX file, please **skip these 4 steps** and follow the last 2 steps to upload the new certificate and binding.

**STEP 1:** Generate Certificate Signing Request (CSR).

To renew an SSL/TLS certificate, you need to generate a new CSR.  

Best practice is to generate a new CSR when renewing your SSL/TLS certificate, which creates a new, unique keypair (public/private) for the renewed certificate.

**STEP 2:** Log on to your preferred Certificate Authority (CA) website and Fill out the renewal form.

On the Expiring certificates page, next to the certificate that needs to be renewed, select Renew now.

A certificate doesn't appear on the Expiring Certificates page until 90 days before it expires.

**STEP 3:** Your CA issues the SSL/TLS certificate

Once approved, CA issues and sends the renewed certificate to the certificate contact via email. You can also download the renewed certificate from CA website.

**STEP 4:** Install your renewed SSL/TLS certificate (Preferably on the machine from step 1 where you installed the CSR, which will auto-associate the private key so that you can later export the .PFX file). While exporting the PFX file on Windows just ensure that the Export is a password-protected PFX file, encrypted using triple DES as shown below:

:::image type="content" source="media/add-custom-domain/renewed-certificate.svg" alt-text="The Certificate Export Wizard with the triple DES Encryption information emphasized.":::

Once you have the renewed (reissued) certificate .PFX file, select  the edit icon (pencil icon) beside your custom domain in [Power Portals admin center](https://admin.powerplatform.microsoft.com/resources/portals) to replace your old certificate.

1. Upload your renewed certificate .pfx file by choosing **New** from the Edit Custom Domain pane.

1. Post the upload, delete the existing binding with the old certificate and a "New" binding as shown below. Clicking on "New" button brings a popup where you can choose your preferred host name & your new certificate for this binding.

Legend:

1. To delete the existing binding, select the ellipse, then choose **Delete**.
1. Select the **+ New** button to add a new SSL certificate.

### See also

[Configure SSL certificates and custom domain names](/training/modules/portals-administration/2-custom-domain)
