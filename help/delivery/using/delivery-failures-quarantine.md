---
product: campaign
title: Delivery failures and quarantine management
description: Learn how to understand delivery failures and manage quarantines in Campaign Classic v7
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
---
# Delivery failures and quarantine management {#delivery-failures-quarantine}

>[!NOTE]
>
>Comprehensive guidance on delivery failures and quarantine management is documented in Campaign v8 documentation. This content applies to both Campaign Classic v7 and Campaign v8 users:
>
>* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} - Covers failure types, error reasons, synchronous/asynchronous errors, retry management, and troubleshooting
>* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} - Covers quarantine vs denylist, soft error thresholds, quarantine reports, and address removal
>
>This page documents **Campaign Classic v7-specific configuration** for bounce mail and quarantine management in hybrid and on-premise deployments.

## Understanding delivery failures

For common delivery failure concepts, error types, and troubleshooting guidance, refer to the [Campaign v8 Understanding delivery failures documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Bounce mail configuration {#bounce-mail-config}

The following configuration options are available for **Campaign Classic v7 hybrid/on-premise deployments** to manage bounce mail processing.

### Bounce mailbox configuration {#bounce-mailbox-configuration}

For on-premise installations, configuration of the bounce mailbox is detailed in [this section](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

Asynchronous error messages are collected by the Adobe Campaign platform through the bounce mailbox and qualified by the inMail process to enrich the list of email management rules.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, the bounce mailbox configuration is performed and managed by Adobe. No configuration is required.

### Bounce mail qualification management {#bounce-mail-qualification-management}

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, when the delivery of an email fails, the Adobe Campaign delivery server receives an error message from the messaging server or the remote DNS server. The list of errors is made up of strings contained in the message returned by the remote server. Failure types and reasons are assigned to each error message.

This list is available via the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** node. It contains all the rules used by Adobe Campaign to qualify delivery failures. It is non-exhaustive, and is regularly updated by Adobe Campaign and can also be managed by the user.

![](assets/tech_quarant_rules_qualif.png)

The message returned by the remote server on the first occurrence of this error type is displayed in the **[!UICONTROL First text]** column of the **[!UICONTROL Delivery log qualification]** table. If this column is not displayed, click the **[!UICONTROL Configure list]** button at the right bottom of the list to select it.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filters this message to delete the variable content (such as IDs, dates, email addresses, phone numbers, etc.) and displays the filtered result in the **[!UICONTROL Text]** column. The variables are replaced with **`#xxx#`**, except addresses that are replaced with **`*`**.

This process allows to bring together all failures of the same type and avoid multiple entries for similar errors in the Delivery log qualification table.
  
>[!NOTE]
>
>The **[!UICONTROL Number of occurrences]** field displays the number of occurrences of the message in the list. It is limited to 100 000 occurrences. You can edit the field, if you want, for example, to reset it.

Bounce mails can have the following qualification status:

* **[!UICONTROL To qualify]**: the bounce mail could not be qualified. Qualification must be assigned to the Deliverability team to guarantee efficient platform deliverability. As long as it isn't qualified, the bounce mail isn't used to enrich the list of email management rules.
* **[!UICONTROL Keep]**: the bounce mail was qualified and will be used by the **Refresh for deliverability** workflow to be compared to existing email management rules and enrich the list.
* **[!UICONTROL Ignore]**: the bounce mail is ignored by the Campaign MTA, meaning that this bounce will never cause the recipient's address to be quarantined. It will not be used by the **Refresh for deliverability** workflow and it will not be sent to client instances.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In case of an outage of an ISP, emails sent through Campaign will be wrongly marked as bounces. To correct this, you need to update bounce qualification. For more on this, see [this page](update-bounce-qualification.md).

### Email management rules configuration {#email-management-rules}

Mail rules are accessed via the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** node. Email management rules are shown in the lower part of the window.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>The default parameters of the platform are configured in the deployment wizard. For further information, refer to [this section](../../installation/using/deploying-an-instance.md).

The default rules are as follows:

>[!IMPORTANT]
>
>* The delivery server (MTA) has to be restarted if the parameters have been changed.
>* The modification or creation of management rules is for expert users only.

#### Inbound email {#inbound-email}

These rules contain the strings which can be returned by remote servers and which enable you to qualify the error (**Hard**, **Soft** or **Ignored**).

When an email fails, the remote server returns a bounce message to the address specified in the platform parameters. Adobe Campaign compares the content of each bounce message to the strings in the rule list, and then assigns it one of the three error types.

>[!NOTE]
>
>The user can create their own rules. When importing a package and when updating data via the **Refresh for deliverability** workflow, the user-created rules are overwritten.

For more on bounce mail qualification, refer to [this section](#bounce-mail-qualification-management).

#### Domain management {#domain-management}

For on-premise installations, the MTA applies a single **Domain management** rule to all domains.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* You can choose whether or not to activate certain identification standards and encryption keys to check the domain name, such as **Sender ID**, **DomainKeys**, **DKIM**, and **S/MIME**.
* The **SMTP relay** parameters let you configure the IP address and port of a relay server for a particular domain. For more on this, refer to [this section](../../installation/using/configuring-campaign-server.md#smtp-relay).

If your messages display **[!UICONTROL on behalf of]** in the sender address, make sure not to sign emails with **Sender ID**, which is the obsoleted proprietary email authentication standard from Microsoft. If the **[!UICONTROL Sender ID]** option is enabled, uncheck the corresponding box and contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Your deliverability will not be impacted.

#### MX management {#mx-management}

For on-premise installations, MX management rules are used to regulate the flow of outgoing emails for a specific domain.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

These rules are available in the deployment wizard and can be customized:

* **[!UICONTROL MX Management]**: this rule is used to control the flow of outgoing emails for a domain. It samples bounce messages and blocks sending where appropriate.

* **[!UICONTROL Period]**: the time frame during which messages are throttled or blocked.

* **[!UICONTROL Limit]**: the maximum number of messages allowed per time period.

* **[!UICONTROL Type]**: the error type (hard, soft, or ignored) used to determine sending behavior. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} for error type definitions.

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, MX rules and email flow management are managed by Adobe as part of the managed infrastructure. Contact Adobe Customer Care if you need to adjust MX settings for specific use cases.

## Quarantine management {#quarantine-management}

For comprehensive quarantine management guidance, refer to the [Campaign v8 Quarantine management documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantine configuration {#quarantine-config}

The following configuration options are available for **Campaign Classic v7 hybrid/on-premise deployments** to customize quarantine behavior.

### Soft error threshold configuration {#soft-error-threshold}

For on-premise installations using the legacy Campaign MTA, you can modify the number of errors and the period between two errors before an address is quarantined.

To configure these settings:

1. Access the deployment wizard from **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Navigate to **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configure:
   * **Number of errors**: The maximum number of soft errors before an address is quarantined (default: 5)
   * **Period between two significant errors**: The time window (in seconds) for error counting (default: 86,400 seconds = 1 day)

When the error counter reaches the threshold, the address is quarantined. If the last significant error occurred more than 10 days ago, the error counter is reinitialized.

For more details, refer to [this page](communication-channels.md) under **Delivery sending** > **Configure retries**.

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, retry settings and error thresholds are managed by Adobe based on IP performance and domain reputation. No configuration is required.

### Database cleanup workflow {#database-cleanup-workflow}

For on-premise installations, the **[!UICONTROL Database cleanup]** technical workflow automatically removes quarantined addresses that match specific conditions.

Access this workflow from **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

The workflow removes addresses from quarantine in the following cases:

* Addresses in **[!UICONTROL With errors]** status after a successful delivery
* Addresses in **[!UICONTROL With errors]** status if the last soft bounce occurred more than 10 days ago
* Addresses in **[!UICONTROL With errors]** status with **[!UICONTROL Mailbox full]** error after 30 days

Ensure this workflow runs regularly (recommended: daily) to maintain quarantine list hygiene.

For more on database cleanup, refer to [this section](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>For Campaign v8 Managed Cloud Services users, the database cleanup workflow is monitored and managed by Adobe.

### Push notification quarantine specifics {#push-quarantine-specifics}

For Campaign Classic v7, push notification quarantines follow the general quarantine mechanism with some channel-specific behaviors.

For **iOS** and **Android** push notifications, the quarantine mechanism uses device tokens rather than email addresses. When a mobile application is uninstalled or reinstalled, the associated token is quarantined.

For detailed information about push notification quarantine scenarios (iOS and Android error types, retry behavior, etc.), refer to the [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentation which includes comprehensive push notification error type tables.

### SMS quarantine specifics {#sms-quarantine-specifics}

For Campaign Classic v7, SMS quarantines follow the general quarantine mechanism with some channel-specific behaviors related to phone numbers rather than email addresses.

The SMS quarantine mechanism varies depending on the connector used:

* **Standard SMPP connectors**: Error qualification rules defined in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** apply to SMS deliveries.

* **Extended generic SMPP connector**: Error management is handled differently using regular expressions (regexes) to parse Status Report (SR) messages returned by the SMSC provider.

For detailed information about SMS quarantine scenarios and error types, refer to the [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentation which includes comprehensive SMS error type tables.

## Related topics

* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation)
* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation)
* [Delivery best practices](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Campaign v8 documentation)
* [Delivery statuses](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Campaign v8 documentation)
* [Database cleanup workflow](../../production/using/database-cleanup-workflow.md) (v7 hybrid/on-premise)
* [Configure delivery retries](communication-channels.md) (v7 hybrid/on-premise)
* [Update bounce qualification](update-bounce-qualification.md) (v7 hybrid/on-premise)
* [Email deliverability configuration](../../installation/using/email-deliverability.md) (v7 hybrid/on-premise)
* [Deploying an instance](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 hybrid/on-premise)

