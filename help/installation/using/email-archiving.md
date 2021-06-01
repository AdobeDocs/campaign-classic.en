---
product: campaign
title: Email archiving
description: Email archiving
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
---
# Email BCC {#email-archiving}

You can configure Adobe Campaign to keep a copy of emails sent from your platform.

However, Adobe Campaign itself does not manage archived files. It does enable you to send the messages of your choice to a dedicated address, from where they can be processed and archived using an external system.

To do this, .eml files corresponding to the sent emails are transferred to a remote server, such as an SMTP email server. The archiving destination is a BCC email address (invisible to the delivery recipients) that you must specify.

## Recommendations and limitations {#recommendations-and-limitations}

* Email BCC capability is optional. Please check your license agreement.
* For **hosted and hybrid architectures**, contact your account executive to activate it. The BCC email address of your choice must be provided to the Adobe team who will configure it for you.
* For **on-premise installations**, follow the guidelines below to activate it - see the [Activating email BCC (on premise)](#activating-email-archiving--on-premise-) and [Configuring the BCC email address (on premise)](#configuring-the-bcc-email-address--on-premise-) sections.
* You can only use one BCC email address.
* Once email BCC is configured, make sure the feature is enabled in the delivery template or in the delivery through the **[!UICONTROL Email BCC]** option. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
* Only successfully sent emails are taken in account, bounces are not.
* The email archiving system changed with Adobe Campaign 17.2 (build 8795). If you were already using email archiving, you must upgrade manually to the new email BCC system. For more on this, see the [Moving to the new Email BCC](#updated-email-archiving-system--bcc-) section.

## Activating Email BCC (on premise) {#activating-email-archiving--on-premise-}

To activate BCC email archiving when Adobe Campaign is installed on premise, follow the steps below.

### Local folder {#local-folder}

To enable transferring sent emails to a BCC email address, exact raw copies of sent emails must first be saved as .eml files to a local folder.

The path for the local folder must be specified in the **config-`<instance>`.xml** file, from the configuration. For example:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>It is the responsibility of the team implementing the project to ensure that the security settings allow access to the folder defined through the **dataLogPath** parameters.

The full path is as follows: **`<datalogpath>  YYYY-MM-DDHHh`**. The date and time are set according to the MTA server's clock (UTC). For example:

```
C:\emails\2018-12-02\13h
```

The archive file name is **`<deliveryid>-<broadlogid>.eml`** when the status of the emails is not **[!UICONTROL Sent]**. Once the status has changed to **[!UICONTROL Sent]**, the file name becomes **`<deliveryid>-<broadlogid>-sent.eml`**. For example:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In a mid-sourcing instance, the directory for the BCC emails is located on the mid-sourcing server.  
>
>The deliveryID and the broadlogID come from the mid-sourcing server when the status of the emails is not sent. Once the status has changed to **[!UICONTROL Sent]**, these IDs come from the marketing server.

### Parameters {#parameters}

Once the local folder path is defined, add and edit the following elements as desired in the **config-`<instance name>.xml`** file. Below are the default values:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: format used when compressing the .eml files. The possible values are:

  **0**: no compression (default value)

  **1**: compression (.zip format)

* **compressBatchSize**: number of .eml files added to an archive (.zip file).
* **archivingType**: archiving strategy to be used. The possible values are:

  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

  **1**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder and they are sent to the BCC email address over SMTP. Once the email copies are sent to the BCC address, the archive file name becomes **`<deliveryid>-<broadlogid>-sent-archived.eml`** and the file is moved to the **dataLogPath/archives** folder. The sent and BCC archived email file path is then **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: number of days .eml files are kept for archiving. After that delay, they are automatically moved to the **dataLogPath/archives** folder for compression. By default, .eml files expire after two days.
* **purgeArchivesDelay**: number of days archives are kept in the **dataLogPath/`<archives>`** folder. After that period, they are permanently deleted. The purge begins when the MTA is started. By default, it is carried out every seven days.
* **pollDelay**: checking frequency (in seconds) for new incoming sent emails to the **dataLogPath** folder. For example, if this parameter is set to 60, it means that every minute, the archiving process goes through the .eml files inside the **dataLogPath/ `<date and time>`** folders, apply a purge if needed and sends email copies to the BCC address and/or compress the archived files whenever needed.
* **acquireLimit**: number of .eml files processed at once before the archiving process is applied again according to the **pollDelay** parameter. For example, if you set the **acquireLimit** parameter to 100 while the **pollDelay** parameter is set to 60, 100 .eml files per minute will be processed.
* **smtpNbConnection**: number of SMTP connections to the BCC email address.

Make sure you adjust these parameters according to the email sending throughput. For example, in a configuration where the MTA is sending 30,000 emails per hour, you can set the **pollDelay** parameter to 600, the **acquireLimit** parameter to 5000 and the **smtpNbConnection** parameter to 2. It means that using 2 SMTP connections, 5,000 emails will be sent to the BCC address every 10 minutes.

## Configuring the BCC email address (on premise) {#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>For privacy reasons, BCC emails must be processed by an archiving system capable of storing securely personally identifiable information (PII).

In the **config- `<instance name>.xml`** file, use the following parameters to define the SMTP email server to which the stored files will be transferred:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archiving target destination
* **smtpEnableTLS**: using a secured SMTP connection (TLS/SSL protocol)
* **smtpRelayAddress**: relay address to use
* **smtpRelayPort**: relay port to use

>[!NOTE]
>
>If you are using an SMTP relay, the changes to the emails made by the relay are not taken into account in the archiving process.
>
>Besides, the relay assigns a **[!UICONTROL Sent]** status to all emails, including those that are not sent. Therefore, all messages are archived.

## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).

## Email BCC best practices {#best-practices}

* **BCC address mailbox**: make sure it has enough reception capacity to archive all the emails that are sent by the MTA.
* **MTA mutualization**: the BCC archiving feature works at the MTA level. It lets you duplicate every email sent by the MTA. As the MTA can be mutualized across several instances (dev, test, or prod for example) or even across several clients (in a mid-sourcing environment), setting up this feature impacts security:

    * If you share an MTA with multiple clients and one of them has this option activated, this client will access all the emails of the other clients that share the same MTA. To avoid such a situation, use a different MTA for each client.
    * If you use the same MTA across multiple instances (development, test, prod) for a single client, the messages sent from all three instances will be duplicated by the dataLogPath option.

* **Emails per connection**: BCC email archiving operates by opening a connection and trying to send all emails through that connection. Adobe recommends checking with your internal technical contact the number of emails that are accepted on a given connection. Increasing this number can have a great impact on BCC throughput.
* **BCC sending IPs**: currently, BCC emails are not sent through the normal MTA proxies. Instead, a direct connection is open from the MTA server to the destination email server. This means that you may need to add additional IPs to the allowlist on your network, depending on your email server configuration.
