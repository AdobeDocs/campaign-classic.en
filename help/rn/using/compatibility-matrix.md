---
solution: Campaign Classic
product: campaign
title: Compatibility matrix for Campaign Classic
description: Campaign Classic Compatibility matrix
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
---
# Compatibility matrix{#compatibility-matrix}

This document lists all systems and components supported for [the latest build](../../rn/using/latest-release.md) of **Adobe Campaign Classic**. Products and versions that are not part of this list are not compatible with Adobe Campaign.

If you are a [!DNL Gold Standard] user, refer to the [[!DNL Gold Standard] Compatibility matrix](../../rn/using/compatibility-matrix-gs.md).

## Important notes{#important-notes}

Unless mentioned otherwise, all minor releases are supported.

In its [latest build](../../rn/using/latest-release.md), Adobe Campaign Classic is compatible with all the systems and tools listed in this page. As specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign will no longer be compatible with those versions, and they will be removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.

To learn more about deprecated items, visit [this page](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>This matrix is regularly updated with new supported items being added and deprecated items being removed.

## Operating Systems{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10 (64 bits)</p>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
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
<p>10.0 on Windows Server 2016</p>
<p>8.5 on Windows Server 2012 R2</p>
<p>8.0 on Windows Server 2012 - Windows 8</p>
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
<p>11</p>
<p>9</p>
<p>8</p>
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

## RDBMS servers{#RDBMSservers}

>[!NOTE]
>
>RDBMS driver must match with RDBMS server version.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Note: you can also use Amazon RDS for PostgreSQL with the versions specified above.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 and SP2</p>
<p>Warning: Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Learn more</a>.</p>
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
<p>API version 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics connector</td>
<td>
<p>Web API: Dynamics 365 On-premise and Online</p>
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
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 and SP2</p>
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
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
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
<p>version 1 SPS 12</p>
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
<p>2016</p>
<p>2012</p>
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
<p>7.x, 8.x, 9.0</p>
<p>with mobile SDK build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>with mobile SDK build 1.0.26, compatible with 32 and 64-bit versions.</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers}

For the following browsers, the latest version is supported: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 is supported.

## More like this{#Morelikethis}

* [Campaign Classic Release notes](../../rn/using/latest-release.md)
* [Installation Guide](../../installation/using/general-architecture.md)
* [Deprecated features and systems](../../rn/using/deprecated-features.md)
* [Build upgrade procedure](../../production/using/build-upgrade.md)
