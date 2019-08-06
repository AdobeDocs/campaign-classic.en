---
title: Attaching files
seo-title: Attaching files
description: Attaching files
seo-description: 
page-status-flag: never-activated
uuid: a0079b2c-30fa-4914-ad4f-450b57030bd3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 264f7761-477d-4a54-a600-a0e2707306e8
index: y
internal: n
snippet: y
---

# Attaching files{#attaching-files}

## About email attachments {#about-email-attachments}

You can attach one or more files to an email delivery. There are two possible cases:

1. Select a file and attach it to the delivery as it is.
1. Personalize the content of the attachment for each recipient. In this case, you need to create a calculated attachment: the name of the attachment is computed at the time of delivery for each message depending on the recipient. The content can also be personalized and converted into PDF format at the time of delivery, if you have the **Variable Digital Printing** option.

>[!NOTE]
>
>This type of configuration is generally carried out in the delivery templates. For more on this, refer to [About templates](../../delivery/using/about-templates.md).

## Attaching a local file {#attaching-a-local-file}

To attach a local file to a delivery, click the **Attachments** link and select the file you want to attach to the message. 

![](assets/s_ncs_user_wizard_add_file.png)

You can also use the matching icon in the toolbar.

![](assets/s_ncs_user_wizard_add_file_ico.png)

Once the document is selected, it is immediately uploaded onto the server to be available at the time of delivery. 

![](assets/s_ncs_user_wizard_add_file_load.png)

>[!NOTE]
>
>For more on this, refer to [Adding attachments](../../delivery/using/attaching-files.md#adding-attachments).

## Creating a calculated attachment {#creating-a-calculated-attachment}

When you create a calculated attachment, the name of the attachment can be computed during analysis or delivery of each message and can depend on the recipient. It can also be personalized and converted to PDF.

![](assets/s_ncs_user_wizard_attachment.png)

To create a personalized attachment, click the **Attachments** link and then the **Add** button, and select **Calculated attachment**.

Select the type of calculation from the **Type** drop-down list:

![](assets/s_ncs_user_wizard_email01_136.png)

The following options are available:

* **File name is specified when creating the delivery template**
* **The content of the file is personalized and converted to PDF during the delivery of each message**
* **The file name is computed during delivery analysis (it cannot depend on the recipient profile)**
* **File name is computed at the time of delivery for each recipient (it can depend on the recipient)**

### Attach a local file {#attach-a-local-file}

When the attachment is a local file, select the option: **File name is specified when creating the delivery template**. The file is selected locally and uploaded onto the server. Follow the steps below:

1. Select the file to upload in the **Local file** field.
1. Specify the label if necessary. The label replaces the filename when viewed in messaging systems. If nothing is specified, the filename is used by default.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. If necessary, select **Upload file on the server**, and then click **Update on server** to start the transfer.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

   The file is then available on the server to be attached to the different deliveries created from this template.

### Attach a personalized message {#attach-a-personalized-message}

The option **The file content is personalized and converted into PDF format at the time of delivery for each message** lets you select a fine with personalization fields, such as the last name and first name of the intended recipient.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

For this type of attachment, apply the following configuration steps:

1. Select the file to upload.

   >[!NOTE]
   >
   >The source file must be created in LibreOffice. The instance must be configured in keeping with the prerequisites detailed in [this section](../../installation/using/before-starting.md).

1. Specify the label if necessary. 
1. Select **Upload file on the server**, and then click **Update on server** to start the transfer.
1. You can display a preview. To do this, select a recipient.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analyze your delivery and then start it.

   Each recipient receives a personalized PDF attached to the delivery.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

### Attach a calculated file {#attach-a-calculated-file}

You can calculate the attachment name during the delivery preparation. To do this, select the option **The file name is calculated during delivery analysis (it cannot depend on the recipient)**.

>[!NOTE]
>
>This option is used only when the delivery is sent by an external process or a workflow.

1. Specify the label you wish to apply to the attachment. 
1. Specify the access path of the file and its exact name in the definition window.

   >[!CAUTION]
   >
   >The file must be present on the server.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analyze and then start your delivery.

   The filename computation can be seen in the analysis log.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Attach a personalized file {#attach-a-personalized-file}

When selecting the attachment, you can choose the option **The file name is calculated during delivery for each recipient (it can depend on the recipient)**. You can then map recipient personalization data with the name of the file to send.

>[!NOTE]
>
>This option is used only when the delivery is sent by an external process or a workflow.

1. Specify the label you wish to apply to the attachment.
1. Specify the access path of the file and its exact name in the definition window. If the filename is personalized, you can use the Personalization fields for the relevant values.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!CAUTION]
   >
   >The file must be present on the server.

1. Analyze and then start your delivery.

   In the example below, the attached file was chosen according to its name as defined using the merge fields.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Attachment settings {#attachment-settings}

For the first two options, you can choose **Upload file on the server** by selecting the appropriate option. The **Update the file on the server** link lets you start uploading.

![](assets/s_ncs_user_wizard_email01_137.png)

A message tells you that the file has been uploaded to the server:

![](assets/s_ncs_user_wizard_email01_1371.png)

For a change of file, a warning message is displayed:

![](assets/s_ncs_user_wizard_email01_1372.png)

The **Advanced** tab lets you define advanced options on attached files:

* You can define filter options to avoid sending the attached file to all recipients. The option **Enable filtering of recipients who will receive the attachment** activates an input field used to define a recipient selection script, which must be entered in JavaScript.
* You can script the name of the file in order to personalize it.

  Enter your text in the window and use the personalization fields available in the drop-down list. In the following example, the filename is personalized to contain today's date and the name of the recipient.

  ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)

