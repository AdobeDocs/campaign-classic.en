---
product: campaign
title: Validating
description: Validating
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Direct Mail
hide: true
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
TQID: https://experienceleague.adobe.com/I31u-kAqMRpzti-bOtfYjrGbwvmsfeEPwWU7kCFLzcQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
---
# Validating{#validating}

 

Global concepts when validating a delivery are presented in [this section](steps-validating-the-delivery.md).

The output file of a direct mail delivery is generated during the delivery analysis. The file's content depends on the selected output columns (refer to [Extraction file](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>The analysis phase is detailed in [Analyzing the delivery](steps-validating-the-delivery.md#analyzing-the-delivery).

During the analysis phase, the file is generated but information concerning recipients (i.e. delivery logs) is not updated. You can therefore cancel this job without running any risks.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. A confirmation message lets you launch the delivery.

The send confirmation starts the data extraction in the specified file.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the assistant and look at the delivery logs via the **[!UICONTROL Delivery]** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

There are two modes:

* **[!UICONTROL Messages are considered sent after validation]** (default mode): in this function mode, all broadlogs are updated when the operator confirms the send (their status passes from 'Pending delivery' to 'Sent') and the delivery is automatically set to **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : this mode allows you to update the broadlogs via an external file sent by the service provider. In this case, a workflow to process this information needs to be used in order to update the broadlog status.

  >[!NOTE]
  >
  >In this case, the delivery's status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
