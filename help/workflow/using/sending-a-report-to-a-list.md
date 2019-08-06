---
title: Sending a report to a list
seo-title: Sending a report to a list
description: Sending a report to a list
seo-description: 
page-status-flag: never-activated
uuid: 28b7a568-fd5d-4f75-b87a-b4254fbd4e93
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: cb5a8a60-bb35-424e-9b96-5b4cbd068bbe
index: y
internal: n
snippet: y
---

# Sending a report to a list{#sending-a-report-to-a-list}

This use case details how to generate a monthly out-of-the-box **Tracking indicators** report in PDF format and how to send it to a list of recipients.

![](assets/use_case_report_intro.png)

The main implementation steps for this use case are:

* Creating a list of recipients who will receive the delivery (refer to: [Step 1: Creating the recipient list](../../workflow/using/sending-a-report-to-a-list.md#step-1--creating-the-recipient-list)). 
* Creating a delivery template that will let you generate a new delivery each time the workflow is executed (refer to: [Step 2: Creating the delivery template](../../workflow/using/sending-a-report-to-a-list.md#step-2--creating-the-delivery-template)).
* Creating a workflow that will let you generate the report in PDF format and send it to the list of recipients (refer to: [Step 3: Creating the workflow](../../workflow/using/sending-a-report-to-a-list.md#step-3--creating-the-workflow)).

## Step 1: Creating the recipient list {#step-1--creating-the-recipient-list}

Go to the **Profiles and targets** universe, click the **Lists** link, then the **Create** button. Select **New list** and create a new recipient list for the report to be sent to.

![](assets/use_case_report_1.png)

For more on creating lists, refer to this [section](../../platform/using/creating-and-managing-lists.md).

## Step 2: Creating the delivery template {#step-2--creating-the-delivery-template}

1. Go to the **Resources > Templates > Delivery templates** node of the Adobe Campaign explorer and duplicate the **Email delivery** out-of-the-box template.

   ![](assets/use_case_report_2.png)

   For more on creating a delivery template, refer to this [section](../../delivery/using/about-templates.md).

1. Enter the various template parameters: label, target (the list of previously created recipients), subject and content.

   ![](assets/use_case_report_3.png)

1. Each time the workflow is executed, the **Tracking indicators** report is updated (refer to [Step 3: Creating the workflow](../../workflow/using/sending-a-report-to-a-list.md#step-3--creating-the-workflow)). To include the latest version of the report in the delivery, you need to add a **Calculated attachment**:

   For more on creating a calculated attachment, refer to this [section](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

    * Click the **Attachments** link and click **Add**, then select **Calculated attachment**.
    
      ![](assets/use_case_report_4.png)

    * Go to the **Type** field and select the fourth option: **File name is computed during delivery of each message (it may then depend on the recipient profile)**. 
    
      ![](assets/use_case_report_5.png)

      The value entered in the **Label** field will not appear in the final delivery.
    
    * Go to the edit zone and enter the access path and name of the file. 
    
      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >The file must be present on the server. Its path and name must be identical to those entered in the **JavaScript code** type activity of the workflow (refer to: [Step 3: Creating the workflow](../../workflow/using/sending-a-report-to-a-list.md#step-3--creating-the-workflow)).

    * Select the **Advanced** tab and check **Script the name of the file name displayed in the mails sent**. Go to the edit zone and enter the name you want to give the attachment in the final delivery.
    
      ![](assets/use_case_report_6bis.png)

## Step 3: Creating the workflow {#step-3--creating-the-workflow}

The following workflow was created for this use case. It has three activities:

* One **Scheduler** type activity that lets you execute the workflow once a month,
* One **JavaScript code** type activity that lets you generate the report in PDF format,
* one **Delivery** type activity that uses the previously created delivery template.

![](assets/use_case_report_8.png)

1. Now go to the **Administration > Production > Technical workflows** node and create a new workflow.

   ![](assets/use_case_report_7.png)

1. Start by adding a **Scheduler** type activity and configure it so that the workflow executes on the first Monday of the month.

   ![](assets/use_case_report_9.png)

   For more on configuring the scheduler, refer to [Scheduler](../../workflow/using/scheduler.md).

1. Then add a **JavaScript code** type activity.

   ![](assets/use_case_report_10.png)

   Enter the following code in the edit zone:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   The following variables are used:

    * **var reportName**: enter the internal name of the report in double quotes. In this case, the internal name of the **Tracking indicator** report is "deliveryFeedback".
    * **var path**: enter the save path of the file ("tmp/files/"), the name you want to give the file ("deliveryFeedback") and the file extension (".pdf"). In this case, we have used the internal name as the file name. Values need to be between double quotes and separated by the "+" character.

      >[!CAUTION]
      >
      >The file must be saved on the server. You must enter the same path and the same name in the **General** tab of the edit window for the calculated attachment (refer to: [Step 2: Creating the delivery template](../../workflow/using/sending-a-report-to-a-list.md#step-2--creating-the-delivery-template)).

    * **var exportFormat**: enter the export format of the file ("PDF").
    * **var _ctx** (context): in this case, we are using the **Tracking indicators** report in its global context.

1. Finish by adding a **Delivery** type activity with the following options:

    * **Delivery**: select **New, created from a template**, and select the delivery template created previously.
    * For the **Recipients** and **Content** fields, select **Specified in the delivery**.
    * **Action to execute**: select **Prepare and start**. 
    * Un-check **Generate an outbound transition** and **Process errors**.

   ![](assets/use_case_report_11.png)

