---
solution: Campaign Classic
product: campaign
title: Sending an email with Adobe Campaign Classic
description: Learn how to send an email and discover the specificities of delivering emails.
audience: delivery
content-type: reference
topic-tags: sending-emails
---

# Sending an email{#sending-an-email}

To approve your email and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

<!--add screnn: ![](assets/email-send-button.png)-->

To validate and send an email, refer to the detailed process presented in the sections below:
* [Validating the delivery](../../delivery/using/steps-validating-the-delivery.md)
* [Sending the delivery](../../delivery/using/steps-sending-the-delivery.md)

The following sections detail the options and parameters that are specific to delivering emails:
* [Email BCC](../../delivery/using/email-bcc.md)
* [Generating the mirror page](../../delivery/using/generating-mirror-page.md)
* [Sending emails with the Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)

## Generating the mirror page {#generating-the-mirror-page}

The mirror page is an HTML page accessible online via a web browser. Its content is identical to the email.

By default, the mirror page is generated if the link is inserted in the content of the mail. For more on personalization blocks insertion, refer to [Personalization blocks](../../delivery/using/personalization-blocks.md).

In the delivery properties, the **[!UICONTROL Mode]** field of the **[!UICONTROL Validity]** tab lets you modify the generation mode for this page.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>An HTML content must have been defined for the delivery for the mirror page to be created.

In addition to the default mode, the following options are also available:

* **[!UICONTROL Force the generation of the mirror page]** : even if no link to the mirror page is inserted in the delivery, the mirror page will be created.
* **[!UICONTROL Do not generate the mirror page]** : no mirror page is generated, even if the link is present in the delivery.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : this option lets you access the content of the mirror page, with personalization information, in the delivery log window. To do this, after the end of the delivery, click the **[!UICONTROL Delivery]** tab and select the line of the recipient whose mirror page you wish to view. Click the **[!UICONTROL Display the mirror page for this message...]** link.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Managing bounce emails {#managing-bounce-emails}

The **[!UICONTROL SMTP]** tab of the delivery parameters lets you configure the management of bounce mails.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

By default, bounced emails are received in the default error box of the platform, but you can define a specific error address for a delivery.

You can also define a specific address from this screen in order to investigate the reasons for bounce mails when these could not be automatically qualified by the application. For each of these fields, the 'add personalized fields' icon lets you add personalization parameters.

## Character encoding {#character-encoding}

In the **[!UICONTROL SMTP]** tab of the delivery parameters, the **[!UICONTROL Character encoding]** section allows you to set a specific encoding.

The default encoding is UTF-8. If some of your recipients' email providers do not support the UTF-8 standard encoding, you may want to set a specific encoding to properly display the special characters to your emails' recipients.

For example, you want to send an email containing Japanese characters. To make sure that all characters will be correctly displayed to your recipients in Japan, you may want to use an encoding that will support the Japanese characters rather than the standard UTF-8.

To do this, select the **[!UICONTROL Force the encoding used for messages]** option in the **[!UICONTROL Character encoding]** section and choose an encoding from the drop-down list that is displayed.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Adding SMTP headers {#adding-smtp-headers}

It is possible to add SMTP headers to your deliveries. To do this, use the relevant section of the **[!UICONTROL SMTP]** tab in the delivery.

The script entered in this window must reference one header per line in the following form: **name:value**.

Values are encoded automatically if necessary.

>[!CAUTION]
>
>Adding a script for inserting additional SMTP headers is reserved for advanced users.
>
>The syntax of this script must comply with the requirements of this content type: no unused space, no empty line, etc.
