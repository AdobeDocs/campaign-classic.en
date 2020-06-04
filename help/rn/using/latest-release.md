---
title: Latest Release
description: Latest Release
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
---

# Latest Release{#latest-release}

[Build upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) &#124; [Control Panel releases](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) &#124; [Documentation updates](../../rn/using/documentation-updates.md) &#124; [Previous releases](../../rn/using/release--19-2.md) &#124; [Deprecated features](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>General Availability</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>No longer available</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Deprecated</strong></td> 
  </tr> 
   <tr> 
   <td>Latest stable build available. Build validated in production.<br>&nbsp;</td>
   <td>Build validated by Adobe. Waiting for production proofing.<br>&nbsp;</td>
   <td>Newer build available with bug fixes. Update is required.<br>&nbsp;</td>
   <td>Contains known regressions. Update is mandatory.<br>&nbsp;</td>
  </tr> 
 </tbody> 
</table>

The **last stable build** is 9032 (3a9dc9c). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Release 20.2.1 - Build XXXX {#release-20-2-1-build-XXXX}

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
    <p>For more information about adding emoticons, refer to the <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons-in-an-email">detailed documentation</a>. Learn how to customize the emoticon list <a href="../../delivery/using/customizing-emoticon-list.md">in this section</a>.</p>
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
    <p>Azure Synapse is only available for Hybrid and On-premise environments. For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse-configure-access-to-azure-synapse">detailed documentation</a>.</p>
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
   <p>Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil.</p>
   <p>These regulations apply to Adobe Campaign customers who hold data for Data Subjects residing in these countries. In addition to the privacy capabilities already available in Campaign (including consent management, data retention settings, and user roles), we are taking this opportunity to include additional capabilities, to help facilitate your readiness for PDPA and LGPD:</p>
   <ul> 
     <li><p>Right to Access and Right to Delete: we are leveraging the capabilities that were added for GDPR and CCPA. <a href= https://helpx.adobe.com/campaign/kb/acc-privacy.html>Read more</a></p></li> 
     <li> <p>When creating a Privacy request using Campaign interface or API, you now select the regulation type field: PDPA, LGPD, GDPR, CCPA. <a href=https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests>Read more</a>.</p></li>
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

* Transactional messaging has been improved for a better user experience. You can now unpublish a transactional message template, which deletes it from the execution instances. [Learn more](../../message-center/using/template-unpublication.md).

* New options are available to set limitations when sending emails that include images or attachments. These guardrails can avoid performance issues, which is particularly useful with transactional messaging. [Read more](../../installation/using/configuring-campaign-options.md#delivery)

* The new **Prepare the delivery parts in the database** option enables to perform delivery preparation directly within the database, which can significantly accelerate the analysis. This option is only available for specific configurations. [Learn more](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* The performance of the [CRM Connector activity](../../workflow/using/crm-connector.md) for Microsoft Dynamics has been improved. (NEO-13303, NEO-12710)

* Shared memory version has been increased.

  >[!WARNING]
  >
  >This improvement requires an additional step after performing the upgrade. Refer to the **Technical evolutions** section below.

* The cleanup workflow has been enhanced. Orphaned worktables of all deleted workflows are now also deleted automatically by the cleanup workflow. [Learn more](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificates for iOS mobile applications with the iOS HTTP2 connector are now validated before sending push notifications, thus preventing deliveries from failing because of expired certificates. 

* The management of HTTP proxy connections has been improved. [Learn more](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Other changes**

* Legacy SMS connectors are now deprecated. Refer to the [Deprecated features page](../../rn/using/deprecated-features.md).

* You can no longer use your own Litmus account to provision and use Inbox rendering in Adobe Campaign. [Learn more](../../delivery/using/inbox-rendering.md).

* To better distinguish views from folders, the color of view names has been changed from dark blue to dark cyan. [Read more](../../platform/using/access-management.md#about-views)

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
```

```
for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done
```

```
for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done
```

```
for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done
```

```
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
* Fixed an issue that deleted the encoding parameter value when redirecting from a tracking URL. (NEO-25637)
* Fixed an issue that could prevent a query from working when comparing float numbers. (NEO-23243)
* Fixed an issue that could prevent the **Modified by** column content from displaying after restarting a workflow. (NEO-23035)
* Fixed an issue that caused the tracking technical workflow to fail when downloading logs from a second container. (NEO-23159)
* Fixed an issue that could cause workflows to fail when running an **Enrichment** activity. (NEO-17338)
* A check has been added to the **Doubles to keep** field in the **Deduplication** workflow activity to prevent entering null or negative values.
* Removed the **Scheduler wizard** from the recurring campaigns to avoid mentioning hours and minutes. Only dates are taken into account.
* Fixed an issue with additional storage fields when creating deliveries through the **Computed by a script** option in the **Script** workflow activity. (NEO-20609)
* Fixed an issue that prevented ghost workflows from being deleted within the database cleanup tasks.
* Fixed an issue which caused the **Billing (active profiles)** technical workflow to fail. (NEO-19777)
* Fixed an issue when testing the connection of the acsDefaultAccount external account. (NEO-23433)
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
* Fixed an issue that could prevent Microsoft Dynamics CRM from retrieving all entities. (NEO-24528)
* Fixed an issue that deleted the **Incremental query** activity history after running the cleanup workflow.
