---
product: campaign
title: Understand delivery failures
description: Learn how to understand delivery failures
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
---
# Understand delivery failures{#understanding-delivery-failures}

>[!NOTE]
>
>Comprehensive guidance on understanding delivery failures is documented in the [Campaign v8 Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures) page. This content applies to both Campaign Classic v7 and Campaign v8 users, covering:
>
>* Delivery failure types and reasons (hard, soft, ignored)
>* Synchronous and asynchronous errors
>* Bounce mail qualification
>* Email, push notification, and SMS error types
>* Retry management and validity periods
>* Troubleshooting common delivery failures
>
>This page documents **Campaign Classic v7-specific configuration** for on-premise bounce mail management.

For common delivery failure concepts, error types, and troubleshooting guidance, refer to the [Campaign v8 Understanding delivery failures documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Campaign Classic v7 on-premise bounce mail configuration {#v7-bounce-mail-config}

The following configuration options are available for **Campaign Classic v7 on-premise installations** to manage bounce mail processing.

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

## Related topics

* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation)
* [Delivery statuses](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Campaign v8 documentation)
* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation)
* [Quarantine configuration](understanding-quarantine-management.md) (v7 on-premise)
* [Update bounce qualification](update-bounce-qualification.md) (v7 on-premise)
* [Email deliverability configuration](../../installation/using/email-deliverability.md) (v7 on-premise)
* [Deploying an instance](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 on-premise)
