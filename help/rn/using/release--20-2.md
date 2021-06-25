---
product: campaign
title: Release 20.2
description: Release 20.2
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: fcaab1aa-c8f9-4606-b0d8-eb481a38f588
---
# Release 20.2{#release-20-2}

## ![](assets/do-not-localize/green_2.png) Release 20.2.5 - Build 9188 {#release-20-2-5-build-9188}

_April 15, 2021_

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)

**Console upgrade only is mandatory. No server upgrade is required.**

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_March 31, 2021_

**Improvements**

* An improvement has been made to prevent crashes on invalid soap calls. This could cause the instance to stop working when trying to run specific complex queries. (NEO-28796, NEO-30553)
* Fixed a regression which prevented SMS deliveries with TLS from being sent due to the hostname verification. (NEO-29581)
* Fixed an issue which prevented signed tracking links from working on some email clients. (NEO-28414, NEO-29615)
* Fixed a tracking id sequence when using webApp tracking tags which could cause conflicts with duplicate IDs. (NEO-27931)
* Fixed an issue which caused running workflows to be stopped by the daily wfserver restart. (NEO-30047)
* Fixed a security issue using API calls made by non-admin users when trying to synchronize Adobe Experience Manager templates. (NEO-32389, NEO-23487)
* Fixed an issue causing the console to crash when closing a delivery dialog on a delivery created with from a template. (NEO-31547)
* Fixed an issue which occurred when creating and saving a delivery within the **Targeting & Workflow** tab of a campaign: the preview would fail with the following error. (NEO-29440)
* Fixed an issue with Tomcat 8.5 sending invalid answers which caused errors in Transactional Messaging logs. (NEO-30858)
* Fixed a regression issue causing memory corruption in external thread management and impacting performance.
* Fixed an issue which could cause the Billing workflow to fail when using a custom target mapping. The primary key of the custom schema is stored in the ‘sourceId’ column which only allowed integer values. It now allows integer as well as string values. (NEO-25914, NEO-28146)
* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453)

## ![](assets/do-not-localize/red_2.png) Release 20.2.4 - Build 9187 {#release-20-2-4-build-9187}

_April 15, 2021_

* Fixed a client console regression which caused persistent error messages on the IMS connection screen. (NEO-34821)
* Fixed a regression preventing the usage of some components of the console, such as the date picker and images management in deliveries. (NEO-31453, NEO-31454)

**Console upgrade only is mandatory. No server upgrade is required.** 

>[!NOTE]
>
> Connect to [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) to download the new version. Learn how to propose the console update to all end users [in this page](../../installation/using/client-console-availability-for-windows.md).

_December 22, 2020_

>[!CAUTION]
>
> * This release comes with a new connection protocol: if you are connecting to Campaign through Adobe Identity Service (IMS), upgrade is mandatory for both Campaign server and client console to be able to connect to Campaign after **June 30, 2021**.  [Learn more](../../technotes/ims-updates.md)
> * This release comes with a [security fix](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): upgrade is mandatory to reinforce your environment security. 
> * If you are using the Experience Cloud Triggers integration through oAuth authentication, you need to move to Adobe I/O as described [in this page](../../integrations/using/configuring-adobe-io.md). Legacy oAuth authentication mode with Campaign will be retired on **November 30, 2021**.

**Improvements**

