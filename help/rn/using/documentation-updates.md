---
product: campaign
title: Adobe Campaign Classic v7 Documentation Updates
description: This page lists all the new features and updates in Adobe Campaign Classic documentation
feature: Release Notes
role: User
level: Beginner
hide: yes
hidefromtoc: yes
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
---
# Documentation Updates{#documentation-updates}

This page lists all the new features and documentation updates per month and Campaign release.

Refer to the [Adobe Campaign Classic Release Notes](../../rn/using/latest-release.md) for release related updates.

## 2025

### March 2025 {#march-2025}

As part of a Campaign v8 promotion initiative, we have started reorganizing the Campaign Classic documentation set. In 7.4.2, we are releasing the first milestone. The following guides have been replaced with landing pages including links to v8 documentation:

* Orchestrate marketing campaigns: this guide has been replaced with a [landing page](../../campaign/using/about-marketing-campaigns.md). 
* Marketing Resource Management: this guide has been removed.
* Distributed Marketing: this guide has been removed. 
* Automate with workflows: this guide has been replaced with a [landing page](../../workflow/using/about-workflows.md)

## 2024

### Sept 2024 {#sept-2024}

The release statuses have been reduced and simplified. [Read more](rn-overview.md)

Linux packages installation has been updated for v7.4.1. [Read more](../../installation/using/installing-packages-with-linux.md)

### June 2024 {#june-2024}

Updated Release Notes section with 7.4.1 improvements, compatibility updates, and patches. [Read more](latest-release.md)

A note has been added to specify how to clear instance variables when restarting workflows. [Read more](../../workflow/using/starting-a-workflow.md)

### April 2024 {#apr-2024}

A caution note has been added about user creation with Adobe Identity Management System (IMS). [Read more](../../platform/using/access-management.md)

Missing options for the Web Download workflow activity have been added. [Read more](../../workflow/using/web-download.md)

A caution note has been added to the **Change Dimension** and **Change Data source** activities about their usage in a workflow. [Read more](../../workflow/using/change-data-source.md)

### March 2024 {#mar-2024}

Mobile app configuration section has been updated for iOS token-based connection to APNs. [Read more](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)

### January 2024 {#jan-2024}

Information has been added on how the default postalAddress field for Direct Mail is defined and why it is important to make sure that addresses are complete. [Read more](../../delivery/using/about-direct-mail-channel.md)

Added a new page on how to configure the SMS channel in Campaign on a mid-sourcing infrastructure. [Read more](../../delivery/using/sms-set-up-mid.md)

## 2023

### December 2023 {#dec-2023}

JWT (JSON Web Tokens) is currently in the process of depreciation and is being replaced with OAuth. The transition is being carried out progressively within Campaign's upcoming releases and documentation will be updated to reflect these updates.

Added FDA external account configuration for Amazon Redshift. [Read more](../../installation/using/configure-fda-redshift.md)

### August 2023 {#aug-2023}

A limitation has been added to specify that you cannot use Adobe Campaign to uncompress zipped files larger than 4Gb. [Read more](../../platform/using/unzip-decrypt.md)

### April 2023 {#apr-2023}

Added a technote about how to enable Microsoft Edge Chromium on on-premise/hybrid environments. [Read more](../../technotes/using/edge-chromium.md)

### March 2023 {#mar-2023}

Updated Release Notes section with 7.3.3 improvements and patches. [Read more](latest-release.md)


+++ 2022


## November 2022 {#nov-2022}

Updated Release Notes section with 7.3.2 improvements and patches. [Read more](latest-release.md)

Updated Compatibility Matrix with Teradata 17 support. [Read more](compatibility-matrix.md)

The File and resource management section has been updated with additional information on the **uploadWhiteList** attribute. [Read more](../../installation/using/file-res-management.md)

