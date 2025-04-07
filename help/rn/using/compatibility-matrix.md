---
product: campaign
title: Compatibility matrix for Campaign Classic
description: Campaign Classic Compatibility matrix
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
---
# Compatibility matrix {#compatibility-matrix}

In its [latest build](../../rn/using/latest-release.md), Adobe Campaign Classic v7 is compatible with all the systems and tools listed in this page. As specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign will no longer be compatible with those versions, and they will be removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in this compatibility matrix to avoid any issues. To learn more about deprecated items, visit [this page](../../rn/using/deprecated-features.md).

Unless mentioned otherwise, all minor releases are supported.

>[!CAUTION]
>
>This matrix is regularly updated with new supported systems and tools being added, and deprecated being removed.

## Operating Systems {#OperatingSystems}

As an on-premise / hybrid customer, you must install Adobe Campaign in one of the operating systems listed below. Learn more about Campaign Classic v7 installation steps in [this page](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Operating system</strong></td>
<td><strong>Operating system version</strong></td>
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td>
<p>Debian</p>
</td>
<td>
<p>11</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Red Hat Enterprise Linux (RHEL)</p>
</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Windows Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>    

>[!IMPORTANT]
>
>With RHEL, you must be willing to disable [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.

## Web Servers {#WebServers}

As an on-premise / hybrid customer, depending on your operating system, you must integrate Campaign into one of the web servers listed below. Learn more about Web servers configuration steps in [this page](../../installation/using/integration-into-a-web-server-for-windows.md) (for Windows) and [this page](../../installation/using/integration-into-a-web-server-for-linux.md) (for Linux) .

<table>
<tbody>
<td><strong>Web Server</strong></td>
<td><strong>Web Server version</strong></td>
<tr>
<td>
<p>Microsoft IIS</p>
</td>
<td>
<p>10.0</p>
</td>
</tr>
<tr>
<td>
<p>Apache</p>
</td>
<td>
<p>2.4</p>
</td>
</tr>
</tbody>
</table>

## Tools {#Tools}

As an on-premise / hybrid customer, you must install and configure the tools listed below. [Learn more](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Tool</strong></td>
<td><strong>Version</strong></td>
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Learn more in <a href="../../installation/using/application-server.md#jdk" target="_blank">this page</a>.</p>
</td>
<td>
<p>17</p>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>required starting v7.4.1</p>
<p>required starting v7.4.1</p>
<p>until v7.4.1</p>
<p>until v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (and previous versions if embedded in your system)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Relation Database Management Systems (RDBMS) {#RDBMSservers}

As an on-premise / hybrid customer, you must install and configure one of the databases listed below. [Learn more](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Database system</strong></td>
<td><strong>Database version</strong></td>
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td>
<p>Oracle</p>
</td>
<td>
<p>23c</p>
<p>21c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>PostgreSQL</p>
</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Microsoft SQL Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* The RDBMS driver must match with the RDBMS server version.
>
>* Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux. [Learn more](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* You can also use Amazon RDS for PostgreSQL with the versions specified above.
>
>* PostgreSQL is the RDBMS for Hosted/Managed Cloud Services environments.


## CRM connectors {#CRMconnectors}

Customer Relationship Management (CRM) systems compatible with Adobe Campaign are listed below. [Learn more](../../platform/using/crm-connectors.md) about Campaign CRM connectors.

<table>
<tbody>
<tr>
<td>
<p>Salesforce connector API</p>
</td>
<td>
<p>API version 49</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Dynamics connector</p>
</td>
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
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p>&nbsp;</p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td>&nbsp;</td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td>&nbsp;</td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td>&nbsp;</td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

In addition, **Hybrid** and **On-premise** environments can also connect Campaign with the following external database systems. These systems are **not compatible** with Campaign **Managed Services** (hosted) environments.

<table>
<tbody>
<td><strong>Database system</strong></td>
<td><strong>Database version</strong></td>
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td>&nbsp;</td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>21c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
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
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (starting Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 and SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (last version)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Client Console {#ClientOS}

The following operating systems and browser are **required** to use [Campaign Client Console](../../installation/using/installing-the-client-console.md). 

### Operating systems

<table>
<tbody>
<td><strong>System</strong></td>
<td><strong>OS version</strong></td>
<td><strong>Minimum Campaign version</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 runtime {#webview}

Microsoft Edge WebView2 runtime latest version is mandatory for Campaign client console. 

Download Microsoft Edge WebView2 from [Microsoft Developer site](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobile SDK {#MobileSDK}

You can use Campaign to [send push notifications](../../delivery/using/about-mobile-app-channel.md), via the Adobe Experience Platform Mobile SDK by configuring the Adobe Campaign extension in the Data Collection UI. 

The Campaign SDK is [deprecated](deprecated-features.md) starting Campaign v7.4. To ensure a smooth transition for existing implementation to the AEP Mobile SDK, you can still use it on the operating systems listed below<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->. 


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>with mobile SDK build 1.1.1.</p>
<p>Android 13 and 14 are supported starting Campaign v7.4.</p>
<p>Android 12 is supported starting Campaign v7.3.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>with mobile SDK build 1.0.26.</p>
<p>Apple iOS 15 is supported starting Campaign v7.3. </p>
<p>Apple iOS 16 and 17 are supported starting Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Browsers {#Browsers}

The following browsers, in their latest version, are compatible with Campaign for [Web Access](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Campaign Classic Release notes](../../rn/using/latest-release.md)
>* [Campaign General Architecture](../../installation/using/general-architecture.md)
>* [Hardware sizing recommendations](../../technotes/using/hardware-sizing.md)
>* [Deprecated features and systems](../../rn/using/deprecated-features.md)
>* [Build upgrade procedure](../../production/using/build-upgrade.md)
