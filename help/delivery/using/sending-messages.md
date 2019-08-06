---
title: Sending messages
seo-title: Sending messages
description: Sending messages
seo-description: 
page-status-flag: never-activated
uuid: 46bd4671-fce4-4674-befe-08d9cde75a51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: d663d200-0738-4873-91e3-0357a63baec7
index: y
internal: n
snippet: y
---

# Sending messages{#sending-messages}

To approve your message and send it to the recipients of the delivery being created, click **Send**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validating the delivery](../../delivery/using/sending-messages.md#validating-the-delivery)
* [Sending the delivery](../../delivery/using/sending-messages.md#sending-the-delivery)

## Archiving emails {#archiving-emails}

Adobe Campaign enables you to store emails on an external system through BCC by simply adding a BCC email address to your message target. Once the option activated, an exact copy of all sent messages will be kept for this delivery.

For more information on configuring Email BCC, refer to [this section](../../installation/using/email-archiving.md).

>[!NOTE]
>
>This feature is optional. Please check your license agreement and contact your account executive to activate it.

When creating a new delivery or delivery template, Email BCC is not enabled by default, even if the option has been purchased. You must enable it manually in each delivery or template where you want to use it.

To do this, follow the steps below:

1. Go to **Campaign Management** > **Deliveries** or **Resources** > **Templates** > **Delivery templates**.
1. Select the delivery of your choice or duplicate the out-of-the-box **Email delivery** template, then select the duplicated template.
1. Click the **Properties** button.
1. Select the **Delivery** tab.
1. Check the **Archive emails** box to keep a copy of all sent messages for this delivery or for each delivery based on this template.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >If the emails sent to the BCC address are opened and clicked through, this will be taken into account in the **Total opens** and **Clicks** from the send analysis, which could cause some miscalculations.

## Generating the mirror page {#generating-the-mirror-page}

The mirror page is an HTML page accessible online via a web browser. Its content is identical to the email.

By default, the mirror page is generated if the link is inserted in the content of the mail. For more on personalization blocks insertion, refer to [Personalization blocks](../../delivery/using/personalization-blocks.md).

In the delivery properties, the **Mode** field of the **Validity** tab lets you modify the generation mode for this page.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>An HTML content must have been defined for the delivery for the mirror page to be created.

In addition to the default mode, the following options are also available:

* **Force the generation of the mirror page**: even if no link to the mirror page is inserted in the delivery, the mirror page will be created.
* **Do not generate the mirror page**: no mirror page is generated, even if the link is present in the delivery.
* **Generates a mirror page accessible using only the message identifier**: this option lets you access the content of the mirror page, with personalization information, in the delivery log window. To do this, after the end of the delivery, click the **Delivery** tab and select the line of the recipient whose mirror page you wish to view. Click the **Display the mirror page for this message...** link.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Managing bounce emails {#managing-bounce-emails}

The **SMTP** tab of the delivery parameters lets you configure the management of bounce mails.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

By default, bounced emails are received in the default error box of the platform, but you can define a specific error address for a delivery.

You can also define a specific address from this screen in order to investigate the reasons for bounce mails when these could not be automatically qualified by the application. For each of these fields, the 'add personalized fields' icon lets you add personalization parameters.

## Adding SMTP headers {#adding-smtp-headers}

It is possible to add SMTP headers to your deliveries. To do this, use the relevant section of the **SMTP** tab in the delivery.

The script entered in this window must reference one header per line in the following form: **name:value**.

Values are encoded automatically if necessary.

>[!CAUTION]
>
>Adding a script for inserting additional SMTP headers is reserved for advanced users.   
>The syntax of this script must comply with the requirements of this content type: no unused space, no empty line, etc.

