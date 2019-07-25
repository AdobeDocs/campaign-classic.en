---
title: Validating
seo-title: Validating
description: Validating
seo-description: 
page-status-flag: never-activated
uuid: 44ab6161-e05e-476b-9360-576027731f49
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 280ef617-e7e4-4dc6-b1dd-176699f24dac
index: y
internal: n
snippet: y
---

# Validating{#validating}

The execution of the delivery can be scheduled (in the calendar or a workflow) or launched manually.

To launch a delivery, edit it and click the **Send** button. Select **Deliver as soon as possible**.

Click **Next** and then **Analyze** to launch the delivery analysis.

The output file is then generated. Its content depends on the selected output columns (refer to [Extraction file](../../delivery/using/validating.md#extraction-file)).

>[!NOTE]
>
>The analysis phase is detailed in [Analyzing the delivery](../../delivery/using/validating.md#analyzing-the-delivery).

You can stop this job at any time by clicking **Stop**.

![](assets/s_ncs_user_stop_analyze.png)

During the analysis phase, the file is generated but information concerning recipients (i.e. delivery logs) is not updated. You can therefore cancel this job without running any risks.

Check the result of the analysis and the content of the output file before clicking **Confirm delivery**. A confirmation message lets you launch the delivery.

The send confirmation starts the data extraction in the specified file.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the wizard and look at the delivery logs via the **Delivery** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **Analysis** tab of the delivery properties.

There are two modes:

* **Messages are considered sent after validation** (default mode): in this function mode, all broadlogs are updated when the operator confirms the send (their status passes from 'Pending delivery' to 'Sent') and the delivery is automatically set to **Finished**.
* **A file of results determines the messages that are sent and those that have failed**: this mode allows you to update the broadlogs via an external file sent by the service provider. In this case, a workflow to process this information needs to be used in order to update the broadlog status.

  >[!NOTE]
  >
  >In this case, the delivery's status also needs to be changed to **Finished** by the user as soon as the broadlogs are updated.

