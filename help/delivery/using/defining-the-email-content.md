---
solution: Campaign Classic
product: campaign
title: Defining the email content in Adobe Campaign Classic
description: Learn how to define the email content when using Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
---
# Defining the email content {#defining-the-email-content}

## Sender {#sender}

To define the name and address of the sender which will appear in the header of messages sent, click the **[!UICONTROL From]** link.

![](assets/s_ncs_user_wizard_email02.png)

This window lets you enter all the information required to create the email message headers. This information can be personalized. To do this, use the buttons to the right of the input fields to insert personalization fields.

To find out how to insert and use personalization fields, refer to [About personalization](../../delivery/using/about-personalization.md) section.

>[!NOTE]
>
>* The sender's address will be used for replies by default.
>* The header parameters must not be empty. By default, they contain the values input when configuring the deployment wizard. For further information, refer to the [Installation Guide](../../installation/using/deploying-an-instance.md).
>* The sender's address is mandatory to allow an email to be sent (RFC standard).
>* Adobe Campaign checks the syntax of email addresses entered.

>[!IMPORTANT]
>
>In the context of the checks implemented by Internet Access Providers (ISPs) to combat unsolicited email (spam), Adobe recommends creating email accounts that correspond to the addresses specified for deliveries and replies. Check with your messaging system administrator.

## Message subject {#message-subject}

The subject of the message is configured in the corresponding field. You can enter it directly in the field or click the **[!UICONTROL Subject]** link to enter a script. The personalization link lets you insert database fields in the subject.

>[!IMPORTANT]
>
>The message subject is mandatory.

![](assets/s_ncs_user_wizard_email_object.png)

The field content will be replaced by the value in the recipient profile when the message is sent.

For example, in the message above, the subject of the message is personalized for each recipient with data from their profile.

>[!NOTE]
>
>The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

You can also insert emoticons to your subject line with the **[!UICONTROL Insert emoticon]** pop-up window.

## Message content {#message-content}

>[!IMPORTANT]
>
>For privacy reasons, we recommend using HTTPS for all external resources.

The content of the message is defined in the lower section of the delivery configuration window.

