---
product: campaign
title: Understand quarantine management
description: Understand quarantine management
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
---
# Understand quarantine management{#understanding-quarantine-management}

Adobe Campaign manages a list of quarantined addresses. Recipients whose address is quarantined are excluded by default during delivery analysis, and will not be targeted. An email address can be quarantined, for example, when the mailbox is full or if the address does not exist. In any case, the quarantine procedure complies with specific rules described below.

>[!NOTE]
>
>This section applies to online channels: email, SMS, push notification.

## Optimize your delivery through quarantine management {#optimizing-your-delivery-through-quarantines}

The profiles whose email addresses or phone number are in quarantine are automatically excluded during message preparation (see [Identify quarantined addresses for a delivery](#identifying-quarantined-addresses-for-a-delivery)). This will speed up deliveries, as the error rate has a significant effect on delivery speed.

Some internet access providers automatically consider emails to be spam if the rate of invalid addresses is too high. Quarantine therefore allows you to avoid being added to denylist by these providers.

Moreover, quarantines help reducing SMS sending costs by excluding erroneous phone numbers from deliveries.

For more on best practices to secure and optimize your deliveries, refer to this page in the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}.

### Quarantine vs denylist {#quarantine-vs-denylist}

Quarantine and denylist do not apply to the same object:

* **Quarantine** applies only to an **address** (or phone number, etc.), not to the profile itself. For example, a profile whose email address is quarantined can update their profile and enter a new address, and could then be targeted by delivery actions again. Likewise, if two profiles happen to have the same phone number, they will both be affected if the number is quarantined.

  The quarantined addresses or phone numbers are displayed in the [exclusion logs](#identifying-quarantined-addresses-for-a-delivery) (for a delivery) or in the [quarantine list](#identifying-quarantined-addresses-for-the-entire-platform) (for the entire platform).

* Being on the **denylist**, on the other hand, will result in the **profile** no longer being targeted by the delivery, such as after an unsubscription (opt-out), for a given channel. For example, if a profile on the denylist for the email channel has two email addresses, both addresses will be excluded from delivery.

  You can check if a profile is on the denylist for one or more channels in the **[!UICONTROL No longer contact]** section of the profile's **[!UICONTROL General]** tab.
>[!NOTE]
>
>Quarantine includes a **[!UICONTROL Denylisted]** status, which applies when recipients report your message as spam or reply to an SMS message with a keyword such as "STOP". In that case, the profile's involved address or phone number is sent to quarantine with the **[!UICONTROL Denylisted]** status. For more on managing STOP SMS messages, refer to [this section](../../delivery/using/sms-send.md#processing-inbound-messages).

## Identify quarantined addresses {#identifying-quarantined-addresses}

Quarantined addresses can be listed for a specific delivery or for the entire platform.

### Identify quarantined addresses for a delivery {#identifying-quarantined-addresses-for-a-delivery}

Quarantined addresses for a specific delivery are listed during the delivery preparation phase, in the delivery logs of the delivery dashboard (see [Delivery logs and history](delivery-dashboard.md#delivery-logs-and-history)).

### Identify quarantined addresses for the entire platform {#identifying-quarantined-addresses-for-the-entire-platform}

Administrators can list the addresses in quarantine for the entire platform from the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** node.

>[!NOTE]
>
>This menu lists quarantined elements for **email**, **SMS** and **Push notification** channels.  

The following information is available for each address:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>The increase in number of quarantines is a normal effect, related to the "wear" of the database. For example, if the lifetime of an email address is considered to be three years and the recipients table increases by 50% each year, the increase in quarantines can be calculated as follows:
>
>End of Year 1: (1&#42;0.33)/(1+0.5)=22%.
>
>End of Year 2: ((1.22&#42;0.33)+0.33)/(1.5+0.75)=32.5%.

### Identify quarantined addresses in delivery reports {#identifying-quarantined-addresses-in-delivery-reports}

The following reports provide information about the addresses in quarantine:

* For each delivery, the **[!UICONTROL Delivery summary]** report shows the number of addresses in quarantine in the delivery target. It displays:

    * The number of addresses placed in quarantine during the delivery analysis,

    * The number of addresses placed in quarantine following the delivery action.

* The **[!UICONTROL Non-deliverables and bounces]** report displays information about the addresses in quarantine, the types of error encountered, etc., and a failure breakdown by domain.

You can look up this information for all deliveries of the platform (**[!UICONTROL Home page > Reports]**) or for a specific delivery. You can also create customized reports and select the information to be displayed.

### Identify quarantined addresses for a recipient {#identifying-quarantined-addresses-for-a-recipient}

You can look up the status of the email address of any recipient. To do this, select the recipient profile and click the **[!UICONTROL Deliveries]** tab. For all deliveries to that recipient, you can find out whether the address failed, was quarantined during analysis, etc. For each folder, you can display only the recipients whose email address is in quarantine. To do this, use the **[!UICONTROL Quarantined email address]** application filter.

![](assets/tech_quarant_recipients_filter.png)


## Conditions for sending an address to quarantine {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign manages quarantine according to the delivery failure type and the reason assigned during error messages qualification (see [Bounce mail qualification](understanding-delivery-failures.md#bounce-mail-qualification) and [Delivery failure types and reasons](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Ignored error**: ignored errors do not send an address to quarantine.
* **Hard error**: the corresponding email address is immediately sent to quarantine.
* **Soft error**: soft errors do not send immediately an address to quarantine, but they increment an error counter. For more on this, see [Soft error management](#soft-error-management).

If a user qualifies an email as a spam ([feedback loop](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)), the message is automatically redirected towards a technical mailbox managed by Adobe. The user's email address is then automatically sent to quarantine with the **[!UICONTROL Denylisted]** status. This status refers to the address only, the profile is not on the denylist, so that the user continues receiving SMS messages and push notifications.

>[!NOTE]
>
>Quarantine in Adobe Campaign is case sensitive. Make sure to import email addresses in lower case, so that they are not retargeted later on.

In the list of quarantined addresses (see see [Identifying quarantined addresses for the entire platform](#identifying-quarantined-addresses-for-the-entire-platform)), the **[!UICONTROL Error reason]** field indicates why the selected address was placed in quarantine.

![](assets/tech_quarant_error_reasons.png)

### Soft error management {#soft-error-management}

As opposed to hard errors, soft errors do not send immediately an address to quarantine, but instead they increment an error counter.

Retries will be performed during the delivery duration. See this [page](communication-channels.md) under **Delivery sending** > **Define the validity period**. When the error counter reaches the limit threshold, the address goes into quarantine. For more on this, refer to [Retries after a delivery temporary failure](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

The error counter is reinitialized if the last significant error occurred more than 10 days ago. The address status then changes to **Valid** and it is deleted from the list of quarantines by the [Database cleanup](../../production/using/database-cleanup-workflow.md) workflow.


For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), the maximum number of retries to be performed in case of **[!UICONTROL Erroneous]** status and the minimum delay between retries are now based on how well an IP is performing both historically and currently at a given domain.

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, you can modify the number of errors and the period between two errors. To do this, change the corresponding settings in the [deployment wizard](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) or at the delivery level. See this [page](communication-channels.md) under **Delivery sending** > **Configure retries**.


## Remove an address from quarantine {#removing-a-quarantined-address}

### Automatic updates {#unquarantine-auto}

Addresses that match specific conditions are automatically deleted from the quarantine list by the [Database cleanup](../../production/using/database-cleanup-workflow.md) workflow. 

The addresses are automatically removed from the quarantine list in the following cases:

* Addresses in a **[!UICONTROL With errors]** status will be removed from the quarantine list after a successful delivery.
* Addresses in a **[!UICONTROL With errors]** status will be removed from the quarantine list if the last soft bounce occurred more than 10 days ago. For more on soft error management, see [this section](#soft-error-management).
* Addresses in a **[!UICONTROL With errors]** status that bounced with the **[!UICONTROL Mailbox full]** error will be removed from the quarantine list after 30 days.

Their status then changes to **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>Recipients with an address in a **[!UICONTROL Quarantine]** or **[!UICONTROL Denylisted]** status are never removed, even if they receive an email.

### Manual updates {#unquarantine-manual}

You can also un-quarantine an address manually. To manually remove an address from the quarantine list, change its status to **[!UICONTROL Valid]** from the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** node.

![](assets/tech_quarant_error_status.png)

### Bulk updates {#unquarantine-bulk}

You might need to perform bulk updates on the quarantine list, for example in case of an ISP outage. In such case, emails are wrongly marked as bounces because they cannot be successfully delivered to their recipient. These addresses must be removed from the quarantine list.

To perform this, create a workflow and add a **[!UICONTROL Query]** activity on your quarantine table to filter out all impacted recipients. Once identified, they can be removed from the quarantine list, and included in future Campaign email deliveries. 

Below are the recommended guidelines for this query:

* For Campaign Classic v7 environments with Inbound Email rule information in the **[!UICONTROL Error text]** field of the quarantine list:

  * **Error text (quarantine text)** contains "Momen_Code10_InvalidRecipient"
  * **Email domain (@domain)** equal to domain1.com OR **Email domain (@domain)** equal to domain2.com OR **Email domain (@domain)** equal to domain3.com
  * **Update status (@lastModified)** on or after `MM/DD/YYYY HH:MM:SS AM`
  * **Update status (@lastModified)** on or before `MM/DD/YYYY HH:MM:SS PM`

* For Campaign Classic v7 instances with SMTP bounce response information in the **[!UICONTROL Error text]** field of the quarantine list:

  * **Error text (quarantine text)** contains "550-5.1.1" AND **Error text (quarantine text)** contains "support.ISP.com" 

  where "support.ISP.com" can be: "support.apple.com" or "support.google.com" for example
        
  * **Update status (@lastModified)** on or after `MM/DD/YYYY HH:MM:SS AM`
  * **Update status (@lastModified)** on or before  `MM/DD/YYYY HH:MM:SS PM`

Once you have the list of affected recipients, add an **[!UICONTROL Update data]** activity to set their email address status to **[!UICONTROL Valid]** so they will be removed from the quarantine list by the **[!UICONTROL Database cleanup]** workflow. You can also just delete them from the quarantine table.

## Push notification quarantines {#push-notification-quarantines}

The quarantine mechanism for push notifications is globally the same as the general process. However certain errors are managed differently for push notifications. For example, for certain soft errors, no retries are performed within the same delivery. The specificities for push notification are listed below. The retry mechanism (number of retries, frequency) is the same as for emails.

The items put in quarantine are device tokens.

### iOS quarantine {#ios-quarantine}

The HTTP/V2 protocol allows a direct feedback and status for each push delivery. If the HTTP/V2 protocol connector is used, the feedback service is no longer called by the **[!UICONTROL mobileAppOptOutMgt]** workflow. A token is considered unregistered when a mobile application is uninstalled or reinstalled.

Synchronously, if the APNs returns an "unregistered" status for a message, the target token will be immediately be put in quarantine.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Error message</strong><br /> </td> 
   <td> <strong>Failure type</strong><br /> </td> 
   <td> <strong>Failure reason</strong><br /> </td> 
   <td> <strong>Retry</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Targeted device powered on<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Targeted device powered off<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> User disables notifications for the application<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Message creation/analysis phase - payload too big<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Payload too long<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Message creation/analysis phase - unexpected content format issue<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Various error messages according to the error<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Undefined<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Certificate issue (password, corruption, etc.) and test connection to APNs issue<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Various error messages according to the error<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Network connection lost during sending<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Connection error<br /> </td> 
   <td> Undefined<br /> </td> 
   <td> Unreachable<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs message rejection: Unregistration<br /> the user has removed the application or the token has expired<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Unregistered<br /> </td> 
   <td> Hard<br /> </td> 
   <td> User unknown<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs message rejection: all other errors<br /> </td> 
   <td> Failure<br /> </td> 
   <td> The error rejection cause will be present in the error message<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android quarantine {#android-quarantine}

**For Android V1**

For each notification, Adobe Campaign receives the synchronous errors directly from the FCM server. Adobe campaign handles them on the fly and generates hard or soft errors according to the severity of the error and retries can be performed:

* Payload length exceeded, connection issue, service availability issue: retry performed, soft error, failure reason is **[!UICONTROL Refused]**.
* Device quota exceeded: no retry, soft error, failure reason is **[!UICONTROL Refused]**.
* Invalid or unregistered token, unexpected error, sender account issue: no retry, hard error, failure reason is **[!UICONTROL Refused]**.

The **[!UICONTROL mobileAppOptOutMgt]** workflow runs every 6 hours to update the **AppSubscriptionRcp** table. For the tokens declared unregistered or no longer valid, the field **Disabled** is set to **True** and the subscription linked to that device token will be automatically excluded from future deliveries.

During the delivery analysis, all the devices that are excluded from the target are automatically added to the **excludeLogAppSubRcp** table.

>[!NOTE]
>
>For customers using the Baidu connector, here are the different types of errors:  
>
>* Connection issue at the beginning of the delivery: failure type **[!UICONTROL Undefined]**, failure reason **[!UICONTROL Unreachable]**, retry is performed.
>* Connection lost during a delivery: soft error, failure reason **[!UICONTROL Refused]**, retry is performed.
>* Synchronous error returned by Baidu during the sending: hard error, failure reason **[!UICONTROL Refused]**, no retry is performed.
>
>Adobe Campaign contacts the Baidu server every 10 minutes to retrieve the sent message's status, and updates the broadlogs. If a message is declared as sent, the status of the message in the broadlogs is set to **[!UICONTROL Received]**. If Baidu declares an error, the status is set to **[!UICONTROL Failed]**.

**For Android V2**

The Android V2 quarantine mechanism uses the same process as Android V1, the same applies to the subscriptions and exclusions update. For more on this refer to the [Android V1](#android-quarantine) section.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Error message</strong><br /> </td> 
   <td> <strong>Failure type</strong><br /> </td> 
   <td> <strong>Failure reason</strong><br /> </td> 
   <td> <strong>Retry</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Message creation/analysis phase: illegal keywords used in the custom fields<br /> </td> 
   <td> Failure<br /> </td> 
   <td> The following keywords cannot be used: {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Message creation/analysis phase: payload too big<br /> </td> 
   <td> Failure<br /> </td> 
   <td> The notification is too heavy: {1} bits, while only {2} are authorized<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Network connection lost during sending<br /> </td> 
   <td> Failure<br /> </td> 
   <td> No response from the Firebase Cloud Messaging service on the address: {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Unreachable<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM message rejection: The FCM server is temporarily unavailable (for example with timeouts). <br /> </td> 
   <td> Failure<br /> </td> 
   <td> The Firebase Cloud Messaging service is temporarily unavailable<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Unreachable<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM message rejection: Error authenticating the sender account<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Failed to identify the developer account, please check your ID and password<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM message rejection: Device quota exceeded<br /> </td> 
   <td> Failure<br /> </td> 
   <td> </td> 
   <td> Soft<br /> </td> 
   <td> Refused<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM message rejection: Invalid registration / not registered<br /> </td> 
   <td> Failure<br /> </td> 
   <td> </td> 
   <td> Hard<br /> </td> 
   <td> User unknown<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM message rejection: All other error<br /> </td> 
   <td> Failure<br /> </td> 
   <td> The Firebase Cloud Messaging server has returned an unexpected error code: {1} </td> 
   <td> </td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM message rejection: Invalid argument<br /> </td> 
   <td> Failure<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Ignored</td> 
   <td> Undefined<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: Third party authentication error<br /> </td> 
   <td> Failure<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignored</td>
   <td> Refused<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: Sender ID mismatch<br /> </td> 
   <td> Failure<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Soft</td>
   <td> User unknown<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: Unregistered<br /> </td> 
   <td> Failure<br /> </td>
   <td> UNREGISTERED </td> 
   <td> Hard</td> 
   <td> User unknown<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: Internal<br /> </td> 
   <td> Failure<br /> </td> 
   <td> INTERNAL </td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: Unavailable<br /> </td> 
   <td> Failure<br /> </td> 
   <td> UNAVAILABLE</td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> FCM message rejection: unexpected error code<br /> </td> 
   <td> Failure<br /> </td> 
   <td> unexpected error code</td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
  <tr> 
   <td> Authentication: Connection issue<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Impossible to connect to authentication server </td> 
   <td> Ignored</td>
   <td> Refused<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Unauthorized client or scope in request.<br /> </td> 
   <td> Failure<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignored</td>
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Client is unauthorized to retrieve access tokens using this method, or client not authorized for any of the scopes requested.<br /> </td> 
   <td> Failure<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignored</td>
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Access denied<br /> </td> 
   <td> Failure<br /> </td>
   <td> access_denied</td> 
   <td> Ignored</td>
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Non-valid email<br /> </td> 
   <td> Failure<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Invalid JWT<br /> </td> 
   <td> Failure<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Invalid JWT Signature<br /> </td> 
   <td> Failure<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: Invalid OAuth scope or ID token audience provided<br /> </td> 
   <td> Failure<br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Authentication: OAuth client disabled<br /> </td> 
   <td> Failure<br /> </td> 
   <td> disabled_client</td> 
   <td> Ignored</td> 
   <td> Refused<br /> </td> 
   <td> No<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS quarantines {#sms-quarantines}

**For standard connectors**

The quarantine mechanism for SMS messages is globally the same as the general process. See [About quarantines](#about-quarantines). The specificities for SMS are listed below.

>[!NOTE]
>
>The **[!UICONTROL Delivery log qualification]** table does not apply to the **Extended generic SMPP** connector.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Error message</strong><br /> </td> 
   <td> <strong>Failure type</strong><br /> </td> 
   <td> <strong>Failure reason</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Sent to the provider<br /> </td> 
   <td> Sent<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Received on the mobile<br /> </td> 
   <td> Received<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Error returned by the provider<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Error while receiving data (SR or MO)<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Unreachable<br /> </td> 
  </tr> 
  <tr> 
   <td> Invalid MT acknowledge<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Error '{1}' while processing acknowledgment frame for send query<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Unreachable<br /> </td> 
  </tr> 
  <tr> 
   <td> Error while sending the MT<br /> </td> 
   <td> Failure<br /> </td> 
   <td> Error while sending messages<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Unreachable<br /> </td> 
  </tr> 
 </tbody> 
</table>

**For the Extended generic SMPP connector**

When using the SMPP protocol to send SMS messages, the error management is handled differently. For more information on the Extended generic SMPP connector, refer to [this page](sms-set-up.md#creating-an-smpp-external-account).

The SMPP connector retrieves data from the SR (Status Report) message that is returned using regular expressions (regexes) to filter its content. This data is then matched against the information found in the **[!UICONTROL Delivery log qualification]** table (available via the **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** menu).

Before a new type of error is qualified, the failure reason is always set to **Refused** by default.

>[!NOTE]
>
>The failure types and reasons for failure are the same as for emails. See [Delivery failure types and reasons](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Ask your provider for a list of status and error codes in order to set proper failure types and reasons for failure in the Delivery log qualification table.

Example of a generated message:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* All error messages begin with **SR** to distinguish SMS error codes from email error codes.
* The second part (**Generic** in this example) of the error message refers to the name of the SMSC implementation such as defined in the **[!UICONTROL SMSC implementation name]** field of the SMS external account. See [this page](sms-set-up.md#creating-an-smpp-external-account).

  Because the same error code may have a different meaning for each provider, this field allows you to know which provider generated the error code. You can then find the error in the relevant provider's documentation.

* The third part (**DELIVRD** in this example) of the error message corresponds to the status code retrieved from the SR using the status extraction regex defined in the SMS external account.

  This regex is specified in the **[!UICONTROL SMSC specificities]** tab of the external account. See [this page](sms-set-up.md#creating-an-smpp-external-account).

  ![](assets/tech_quarant_error_regex.png)

  By default, the regex extracts the **stat:** field as defined by the **Appendix B** section of the **SMPP 3.4 specification**.

* The fourth part (**000** in this example) of the error message corresponds to the error code extracted from the SR using the error code extraction regex defined in the SMS external account.

  This regex is specified in the **[!UICONTROL SMSC specificities]** tab of the external account. See [this page](sms-set-up.md#creating-an-smpp-external-account).

  By default, the regex extracts the **err:** field as defined by the **Appendix B** section of the **SMPP 3.4 specification**.

* Everything that comes after the pipe symbol (|) is only displayed in the **[!UICONTROL First text]** column of the **[!UICONTROL Delivery log qualification]** table. This content is always replaced by **#MESSAGE#** after the message is normalized. This process avoids having multiple entries for similar errors and is the same as for emails. For more on this, see [Bounce mail qualification](understanding-delivery-failures.md#bounce-mail-qualification).

The Extended generic SMPP connector applies a heuristic to find sensible default values: if the status begins with **DELIV**, it is considered a success because it matches the common statuses **DELIVRD** or **DELIVERED** used by most providers. Any other status leads to a hard failure.
