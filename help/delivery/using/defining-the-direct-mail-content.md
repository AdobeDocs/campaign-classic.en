---
product: campaign
title: Define the direct mail content
description: Learn how to define the direct mail content
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Direct Mail
role: User
hide: true
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
TQID: https://experienceleague.adobe.com/LybEpDwVDNAGQg5CA2nZ3IkNoyHFiYvNuKm-VXYW4s4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
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
# Define the direct mail content{#defining-the-direct-mail-content}

## Extraction file {#extraction-file}

The name of the file which contains the extracted data is defined in the **[!UICONTROL File]** field. The button to the right of the field lets you use personalization fields to create the file name.

By default, the extraction file is created and stored on the server. You can save it on your computer. To do this, check the **[!UICONTROL Download the generated file after the analysis of the delivery]**. In this case, you need to indicate the access path to the local storage directory as well as the file name.

![](assets/s_ncs_user_mail_delivery_local_file.png)

For a direct mail delivery, the content of the extraction is defined in **[!UICONTROL Edit the extraction file format...]** link.

![](assets/s_ncs_user_mail_delivery_format_link.png)

This link lets you access the extraction assistant and define the information (columns) to be exported into the output file.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

It is possible to insert a personalized URL into the extraction file. For more on this, refer to [this section](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>This assistant includes the steps of the export assistant detailed in the [Getting Started](../../platform/using/executing-export-jobs.md) section.
