---
title: Understanding delivery failures
seo-title: Understanding delivery failures
description: Understanding delivery failures
seo-description: 
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
---

# Understanding delivery failures{#understanding-delivery-failures}

## About delivery failures {#about-delivery-failures}

When a message (email, SMS, push notification) cannot be sent to a profile, the remote server automatically sends an error message, which is picked up by the Adobe Campaign platform and qualified to determine whether or not the email address or phone number should be quarantined. See [Bounce mail management](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

>[!NOTE]
>
>Email error messages (or "bounces") are qualified by the inMail process. SMS error messages (or "SR" for "Status Report") are qualified by the MTA process.

Once a message is sent, the delivery logs allows you to view the delivery status for each profile and the associated failure type and reason.

Messages can also be excluded during the delivery preparation if an address is quarantined or if a profile is blacklisted. Excluded messages are listed in the delivery dashboard.

**Related topics:**

* [Delivery logs and history](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [Failed status](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [Delivery failure types and reasons](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Delivery failure types and reasons {#delivery-failure-types-and-reasons}

There are three types of error when a message fails. Each error type determines if an address is sent to quarantines. For more on this, refer to [Conditions for sending an address to quarantine](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Hard**: A "hard" error indicates an invalid address. This involves an error message that explicitly states that the address is invalid, such as: "Unknown user".
* **Soft**: This might be a temporary error, or one that could not be categorized, such as: "Invalid domain" or "Mailbox full".
* **Ignored**: This is an error that is known to be temporary, such as "Out of office", or a technical error, for example if the sender type is "postmaster".

The possible reasons for a delivery failure are: 

<table> 
 <tbody> 
  <tr> 
   <td> Error label </td> 
   <td> Error type </td> 
   <td> Technical Value </td> 
   <td> Description </td> 
  </tr> 
  <tr> 
   <td> Account disabled </td> 
   <td> Soft / Hard </td> 
   <td> 4 </td> 
   <td> The account linked to the address is not active anymore. When the Internet Access Provider (IAP) detects a lengthy period of inactivity, it can close the user's account. Deliveries to the user's address will then be impossible. If the account is temporarily disabled due to six months of inactivity and can still be activated, the status With errors will be assigned and the account will be tried again until the error counter reaches 5. If the error signals that the account is permanently deactivated, it will directly be set to Quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Address in quarantine </td> 
   <td> Hard </td> 
   <td> 9 </td> 
   <td> The address was placed in quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Address not specified </td> 
   <td> Hard </td> 
   <td> 7 </td> 
   <td> No address is given for the recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> Bad-quality address </td> 
   <td> Ignored </td> 
   <td> 14 </td> 
   <td> The quality rating for this address is too low.<br /> </td> 
  </tr> 
  <tr> 
   <td> Blacklisted address </td> 
   <td> Hard </td> 
   <td> 8 </td> 
   <td> The address was blacklisted at the time of sending. This status is used for importing data from external lists and external systems when importing data into the Adobe Campaign Quarantine list.<br /> </td> 
  </tr> 
  <tr> 
   <td> Control address </td> 
   <td> Ignored </td> 
   <td> 127 </td> 
   <td> The recipient's address is part of the control group.<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> Ignored </td> 
   <td> 10 </td> 
   <td> The address of the recipient was already in this delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Error ignored </td> 
   <td> No error </td> 
   <td> 25 </td> 
   <td> The address is whitelisted. The error is therefore ignored and an email will be sent.<br /> </td> 
  </tr> 
  <tr> 
   <td> Excluded after arbitration </td> 
   <td> Ignored </td> 
   <td> 12 </td> 
   <td> The recipient was excluded by a 'arbitration' type campaign typology rule.<br /> </td> 
  </tr> 
  <tr> 
   <td> Excluded by a SQL rule </td> 
   <td> Ignored </td> 
   <td> 11 </td> 
   <td> The recipient was excluded by a 'SQL' type campaign typology rule.<br /> </td> 
  </tr> 
  <tr> 
   <td> Invalid domain </td> 
   <td> Soft </td> 
   <td> 2 </td> 
   <td> The domain of the email address is incorrect or no longer exists. This profile will be targeted again until the error count reaches 5. After this, the record will be set to Quarantine status and no retry will follow.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mailbox full </td> 
   <td> Soft </td> 
   <td> 5 </td> 
   <td> The mailbox of this user is full and cannot accept more messages. This profile will be targeted again until the error count reaches 5. After this, the record will be set to Quarantine status and no retry will follow.<br /> This type of error is managed by a clean-up process, the address is set to a valid status after 30 days.<br /> Warning: in order for the address to be automatically removed from the list of quarantined addresses, the Database cleanup technical workflow must be started.<br /> </td> 
  </tr> 
  <tr> 
   <td> Not connected </td> 
   <td> Ignored </td> 
   <td> 6 </td> 
   <td> The recipient's mobile phone is switched off or not connected to the network when the message is sent.<br /> </td> 
  </tr> 
  <tr> 
   <td> Not defined </td> 
   <td> Not defined </td> 
   <td> 0 </td> 
   <td> The address is in qualification because error have not been incremented yet. This type of error occurs when a new error message is sent by the server: it can be an isolated error, but if it occurs again, the error counter increases, which will alert the technical teams. They can then carry out message analysis and qualify this error, via the <span class="uicontrol">Administration</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">Non deliverables Management</span> node in the tree structure.<br /> </td> 
  </tr> 
  <tr> 
   <td> Not eligible for the offers </td> 
   <td> Ignored </td> 
   <td> 16 </td> 
   <td> The recipient was not eligible for the offers in the delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Refused </td> 
   <td> Soft / Hard </td> 
   <td> 20 </td> 
   <td> The address has been placed in quarantine due to a security feedback as a spam report. According to the error, the address will be tried again until the error counter reaches 5, or it will be directly sent to quarantines.<br /> </td> 
  </tr> 
  <tr> 
   <td> Target limited in size </td> 
   <td> Ignored </td> 
   <td> 17 </td> 
   <td> The maximum delivery size was reached for the recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unqualified address </td> 
   <td> Ignored </td> 
   <td> 15 </td> 
   <td> The postal address has not been qualified.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unreachable </td> 
   <td> Soft / Hard </td> 
   <td> 3 </td> 
   <td> An error has occurred in the message delivery chain. It could be an incident on the SMTP relay, a domain that is temporarily unreachable, etc. According to the error, the address will be tried again until the error counter reaches 5, or it will be directly sent to quarantines.<br /> </td> 
  </tr> 
  <tr> 
   <td> User unknown </td> 
   <td> Hard </td> 
   <td> 1 </td> 
   <td> The address does not exist. No further deliveries will be attempted for this profile.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Retries after a delivery temporary failure {#retries-after-a-delivery-temporary-failure}

If a message fails due to a **Soft** or **Ignored** error that is temporary, retries will be performed during the delivery duration.

>[!NOTE]
>
>Temporarily undelivered messages can only be related to a **Soft** or **Ignored** error, but not a **Hard** error (see [Delivery failure types and reasons](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

To modify the duration of a delivery, go to the advanced parameters of the delivery or delivery template and specify the desired duration in the corresponding field. The advanced delivery properties are presented in [this section](../../delivery/using/key-steps-when-creating-a-delivery.md#defining-validity-period).

The default configuration allows five retries at one-hour intervals, followed by one retry per day for four days. The number of retries can be changed globally (contact your Adobe technical administrator) or for each delivery or delivery template (see [this section](../../delivery/using/key-steps-when-creating-a-delivery.md#configuring-retries)).

## Synchronous and asynchronous errors {#synchronous-and-asynchronous-errors}

A message can fail immediately (synchronous error), or later on, after it has been sent (asynchronous error).

* Synchronous error: the remote mail server contacted by the Adobe Campaign delivery server immediately returned an error message, the delivery is not allowed to be sent to the profile's server. Adobe Campaign qualifies each error in order to determine whether or not the email addresses concerned should be quarantined. See [Bounce mail qualification](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification). 
* Asynchronous error: a bounce mail or a SR was resent later by the receiving server. This mail is loaded into a technical mailbox the application uses to label messages with an error. Asynchronous errors can occur up until one week after a delivery has been sent.

  >[!NOTE]
  >
  >Configuration of the bounce mailbox is detailed in [this section](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

  The feedback loop operates like bounce emails. When a user qualifies an email as spam, you can configure email rules in Adobe Campaign to block all deliveries to this user. Messages sent to users who have qualified an email as spam are automatically redirected towards an email box specifically created for this purpose. The addresses of these users are blacklisted even though they didn't click the unsubscription link. Addresses are blacklisted in the (**NmsAddress**) quarantine table and not the (**NmsRecipient**) recipient table.

  >[!NOTE]
  >
  >Complaint management is detailed in the [Deliverability management](../../delivery/using/about-deliverability.md) section.

## Bounce mail management {#bounce-mail-management}

The Adobe Campaign platform lets you manage email delivery failures via the bounce mail functionality. When an email cannot be delivered to a recipient, the remote messaging server automatically returns an error message (bounce mail) to a technical inbox designed for this purpose. Error messages are collected by the Adobe Campaign platform and qualified by the inMail process to enrich the list of email management rules

### Bounce mail qualification {#bounce-mail-qualification}

When the delivery of an email fails, the Adobe Campaign delivery server receives an error message from the messaging server or the remote DNS server. The list of errors is made up of strings contained in the message returned by the remote server. Failure types and reasons are assigned to each error message.

This list is available via the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** node. It contains all the rules used by Adobe Campaign to qualify delivery failures. It is non-exhaustive, and is regularly updated by Adobe Campaign and can also be managed by the user.

![](assets/tech_quarant_rules_qualif.png)

* The message returned by the remote server on the first occurrence of this error type is displayed in the **[!UICONTROL First text]** column of the **[!UICONTROL Delivery log qualification]** table. If this column is not displayed, click the **[!UICONTROL Configure list]** button at the right bottom of the list to select it.

  Adobe Campaign filters this message to delete the variable content (such as IDs, dates, email addresses, phone numbers, etc.) and displays the filtered result in the **[!UICONTROL Text]** column. The variables are replaced with **#**xxx**#**, except addresses that are replaced with **&#42;**.

  This process allows to bring together all failures of the same type and avoid multiple entries for similar errors in the Delivery log qualification table.

* The **[!UICONTROL Number of occurrences]** field displays the number of occurrences of the message in the list. It is limited to 100 000 occurrences. You can edit the field, if you want, for example, to reset it.

Bounce mails can have the following qualification status:

* **[!UICONTROL To qualify]** : the bounce mail could not be qualified. Qualification must be assigned to the Deliverability team to guarantee efficient platform deliverability. As long as it isn't qualified, the bounce mail isn't used to enrich the list of email management rules.
* **[!UICONTROL Keep]** : the bounce mail was qualified and will be used by the **Refresh for deliverability** workflow to be compared to existing email management rules and enrich the list.
* **[!UICONTROL Ignore]** : the bounce mail was qualified but will not be used by the **Refresh for deliverability** workflow. It will not be sent to client instances.

![](assets/deliverability_qualif_status.png)

### Email management rules {#email-management-rules}

Mail rules are accessed via the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** node. Email management rules are shown in the lower part of the window.

These rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>The default parameters of the platform are configured in the deployment wizard. For further information, refer to [this section](../../installation/using/deploying-an-instance.md).

The default rules are as follows:

* **Inbound email**

  When an email fails, the remote server returns a bounce message to the address specified in the platform parameters. Adobe Campaign compares the content of each bounce mail to the strings in the list of rules, and then assigns it one of the three error types.

  The user can create his own rules.

  >[!CAUTION]
  >
  >When importing a package and when updating data via the **Refresh for deliverability** workflow, the user-created rules are overwritten.

* **Domain management**

  The domain management rules are used to regulate the flow of outgoing emails for a specific domain. They sample the bounce messages and block sending where appropriate. The Adobe Campaign messaging server applies rules specific to the domains, and then the rules for the general case represented by an asterisk in the list of rules. Rules for the Hotmail and MSN domains are available by default in Adobe Campaign.

  Click the **[!UICONTROL Detail]** icon to access rule configuration.

  ![](assets/tech_quarant_domain_rules_02.png)

  To configure domain management rules, simply set a threshold and select certain SMTP parameters. A **threshold** is a limit calculated as an error percentage beyond which all messages towards a specific domain are blocked.

  For example, in the general case, for a minimum of 300 messages, the sending of emails is blocked for three hours if the error rate reaches 90%.

  The **SMTP parameters** act as filters applied for a blocking rule.

    * You can choose whether or not to activate certain identification standards and encryption keys to check the domain name, such as **Sender ID**, **DomainKeys**, **DKIM**, and **S/MIME**.
    * **SMTP relay**: lets you configure the IP address and the port of a relay server for a particular domain.

* **MX Management**

  For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

>[!CAUTION]
>
>* The delivery server (MTA) must be restarted if the parameters have been changed.
>* The modification or creation of management rules is for expert users only.
>

