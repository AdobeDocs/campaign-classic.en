---
product: campaign
title: About deliveries settings
description: Discover the specific v7 delivery settings
feature: Channel Configuration
role: User
hide: yes
hidefromtoc: yes
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
---
# Delivery settings {#about-delivery-settings}

The following settings are specific to Campaign Classic. For other delivery settings, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}. 

## Delivery analysis {#delivery-analysis}

### Improve the delivery analysis performance {#improving-delivery-analysis}

To speed up the delivery preparation, you can check the **[!UICONTROL Prepare the delivery parts in the database]** option before launching the analysis.

When this option is enabled, the delivery preparation is performed directly within the database, which can significantly accelerate the analysis.

Currently, this option is only available when the following conditions are met:

* The delivery must be an email. The other channels are not supported for now.
* You must not use mid-sourcing or external routing, only bulk delivery routing type. You can check the routing that is used in the **[!UICONTROL General]** tab of the **[!UICONTROL Delivery properties]**.
* You cannot target a population coming from an external file. For a single delivery, click the **[!UICONTROL To]** link from the **[!UICONTROL Email parameters]** and check that the **[!UICONTROL Defined in the database]** option is selected. For a delivery used in a workflow, check that the recipients are **[!UICONTROL Specified by the inbound event(s)]** in the **[!UICONTROL Delivery]** tab.
* You must be using a PostgreSQL database.

### Configure the analysis priority {#analysis-priority-}

When the delivery is part of a campaign, the **[!UICONTROL Advanced]** tab offers an additional option. This lets you organize the processing order for deliveries in the same campaign.

Before sending, each delivery is analyzed. The analysis duration depends on the delivery extraction file. The more significant the size of the file, the longer the analysis takes, making the following deliveries wait.

The options for the **[!UICONTROL Message preparation by the scheduler]** let you prioritize the delivery analysis in a campaign workflow.

![](assets/delivery_analysis_priority.png)

If a delivery is too large, it is better to assign a low priority to it in order to avoid slowing down the analysis of other workflow deliveries.

>[!NOTE]
>
>To ensure that the larger delivery analyses do not slow down the progress of your workflows, you can schedule their executions by ticking the **[!UICONTROL Schedule execution for a time of low activity]**.

## Delivery sending {#delivery-sending}

### Configure retries {#configuring-retries}

Temporarily undelivered messages due to a **Soft** or **Ignored** error are subject to an automatic retry. The delivery failure types and reasons are presented in this [section](delivery-failures-quarantine.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), the retry settings in the delivery are no longer used by Campaign. Soft bounce retries and the length of time between them are determined by the Enhanced MTA based on the type and severity of the bounce responses coming back from the message's email domain.

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, the central section of the **[!UICONTROL Delivery]** tab for delivery parameters indicates how many retries should be performed the day after the delivery and the minimum delay between retries.

![](assets/s_ncs_user_wizard_retry_param.png)

By default, five retries are scheduled for the first day of the delivery with a minimum interval of one hour spread out over the 24 hours of the day. One retry per day is programmed after that and until the delivery deadline, which is defined in the **[!UICONTROL Validity]** tab. See [Define the validity period](#defining-validity-period).

### Define the validity period {#defining-validity-period}

When the delivery has been launched, the messages (and any retries) can be sent until the delivery deadline. This is indicated in the delivery properties, via the **[!UICONTROL Validity]** tab.

![](assets/s_ncs_user_email_del_valid_period.png)

* The **[!UICONTROL Delivery duration]** field lets you enter the limit for global delivery retries. This means that Adobe Campaign sends the messages beginning on the start date, and then, for messages returning an error only, regular, configurable retries are performed until the validity limit is reached.

  You can also choose to specify dates. To do this, select **[!UICONTROL Explicitly set validity dates]**. In this case, the delivery and validity limit dates also let you specify the time. The current time is used by default, but you can modify this directly in the input field.

  >[!IMPORTANT]
  >
  >For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), the **[!UICONTROL Delivery duration]** setting in your Campaign email deliveries will be used only if set to **3.5 days or less**. If you define a value higher than 3.5 days, it will not be taken into account.

* **Validity limit of resources**: The **[!UICONTROL Validity limit]** field is used for uploaded resources, mainly for the mirror page and images. The resources on this page are valid for a limited time (to save disk space).

  The values in this field can be expressed in the units listed in [this section](../../platform/using/adobe-campaign-workspace.md#default-units).