Messages are sent in HTML or text format by default, according to recipient preference. We recommend creating content in both formats to ensure that messages can be correctly displayed in any mail system. For more on this, refer to [Selecting message formats](#selecting-message-formats).

* To import an HTML content, use the **[!UICONTROL Open]** button. You can also paste the source code directly into the **[!UICONTROL Source]** sub-tab.

  If you are using the [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE), refer to [Selecting a content template](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >The HTML content must be created beforehand, then imported into Adobe Campaign. The HTML editor is not designed for content creation.

  The **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. The personalization fields and the conditional elements of content are replaced with the corresponding information for the selected profile.

  The toolbar buttons provide access to the standard actions and formatting parameters for the HTML page.

  ![](assets/s_ncs_user_wizard_email01_138.png)

  You can insert images in messages from a local file or from an image library in Adobe Campaign. To do this, click the **[!UICONTROL Image]** icon and select the appropriate option.

  ![](assets/s_ncs_user_wizard_email01_18.png)

  Library images can be accessed via the **[!UICONTROL Resources>Online>Public resources]** folder in the folder tree. Also refer to [Adding images](#adding-images).

  The last button in the toolbar lets you insert personalization fields.

  >[!NOTE]
  >
  >The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

  The tabs at the bottom of the page let you display the HTML code of the page being created and view the rendering of the message with its personalization. To launch this display, click **[!UICONTROL Preview]** and select a recipient using the **[!UICONTROL Test personalization]** button in the toolbar. You can select a recipient from the defined target(s) or choose another recipient.

  ![](assets/s_ncs_user_wizard_email01_139.png)

  You can validate the HTML message. You can also view the content of the email header.

  ![](assets/s_ncs_user_wizard_email01_140.png)

* To import a text content, use the **[!UICONTROL Open]** button, or the **[!UICONTROL Text Content]** tab to enter the content of the message when displayed in text format. Use the toolbar buttons to access actions on the contents. The last button lets you insert personalization fields.

  ![](assets/s_ncs_user_wizard_email01_141.png)

  As for the HTML format click the **[!UICONTROL Preview]** tab at the bottom of the page to view the rendering of the message with its personalization. 

  ![](assets/s_ncs_user_wizard_email01_142.png)

<!--## Selecting message formats {#selecting-message-formats}

You can change the format of email messages sent. To do this, edit the delivery properties and click the **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_email_param.png)

Select the format of the email in the lower section of the window:

* **[!UICONTROL Use recipient preferences]** (default mode)

  The message format is defined according to the data stored in the recipient profile and stored by default in the **[!UICONTROL email format]** field (@emailFormat). If a recipient wishes to receive messages in a certain format, this is the format sent. If the field is not filled in, a multipart-alternative message is sent (see below).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  The message contains both formats: text and HTML. The format displayed on reception depends on the configuration of the recipient's mail software (multipart-alternative).

  >[!IMPORTANT]
  >
  >This option includes both versions of the document. It therefore impacts the delivery rate, because the message size is greater.

* **[!UICONTROL Send all messages in text format]**

  The message is sent in text format. HTML format will not be sent, but used for the mirror page only when the recipient clicks on the message.-->

## Defining interactive content {#amp-for-email-format}

Adobe Campaign enables you to try the new interactive [AMP for Email](https://amp.dev/about/email/) format, which enables to send dynamic emails, under certain conditions.

For more on this, see [this section](../../delivery/using/defining-interactive-content.md).

## Using content management {#using-content-management}

You can define the content of the delivery using the content management forms, directly in the delivery wizard. To do this, you must reference the publication template of the content management to be used, in the **[!UICONTROL Advanced]** tab of the delivery properties.

![](assets/s_ncs_content_in_delivery.png)

An additional tab lets you enter content that will automatically be integrated and formatted according to the content management rules.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>For further information about content management in Adobe Campaign, refer to [this section](../../delivery/using/about-content-management.md).

## Inserting emoticons {#inserting-emoticons}

You can insert emoticons to your email content.

1. Click the **[!UICONTROL Insert emoticon]** icon.
1. Select an emoticon from the pop-up window.

    ![](assets/emoticon_4.png)

1. Click the **[!UICONTROL Close]** button when done.

To customize the emoticon list, refer to this [page](../../delivery/using/customizing-emoticon-list.md).

## Adding images {#adding-images}

HTML format email deliveries can contain images. From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon.

Images can be:

* A local image, or an image called from a server
* An image stored in the Adobe Campaign public resources library

  Public resources are accessible via the **[!UICONTROL Resources > Online]** node of the Adobe Campaign hierarchy. They are grouped in a library and can be included in email messages, but can also be used for campaigns or tasks, or for content management.

* An asset shared with Adobe Experience Cloud. Refer to [this section](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!IMPORTANT]
>
>To include images in the email messages using the delivery wizard, the Adobe Campaign instance must be configured to enable public resource management. This procedure can be performed from the deployment wizard. Refer to the [this section](../../installation/using/deploying-an-instance.md) for further information on configuration.

The delivery wizard lets you add local images, or images stored in the library, to the content of messages. To do this, click the **[!UICONTROL Image]** button in the HTML content toolbar.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>In order for the recipients to be able to view the images included in the messages that they receive, these messages must be available on a server accessible from the outside.

To manage images via the delivery wizard:

1. Click the **[!UICONTROL Tracking & Images]** icon in the toolbar.
  ![](assets/s_ncs_user_email_del_img_param.png)

1. Select **[!UICONTROL Upload images]** in the **[!UICONTROL Images]** tab.
1. You can then choose whether you wish to include the images in the email message.
  ![](assets/s_ncs_user_email_del_img_upload.png)

* You can upload images manually without waiting for the delivery analysis phase. To do this, click the **[!UICONTROL Upload the images straightaway...]** link.
* You can specify another path for access to the images on the tracking server. To do this, enter it in the **[!UICONTROL Images URL]** field. This value overrides the value defined in the parameters of the installation wizard.

When you open HTML content with included images in the delivery wizard, a message gives you the option of uploading the images immediately, according to the delivery parameters.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>The image access paths are modified during manual uploading or when sending messages.

### Sending a message with images {#sending-a-message-with-images}

>[!NOTE]
>
>To avoid performance issue, if you include images downloaded on the fly from a personalized URL as [attachment](../../delivery/using/attaching-files.md), each image size should not exceed 100,000 bytes by default. This recommended threshold can be configured from [the list of Campaign Classic options](../../installation/using/configuring-campaign-options.md#delivery).

Here is a sample of a delivery with four images:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

These images come from a local directory or Web site as you can verify from the **[!UICONTROL Source]** tab.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Click the **[!UICONTROL Tracking & Images]** icon and then the **[!UICONTROL Images]** tab to start detecting images in the message.

For each image detected, you can view its status:

* If an image is stored locally or located on another server, even if this server is visible from the outside (on an internet site, for example), it will be detected as **[!UICONTROL Not yet online]**.
* The images are detected as **[!UICONTROL Already online]** if they were uploaded earlier while creating another delivery.
* In the deployment wizard, you can define URLs for which image detection is not enabled: uploading these images will be **[!UICONTROL Skipped]**.

>[!NOTE]
>
>Images are identified by their content and not by their access paths. This means that an image uploaded previously under a different name or in a different directory will be detected as **[!UICONTROL Already online]**.

During the analysis phase, the images are automatically uploaded to the server so that they are accessible from the exterior, except for the local images which must be uploaded beforehand.

You can work ahead and upload images so that they can be viewed by other Adobe Campaign operators. You may find this useful if working collaboratively. To do this, click **[!UICONTROL Upload the images straightaway...]** to upload the images onto the server.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>The URLs of the images in the email, and their names in particular, are then modified.

Once the images are online, you can view changes to their names and paths from the **[!UICONTROL Source]** tab of the message.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

If you select **[!UICONTROL Include the images in the email]**, you can choose which images to include in the corresponding column.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>If local images are included in the message, you must confirm changes to the message source code.

## Inserting a barcode in an email{#inserting-a-barcode-in-an-email}

The barcode generation module lets you create several types of barcodes that comply with many common standards, including 2D barcodes.

It is possible to dynamically generate a barcode as a bitmap using a value defined using customer criteria. Personalized barcodes can be included in email campaigns. The recipient can print the message and show it to the issuing company for scanning (when checking out for example).

To insert a barcode into an email, place the cursor in the content where you want to display it, then click the personalization button. Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Then configure the following elements to suit your needs:

1. Select the type of barcode.

    * For 1D format, the following types are available in Adobe Campaign: Codabar, Code 128, GS1-128 (formerly EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET and Royal Mail (RM4SCC).

      Example of a 1D barcode:

      ![](assets/barcode_insert_08.png)

    * The DataMatrix and PDF417 types concern the 2D format.

      Example of a 2D barcode:

      ![](assets/barcode_insert_09.png)

    * To insert a QR code, select this type and enter the error correction rate to apply. This rate defines the quantity of information repeated and the tolerance to deterioration.

      ![](assets/barcode_insert_06.png)

      Example of a QR code:

      ![](assets/barcode_insert_12.png)

1. Enter the size of the barcode that you want to insert into the email: configuring the scale lets you increase or reduce the size of the barcode, from x1 to x10.
1. The **[!UICONTROL Value]** field enables you to define the value of the barcode. A value can match a special offer and can be the function of a criteria, it can be the value of a database field linked to the customers.

   This example shows an EAN-8 type barcode, to which was added the account number of a recipient. To add this account number, click the personalization button to the right of the **[!UICONTROL Value]** field and select **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. The **[!UICONTROL Height]** field lets you configure the height of the barcode without changing its width, by altering the amount of space between each bar.

   There is no restrictive entry control depending on the type of barcode. If a barcode value is incorrect, it will only be visible in **Preview** mode where the barcode will be crossed out in red.

   >[!NOTE]
   >
   >The value assigned to a barcode depends on its type. For example, an EAN-8 type shall have exactly 8 numbers.
   >
   >The personalization button to the right of the **[!UICONTROL Value]** field lets you add data in addition to the value itself. This enriches the barcode, provided that the barcode standard accepts it.
   >
   >For example, if you are using a GS1-128 type barcode and want to enter the account number of a recipient in addition to the value, click the personalization button and select **[!UICONTROL Recipient > Account number]**. If the account number of the selected recipient is entered correctly, the barcode takes it into account.

Once these elements have been configured, you can finalize your email and send it. To avoid errors, always make sure your content is displayed correctly before performing a delivery by clicking the **[!UICONTROL Preview]** tab.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>If the value of a barcode is incorrect, its bitmap is shown crossed out in red.

![](assets/barcode_insert_11.png)

<!--## Sending emails on Japanese mobiles {#sending-emails-on-japanese-mobiles}

### Email formats for Japanese mobiles {#email-formats-for-japanese-mobiles}

Adobe Campaign manages three specific Japanese formats for email on mobiles: **Deco-mail** (DoCoMo mobiles), **Decore Mail** (Softbank mobiles) and **Decoration Mail** (KDDI AU mobiles). These formats impose particular coding, structure, and size constraints. Learn more about limitations and recommendations in [this section](#limitations-and-recommendations).

In order for the recipient to correctly receive messages in one of these formats, we recommend selecting **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** in the corresponding profile:

![](assets/deco-mail_03.png)

However, if you leave the **[!UICONTROL Email format]** option as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]**, Adobe Campaign will automatically detect (when sending the email) the Japanese format to use so that the message is correctly displayed.

This automatic detection system is based on the list of predefined domains defined in the **[!UICONTROL Management of Email Formats]** mail rule set. For more on managing email formats, refer to [this page](../../installation/using/email-deliverability.md#managing-email-formats).

### Limitations and recommendations {#limitations-and-recommendations}

A certain number of constraints apply for sending emails that will be read on a mobile operated by a Japanese provider (Softbank, DoCoMo, KDDI AU).

Therefore, you must:

* Only use images in JPEG or GIF format
* Create a delivery with text and HTML sections that are strictly lower than 10 000 bytes (for KDDI AU and DoCoMo)
* Use images with a total size (before encoding) that is lower than 100 KB
* Do not use more than 20 images per message
* Use a reduced size HTML format (a limited number of tags are available for each operator)

>[!NOTE]
>
>Limitations specific to each operator are to be taken into account when creating your message. Refer to:  
>
>* For DoCoMo, refer to [this page](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* For KDDI AU, refer to [this page](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* For Softbank, refer to [this page](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)

### Testing the email content {#testing-the-email-content}

#### Previewing the message {#previewing-the-message}

Adobe Campaign allows you to check that your message format is adapted to be sent to a Japanese mobile.

Once you have defined your content and entered the email subject, you can check the display and formatting when the message is created.

In the **[!UICONTROL Preview]** tab of the content editing window, clicking **[!UICONTROL More... > Deco-mail diagnostic]** allows you to:

* Check that the HTML content tags conform to the Japanese format restrictions
* Check that the number of images in the message does not exceed the limit imposed by the format (20 images)
* Check the total message size (less than 100kB)

  ![](assets/deco-mail_06.png)

#### Running typology rule {#running-typology-rule}

In addition to the previewing diagnosis, a second check is carried out when sending a proof or a delivery: a specific typology rule, **[!UICONTROL Deco-mail check]**, is started during the analysis.

>[!IMPORTANT]
>
>This typology rule is only executed if at least one of the recipients is configured to receive emails in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** format.

This typology rule allows you to make sure that the delivery respects the [format constraints](#limitations-and-recommendations) defined by the Japanese operators, particularly in relation to the total size of the email, the size of the HTML and text sections, the number of images in the messages, and the tags in the HTML content.

#### Sending proofs {#sending-proofs}

You can send proofs to test your delivery. When you send the proof, if you are using substitution addresses, please enter addresses that correspond to the email format of the profile used.

For example, you can replace a profile's address by test@softbank.ne.jp if the email format for this profile was defined beforehand on **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

### Sending messages {#sending-messages}

To send an email to recipients with Japanese email formats with Campaign, two options are possible:

* Create two deliveries: one only for Japanese recipients and another for other recipients - refer to [this section](#designing-a-specific-delivery-for-japanese-formats).
* Create a single delivery and Adobe Campaign will automatically detect the format to use - refer to [this section](#designing-a-delivery-for-all-formats).

#### Designing a specific delivery for Japanese formats {#designing-a-specific-delivery-for-japanese-formats}

You can create a workflow that contains two deliveries: one to be read on a Japanese mobile and another for recipients with a standard email format.

To do this, use the **[!UICONTROL Split]** activity in your workflow and define the Japanese email formats (Deco-mail, Decoration Mail and Decore Mail) as filtering conditions.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### Designing a delivery for all formats {#designing-a-delivery-for-all-formats}

When Adobe Campaign dynamically manages the formats according to the domain (profiles with email formats defined as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]** ), you can send the same delivery to all of your recipients.

The message contact will display correctly for the users on Japanese mobiles, just as for the standard recipients.

>[!IMPORTANT]
>
>Make sure to respect the special features associated with each Japanese email format (Deco-mail, Decoration Mail, and Decore Mail). For more information on limitations, refer to [this section](#limitations-and-recommendations).-->
