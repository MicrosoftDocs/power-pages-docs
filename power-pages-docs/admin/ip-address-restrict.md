---
title: Restrict website access by IP address
description: Learn how to restrict website access by IP address.
author: neerajnandwana-msft

ms.topic: conceptual
ms.custom: 
ms.date: 07/09/2024
ms.subservice: 
ms.author: nenandw
ms.reviewer: kkendrick
contributors:
    - neerajnandwana-msft
    - nickdoelman
---

# Restrict website access by IP address

Once a website is provisioned, it's accessible by anyone from any computer.

> [!NOTE]
> Users will still need to provide credentials to view the site if it set to private mode. See [Site visibility](../security/site-visibility.md) for more details.

You can restrict access to your website from a list of IP addresses. For example, a government organization might want to surface their content only within their corporate network. A commercial organization might want to display the website only when it's published and not while it is in development to avoid any data leak.

When a request to the website is generated from any user, their IP address is evaluated against the allow list. If the IP address isn't on the list, the website displays a web page with an HTTP 403 status code.

To add or remove IP addresses, you must be assigned any one of the following roles:
- Service Administrator. More information: [Use the service admin role to manage your tenant](/power-platform/admin/use-service-admin-role-manage-tenant)  
- System Administrator of the Microsoft Dataverse environment selected for the website

## Add an IP address

To allow access to a website from an IP address or a set of IP addresses, you can add the IP addresses to the list. This allows the website to be accessed only from the list of added IP addresses. If you don't add any IP address, the website is accessible from all IP addresses.

Once you add an IP address to the restriction list, the website is accessible to the specified IP address only. If you try to access the website from any other IP addresses, access is denied and a web page with an HTTP 403 status code is displayed. The content of this web page is static and can't be modified.

:::image type="content" source="media/ip-address-restriction/error-403.png" alt-text="403 error when accessing website.":::

> [!NOTE]
> You must specify a public IP address that can be accessed by the website. Private IP address can't be accessed by the website.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to restrict by IP address.

1. In the site details page, in the **Security** section, select **IP Restrictions**.

1. On the side panel, select **+ New** to add a new IP address.

    :::image type="content" source="media/ip-address-restriction/configure-restricted-ip.png" alt-text="Configure IP address restriction.":::

1. In the Add an IP address window, enter the following values:

    - **Select type of IP address**: Select whether the IP address is IPv4 or IPv6.

    - **Specify IP address in CIDR notation**: Specify the IP address in CIDR notation. More information: [Classless Inter-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

1. Select **OK**.

## Remove an IP address

To remove access to a website from a previously allowed IP address, you can remove the IP address from the list. If you remove all IP addresses, the website is accessible from all IP addresses.

1. Open the [Power Platform admin center](https://aka.ms/ppac).

1. In the **Resources** section, select **Power Pages sites**.

1. Choose the site to which want to restrict by IP address.

1. In the site details page, in the **Security** section, select **IP Restrictions**.

1. Select the IP address you would like removed.

1. Select the ellipse (**...**) and select **Delete**.

1. Select **OK** in the confirmation message.

## See also
- [Site visibility](../security/site-visibility.md)
