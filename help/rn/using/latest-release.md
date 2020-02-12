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

[Build upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) &#124; [Control Panel releases](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) &#124; [Documentation updates](../../rn/using/documentation-updates.md) &#124; [Previous releases](../../rn/using/release--19-2.md) &#124; [Deprecated features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>General Availability</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>No longer available</strong></td> 
   <td><img src="assets/red3.png"/><strong>Deprecated</strong></td> 
  </tr> 
   <tr> 
   <td>Latest stable build available. Build validated in production.<br>&nbsp;</td>
   <td>Build validated by Adobe. Waiting for production proofing.<br>&nbsp;</td>
   <td>Newer build available with bug fixes. Update is required.<br>&nbsp;</td>
   <td>Contains known regressions. Update is mandatory.<br>&nbsp;</td>
  </tr> 
 </tbody> 
</table>

Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032) to view the **last stable build** (GA).

## ![](assets/blue2.png) Release 20.1 - Build XXXX {#release-20-1-build-XXXX} 

_February 17, 2020_

**What's new?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake is a fully managed cloud data warehouse built to scale on both storage and compute level. With this new connector, Adobe Campaign can now leverage the power of Snowflake to perform Big Data Segmentation. This connector is available to all customers, including hosted by Adobe.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">detailed documentation</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA Connector Enhancements</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>The Hadoop FDA Connector has been improved to support Hadoop 3.0 as well as Cloudera.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">XXXX</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Security enhancements**

* Improved security in report configuration to protect from clickjacking. This applies to new reports. For old reports, you need to republish them to apply changes. (NEO-13282)

* Improved the key encryption in the cryptString to fix a potential heap buffer read overflow. (NEO-20071)

* Improved monitor JSP to fix an internal IP disclosure. (NEO-16821)

* Fixed an issue which could display stack traces in error messages. (NEO-12388)

* Improved the management of cached data from previous sessions. (NEO-17039)



**Improvements**

* iOS 13 is now supported with the HTTP2 connector.

* Improved quarantine management and cleanup of the tables used by the push notification feature (nms:address and nms:appSubscriptionRcp). For iOS (HTTP2 connector only), disabled tokens are now handled in the same way as for Android. The disable flag is now set in the NmsAppSubscriptionRcp table.

* A new option has been added in the **JavaScript code** and **Advanced JavaScript code** workflow activities to define a time-out period. This prevents the javascript execution phase from running for too long. If the time-out period elapses, the workflow is stopped. The default time-out is 1 hour.

* The delivery analysis is now stopped when no matching affinity is found on the mid-sourcing server, with the corresponding error message being displayed.

* Database failover for Postgres is now supported: when the database server crashes and restarts, Campaign now reconnects to it automatically.

**Other changes**

* The most consuming custom tables have been moved from the **xtkNewId** sequence to dedicated sequences. [Read more](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) 

* Improved query performance which could be affected by unnecessary database connections.

* The **Start Pending** view has been added to the Administration > Audit > Workflows Status node. This allows you to monitor all workflows on your instance that are waiting to be started by the **operationMgt** process. This view comes with the Marketing campaigns package. [Read more](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

* The email address validation rules in relation to soft bounces have been enhanced. [Read more](help/delivery/using/understanding-delivery-failures.md)

**Patches**

* Fixed an account key encryption issue when using the Hadoop connector. 
