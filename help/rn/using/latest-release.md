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
   <td> <p>When designing a message in Campaign, you can now insert emoticons in the message body quickly, using a dedicated button. They can also be added in the email subject line. You can customize the list of available emoticons in the interface.</p>
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
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse-configure-access-to-azure-synapse">detailed documentation</a>.</p>
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

Improved security on tracking links in email is enabled by default for all customers. An additional, enhanced security feature is available which can be enabled by reaching out to Customer Care. More details on the feature and steps for non-hosted customers to enable it can be found in the [Security and Privacy checklist](https://helpx.adobe.com/campaign/kb/acc-security.html). (NEO-24232)

**Compatibility enhancements**

The following systems are now supported with Campaign:
* Operating systems: Debian 10
* RDBMS: Oracle 18c and Oracle 19c
* FDA: Azure Synapse Analytics

Learn more in [Campaign Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

**Improvements**

* Transactional messaging has been improved for a better user experience. It is now possible to unpublish a transactional message template, which deletes it from the execution instances. [Learn more](../../message-center/using/template-unpublication.md).

* New options are available to set limitations when sending emails that include images or attachments. These guardrails can avoid performance issues, which is particularly useful with transactional messaging. [Read more](../../installation/using/configuring-campaign-options.md#delivery)

* The new **Prepare the delivery parts in the database** option enables to perform delivery preparation directly within the database, which can significantly accelerate the analysis. This option is only available for specific configurations. [Learn more](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Performances of the [CRM Connector activity](../../workflow/using/crm-connector.md) for Microsoft Dynamics have been improved. (NEO-13303)

* Shared memory version has been increased.

  >[!WARNING]
  >
  >This improvement requires an additional step after performing the upgrade. Refer to the **Technical evolutions** section below.

* The cleanup workflow has been enhanced. Orphaned worktables of all deleted workflows are now also deleted automatically by the cleanup workflow.

**Technical evolutions**

This new build updates shared memory and requires an additional step after performing the upgrade.
As a Campaign administrator, you need to remove memory segments. This steps is mandatory, as old segments will prevent nlserver/nlsrvmod from starting.

On Windows, a system restart is needed.

On Debian/CentOs, shared memory deletion is needed. Here are the steps:

Before the upgrade, you need to follow these steps:

1. Stop the apache2 (http2 on CentOS) service if it's running.
1. Stop the nlserver (nlserver6 for build before NEO-18009) service if it's running.

After the upgrade:

1. Remove the shared memory using the **ipcrm** command, if the version is below the current version.
1. Start the nlserver service if it was running.
1. Start the apache2 service if it was running.

Here are the command lines for Debian for above:

/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

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

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start

An example for Linux is available on this [page](../../configuration/using/additional-parameters.md#redirection-server-configuration).


**Other changes**

Legacy SMS connectors are now deprecated. Refer to the [Deprecated features page](../../rn/using/deprecated-features.md).

You can no longer use your own Litmus account to provision and use Inbox rendering in Adobe Campaign. [Learn more](../../delivery/using/inbox-rendering.md).



