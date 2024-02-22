---
title: Set up Azure Front Door with Power Pages sites
description: Learn about how to set up Azure Front Door, or any other content delivery network or WAF, with sites to benefit from features such as edge caching.
author: dileepsinghmicrosoft

ms.topic: conceptual
ms.custom: 
ms.date: 01/04/2023
ms.author: dileeps
ms.reviewer: kkendrick
contributors:
    - dileepsinghmicrosoft
    - nickdoelman
---

# Set up Azure Front Door with Power Pages sites

As a website maker, you can use Azure Front Door with Power Pages to use its edge caching and web application firewall (WAF) capabilities. In this article, you'll learn how to set up [Azure Front Door](/azure/frontdoor/front-door-overview) with Power Pages.

> [!NOTE]
> - Although this article is focused on [Azure Front Door](/azure/frontdoor/front-door-overview), similar steps can be used for any other content delivery network or WAF provider. The terminology used by various components might be different.
> - While [custom domain HTTPS settings using Azure portal](/azure/frontdoor/front-door-faq#can-i-configure-tls-policy-to-control-tls-protocol-versions-) allows you to choose a [default minimum](/azure/frontdoor/front-door-faq#what-tls-versions-are-supported-by-azure-front-door-) TLS version between 1.0 and 1.2, use TLS version 1.2 for strong ciphers.

Follow these steps to set up Azure Front Door with Power Pages:

1. [Set up the Azure Front Door endpoint and custom domain name that website users will use](#set-up-the-azure-front-door-endpoint-and-custom-domain-name).
1. [Configure your Power Pages site as the origin](#configure-the-site-as-an-origin-server).
1. [Set up routing rules to cache static requests](#set-up-routing-rules-to-cache-static-requests).
1. [Set up WAF rules to analyze incoming requests](#set-up-waf-rules-to-analyze-incoming-requests).
1. [Set up the site to accept traffic only from Azure Front Door](#set-up-power-pages-to-accept-traffic-only-from-azure-front-door).

## Set up the Azure Front Door endpoint and custom domain name

In this section, you'll learn how to set up the Azure Front Door service and enable a custom domain name for this setup.

### Prerequisites

- An Azure subscription with the access to create new services.

- A custom domain name and access to the DNS provider for custom domain name setup.

- An SSL certificate that will be used for the custom domain name. The certificate must meet the [minimum requirements](/power-apps/maker/portals/admin/add-custom-domain) for Power Pages.

- [Owner access](/power-apps/maker/portals/admin/portal-admin-roles#portal-owner) to Power Pages, to set up the custom domain name.

### Set up the Azure Front Door endpoint

> [!NOTE]
> If you've already created the Azure Front Door resource, go to step 3 of the following procedure.

1. Sign in to the [Azure portal](https://portal.azure.com), and create a new Azure Front Door (Standard or Premium) resource. More information: [Quickstart: Create an Azure Front Door Standard/Premium profile - Azure portal](/azure/frontdoor/create-front-door-portal)

    :::image type="content" source="media/azure-front-door/create-azure-front-door.png" alt-text="Create an Azure Front Door resource.":::

1. Select **Quick create**.

    > [!TIP]
    > Most of the Azure Front Door settings can be changed later.

    :::image type="content" source="media/azure-front-door/quick-create.png" alt-text="Create the Azure Front Door and settings.":::

1. Select, or fill in, the following details to configure the resource.

    | Option | Description |
    | - | - |
    | **Project details** | Settings related to the resource organization, similar to any other Azure resource.
    | Subscription |Select the subscription where the Azure Front Door resource will be created.  |
    | Resource group | Select the resource group for Azure Front Door. You can also create a new resource group. |
    | Resource group location | The location of the resource group. |
    | **Profile details** | The configuration for Azure Front Door. |
    | Name | Name of the Azure Front Door resource. |
    | Tier | Select a tier for the Azure Front Door resource. For this article, we've selected the Premium tier, which allows access to the Microsoft-managed rule set and bot prevention rule set for WAF. |
    | **Endpoint settings** | Settings for the Azure Front Door endpoint. |
    | Endpoint name | Enter a name for your Azure Front Door requests. This name is the actual URL that will serve the traffic for users. Later, we'll set up a custom domain name that points to this URL. |
    | Origin type | Select **Custom**. |
    | Origin host name | The host name of your Power Pages site. <br> Format: `yoursitename.powerappsportals.com` or `yoursitename.microsoftcrmportals.com` without `https://` at the beginning. <br> For example, `contoso.powerappsportals.com` |
    | Private link | Don't enable the private link service. |
    | Caching | Enable caching. Caching uses the edge caching capabilities for static content. <br> Caching is discussed further in "[Set up routing rules to cache static requests](#set-up-routing-rules-to-cache-static-requests)," later in this article. |
    | Query string caching behavior | Select **Use Query String**. This option will ensure that if a page has dynamic content that satisfies the query string, it takes the query string into account. |
    | Compression | Enable compression. |
    | WAF policy | Create a new WAF policy, or use an existing one. <br> For information about WAF policy, go to ["Set up WAF rules to analyze incoming requests"](#set-up-waf-rules-to-analyze-incoming-requests) later in this article, and also [Tutorial: Create a Web Application Firewall policy on Azure Front Door using the Azure portal](/azure/web-application-firewall/afds/waf-front-door-create-portal). |

1. Select **Review + Create**, and wait for setup to finish. This typically takes 5 to 10 minutes.<

1. Validate the setup by browsing to the endpoint URL (for example, `contoso.example.azurefd.net`) and verifying that it shows the content from your Power Pages site.

    :::image type="content" source="media/azure-front-door/browse-endpoint.png" alt-text="Browse the endpoint.":::

    > [!TIP]
    > If you see a "404 Not Found" response, setup might not have finished. Wait a while and try again.

### Set up a custom domain name

So far, the Azure Front Door endpoint has been set up to serve traffic from the Power Pages back end. However, this setup still uses the Azure Front Door URL, which will cause problems such as captcha check failures or scaling issues.

Web browsers reject cookies set by Power Pages when you use an Azure Front Door endpoint URL that's different from the URL of your site. Hence, you must set up a custom domain name both for your site and the Azure Front Door endpoint.

1. Set up a custom domain name on your site. More information: [Add a custom domain name](/power-apps/maker/portals/admin/add-custom-domain).

1. Enable your site custom domain name on the Azure Front Door resource by doing the following:

    1. Update your DNS provider by removing the CNAME record created earlier during the custom domain setup for Power Pages. Only CNAME should be updated; don't remove the origin host name. DNS will point CNAME to the Azure Front Door endpoint. The only purpose for adding CNAME was to ensure that the custom host name will be present on Power Pages. This presence ensures that Power Pages can serve traffic to this custom domain name through Azure Front Door, and all site cookies will also have the domain set up correctly.

    1. Set up the custom domain name on the Azure Front Door endpoint by following these steps: [Create a custom domain on Azure Front Door Standard/Premium SKU using the Azure portal](/azure/frontdoor/standard-premium/how-to-add-custom-domain).

1. Check the following to validate the setup:

    1. The custom domain name points to the Azure Front Door endpoint. Use [nslookup](/windows-server/administration/windows-commands/nslookup) to verify that a CNAME entry to the Azure Front Door endpoint is returned correctly. If the CNAME entry still points to Power Pages, you need to correct that.

    1. Browsing to the custom domain name shows your Power Pages website page.

After following these steps, you have a basic Azure Front Door endpoint setup completed for the website. In the next steps, you'll update various settings and rules to make this configuration more efficient and better at handling different use cases.

## Configure the site as an origin server

The next step is to optimize the origin server settings to ensure that the setup works correctly. Use **Endpoint manager** in Azure Front Door configurations on the Azure portal to update the origin group settings.

:::image type="content" source="media/azure-front-door/endpoint-manager.png" alt-text="Endpoint manager.":::

During the quick-create setup you performed earlier, you entered endpoint details that automatically created the configuration with the name **default-origin-group(associated)** (this name can vary depending on locale settings). For this step, you'll modify the settings for the **default-origin-group**. The following image shows what the settings for this step look like when you open the origin group for the first time.

:::image type="content" source="media/azure-front-door/origin-group-initial.png" alt-text="Origin group as seen for the first time.":::

Origins in Azure Front Door represent the back-end service that the Azure Front Door edge servers connect to, to serve content to users. You can add multiple origins to your Azure Front Door instance to get content from multiple back-end services.

> [!TIP]
> Power Pages provides high availability at its service layer, hence a single origin server is sufficient when setting up origins for sites.

The single origin for Power Pages sites should point to the host name of your site (which you set up earlier). If you didn't follow the quick-create setup steps, you can add a new origin that points to your site host name. 

The following image shows an example of the origin configuration.

:::image type="content" source="media/azure-front-door/origin-configuration.png" alt-text="Origin configuration.":::

Use the following settings to configure the origin for Power Pages sites.

| Option | Configuration type or value |
| - | - |
| Origin type | Select **Custom**. |
| Origin host name | Enter your site host name. For example, `contoso.powerappsportals.com` |
| Origin host header | Enter your custom domain name, or leave empty. The former ensures that Azure Front Door sends the origin header as a custom domain name; the later causes it to pass through whatever the user provided while making the request. |
| HTTP port | 80 |
| HTTPS port | 443 |
| Priority | 1 |
| Weight | 1000 |
| Private link | Disabled |
| Status | Select the **Enable this origin** checkbox. |

After you've configured the origin and returned to the origin group, update the settings for health probes and load-balancing options as described in the following table.

| Option | Configuration type or value |
| - | - |
| Health probes | Health probes are a mechanism to ensure that the origin service is up and running, and to make the traffic routing decisions depending on the probe results. In this case, we don't require health probes, so we turned it off. |
| Load balancing | Because we have a single origin set up and health probes are turned off, this setting won't play any role in this setup. |

Validate that the origin group configuration looks like the following image.

:::image type="content" source="media/azure-front-door/origin-configuration-validate.png" alt-text="Validate origin configuration.":::

## Set up routing rules to cache static requests

Routes determine how we use the edge caching capabilities of Azure Front Door to improve the scalability of a site. Setting up routes is also an important step to ensure that we're not caching dynamic content served by the site, which can lead to unintended data access.

:::image type="content" source="media/azure-front-door/configure-routes.png" alt-text="Configure routes.":::

For rules setup, we'll need to do the following:

1. [Set up route configuration](#set-up-route-configuration).
1. [Set up a rule set](#set-up-a-rule-set).
1. [Associate the rule set with a route](#associate-the-rule-set-with-a-route).
1. [Validate the rules and route configuration](#validate-the-rules-and-route-configuration).

### Set up route configuration

To set up route configuration, select **Endpoint manager** on the left pane, select **Routes**, and then select the default route. **Default-route** is created during the quick-create setup experience.

:::image type="content" source="media/azure-front-door/route-configuration.png " alt-text="Route configuration.":::

Update the route configuration as described in the following table.

| Option | Configuration |
| - | - |
| **Domains section** |  |
| Domains | The domain name you used while setting up the custom domain name earlier. |
| Patterns to match | Set to **/\*** (default value); all site requests will be sent to the same origin in our setup. |
| Accepted protocols | Set to **HTTPS only** to ensure that all the traffic served is secure. |
| Redirect | Select the **Redirect all traffic to use HTTPS** checkbox. |
| **Origin group section** |  |
| Origin group | Set to the origin group you defined earlier. |
| Origin path | Keep empty. |
| Forwarding protocol | Set to either **HTTPS only** or **Match incoming request**. |
| **Caching section** |  |
| Caching | Select the **Enable caching** checkbox if you want to use edge caching. |
| Query string caching behavior | Select **Use Query String** to ensure that dynamic content based on the query string can be served. |
| Compression | Select **Enable compression** to optimize content delivery. |

### Set up a rule set

Rule sets govern how content should be cached. This step is important, because it governs how content will be cached by edge servers to improve scaling for the site. However, an incorrectly configured rule set can lead to caching dynamic content that should be served specifically for each individual user.

To set up the rule set correctly, it's important that you understand the type of content your site is serving. This understanding helps you configure the rule set by using effective rules. For the scenario in this article, the site uses dynamic content on all pages and it also serves static files; therefore, the site is trying to achieve the following:

- All static files are cached and served from the edge servers.
- None of the page content is cached.

**To configure this rule set**

1. On the left pane, select **Rule set**, and then select **Add a rule set**.

    :::image type="content" source="media/azure-front-door/rule-set.png" alt-text="Configure rule set.":::

1. Enter a rule set name, and then save it.

    :::image type="content" source="media/azure-front-door/create-rule-set.png" alt-text="Create a new rule set.":::

Now, lets configure the rule set based on the business requirement, with the following configuration to meet the requirements for the scenario mentioned earlier.

#### Requirement: All static files are cached and served from the edge servers

The site in this scenario can contain static files with file name extensions of .css, .png, .jpg, .js, .svg, .woff, or .ico. Hence, we need a rule to evaluate the file name extension of the request and check for specific file types.

> [!NOTE]
> There are other ways to write this rule, such as by using the request URL or file name. For more information about the Azure Front Door rules matching conditions, go to [Azure Front Door Rules Engine match conditions](/azure/frontdoor/front-door-rules-engine-match-conditions).

:::image type="complex" source="media/azure-front-door/file-extensions-rule-set.png" alt-text="Example Request file extensions condition.":::
   Screenshot of an IF condition named "Request file extension" with the Operator set to Equal, the Value set to css png jpg js svg woff ico, and Case transform set to No transform.
:::image-end:::

In the following action configuration, you override the cache header set by Power Pages so that these files will be cached a little longer on the browser. By default, Power Pages sets the caching expiration to one day. But we'll override that in this scenario and set it to seven days by setting up a **Cache expiration** action and setting **Cache behavior** to **Override** as shown in the following image.

:::image type="content" source="media/azure-front-door/cache-expiration-action.png" alt-text="Example cache expiration action.":::

At the end, the complete rule looks like the following image.

:::image type="content" source="media/azure-front-door/final-file-rule.png" alt-text="Final file extension rule.":::

#### Requirement: None of the page content is cached

In general, Power Pages site setup ensures that if a page has a form embedded in it (which means it's serving content specific to a record), it will have its **Cache-control** header value set to **private**, which ensures that Azure Front Door won't cache that request. However, this method doesn't take into account the scenarios where you're using liquid templates to embed user-specific content on the pages, such as displaying a specific record to a set of users. Hence, we'll add an explicit rule to ensure that no website page is cached.

The first step is setting up the condition. The condition does an inverse check of what we did in the first rule, and checks that the request *doesn't* include a file name extension that points to one of the file types we want to cache.

:::image type="complex" source="media/azure-front-door/caching-condition.png" alt-text="Example of a Not equal Request file extensions condition.":::
   Screenshot of an IF condition named "Request file extension" with the Operator set to Not equal, the Value set to css png jpg js svg woff ico, and Case transform set to No transform.
:::image-end:::

In the action condition, similar to previous rule, we'll write an action for **Cache expiration**. However, this time, we'll set the behavior to **Bypass cache**. This will ensure that any request that fulfills this rule isn't cached.

:::image type="content" source="media/azure-front-door/cache-expiration.png" alt-text="Cache expiration configuration.":::

The complete rule looks like the following image.

:::image type="content" source="media/azure-front-door/no-page-content-cache-rule.png" alt-text="Complete rule for page content cache.":::

### Associate the rule set with a route

After you've created the rule set, the next step is to associate it with a route.

1. Select the rule set, and then select **Associate a route** in the command bar.

    :::image type="content" source="media/azure-front-door/select-associate-route.png" alt-text="Select to associate a route on a rule set.":::

1. Select the endpoint name and available route. There might be multiple routes available, so select the one you configured earlier.

    :::image type="content" source="media/azure-front-door/associate-route.png" alt-text="Associate a route":::

1. If you have multiple rule sets and you want to define the order they should be evaluated in, select **Change rule set orders** and configure the order. Our example scenario has only one rule set.

    :::image type="content" source="media/azure-front-door/change-rule-set-order.png" alt-text="Change the order of rule sets.":::

1. Select **Done** to finish.

### Validate the rules and route configuration
To validate that rules and route configurations are working correctly, ensure that all traffic is served through HTTPS and that caching rules are evaluated correctly.

**To ensure that all traffic is served through HTTPS and all HTTP calls are redirected to HTTPS**

* Enter the domain name in a browser and ensure that the URL changes to HTTPS automatically while the content is rendered.

**To ensure that caching rules are evaluated and working as expected**

To check caching rules, we'll need to analyze network traces in a web browser's developer toolbar to validate that the caching headers for different types of content are set correctly.

> [!NOTE]
> Rule changes might take up to 10 minutes to be reflected.

1. Open a new browser tab, open the developer toolbar, and browse to the Power Pages site URL (ensure that you open the developer toolbar *before* you browse to the URL).

1. Go to the network tab to see all network requests.

1. Select a request for any **CSS** file from the list of requests.

   In the **Response headers** section of the request details, ensure that a header named **x-cache** is present. This header ensures that the request is served through edge servers and can be cached. If the value of **x-cache** is set to **CONFIG_NOCACHE**&mdash;or any other value containing the term **NOCACHE**&mdash;the setup isn't correct.

    :::image type="content" source="media/azure-front-door/response-header-x-cache.png" alt-text="Response header called x-cache with cache hit value.":::

1. Similar to the previous step, select a **Page** request and check its headers. If **x-cache** is set to **CONFIG_NOCACHE**, your setup is working correctly.

    :::image type="content" source="media/azure-front-door/response-header-x-cache-config-nocache.png" alt-text="Response header called x-cache with CONFIG_NOCACHE value for a Page.":::

## Set up WAF rules to analyze incoming requests

The next step in the setup is to configure the WAF rules on incoming requests. In this article, we'll cover only basic steps. For advanced WAF configuration, go to [Azure Web Application Firewall on Azure Front Door](/azure/web-application-firewall/afds/afds-overview).

1. On the left pane, select **Security**.

    :::image type="content" source="media/azure-front-door/security-tab.png" alt-text="Security tab for Azure Front Door configuration.":::

    During quick-create setup, we already set up a new WAF policy that shows up here. However, if you skipped that step, you can set up a new policy by selecting **New**.

1. Select the name of the WAF policy.

1. Select **Policy Settings**, and then:

    1. **Enable request body inspection**: Select this checkbox if you want the request body to be inspected in addition to cookies, headers, and URLs.

    1. **Redirect URL**: Enter a non-site URL. This URL is where the user would be redirected if a WAF rule were set to redirect. Ensure that this URL is accessible publicly and anonymously.

    1. **Block Request Status Code**: This HTTP status code is returned to the user if the request is blocked by WAF.

    1. **Block response body**: You can add a custom message here that will be shown to the user if the request is blocked by WAF.

    :::image type="content" source="media/azure-front-door/waf-policy-settings.png" alt-text="Policy Settings for WAF.":::

1. To configure the rule set against which every request will be evaluated, do the following:

    1. On the left pane, select **Managed Rules**.

        :::image type="content" source="media/azure-front-door/managed-rules.png" alt-text="Managed rules - rule set":::

    1. On the command bar, select **Assign**, and then select from the list of default rule sets. Managed rule sets are managed by Microsoft and updated regularly. For more information about rule sets, go to [Web Application Firewall DRS rule groups and rules](/azure/web-application-firewall/afds/waf-front-door-drs).

        :::image type="content" source="media/azure-front-door/manage-rule-set.png" alt-text="Manage rule set - Assign":::

After the managed rule set is assigned, your setup is complete. As an extra step, you can also look at setting up exclusion lists for existing rules and enabling custom rules.

> [!IMPORTANT]
> By default, WAF is set up in **Detection Policy** mode, which detects issues against the defined rule set and logs them. However, this mode doesn't block the requests. To block requests, WAF must be switched to **Prevention** mode.

We recommend that you perform thorough testing in Prevention mode to verify that all the scenarios are working and to ensure that you don't have to tweak the rule set or add exclusion policies. You should only enable Prevention mode after you've verified that the entire setup is working as expected.

## Set up Power Pages to accept traffic only from Azure Front Door

The last step in this setup is to ensure that your Power Pages site accepts traffic only from Azure Front Door. For this verification, we'll need to enable [IP address restrictions](/power-apps/maker/portals/admin/ip-address-restrict) on the site.

To find the IP address range on which Azure Front Door operates, go to [How do I lock down the access to my back end to only Azure Front Door?](/azure/frontdoor/front-door-faq#how-do-i-lock-down-the-access-to-my-backend-to-only-azure-front-door-).

> [!NOTE]
> Power Pages doesn't support **X-Azure-FDID**–based filtering.

## Increase origin response time

By default, Azure Front Door has an origin response timeout of 60 seconds. However, we recommend increasing this to 240 seconds to ensure that long-running scenarios like file uploads or export to Excel work as expected.

1. On the left pane, select **Endpoint manager**.

    :::image type="content" source="media/azure-front-door/endpoint-manager-tab.png" alt-text="Select Endpoint manager.":::

1. Select **Edit endpoint**.

    :::image type="content" source="media/azure-front-door/edit-endpoint.png" alt-text="Select to edit endpoint.":::

1. In the upper-right corner, select **Endpoint properties**.

    :::image type="content" source="media/azure-front-door/endpoint-properties.png" alt-text="Select properties for endpoint.":::

1. Change the origin response time to 240 seconds, and then select **Update**.

    :::image type="content" source="media/azure-front-door/update-endpoint.png" alt-text="Set the endpoint origin response time to 240 seconds.":::

### See also

[What is Azure Front Door?](/azure/frontdoor/front-door-overview) <br>
[Quickstart: Create an Azure Front Door profile - Azure portal](/azure/frontdoor/create-front-door-portal) <br>
[Create a custom domain on Azure Front Door Standard/Premium SKU using the Azure portal](/azure/frontdoor/standard-premium/how-to-add-custom-domain) <br>
[How do I lock down the access to my back end to only Azure Front Door?](/azure/frontdoor/front-door-faq#how-do-i-lock-down-the-access-to-my-backend-to-only-azure-front-door-) <br>
[Azure Front Door Rules Engine match conditions](/azure/frontdoor/front-door-rules-engine-match-conditions) <br>
