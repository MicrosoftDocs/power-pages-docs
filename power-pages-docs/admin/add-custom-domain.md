---
title: Add a custom domain name
description: Learn how to add a custom domain name to your Power Pages website.
author: neerajnandwana-msft
ms.topic: how-to
ms.date: 08/26/2026
ms.subservice: 
ms.author: nenandw
ms.reviewer: smurkute
contributors:
    - neerajnandwana-msft
    - nageshbhat-msft
ms.custom:
  - sfi-image-nochange

---

# Add a custom domain name

A custom domain enhances your brand and helps your customers more easily find your support resources. After you provision your website and acquire your domain name, get an SSL certificate to set up a custom host name. When you purchase the SSL certificate, use the following wizard experience to link your website to a custom domain. You can add only one custom domain name to a website.

> [!IMPORTANT]
> - You can add a custom domain name to a website only when the website is in production state. Learn more about website stages, in [Power Pages lifecycle](/power-apps/maker/portals/admin/portal-lifecycle).


To learn about the roles required to perform this task, see [Admin roles required for website administrative tasks](/power-apps/maker/portals/admin/portal-admin-roles).

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site to which you want to add a custom domain. Select **Manage** from the main menu. A page opens with details about your site.

1. In the **Site Details** section, select **Connect Custom Domain**.

