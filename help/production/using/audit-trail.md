---
product: campaign
title: Audit trail
description: Learn how to monitor your instance with Campaign Audit trail
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
TQID: https://experienceleague.adobe.com/y8kDwxCY0MkBcDPUPY7hmFlpJc3l3qsEiDRhhMGqT00
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
---
# Audit trail{#audit-trail}

>[!INFO]
>
>Discover more about the Audit trail functionality in the [Adobe Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/audit-trail).

In Adobe Campaign, the **[!UICONTROL Audit trail]** gives you access to the complete history of changes made within your instance.

**[!UICONTROL Audit trail]** captures, in real-time, a comprehensive list of actions and events occurring within your Adobe Campaign instance. It includes a self-serve way to access a history of data to help answer questions such as: what happened to your workflows, and who last updated them or what did your users do in the instance.

>[!NOTE]
>
>Adobe Campaign is not auditing changes made within user rights, templates, personalization or campaigns.  
>Audit trail can only be managed by administrators of the instance.

![](assets/audit_trail_2.png)

+++ Learn more on Audit Trail available entities

* **Schema audit trail**: allows you to explore the changes made to your schemas, as well as identify who made these modifications and when they occurred.

  For detailed information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Workflow audit trail** tracks all actions related to your workflows, including:

    * Start
    * Pause
    * Stop
    * Restart
    * Cleanup which equals to the action Purge history
    * Simulate which equals to the action Start in simulation mode
    * Wakeup which equals to the action Execute pending tasks now
    * Unconditional Stop

  For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).
  
  For more on how to monitor workflows, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.


* **Option audit trail** allows you to check activities and last modifications done to your options.

  For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

* **Delivery audit trail** allows you to check the activities and last modifications done to your deliveries. 

  For more information on deliveries, refer to this [page](../../delivery/using/communication-channels.md).

* **External Account** allows you to check modifications made to external accounts, used by technical processes such as technical workflows or campaign workflows.

  For more information on external account, refer to this [page](../../installation/using/external-accounts.md).

* **Delivery Mapping** enables you to monitor activities and recent modifications made to your Delivery Mappings. 

  For more information on delivery mapping, refer to this [page](../../configuration/using/target-mapping.md).

* **Web Application** allows you to check modifications made to Web forms in Campaign V8 used to create pages with input and selection fields, and which may include data from the database. 

  For more information on web application, refer to this [page](../../web/using/about-web-applications.md).

* **Offer** allows you to check the activities and last modifications done to your offers.

  For more information on offer, refer to this [page](../../interaction/using/interaction-and-offer-management.md).

* **Operator** enables you to monitor activities and recent modifications made to your Operators.

  For more information on operators, refer to this [page](../../platform/using/access-management-operators.md).

+++
