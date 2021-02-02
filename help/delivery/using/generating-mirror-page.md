---
solution: Campaign Classic
product: campaign
title: Sending an email with Adobe Campaign Classic
description: Learn about email delivery parameters
audience: delivery
content-type: reference
topic-tags: sending-emails
---

# Generating the mirror page {#generating-mirror-page}

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