The documentation on security zones has been updated withn additional information on the **allowDebug** attribute attribute. [Read more](../../installation/using/security-zones.md#recommendations)

The migration guide has been updated. References to unsupported Adobe Campaign versions have been removed. [Read more](../../migration/using/about-migration.md)


## July 2022 {#july-2022}

<!--Transition to the new deliverability server is detailed in a new technote. [Read more](../../technotes/using/deliverability-server.md)-->

**Documentation updates coming with the 7.3.1 release**

Updated Compatibility Matrix. [Read more](compatibility-matrix.md)

Updated Release Notes section. [Read more](rn-overview.md)

Time Sensitive notifications with iOS 15. [Read more](../../delivery/using/create-notifications-ios.md)


## March 2022 {#mar-2022}

Added a detailed description for the **[!UICONTROL Test SMTP delivery]** option. [Read more](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

The Get Started with upgrades page has been updated to clarify Campaign Console upgrade guidelines. [Read more](../../rn/using/rn-overview.md)

New Campaign v7.2.2 build is now available. [Read more](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

Legacy PostgreSQL versions that have reached end of life have been added to the [Deprecated and removed features](../../rn/using/deprecated-features.md#dbe-eol) page.

## February 2022 {#february-2022}

Updated the **File transfer** activity section with a reminder to manually monitor the size of the archived content in the SFTP directory in case the **Delete the source files after transfer** option is not selected. [Read more](../../workflow/using/file-transfer.md#properties)

The Quarantine vs Denylist section has been clarified. [Read more](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

The sections on how to send an address to quarantine and how to remove addresses from the quarantine list have been updated. [Read more](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Added a workflow best practice to recommend not to perform multiple stop requests on the same workflow. [Read more](../../workflow/using/workflow-best-practices.md)

Added information on how to stop a recurring delivery from running within a campaign. [Read more](../../workflow/using/recurring-delivery.md)

## January 2022 {#january-2022}

**Documentation updates coming with the 7.2.1 release**

Updated Compatibility Matrix. [Read more](compatibility-matrix.md)

Updated Release Notes section. [Read more](rn-overview.md)

Updated FDA external account configuration for Snowflake. [Read more](../../installation/using/configure-fda-snowflake.md)

Updated FDA external account configuration for Azure Synapse Analytics. [Read more](../../installation/using/configure-fda-synapse.md#azure-external)

Updated Google BigQuery FDA Connector. [Read more](../../installation/using/configure-fda-google-big-query.md)

Following their deprecation, Microsoft CRM, Salesforce, Oracle CRM On Demand action activities have been removed from the documentation.

New option **Abort on error** added to the workflow Error Management section. [Read more](../../workflow/using/advanced-parameters.md#in-case-of-errors)

Added batch update option in the CRM connector activity. [Read more](../../workflow/using/crm-connector.md)

+++

+++ 2021

## December 2021{#dec-2021}

Campaign Classic v7 Release Notes have been reorganized to simplify navigation. [Read more](rn-overview.md)

Documentation about Form edition in Campaign has been updated and improved. [Read more](../../configuration/using/editing-forms.md)

CentOs 8 has reached End-of-Life and is now deprecated with Adobe Campaign Classic. [Read more](deprecated-features.md)

## November 2021{#nov-2021}

Added a limitation about Incoming SMS (MO). [Read more](../../delivery/using/sms-protocol.md#multipart)

Updated the migration process logs details for CRM connector deployment. [Read more](../../migration/using/testing-the-migration.md#verification-process)

Added requirements about IMS permissions to implement Adobe Campaign-Adobe Analytics integration. [Read more](../../integrations/using/adobe-analytics-provisioning.md)

Updated Adobe Analytics Data Connector End-of-Life date from March 1, 2022 to August 17, 2022. [Read more](deprecated-features.md)

Added a section about how to use JavaScript to calculate values, exchange data and to execute specific operations using SOAP calls.[Read more](../../workflow/using/javascript-scripts-and-templates.md) 

Added samples of JavaScript codes implementation in workflows. [Read more](../../workflow/using/javascript-in-workflows.md)


## October 2021{#oct-2021}

Existing technotes have been grouped to the new **Technote** section.

The **Hardware sizing recommendations** page has been updated and added to the **Technotes** section. [Read more](../../technotes/using/hardware-sizing.md)

## September 2021{#sept-2021}

**Documentation updates coming with the 21.1.4 release**

The **Gauge** chart type has been removed.

Reports and web applications screenshots and parameters have been updated following Adobe Flash removal.

The [billing technical workflow](../../production/using/monitoring-processes.md#billing-report) description has been updated with a new guardrail.

## August 2021{#aug-2021}

Added new workflow activity: Change Data Source - [Learn more](../../workflow/using/change-data-source.md)

Applicability badges have been added to the documentation pages: **Applies to v7** for Campaign Classic v7 capabilities only, and **Applies to v7 & v8** for common capabilities.

Added a note about the integration between Campaign and AEM Assets which has been decomissonned starting Adobe Experience Manager 6.4. [Learn more](../../integrations/using/configuring-access-to-assets.md)


## July 2021 {#july-2021}

[Campaign 21.1.3 release](../../rn/using/latest-release.md#release-21-1-3-build-9330) has moved to General Availability (GA).


## June 2021 {#june-2021}

The **Transactional Messaging** section has been reorganized and clarified with a new Get started section, including an [enhanced schema](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle) for a better understanding of the process. [Read more](../../message-center/using/about-transactional-messaging.md)

**Documentation updates coming with the 21.1.3 release**

Integration with Adobe Journey Orchestration - [Learn more](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html). A step-by-step use case is presented in [this page](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html)

LINE channel enhancements - [Learn more](../../delivery/using/line-channel.md)

New Vertica Analytics FDA connector - [Learn more](../../installation/using/configure-fda-vertica.md)

New Google BigQuery FDA connector - [Learn more](../../installation/using/configure-fda-google-big-query.md)

The "Billing (billing)" technical workflow description now includes the tasks originally performed by the "Number of active billing profiles (billingActiveContactCount)". [Read more](../../workflow/using/about-technical-workflows.md)

## May 2021 {#may-2021}

The Workflow Heatmap report documentation has been updated and improved. [Read more](../../workflow/using/heatmap.md)

Campaign Client Console requirements have been updated in the Compatibility Matrix. [Read more](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

Campaign Client Console installation for steps have been improved and clarified. [Read more](../../installation/using/installing-the-client-console.md)

A new technote has been created about the Tracked URLs signature issue. [Read more](../../technotes/using/tracked-urls.md)

## April 2021 {#april-2021}

A new section has been on how to work with Adobe Experience Platform Sources and Destinations to share data between Campaign Classic and Adobe Real-time Customer Data Platform (RTCDP). [Read more](../../integrations/using/get-started-sources-destinations.md)

A new technote has been created to learn how to update bounce qualification after an ISP outage. [Read more](../../delivery/using/update-bounce-qualification.md)

## March 2021 {#march-2021}

The [Get started with SMS section](../../delivery/using/sms-channel.md) has been reorganized and improved. You can now learn how to [configure the SMS channel](../../delivery/using/sms-set-up.md), [create an SMS](../../delivery/using/sms-create.md), [send and track SMS](../../delivery/using/sms-send.md) in dedicated sections.

The "Help & support options" page for Campaign Classic has been integrated into the core documentation. [Read more](../../support.md)

A new section has been added with best practices and checks to perform regarding security and privacy. [Read more](../../installation/using/get-started-security-privacy.md)

The [permission management chapter](../../platform/using/access-management.md) has been improved and split into sections, including details about [Operators](../../platform/using/access-management-operators.md) , [Groups of operators](../../platform/using/access-management-groups.md) , [Named rights](../../platform/using/access-management-named-rights.md)  and [Folder management](../../platform/using/access-management-folders.md) .

Learn how to create and manage your campaigns through these new pages: 
* [Create and configure campaign templates](../../campaign/using/marketing-campaign-templates.md)
* [Marketing campaign deliveries](../../campaign/using/marketing-campaign-deliveries.md)
* [Select the audience of your campaigns](../../campaign/using/marketing-campaign-target.md)
* [Manage associated documents](../../campaign/using/marketing-campaign-assets.md) 
* [Set up and manage the approval process](../../campaign/using/marketing-campaign-approval.md)

Information has been added in the **[!UICONTROL Advanced JavaScript]** activity section on how to use the task.setCompleted() method to terminate the task and prevent future recalls. [Read more](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

The [Deliverability](../../delivery/using/about-deliverability.md) section has been updated and now includes links to the new [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html). All generic information related to deliverability that can apply to various Adobe solutions has been moved to the [Best Practice Guide Appendix](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html#additional-resources).

## February 2021 {#release-21.1}

**Documentation updates coming with the 21.1 release**

The new **Email Feedback Service** capability (private beta) is documented [here](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

The **Server configuration file** section has been updated with the configuration parameters needed for Campaign to connect to another service using IMS. [Read more](../../installation/using/the-server-configuration-file.md#ims)

In the list of delivery statuses, the description for **Taken into account by the service provider** has been updated: this status is now also used for email deliveries sent using the [Email Feedback Service](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Read more](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

The keyboard shortcuts available on the new logon screen to connect to Adobe Campaign are now documented. [Read more](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Other updates**

A new section has been added with detailed information on how to perform A/B testing using workflows. [Read more](../../delivery/using/get-started-a-b-testing.md)

The Adobe Campaign Enhanced MTA section has moved [here](../../delivery/using/sending-with-enhanced-mta.md).

A new page has been added to provide an overview of tracking capabilities in [!DNL Campaign Classic]. [Read more](../../delivery/using/about-message-tracking.md)

Tracking documentation has been consolidated. For general tracking guidance, refer to [Campaign v8 tracking documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}. For v7-specific features, see [Message tracking](../../delivery/using/about-message-tracking.md).

The **Sending an email** section has been reorganized and clarified with new subsections. [Read more](../../delivery/using/sending-messages.md)

## January 2021 {#jan-2021}

The **[!UICONTROL Fork]** activity section has been enriched with best practices. [Read more](../../workflow/using/fork.md)

The **CRM Connectors** section has been updated, improved and reorganized. [Read more](../../platform/using/crm-connectors.md).

Steps to connect **Adobe Campaign and Microsoft Dynamics** are now detailed in a dedicated page. [Read more](../../platform/using/crm-ms-dynamics.md).

Oracle On Demand API is now deprecated as a CRM connected with Campaign. [Read more](../../rn/using/deprecated-features.md).

Learn how to find out the current version of embedded Tomcat web servlet used in an instance of Adobe Campaign [here](../../production/using/locate-tomcat-version.md).

The list of technical workflows with their associated packages has been enhanced and centralized into one single page. [Read more](../../workflow/using/about-technical-workflows.md)

The troubleshooting section of the **Monitoring** guide has been reorganized and enhanced with a landing page. [Read more](../../production/using/troubleshooting.md).

A new **Importing and exporting data** section is available with new pages related to workflows, data compression, encryption, and import best practices. [Read more](../../platform/using/get-started-data-import-export.md)

+++
