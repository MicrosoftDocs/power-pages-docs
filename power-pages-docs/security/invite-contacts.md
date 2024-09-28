---
title: Invite contacts to your Power Pages site
description: Learn how to create and send invitations to users to register on sites you create with Microsoft Power Pages.
ms.date: 07/20/2023
ms.topic: how-to
author: sandhangitmsft
ms.author: sandhan
ms.reviewer: danamartens
contributors:
    - nickdoelman
    - sandhangitmsft
ms.custom: bap-template
---

# Invite contacts to your Power Pages site

You can register users on your site directly by [adding a username and password](external-access.md) to their contact record. If you need to add many users to your site, an easier way is to send them an invitation by automated email. The email contains a link to your website and an invitation code that can include granting the user specific roles or privileges. With a Power Pages invitation, you can:

- Send a single invitation or invite a group.
- Specify an expiration date.
- Make the invitation appear to be sent by a specific user or site contact.

And when a contact redeems the invitation, Power Pages can:

- Assign the contact to an account.
- Assign the contact to one or more roles.
- Execute a workflow.

Contacts can redeem an invitation using any of the [authentication methods](authentication/configure-site.md) that Power Pages supports. [Learn more about local authentication, registration, and other settings](authentication/set-authentication-identity.md). When a contact redeems an invitation, it creates an Invite Redemption activity in both the invitation record and the contact record.

Power Pages uses the send invitation workflow to send your invitations. Edit the workflow's email template to customize the message and provide the link to your site's invitation redemption page.

The workflow sends the email only to the invited contact's primary email address (emailaddress1), not to a secondary (emailaddress2) or alternate (emailaddress3) address.

> [!IMPORTANT]
> Don't convert the send invitation workflow to a [real-time workflow](/power-apps/maker/data-platform/overview-realtime-workflows). It is **not supported** and will cause issues with the invitation process.

Use the [Portal Management app](../configure/portal-management-app.md) to create and edit invitations.

## Create and send an invitation from a contact record

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com) and open your site for editing.

1. In the left side panel, select **More items** (**&hellip;**) > **Portal Management**.

1. In the left side panel of the Portal Management app, scroll down to the **Security** section and select **Contacts**.

1. Select a contact.

1. In the command bar, select **Create Invitation**. It may be hidden in the **More commands** (**&vellip;**) menu.

1. Select or enter the [invitation attributes](#invitation-attributes).

1. Select **Save**.

1. In the command bar, select **Flow** > **Send Invitation**. It may be hidden in the **More commands** (**&vellip;**) menu.

1. Select **OK**.

## Create and send an invitation from the Invitations page

The **Invitations** page lists all the invitations you've created. Select a view to list new, open, completed (redeemed), and inactive invitations.

1. In the Portal Management app, left side panel, select **Security** > **Invitations**.

1. In the command bar, select **+ New**.

1. Select or enter the [invitation attributes](#invitation-attributes).

1. Select **Save**.

1. In the command bar, select **Flow** > **Send Invitation**.

### Send multiple invitations at the same time

1. In the Portal Management app, left side panel, select **Security** > **Invitations**.

1. In the list of views, select **New invitations** or **Open invitations**.

1. Select the invitations you want to send as a group.

1. In the command bar, select **Flow** > **Send Invitation**. It may be hidden in the **More commands** (**&vellip;**) menu.

1. Select **OK**.

## Invitation attributes

The following table describes the invitation attributes you can change.

| Name | Description |
|------|-------------|
| Name | Enter a descriptive name to help you recognize the invitation. If you create the invitation from a contact record, the contact's name is filled automatically, but you can change it if you like. |
| Type | Select **Single** to invite one contact, who can redeem the invitation once. Select **Group** to add multiple contacts to the invitation, with multiple redemptions. |
| Owner/Sender | By default, whoever creates the invitation owns it and is the sender when the invitation is sent. You can select a different owner if the user you select has sufficient privileges. If the **From** field in the invitation email contains someone else, you can override the address in the send invitation workflow. |
| Invitation Code | A unique code is generated for each invitation. Only the invited contact sees it, in the invitation email. You can change it if you like. |
| Expiry Date | (Optional) Select a date after which the invitation can no longer be redeemed. |
| Inviter | (Optional) If a contact should appear as the sender of the invitation, select the contact's name. |
| Invited Contact(s) | Select a contact, if the invitation type is **Single**, or contacts if it's a **Group** invitation, to invite. If you create the invitation from a contact record, the contact's name is listed automatically. |
| Assign to Account | (Optional) Select an account record to associate with the contact when the invitation is redeemed. |
| Execute Workflow on Redeeming Contact | (Optional) Select a workflow process to execute with the contact as the primary entity when the invitation is redeemed. |
| Assign to Web Roles | Select the web roles to associate with the contact when the invitation is redeemed. |
| Redeemed Contact(s) | Lists the contacts who have redeemed the invitation. |
| Maximum Redemptions Allowed | For group invitations only, enter the number of times the invitation can be redeemed. |
| Number of Successful Redemptions | For group invitations only, displays the number of times the invitation has been redeemed. |

### See also

[Add a username to a contact record](external-access.md#add-a-username-to-a-contact-record)  
[Local authentication, registration, and other settings](authentication/set-authentication-identity.md)