* The connection protocol has been updated to follow the new IMS authentication mechanism. 
* Triggers integration authentication originally based on oAUTH authentication setup to access pipeline has been changed and moved to Adobe I/O. [Learn more](../../integrations/using/configuring-adobe-io.md)
* Following the [end of support for iOS APNs legacy binary protocol](https://developer.apple.com/news/?id=c88acm2b), all instances using this protocol are updated to HTTP/2 protocol during postupgrade.
* Fixed a security issue to reinforce protection against Server Side Request Forgery (SSRF) issues. (NEO-27777)
* Fixed an issue causing the deactivation of the SMPP connector after a connection error, preventing other SMS deliveries from being sent and leading to performance issues. (NEO-28609)
* Fixed a server crash issue by preventing memory corruption when cleaning the expression parser. (NEO-26856)
* Fixed an issue that caused the server to crash when displaying the target data of the remainder from a **Split** activity in a workflow.
* Fixed an issue that could display an error message when trying to preview SMS messages after a query on another schema than **Recipient** (nms:recipient). (NEO-27517)
* Fixed an issue when making an HTTPS connection request with the port number explicitly defined in the host name, the call failed with a certificate error. (NEO-29146)
* Fixed an issue in POSIX thread management which generated large core dump files on the marketing instance. (NEO-28117, NEO-29281)
* Fixed issues which could cause the web process to crash when preparing deliveries or with recurring delivery preview. (NEO-27790, NEO-27517)
* Fixed an issue which caused deliveries or proof sending to fail when triggered by a non-admin operator. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **New Control Panel October release** with domain configuration using CNAMEs and new database monitoring capabilities. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Release 20.2.3 - Build 9182 {#release-20-2-3-build-9182}

_September 11, 2020_

* Fixed a regression causing delivery preparation to be blocked due to a single erroneous function on delivery part leading to memory overload. (NEO-27346)
* Fixed a postupgrade issue which turned off Apache and the web server before the web application republication. (NEO-27155)
* Fixed a regression on HTML template management leading to tracking URLs becoming visible due to a misintepretation of tabs. (NEO-25909)
* Fixed an issue with the database cleanup workflow which could fail due to unmanaged data source. (NEO-23160, NEO-23364)
* The cleanup workflow now purges expired lists by batches of 100 instead of one by one.
* Fixed a regression which prevented you from modifying the internal name of an external account. (NEO-27323)
* Fixing a regression during postupgrade causing an incorrect start of nlserver (error logs).
* The update management for shared memory has been improved. The additional steps required in 20.2 are not needed anymore. 

## ![](assets/do-not-localize/red_2.png) Release 20.2.2 - Build 9180 {#release-20-2-2-build-9180}

_July 22, 2020_

* Fixed an issue which prevented tracking from working when the signature feature was disabled. (NEO-26411)
* Fixed an issue which led to unsigned links from personalized domains being blocked when they should be allowed. (NEO-25210)
* Fixed an issue which could prevent you from opening/clicking tracking URLs when using certain legacy versions of Outlook. (NEO-25688)
* Fixed an issue which led to mirror page URLs being incorrectly defined in email deliveries (due to improper ASCII character control). (NEO-26084)
* Fixed an issue with encoding URL management in the anti-phishing service. (NEO-25283)
* Fixed an issue which prevented the tracking of URLs using fragments in personalization parameters (anchor tags with pound-sign) from working. (NEO-25774)
* Fixed a tracking issue when using specific custom tracking formulas. (NEO-25277)
* Fixed an issue which prevented the tracking of "notification clicks" from working (iOS and Android push notifications). (NEO-25965)
* Fixed a regression impacting calculated fields in a workflow causing the workflow to fail. (NEO-25194)
* Fixed a regression which prevented the on-the-fly creation of web tracking URLs from working. (NEO-20999)
* Fixed a regression issue with out-of-the-box delivery reports which appeared truncated when exported to PDF. (NEO-25757)
* Fixed a crash issue in the deployment wizard.
* Fixed an issue which could prevent the Offer notification workflow from properly working after a postupgrade.
* The iOS HTTP2 connector has been improved (third-party updates and error management). (NEO-25904, NEO-25903)
* The jarsToSkip list in catalina.properties has been updated to remove the reference to a jar file that was no longer used (iOS notifications).
* Fixed an issue blocking delivery preparation after postupgrade.
* Following the switch to the [new sequence ID mechanism](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), all web applications that are updating the recipient table are republished during postupgrade.
* Fixed a potential XSS vulnerability in delivery content. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **New Control Panel June release** with Active profiles monitoring, Subdomain deliverability audit and GPG keys management. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Release 20.2.1 - Build 9178 {#release-20-2-1-build-9178}

_June 8, 2020_

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Support of Emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>When designing a message in Campaign, you can now easily insert emoticons in the message body, using a dedicated button. They can also be added in the email subject line. You can customize the list of available emoticons in the interface.</p>
    <p>For more information about adding emoticons, refer to the <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">detailed documentation</a>. Learn how to customize the emoticon list <a href="../../delivery/using/customizing-emoticon-list.md">in this section</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>You can now connect your Campaign instance to your Azure Synapse external database. This connection is managed through a new external account.</p>
    <p>Azure Synapse is only available for Hybrid and On-premise environments. For more information, refer to the <a href="../../installation/using/configure-fda-synapse.md">detailed documentation</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thailand and Brazil Privacy Laws</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Thailand’s Personal Data Protection Act (PDPA) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. </p>
   <p>Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective early 2021 for all companies collecting or processing personal data in Brazil.</p>
   <p>These regulations apply to Adobe Campaign customers who hold data for Data Subjects residing in these countries. In addition to the privacy capabilities already available in Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity to include additional capabilities, to help facilitate your readiness for PDPA and LGPD:</p>
   <ul> 
     <li><p>Right to Access and Right to Delete: we are leveraging the capabilities that were added for GDPR and CCPA. <a href= https://helpx.adobe.com/campaign/kb/acc-privacy.html>Read more</a></p></li> 
     <li> <p>When creating a Privacy request using Campaign interface or API, you now select the <strong>Regulation</strong> type: PDPA, LGPD, GDPR, CCPA. <a href=https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests>Read more</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Improved security on tracking links in email is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html). (NEO-24232)

* To optimize security, the MD5 hashing algorithm used to generate file names has been reinforced with sha256 for public file upload. (NEO-17044)

* To reinforce security against XSS attacks, client-side scripts are disabled when executing a mirror page. (NEO-17987)

* Fixed an issue which prevented the **Privacy Request Cleanup** technical workflow from deleting reconciliation data. (NEO-25168, NEO-21004)

* Fixed an issue with the **File Transfer** activity which prevented SFTP key based authentication from working on Debian 9. (NEO-23183)

**Compatibility enhancements**

The following systems are now supported with Campaign:
* Operating systems: Debian 10
* RDBMS: Oracle 18c and Oracle 19c
* FDA: Azure Synapse Analytics

Learn more in [Campaign Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

**Improvements**

* Transactional messaging has been improved for a better user experience. You can now unpublish a transactional message template, which deletes it from the execution instances. [Learn more](../../message-center/using/publishing-message-templates.md#template-unpublication).

* New options are available to set limitations when sending emails that include images or attachments. These guardrails can avoid performance issues, which is particularly useful with transactional messaging. [Read more](../../installation/using/configuring-campaign-options.md#delivery)

* The new **Prepare the delivery parts in the database** option enables to perform delivery preparation directly within the database, which can significantly accelerate the analysis. This option is only available for specific configurations. [Learn more](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* The performance of the [CRM Connector activity](../../workflow/using/crm-connector.md) for Microsoft Dynamics has been improved. (NEO-13303, NEO-12710)

* Shared memory version has been increased.

  >[!WARNING]
  >
  >This improvement requires an additional step after performing the upgrade. Refer to the **Technical evolutions** section below.

* The cleanup workflow has been enhanced. Orphaned worktables of all deleted workflows are now also deleted automatically by the cleanup workflow. [Learn more](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificates for iOS mobile applications with the iOS HTTP2 connector are now validated before sending push notifications, thus preventing deliveries from failing because of expired certificates. 

* The management of HTTP proxy connections has been improved. [Learn more](../../installation/using/file-res-management.md).

* New option in **[!UICONTROL Javascript Code]** and **[!UICONTROL Advanced Javascript Code]** workflow activities to stop execution after a limit. Default value is 1 hour. [Learn more](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Other changes**

* Legacy SMS connectors are now deprecated. Refer to the [Deprecated features page](../../rn/using/deprecated-features.md).

* You can no longer use your own Litmus account to provision and use Inbox rendering in Adobe Campaign. [Learn more](../../delivery/using/inbox-rendering.md).

* To better distinguish views from folders, the color of view names has been changed from dark blue to dark cyan. [Read more](../../platform/using/access-management-folders.md)

* Campaign Classic can now be connected to Microsoft Dynamics CRM accounts hosted in the UK, India and Canada regions. This applies to  Office 365 and On premise (Dynamics 2015) deployment types.

* Campaign now performs a TLS verification to check that the hostname of the server matches the hostname in the provided certificate.

* The Delivery and tracking statistics table now displays one entry per delivery for the SMS channel, instead of one entry per delivery recipient.  

* Added an error message in the log file to warn users when the downloaded file is larger than the disk space.

* The following functions are now available for the Snowflake connector: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Technical evolutions**

This new build updates shared memory and requires additional steps to perform the upgrade. As a Campaign administrator, you need to remove memory segments. These steps are mandatory, as old segments will prevent nlserver/nlsrvmod from starting.

On Windows, a system restart is needed.

On Debian/CentOs, shared memory deletion is needed. Here are the steps:

Before the upgrade, you need to follow these steps:

1. Stop the apache2 (http2 on CentOS) service if it's running.
1. Stop the nlserver (nlserver6 for older builds) service if it's running.

After the upgrade:

1. Remove the shared memory using the **ipcrm** command, if the version is older than the current version.
1. Start the nlserver service if it was running.
1. Start the apache2 service if it was running.

Here are the command lines for Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

An example for Linux is available on this [page](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patches**

* Fixed a minor regression in the cleanup workflow logs.
* Fixed an issue in the workflow **Loading (SOAP)** activity when parsing WSDL files.
* Fixed an issue which caused an error when upgrading numerous workflows using a **Survey** activity to process efficiently a high number of workflows.
* Fixed an intermittent connectivity issue during the processing of inMail messages from the Enhanced MTA. (NEO-20380)
* Fixed an issue that prevented the hot click percentages from showing properly when images were displayed with a 100% width in the HTML. (NEO-23203)
* Fixed an issue that prevented the delivery’s conditional content from being fully displayed in the hot clicks report. (NEO-18729)
* Fixed an issue that skipped the target approval step when resuming a workflow to send a recurring delivery. (NEO-18166)
* Fixed an issue that prevented the **Restart message preparation** button from resuming the delivery after fixing an error in the workflow. (NEO-13488)
* Fixed an issue that could cause deliveries to fail in mid-sourcing mode during the ramp-up phase where target included recipients with Japanese email formats. (NEO-23846)
* Fixed a timezone conversion issue with the Snowflake Connector (NEO-20105)
* Fixed an issue with external accounts using FTP over SSL. (NEO-20498)
* Fixed an issue which could prevent images from being displayed in Line deliveries. (NEO-23207)
* Fixed an issue that caused an error when publishing an offer. (NEO-23312)
* Fixed an issue with push notifications which allowed test connections to work in mobile applications, even when the certificate had expired. (NEO-22991)
* Fixed an issue which could affect push notifications when sent at a high frequency. (NEO-20516)
* Fixed an issue that caused the tracking data to include duplicates even though the tracking logs did not. (NEO-20040)
* Fixed an issue that caused duplicate transactional emails to be sent after a tracking server communication failure was fixed. (NEO-23640)
* Fixed an issue that deleted the encoding parameter value when redirecting from a tracking URL (impact on Japanese characters). (NEO-25637)
* Fixed an issue that could prevent a query from working when comparing float numbers. (NEO-23243)
* Fixed an issue that could prevent the **Modified by** column content from displaying after restarting a workflow. (NEO-23035)
* Fixed an issue that caused the tracking technical workflow to fail when downloading logs from a second container. (NEO-23159)
* Fixed an issue that could cause workflows to fail when running an **Enrichment** activity. (NEO-17338)
* A check has been added to the **Doubles to keep** field in the **Deduplication** workflow activity to prevent entering null or negative values.
* Removed the **Scheduler wizard** from the recurring campaigns to avoid mentioning hours and minutes. Only dates are taken into account.
* Fixed an issue with additional storage fields when creating deliveries through the **Computed by a script** option in the **Script** workflow activity. (NEO-20609)
* Fixed an issue that prevented ghost workflows from being deleted within the database cleanup tasks.
* Fixed an issue which caused the **Billing (active profiles)** technical workflow to fail. (NEO-19777)
* Fixed a regression issue when using the ACS Connector feature which prevented the connection to a Campaign Standard instance (incorrect management of the FOH/FOH2 connection). (NEO-23433)
* Fixed an issue which prevented you from to creating a schema extension on a primary key with multiple columns with a Hadoop table. (NEO-17390)
* Fixed an issue in the **Loading (SOAP)** activity that could prevent WSDL files from being loaded from a URL. (NEO-16924)
* Fixed an issue which prevented you from performing an **Unconditional stop** through the console when multiple active workflow servers were load balanced. (NEO-19556)
* Fixed a regression causing the cleanup workflow to crash.
* Fixed an issue that could occur when publishing a template on an execution instance.
* Fixed an issue that could prevent the collectPrivacyRequests technical workflow from running. (NEO-20513, NEO-25169)
* Fixed issues that could happen when trying to connect to Audience Manager after updrading to build 9080. (NEO-20511, NEO-25167)
* Fixed issues that could occur when exporting reports in PDF or XLS format. (NEO-20982, NEO-23493, NEO-23348)
* Fixed an issue that could display a delivery twice in the delivery list after it was sent.
* Fixed an issue with delivery preparation that could occur when the routing configuration was set to send the delivery via mid-sourcing.
* Fixed an issue that could display an error message when clicking a web application link within a Line message.
* Fixed an issue that deleted the **Incremental query** activity history after running the cleanup workflow.
* Fixed an issue when creating a mid-sourcing external account where the NmsMidSourcing_LastBroadLog_&lt;InternalName&gt; option was missing.
* Fixed a regression issue on database connection causing the web server to constantly restart due to a database encoding problem. This could lead to overconsumption. (NEO-23264)
