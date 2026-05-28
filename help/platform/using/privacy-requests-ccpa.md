---
product: campaign
title: Opt-out for the Sale of Personal Information
description: Learn about opt-out for the sale of personal data
feature: Privacy, Privacy Tools
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
TQID: https://experienceleague.adobe.com/EIMnHxqbi5XFMKI5kQRv11A3c-g50crZlx-Uq-ZcowE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences (Campaign)
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles (Campaign)
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences (Campaign)
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor (Campaign)
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management (Campaign)
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Opt-out for the Sale of Personal Information (CCPA) {#sale-of-personal-information-ccpa}

 

The **California Consumer Privacy Act** (CCPA) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

The configuration and usage of Access and Delete requests are common to both GDPR and CCPA. This section presents the opt-out for the sale of personal data, which is specific to CCPA.

In addition to the [Consent management](privacy-management.md#consent-management) tools provided by Adobe Campaign, you have the possibility to track whether a consumer has opted-out for the sale of Personal Information.

Contacts can decide, through your system, that they do not allow their personal information from being sold to a third-party. In Adobe Campaign, you will be able to store and track this information.

For this to work, you need to extend the Profiles table and add an **[!UICONTROL Opt-Out for CCPA]** field.

>[!IMPORTANT]
>
>It is your responsibility as the Data Controller to receive the Data Subject's request and to keep track of the request dates for CCPA. As a technology provider, we only provide a way to opt-out. For more on your role as a Data Controller, see [Personal data and Personas](privacy-and-recommendations.md#personal-data).

## Prerequisite {#ccpa-prerequisite}

To leverage this information, you need to create this field in Adobe Campaign Classic. For this, you will add a boolean field to the **[!UICONTROL Recipient]** table. When a new field is created, it is automatically supported by the Campaign API.

If you use a custom recipient table, you also need to perform this operation.

For more detailed information on how to create a new field, refer to the [Schema edition documentation](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Modifying schemas is a sensitive operation which must be performed by expert users only.

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, select **[!UICONTROL Recipients]** as the **[!UICONTROL Document type]** and click **[!UICONTROL Next]**. For more on adding fields to a table, see [this section](../../configuration/using/new-field-wizard.md).

    ![](assets/privacy-ccpa-1.png)

1. For the **[!UICONTROL Field type]**, select **[!UICONTROL SQL field]**. For the Label, use **[!UICONTROL Opt-Out for CCPA]**. Select the **[!UICONTROL 8-bit integer (boolean)]** type and define the following unique **[!UICONTROL Relative path]**: @OPTOUTCCPA. Click **[!UICONTROL Finish]**.

    ![](assets/privacy-ccpa-2.png)

    This will extend or create the **[!UICONTROL Recipient (cus)]** schema. Click it to verify that the field has been correctly added.

    ![](assets/privacy-ccpa-3.png)

1. Click the **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** node of the explorer. In **[!UICONTROL Recipient (nms)]**, under "General Package", add an `<input>` element and use, for the xpath value, the relative path defined in step 2. For more on identifying a form, see [this section](../../configuration/using/identifying-a-form.md).

    ```
    <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
    ```

    ![](assets/privacy-ccpa-4.png)

1. Disconnect and re-connect. Follow the steps described in the next section to verify that the field is available on a recipient's details. 

## Usage {#usage}

It is the responsibility of the Data Controller to populate the value of the field and follow the CCPA guidelines and rules concerning data selling.

To populate the values, several methods can be used:

* Using Campaign's interface by editing the recipient's details
* Using the API
* Via a data import workflow

You should then ensure that you never sell to any third party the personal information of profiles who have opted-out.

1. To change the opt-out status, go to **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** and select a recipient. In the **[!UICONTROL General]** tab, you will see the field configured in the previous section.

    ![](assets/privacy-ccpa-5.png)

1. Configure the recipients list to display the op-out column. To learn how to configure lists, refer to the [detailed documentation](../../platform/using/adobe-campaign-ui-lists.md#configuring-lists).

    ![](assets/privacy-ccpa-6.png)

1. You can click the column to sort recipients according to the opt-out information. You can also create a filter to only display recipients who have opted-out. For more information about filters, refer to the [Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.


    ![](assets/privacy-ccpa-7.png)