1. A side panel appears. In the **Choose a SSL certificate** section, select one of these options:
   - **Add Microsoft Managed certificate**: Select this option to use a managed certificate provided by Microsoft. This certificate is automatically provisioned, configured, and renewed by Microsoft, so you don't need to purchase or manage your own SSL certificate.
   - **Upload a new certificate**: Select this option to upload the .pfx file if you didn't upload it earlier. Select the upload button under **File** to select the .pfx file. After selecting the file, enter the password for your SSL certificate in the **Password** field.
   - **Use an existing certificate**: Select this option to choose the correct certificate from the drop-down list.
  
    > [!NOTE]
    > The **Add Microsoft Managed certificate** option isn't available if either [Content Delivery Network (CDN)](../configure/configure-cdn.md) or [Web Application Firewall (WAF)](../security/web-application-firewall.md) is enabled. The add option isn't displayed when CDN or WAF are enabled.

    :::image type="content" source="media/add-custom-domain/cdn-waf-disabled.png" alt-text="The CDN and WAF options are disabled"::: 

    :::image type="content" source="media/add-custom-domain/add-ssl-certificate-with-three-option.png" alt-text="Upload an SSL certificate.":::

    > [!NOTE]
    > If you're using your own SSL certificate, the SSL certificate must meet all the following requirements: 
    > - Signed by a trusted certificate authority.
    > - [Exported](/powershell/module/pki/export-pfxcertificate) as a password-protected PFX file.
    > - Contains private key that's at least 2,048 bits long.
    > - Contains all intermediate certificates in the certificate chain.
    > - Must be SHA2 enabled; SHA1 support is being removed from popular browsers.
    > - PFX file must be encrypted with TripleDES encryption. Power Pages doesn't support AES-256 encryption.
    > - Contains an [Extended Key Usage](https://en.wikipedia.org/w/index.php?title=X.509&section=4#Extensions_informing_a_specific_usage_of_a_certificate) for server authentication (OID = 1.3.6.1.5.5.7.3.1).
    >
    > The steps to export SSL certificate as a password-protected PFX file might vary depending on your certificate provider. Check with your certificate provider for recommendation. For example, certain providers might suggest using OpenSSL 3rd party tool from [OpenSSL](https://www.openssl.org/) or [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) sites.
1. Select **Next**.

1. Enter the hostname you want in the **Host Name** field (for example `www.contoso.com`).

   > [!NOTE]
   > - You can have only one custom domain name for a website.
   > - To create a custom host name, you need to create a CNAME with your domain provider that points your hostname to the Power Pages site URL of your website.
   > - You can't have CNAME mapping for root domain in DNS srver. Ensure you aren't selecting root domain as hostname.
   > - If you just added a CNAME with your domain provider, it takes some time to propagate to all DNS servers. If the CNAME mapping isn't propagated and if you try to add hostname here, you will see an incorrect URL mapping error, please retry after sometime.
   > - The CNAME record used for custom domain configuration must be publicly resolvable. Power Pages can't validate DNS records that exist only in private or internal DNS zones, and will cause custom domain setup to fail.
   > - Before adding the custom domain, check that the CNAME resolves by using a public DNS tool (for example, `nslookup` or `dig`). If the record can't be resolved publicly, Power Pages can't validate it. Learn more about how to verify CNAME in [Verify your CNAME](#verify-your-cname).

1. Select **Next**.

1. This step is applicable for a [Content Delivery Network](../configure/configure-cdn.md) or [Web Application Firewall](../security/web-application-firewall.md) enabled site. In the **Validate the domain** section, copy the **Record type**, **Record name**, and the **Record value** and create a **TXT** record with your domain provider. For detailed instructions, see [Add the TXT record for domain validation](#add-the-txt-record-for-domain-validation).

    > [!NOTE]
    > To successfully bind your custom domain, ensure there's no TXT record in your DNS named `asuid.<customDomain>`. If such a record exists, delete it and try binding the domain again. For example, if your domain is `www.contoso.com`, check for a TXT record named `asuid.www.contoso.com`. If found, remove it before retrying the domain configuration. 

1. Select **Next**.

1. Review the information comparing the **Custom host name** and the **SSL certificate** (subject), and then select **Next** to begin creating the SSL Binding.

1. After the configuration is complete, a success message appears. 
    > [!NOTE]
    > Microsoft managed certificates can take few minutes for successful configuration.
    
   You can now go to {Custom Domain Name} to access this website.
1. Select **Close**.

## Verify your CNAME

After you add a CNAME record at your DNS provider, DNS servers take some time to sync the record. Check whether the CNAME mapping is publicly visible by following these steps:

In the following commands, replace `<hostname>` with your host name.

- On Windows, open Command Prompt, and then run the following command.

    ```bash
    
     nslookup -type=CNAME <hostname> 
    ```

- On macOS or Linux, run the following command.

    ```bash

     dig CNAME <hostname>
     ```


## Add the TXT record for domain validation

This step verifies you own the domain before Power Pages routes traffic through Azure Front Door.

**What you'll need** 
     
  In the Power Platform admin center, copy these values from the **Custom domain setup** panel:
 - Record type: TXT
 - Record name: for example, _dnsauth.www 
 - Record value: for example, abc123def456...


### Instructions for your DNS provider
General steps for any DNS provider:
        
1. Sign in to your DNS management console.
1. Find the option to add DNS records.
1. Create a new TXT record with:
    - **Record Name**: The record name from admin center.
    - **Record Type**: TXT
    - **Record Value**: The record value from admin center.
1. Save the record.
        
Learn more in [Create DNS records and zones using the Azure portal](/azure/dns/dns-getstarted-portal#create-a-dns-record) if you use Azure DNS.
    
### Verify your TXT record
After adding the record, verify it's publicly visible:
    
*Option 1: Command line*

 Replace `<hostname>` with your domain name. Run the command for your operating system.

 - On Windows, run

 ```
  nslookup -type=TXT _dnsauth.www.<hostname>
 ```
      
 - On macOS or Linux, run
 
 ```
 dig TXT _dnsauth.www.<hostname> +short
 ```
            
*Option 2: Online tools*
  - [MXToolbox TXT Lookup](https://mxtoolbox.com/TXTLookup.aspx)
  - [Google Admin Toolbox](https://toolbox.googleapps.com/apps/dig/)
            
If the record appears, return to admin center and select **Refresh**.
            
> [!IMPORTANT]
> TXT record details shown in this setup wizard have an expiry. If you don't create the TXT record before it expires, Power Pages automatically regenerates a new validation token. Before creating the DNS record, always copy the current **Record value** from the admin center. Adding an expired token won't let you proceed to the next step, and validation only succeeds against the currently active value.
        
When you add a TXT entry with your domain provider, it takes some time to propagate to all DNS servers. Select **Refresh** to validate the custom domain. When the information is validated, the **Next** button is activated.  
    
> [!NOTE]
 > - When you add a custom domain name for a [Content Delivery Network](../configure/configure-cdn.md) enabled site, Power Pages uses Azure Front Door-managed TLS certificates to enforce HTTPS for custom domains. These certificates are created with a lifetime validity of six months and are auto-renewed 45 days prior to the expiry date.
 > - Azure Front Door (AFD) automatically creates certificates for sites that use a content delivery network (CDN) or web application firewall (WAF). These certificates differ from certificates that you upload during custom domain configuration. You manage the expiration and renewal of these uploaded certificates.


## Change current custom domain name

To change your existing custom domain name:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site where you want to change the custom domain. Select **Manage** from the main menu. A page opens with details about your site.

1. In the **Site Details** section, select the pencil icon to the right of your custom URL.

1. A side panel appears.

    1. Select and delete the current SSL binding.
    1. Select and delete the current SSL certificate.
    1. Select and delete the current assigned hostname.

To configure your new domain, follow the instructions in [**Add a custom domain name**](#add-a-custom-domain-name).

## Moving between user-managed certs and Microsoft-managed certificates for existing domain 

To change the SSL certificate for your existing custom domain name:

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. Under **Resources**, select **Power Pages sites**.

1. Select the site where you want to change the custom domain. Select **Manage** from the main menu. A page opens with details about your site.

1. In the **Site Details** section, select the pencil icon to the right of your custom URL.

1. A side panel appears.
    1. Delete SSL binding if one exists.
    1. Delete SSL certificate if one exists.

1. To reconfigure your domain, follow the same instructions outlined in [**Add a custom domain name**](#add-a-custom-domain-name).

## Renew or reissue SSL/TLS certificate for Power Pages

To renew or reissue an SSL/TLS certificate that covers your portal's custom domain name, follow these high-level steps:

>[!NOTE]
> 
> - Steps might vary depending on your preferred Certificate Authority. For the complete renewal process, check the CA website.
> - If you already have your new certificate .PFX file, skip these four steps and follow the last two steps to upload the new certificate and binding.

**STEP 1:** Generate Certificate Signing Request (CSR).

To renew an SSL/TLS certificate, generate a new CSR.  

Generate a new CSR when renewing your SSL/TLS certificate. This process creates a new, unique key pair (public and private keys) for the renewed certificate.

**STEP 2:** Sign in to your preferred Certificate Authority (CA) website and fill out the renewal form.

On the **Expiring certificates** page, next to the certificate that needs to be renewed, select **Renew now**.

A certificate doesn't appear on the **Expiring Certificates** page until 90 days before it expires.

**STEP 3:** Your CA issues the SSL/TLS certificate.

Once approved, the CA issues and sends the renewed certificate to the certificate contact via email. You can also download the renewed certificate from the CA website.

**STEP 4:** Install your renewed SSL/TLS certificate (preferably on the machine from step 1 where you installed the CSR, which auto-associates the private key so that you can later export the .PFX file). While exporting the PFX file on Windows, just ensure that the export is a password-protected PFX file, encrypted using triple DES as shown in the following image:

:::image type="content" source="media/add-custom-domain/renewed-certificate.svg" alt-text="The Certificate Export Wizard with the triple DES Encryption information emphasized.":::

When you have the renewed (reissued) certificate .PFX file, select the edit icon (pencil icon) beside your custom domain in [Power Portals admin center](https://admin.powerplatform.microsoft.com/resources/portals) to replace your old certificate.

1. Upload your renewed certificate .pfx file by choosing **New** from the **Edit Custom Domain** pane.

1. After the upload, delete the existing binding with the old certificate and create a **New** binding as shown in the following image. Selecting **New** opens a popup where you can choose your preferred host name and your new certificate for this binding.

**Legend:**

1. To delete the existing binding, select the ellipse, and then choose **Delete**.
1. Select the **+ New** button to add a new SSL certificate.

### See also

[Configure SSL certificates and custom domain names](/training/modules/portals-administration/2-custom-domain)
