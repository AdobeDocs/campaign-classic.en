---
product: campaign
title: Compatibility matrix for Campaign Classic
description: Campaign Classic Compatibility matrix
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
---
# Compatibility matrix{#compatibility-matrix}



This document lists all systems and components supported for [the latest build](../../rn/using/latest-release.md) of **Adobe Campaign Classic v7**. Products and versions that are not part of this list are not compatible with Adobe Campaign.

If you are a [!DNL Gold Standard] user, refer to the [[!DNL Gold Standard] Compatibility matrix](../../rn/using/gold-standard.md#compatibility-matrix-gs).

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
<p>7.x</p>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (starting Campaign v7.3)</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (starting Campaign v7.2)</p>
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
<p>10.0 on Windows Server 2016 and 2019</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7, Debian 8/9, Windows</p>
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
<p>Campaign supports the Java Development Kit (JDK) developed by Oracle, and OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (and previous versions if embedded in your system)</p>
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

## Relation Database Management Systems (RDBMS){#RDBMSservers}

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
<p>14.x (starting Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>Note:</strong> you can also use Amazon RDS for PostgreSQL with the versions specified above.</p>
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
<p><strong>Important:</strong> Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux. <a href=https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux-/prerequisites-of-campaign-installation-in-linux.html#database-access-layers>Learn more</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS driver must match with RDBMS server version.
>
>* PostgreSQL is the RDBMS for Hosted environments.

## CRM connectors{#CRMconnectors}

Customer Relationship Management (CRM) systems compatible with Adobe Campaign are listed below. [Learn more](../../platform/using/crm-connectors.md) about Campaign CRM connectors.

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
<p>Web API</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

External databases compatible with Adobe Campaign [Federated Data Access module](../../installation/using/about-fda.md) are listed below. Compatibility depends on your [hosting model](../../installation/using/hosting-models.md).

**Managed Services** (hosted), **Hybrid** and **On-premise** environments can connect Campaign with the following external database systems:

<table>
<tbody>
<td><strong>Database system</strong></td>
<td><strong>Database version</strong></td>
<td><strong>Campaign version</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p>&nbsp;</p>
<td>v7.0 19.1.4 minimum</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td>&nbsp;</td>
<td>7.2 minimum</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4 minimum</td>
</tr>
<tr>
<td>Snowflake</td>
<td>&nbsp;</td>
<td>7.2 minimum</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td>&nbsp;</td>
<td>v7.0 19.1.4 minimum</td>
</tr>
</tbody>
</table>

In addition, **Hybrid** and **On-premise** environments can also connect Campaign with the following external database systems. These systems are **not compatible** with Campaign **Managed Services** (hosted) environments.

<table>
<tbody>
<td><strong>Database system</strong></td>
<td><strong>Database version</strong></td>
<td><strong>Campaign version</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td>&nbsp;</td>
<td>v7.0 19.1.4 minimum</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3 minimum</p>
<p>v7.0 minimum</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>v7.0 minimum</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.0 minimum</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SPS 12</p>
</td>
<td>v7.0 minimum</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 and SP2</p>
</td>
<td>v7.0 minimum</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>v7.0 minimum</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (last version)</p>
</td>
<td>v7.0 minimum</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>v7.0 minimum</td>
</tr>
</tbody>
</table>



## Client Console {#ClientConsoleoperatingsystems}

The following operating systems and browser are **required** to use [Campaign Client Console](../../installation/using/installing-the-client-console.md). 

### Operating systems

<table>
<tbody>
<td><strong>System</strong></td>
<td><strong>OS version</strong></td>
<td><strong>Campaign version</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3 minimum</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.2.1 minimum</p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 runtime

Microsoft Edge WebView2 runtime latest version is mandatory for Campaign client console. 

Download Microsoft Edge WebView2 from [Microsoft Developer site](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobile SDK{#MobileSDK}

You can use Campaign to [send push notifications](../../delivery/using/about-mobile-app-channel.md) on the operating systems listed below, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). 

You can also use the Adobe Experience Platform Mobile SDK by configuring the Adobe Campaign extension in the Data Collection UI. 

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (starting Campaign v7.3), 9.0, 8.x, 7.x</p>
<p>with mobile SDK build 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>with mobile SDK build 1.0.26, compatible with 32 and 64-bit versions. iOS 15 is supported starting Campaign v7.3</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers}

The following browsers, in their latest version, are compatible with Campaign for [Web Access](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## More like this{#Morelikethis}

* [Campaign Classic Release notes](../../rn/using/latest-release.md)
* [Campaign General Architecture](../../installation/using/general-architecture.md)
* [Hardware sizing recommendations](../../technotes/using/hardware-sizing.md)
* [Deprecated features and systems](../../rn/using/deprecated-features.md)
* [Build upgrade procedure](../../production/using/build-upgrade.md)
