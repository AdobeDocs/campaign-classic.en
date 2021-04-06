---
solution: Campaign Classic
product: campaign
title: Personalization fields
description: Personalization fields
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
---
# Personalization fields{#personalization-fields}

Personalization fields are used for first-level personalization of the content of delivered messages. The fields you insert in a main content show the position where to insert the data from the selected data source.

For example, the personalization field with the **<%= recipient.LastName %>** syntax tells Adobe Campaign to insert the name of the recipient into the database (recipient table).

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](#personalization-fields-video)

>[!CAUTION]
>
>Personalization fields content cannot exceed 1024 characters.

## Data sources {#data-sources}

Personalization fields can come from two types of data source, according to the delivery mode selected:

* The Adobe Campaign database is the data source. This is the most common case, with for example 'recipient personalization fields'. These are all the fields defined in the recipients table, whether standard fields (typically: last name, first name, address, town, date of birth, etc.) or user defined fields.
* An external file is the data source. These are all the fields defined in the columns of the file presented as input during a delivery using the data found in an external file.

>[!NOTE]
>
>An Adobe Campaign personalization tag always has the following form **<%=table.field%>**.

## Inserting a personalization field {#inserting-a-personalization-field}

To insert personalization fields, click the drop-down icon that is accessible from any header, subject, or message body editing field.

![](assets/s_ncs_user_add_custom_field.png)

After the selection of a data source (recipient fields or file field), this insertion takes the form of a command that will be interpreted by Adobe Campaign and replaced by the value of the field for a given recipient. The physical replacement can then be viewed in the **[!UICONTROL Preview]** tab.

## Personalization fields example {#personalization-fields-example}

We create an email in which we will first insert the name of the recipient and then add the profile creation date in the body of the message. To do this:

1. Create a new delivery or open an existing email type delivery.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Enter " **[!UICONTROL Special offer for]** " and use the button in the toolbar to insert a personalization field. Select **[!UICONTROL Recipients>Title]**.

    ![](assets/s_ncs_user_insert_custom_field.png)

1. Repeat the operation to insert the name of the recipient. Insert spaces between all the personalization fields.
1. Click **[!UICONTROL OK]** to validate.
1. Insert the personalization in the message body. To do this, click in the message content and click the field insertion button.
1. Select **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Select the field with the information to display and click **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Click the **[!UICONTROL Preview]** tab to view the personalization result. You must select a recipient to display that recipient's message.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >When a delivery is part of a workflow, you can use the data from the temporary workflow table. This data is grouped in the **[!UICONTROL Target extension]** menu. For more on this, refer to [this section](../../workflow/using/data-life-cycle.md#target-data).

## Optimizing personalization {#optimizing-personalization}

You can optimize personalization using a dedicated option: **[!UICONTROL Prepare the personalization data with a workflow]**, available in the **[!UICONTROL Analysis]** tab of the delivery properties. For more on analyzing the delivery, see [this section](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

During the delivery analysis, this option automatically creates and executes a workflow that stores all of the data linked to the target in a temporary table, including data from tables linked in FDA.

Checking this option can highly improve the delivery analysis performance when a lot of data are being processed, especially if the personalization data come from an external table through FDA. For more on this, see [Accessing an external database (FDA)](../../installation/using/about-fda.md).

For example, if you are experiencing performance issues when delivering to a high number of recipients while using a lot of personalization fields and/or personalization blocks in the content of your messages, this option can accelerate the handling of personalization and therefore the delivering of your messages.

To use this option, follow the steps below:

1. Create a campaign. For more on this, refer to [this section](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **Query** activity to your workflow. For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. Add an **[!UICONTROL Email delivery]** activity to the workflow and open it. For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. Go to the **[!UICONTROL Analysis]** tab of the **[!UICONTROL Delivery properties]** and select the **[!UICONTROL Prepare the personalization data with a workflow]** option.

   ![](assets/perso_optimization.png)

1. Configure the delivery and start the workflow to launch the analysis.

Once the analysis is done, the personalization data are stored in a temporary table through a temporary technical workflow that is created on the fly during the analysis.

This workflow is not visible in the Adobe Campaign interface. It is only meant to be a technical means to quickly store and handle personalization data.

Once the analysis is complete, go to the workflow **[!UICONTROL Properties]** and select the **[!UICONTROL Variables]** tab. There you can see the name of the temporary table that you may use to make an SQL call in order to display the IDs that it contains.

![](assets/perso_optimization_temp_table.png)

## Timing out personalization phase {#timing-out-personalization}

To improve delivery protection, you can set a time-out period for the personalization phase.

In the **[!UICONTROL Delivery]** tab of the **[!UICONTROL Delivery properties]**, select a maximum value in seconds for the **[!UICONTROL Maximum personalization run time]** option.

During preview or sending, if the personalization phase exceeds the maximum time that you set in this field, the process will be aborted with an error message and the delivery will fail.

![](assets/perso_time-out.png)

The default value is 5 seconds.

If you set this option to 0, there will be no time limit for the personalization phase.

## Tutorial video {#personalization-fields-video}

Learn how to add a personalization field to the subject line and the content of an email delivery.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).
