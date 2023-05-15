---
product: campaign
title: Compatibility matrix
description: Compatibility matrix
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: rns
content-type: reference
topic-tags: latest-release-notes
---

# Compatibility matrix{#compatibility-matrix}



This document lists all systems and components supported for the latest build of **Adobe Campaign Classic (v6.11 and v7)**. Products and versions that are not part of this list are not compatible with Adobe Campaign.

## Important notes{#important-notes}

This matrix is regularly updated with new supported items being added and deprecated items being removed.

Unless mentioned otherwise, all minor releases are supported.

Adobe Campaign Classic is compatible with all the systems and tools listed in this page. As specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign will no longer be compatible with those versions, and they will be removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.

To learn more about deprecated items, visit [this page](../../rn/using/deprecated-features.md).

## Operating Systems{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8 (64 bits)</p>
<p>9 (64 bits)</p>
<p>10 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2012 R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>    

## Web Servers{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>8.0 on Windows Server 2012 - Windows 8</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>10.0 on Windows Server 2016</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Tools{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (and previous versions if embedded in your system)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## RDBMS drivers{#RDBMSdrivers}

The following RDBMS drivers are supported:

* Oracle SQL&#42;Net 11

* Oracle SQL&#42;Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (ODBC Driver)


>[!NOTE]
>
>RDBMS driver must match with RDBMS server version.

## RDBMS servers{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>Note: you can also use Amazon RDS for PostgreSQL with the versions specified above.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 - SP1 and SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Warning: Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL is the default database server for Hosted environments.

## CRM connectors{#CRMconnectors}

<table>
<tbody>
<tr>
<td>Salesforce connector API</td>
<td>
<p>API version 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API version 15</p>
<p>API version 21</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>Web Services v1.0 API</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - On-premise: 2007, 2015, 2016</p>
<p>Soap API - Online: 2015, 2016</p>
<p>Web API - On-premise and Online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p>&nbsp;</p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1 and SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SP12 or above</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td>&nbsp;</td>
</tr>
</tbody>
</table>

## Client Console operating systems{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (recommended for Japanese instances)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>with mobile SDK build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>with mobile SDK build 1.0.26, compatible with 32 and 64-bit versions.</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers}

Version 11 of Internet Explorer is supported.

For the following browsers, the latest version is supported:

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Experience Cloud integrations{#ExperienceCloudintegrations}

For integrations with Adobe solutions, refer to this [section](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## More like this{#Morelikethis}

* [Campaign Classic Release notes](https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/latest-release.html)
* [Installation Guide](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Deprecated features and systems](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)
* [Build upgrade procedure](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html)
* [Campaign Classic Compatibility matrix for 19.0 release](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html)
* [Campaign Classic Compatibility matrix for 19.1 release](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-1.html)

