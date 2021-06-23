---
product: campaign
title: Build personalized content
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
---
# Build personalized content {#build-personalized-content}

When designing your message content, try to avoid common issues that could prevent you from executing your delivery. Most of the time, possible errors are related to [personalization](about-personalization.md), [formatting](defining-the-email-content.md#message-content) and [images](defining-the-email-content.md#adding-images).

## Optimize personalization {#optimize-personalization}

To avoid common issues that could prevent you from executing your delivery and to improve your recipients' experience, Adobe Campaign enables you to personalize your messages.

You can use recipients' data stored in the Adobe Campaign database, or collected through tracking, landing pages, subscriptions, etc.
Personalization basics are presented in [this section](personalization-fields.md).

Make sure your message content is properly designed to avoid any errors, which are generally related to personalization.

**Tips**: In personalization fields coming from external files provided by third-party vendors, external HTML content can be wrong. To avoid this, check syntax, use of tags, characters, etc. For example, an Adobe Campaign personalization tag always has the following form: <%=table.field%>. For more on this, see [this section](about-personalization.md).

The incorrect use of parameters in personalization blocks can be an issue. For example, variables in JavaScript should be used as follows:

    <%

    var brand = "xxx"

    %>

For more on personalization blocks, refer to the [this section](personalization-blocks.md).

You can prepare personalization data in a workflow to improve delivery preparation analysis. This should be used specially if the personalization data come from an external table through Federated Data Access (FDA). This option is described in this [this section](personalization-fields.md#optimizing-personalization)

## Build optimized content {#optimize-content}

When building your emails, keep the general best practices below in mind.

* Keep design simple

* Keep mobile users in mind

* Avoid entirely image-based emails

* Use email-safe fonts

* Encode special characters

### Subject line

Work on the [subject line](defining-the-email-content.md#message-content) to improve open rates:

* Avoid subjects that are too long. Use 50 characters maximum

* Avoid using repetitively words like "free" or "offer", that could be considered as spam

* Avoid capital letters, and special characters like "!", "£", "€", "$"

### Mirror page

Always include a mirror page link. Preferred position is a the top of the email. [Learn more](sending-messages.md#generating-the-mirror-page) 

### Unsubscription link

The unsubscription link is essential. It must be visible and valid, and the form must be functional. By default, when the message is analyzed, a [typology rule](steps-validating-the-delivery.md#validation-process-with-typologies) checks whether an opt-out link has been included and generates a warning if it is missing.

**Tip**: Because human error is always possible, check that the opt-out link works correctly before each time you send. For example, when sending the proof, make sure the link is valid, that the form is on-line and that the No longer contact this recipient field is changed to Yes.

Learn how to insert an opt-out link [in this section](personalization-blocks.md#personalization-blocks-example).

### Email size

To avoid performance or deliverability issues, the recommended maximum size of an email is about **35KB**. To check the message size, go the **[!UICONTROL Preview]** tab and choose a test profile. Once generated, the message size will be displayed in the top right corner.

To keep your email under the limit, consider the following:

* Remove redundant or unused styles

* Move some of the email content to a landing page

* Minify your code

Make sure to test any changes before the final sending

### SMS length

By default, the number of characters in an SMS meets the GSM (Global System for Mobile Communications) standards. SMS messages using GSM encoding are limited to 160 characters, or 153 characters per SMS for messages sent in multiple parts.

Transliteration consists of replacing one character of an SMS by another when that character is not taken into account by the GSM standard. Note that inserting personalization fields into the content of your SMS message may introduce characters that are not taken into account by the GSM encoding. You can authorize character transliteration by checking the corresponding box in the SMPP channel settings tab of the corresponding **[!UICONTROL External account]**. 
Learn more [in this section](sms-set-up.md#creating-an-smpp-external-account).

**Tips**:

* To keep all of the characters in your SMS messages as they are, to not alter proper names for example, do not enable transliteration.

* However, if your SMS messages contain a lot of characters that are not taken into account by the GSM standard, enable transliteration to limit the costs of sending your messages.

Learn more [in this section](sms-set-up.md#about-character-transliteration).

## Work on formatting {#formatting}

To avoid common formatting errors, check the following elements:

* Correct **date formatting**: Adobe Campaign provides date formatting functions for the JavaScript templates and XSL stylesheets. [Learn more](formatting.md#date-display)

* Usage of **authorized characters** in emails: the list of valid characters for email addresses is defined in the "XtkEmail_Characters" option. Learn how to access Campaign options [in this section](../../installation/using/configuring-campaign-options.md). To correctly handle special characters, Adobe Campaign needs to be installed in Unicode. 

* Configuration of **Email Authentication**: make sure that the email headers contain the DKIM signature. DKIM (Domain Keys Identified Mail) authentication allows the receiving email server to verify that a message was indeed sent by the person or entity it claims it was sent by, and whether the message content was altered in between the time it was originally sent (and DKIM "signed") and the time it was received. This standard typically uses the domain in the From or Sender header. For more on this, refer to the [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Responsive email design

Responsive design ensures that an email renders optimally for the device on which it is opened. 

* Use responsive email HTML rather than web HTML

* Use the preview mode and send proofs to test the rendering on as much devices as possible

* The Adobe Campaign Classic Digital Content Editor (DCE) module includes some responsive design formatted templates for mobile available via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Learn more [in this article](https://theblog.adobe.com/responsive-email-design-101/)

## Manage images {#manage-images}

Follow the guidelines below when it comes to using images.

### Prevent images blocking

Some email clients block images by default, and some users change their settings to block images for saving on data usage. Therefore, if images are not downloaded, the whole message can be lost. To avoid this:

* Balance your content with image and text. Avoid entirely image-based emails.

* If text must be contained in an image, use alt and title text to make sure your message gets across. Style your alt/title text to improve its appearance.

* Avoid the use of background images as they are not supported by some email clients.

### Make images responsive

Try to make images responsive and resizable. Note that this can have a cost impact as it takes longer to build.

### Use absolute image references

To be accessible from the outside, the images used in emails and public resources linked to campaigns must be present on an externally accessible server.

* You can check if the instance configuration enables public resource management. [Learn more](../../installation/using/deploying-an-instance.md#managing-public-resources)
    
* From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon. [Learn more](defining-the-email-content.md#adding-images)

* If images are not displayed, check that the images are available on the server. To do this, click the Source tab from your delivery. Find your images and copy-paste each image's URL in a web browser. If the images are not displayed, contact your IT administrator or the third-party vendor providing your delivery content.

## Preview your message {#preview-msg}

Adobe recommends previewing your message to check its personalization and how your recipients will see your delivery. 

* In the delivery wizard, the **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. The personalization fields and the conditional elements of content are replaced with the corresponding information for the selected profile. [Learn more](defining-the-email-content.md#message-content)

*  An automatic anti-spam checking is performed during each preview. In the **[!UICONTROL Preview]** sub-tab, check [SpamAssassin](spamassassin.md) spam scoring.  Click **[!UICONTROL More...]** to find out more about the warning.  Before doing so, make sure SpamAssassin is correctly installed and configured on the Adobe Campaign application server. [Learn more](../../installation/using/configuring-spamassassin.md)
