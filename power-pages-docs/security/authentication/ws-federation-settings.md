---
title: Set up a WS-Federation provider with AD FS
description: Learn how to set up a WS-Federation identity provider with Active Directory Federation Services (AD FS) for use with sites you create with Microsoft Power Pages.
ms.date: 09/10/2024
ms.topic: how-to
author: sandhangitmsft
ms.author: bipuldeora
ms.reviewer: danamartens
contributors:
    - sandhangitmsft
    - dileepsinghmicrosoft
ms.custom: bap-template
---

# Set up a WS-Federation provider with AD FS

Active Directory Federation Services (AD FS) is one of the WS-Federation identity providers you can use to [authenticate visitors](configure-site.md) to your Power Pages site. You can use any provider that conforms to the WS-Federation specification.

This article describes the following steps:

- [Set up AD FS in Power Pages](#set-up-ad-fs-in-power-pages)
- [Create an AD FS relying party trust](#create-an-ad-fs-relying-party-trust)
- [Finish setting up the provider](#finish-setting-up-the-provider)

> [!IMPORTANT]
> The steps for setting up AD FS might vary depending on the version of your AD FS server.

## Set up AD FS in Power Pages

Set AD FS as an identity provider for your site.

1. In your Power Pages site, select **Security** > **Identity providers**.

    If no identity providers appear, make sure **External login** is set to **On** in your site's [general authentication settings](configure-site.md#select-general-authentication-settings).

1. Select **+ New provider**.

1. Under **Select login provider**, select **Other**.

1. Under **Protocol**, select **WS-Federation**.

1. Enter a name for the provider.

    The provider name is the text on the button that users see when they select their identity provider on the sign-in page.

1. Select **Next**.

1. Under **Reply URL**, select **Copy**.

    Don't close your Power Pages browser tab. You'll return to it soon.

## Create an AD FS relying party trust

1. In Server Manager, select **Tools**, and then select **AD FS Management**.

1. Select **Trust Relationships** > **Relying Party Trusts**.

1. Select **Add Relying Party Trust**.

1. Select **Start**.

1. Select **Enter data about the relying party manually**, and then select **Next**.

1. Enter a name; for example, *https://portal.contoso.com/*.

1. Select **Next**.

1. Select **AD FS 2.0 profile**, and then select **Next**.

1. On the **Configure Certificate** page, select **Next**.

1. Select **Enable support for the WS-Federation Passive protocol**.

1. Under **Relying party WS-Federation Passive protocol URL**, enter the reply URL [you copied](#set-up-ad-fs-in-power-pages). AD FS requires that the website run HTTPS, not HTTP.

1. Select **Next**.

1. On the **Configure Identifiers** page, enter your site's URL, and then select **Add**.

    You can add more identities for each additional relying party website if needed. Users can authenticate using any available identities.

1. Select **Next**.

1. On the **Configure Multi-factor Authentication Now?** page, select **I do not want to configure multi-factor authentication settings for this relying party trust at this time**.

1. On the **Choose Issuance Authorization Rules** page, select **Permit all users to access this relying party**, and then select **Next**.

1. Review the trust settings, and then select **Next**.

1. Select **Close**.

1. In **Edit Claim Rules**, select one the following tabs, depending on the trust you're editing and in which rule set you want to create the rule:

    - **Acceptance Transform Rules**
    - **Issuance Transform Rules**
    - **Issuance Authorization Rules**
    - **Delegation Authorization Rules**

1. Select **Add Rule**.

1. In the **Claim rule template** list, select **Transform an Incoming Claim**, and then select **Next**.

1. Enter or select the following values:

    - **Claim rule name**: *Transform Windows account name to Name ID*

    - **Incoming claim type**: **Windows account name**

    - **Outgoing claim type**: **Name ID**

    - **Outgoing name ID format**: Unspecified

1. Select **Pass through all claim values**.

1. Select **Finish**, and then select **OK**.

## Finish setting up the provider

After you set up the AD FS relying party trust:

1. [Create an app registration in Azure](ws-federation-settings-azure-ad.md#create-an-app-registration-in-azure).

1. [Enter site settings in Power Pages](ws-federation-settings-azure-ad.md#enter-site-settings-in-power-pages).

### See also

[Set up a WS-Federation provider with Microsoft Entra ID](ws-federation-settings-azure-ad.md)