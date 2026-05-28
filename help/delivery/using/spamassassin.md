---
product: campaign
title: SpamAssassin
description: Learn how to set up email spam detection with SpamAssassin
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
TQID: https://experienceleague.adobe.com/nZB19N90xSjDCNnibtwcPBm75SSyxkq1hQxICXCOg2A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
---
# SpamAssassin{#spamassassin}

Adobe Campaign can be configured to work with [SpamAssassin](https://spamassassin.apache.org), a third-party service used for email spam filtering. This allows you to score emails to determine whether a message runs the risk of being considered as spam by the anti-spam tools used upon receipt.

SpamAssassin leverages a variety of spam-detection techniques, including:

* DNS-based and fuzzy-checksum-based spam detection
* Bayesian filtering
* External programs
* Denylists
* Online databases

>[!NOTE]
>
>SpamAssassin must be installed and configured on the Adobe Campaign application server. For more on this, refer to [this section](../../installation/using/configuring-spamassassin.md).
>
>The rules that govern whether an element is spam or not are managed via SpamAssassin and can be edited by an administrator with privileges.

## Use SpamAssassin in Campaign {#using-spamassassin}

Once you have created your email delivery and defined its content, follow the steps below to evaluate the risks.

For more on creating and designing a delivery, refer to [this section](about-email-channel.md).

1. Go to the **[!UICONTROL Preview]** tab.
1. Select a recipient to preview your delivery.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >If you do not select a recipient, the anti-spam checking cannot be performed.

1. A warning message gives the result of the test. If a high level of risk is detected, the following warning message is displayed:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Click the **[!UICONTROL More...]** link next to the warning.
1. Select the **[!UICONTROL Anti-spam checking]** tab.
1. Go to the **[!UICONTROL Points / Rule / Description]** section to view the reasons for this risk.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Each time you click the **[!UICONTROL Anti-spam checking]**, the SpamAssassin service is called and the message is analyzed again for anti-spam detection. Make sure you changed your content before running the anti-spam analysis again.
