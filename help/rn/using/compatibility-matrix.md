---
title: Compatibility matrix
description: Compatibility matrix
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

# Compatibility matrix{#compatibility-matrix}

This document lists all systems and components supported for the latest build of **Adobe Campaign Classic (v6.11 and v7)**. Products and versions that are not part of this list are not compatible with Adobe Campaign.

>[!WARNING]
>
>This matrix is regularly updated with new supported items being added and deprecated items being removed.
>
>Unless mentioned otherwise, all minor releases are supported.
>
>Adobe Campaign Classic is compatible with all the systems and tools listed in this page. As specific versions of these 3rd party systems and tools reach end-of-life (EOL) with their respective creators, Adobe Campaign will no longer be compatible with those versions, and they will be removed from our compatibility matrix in the subsequent product release. Please ensure you are on supported versions of any systems listed in the compatibility matrix to avoid any issues.
>
>To learn more about deprecated items, visit [this page](../../rn/using/deprecated-features.md).

## Operating Systems{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<ul>
<li>7.x (64 bits)</li>
</ul>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<ul>
<li>8 (64 bits)</li>
<li>9 (64 bits)</li>
<li>10 (64 bits)</li>
</ul>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<ul>
<li>7.x (64 bits)</li>
</ul>
<p><strong>Important:</strong> If you are using RHEL, you must be willing to disable SELinux or to have your architects write custom SELinux rules to check that an enabled SELinux is not causing issues with Campaign operations.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<ul>
<li>2012</li>
<li>2012 R2</li>
<li>2016</li>
</ul>
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
<ul>
<li>8.0 on Windows Server 2012 - Windows 8</li>
<li>8.5 on Windows Server 2012 R2</li>
<li>10.0 on Windows Server 2016</li>
</ul>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<ul>
<li>2.4 for RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</li>
</ul>
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
<ul>
<li>8</li>
<li>9</li>
</ul>
<p>The application has been approved for the Java Development Kit (JDK) developed by Oracle as well as for OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<ul>
<li>6 (and previous versions if embedded in your system)</li>
</ul>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<ul>
<li>3.4.x</li>
</ul>
</td>
</tr>
</tbody>
</table>

## RDBMS drivers{#RDBMSdrivers}







    <a name="main-pars_table_752777258"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Oracle SQL*Net 11</td>
</tr><tr><td>Oracle SQL*Net 12</td>
</tr><tr><td>PostgreSQL (libpq)</td>
</tr><tr><td>SQLServer</td>
</tr><tr><td>DB2 (ODBC Driver)</td>
</tr></tbody></table>
</div></div>
<div class="note parbase section">



    
        
            
                <div class="help-note">
                    <p>
                        <span class="help-note-title">Note:</span>
                        <p>RDBMS driver must match with RDBMS server version.</p>

                    </p>
                </div>
                
            



        
    
    



</div>
<div class="header parbase section">



    <a name="main-pars_header_183453300"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="RDBMSservers">
                    RDBMS servers
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_1458404284"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Oracle</td>
<td><ul>
<li>11g R2<br>
</li>
<li>12c</li>
<li>18c</li>
<li>19c</li>
</ul>
</td>
</tr><tr><td>PostgreSQL</td>
<td><ul>
<li>9.4.x<br>
</li>
<li>9.5.x</li>
<li>9.6.x</li>
<li>10.x</li>
<li>11.x</li>
</ul>
<p>Note: you can also use&nbsp;Amazon RDS for PostgreSQL with the versions specified above</p>
</td>
</tr><tr><td>SQL Server</td>
<td><ul>
<li>2012 - SP1 and SP2<br>
</li>
<li>2014</li>
<li>2016</li>
<li>2017</li>
</ul>
<p>Warning:&nbsp;Microsoft SQL Server is not supported as the primary database when the Campaign server is running on Linux. Refer to the <a href="https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html#Microsoft_SQL_Server">Installation guide</a>.<br>
</p>
</td>
</tr></tbody></table>
</div></div>
<div class="note parbase section">



    
        
            
                <div class="help-note">
                    <p>
                        <span class="help-note-title">Note:</span>
                        <p>PostgreSQL is the default database server for Hosted environments.</p>

                    </p>
                </div>
                
            



        
    
    



</div>
<div class="header parbase section">



    <a name="main-pars_header_528988623"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="CRMconnectors">
                    CRM connectors
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_2126291922"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Salesforce connector API&nbsp;<br />
</td>
<td><ul>
<li>API version 37</li>
</ul>
</td>
</tr><tr><td>SFDC API</td>
<td><ul>
<li>API version 15</li>
<li>API version 21</li>
</ul>
</td>
</tr><tr><td>Oracle On Demand API</td>
<td><ul>
<li>Web Services v1.0 API</li>
</ul>
</td>
</tr><tr><td>MS Dynamics</td>
<td><ul>
<li>Soap API - On-premise: 2007, 2015, 2016</li>
<li>Soap API - Online: 2015, 2016</li>
<li>Web API - On-premise and Online: 365, 2016, 2016 Update 1</li>
</ul>
</td>
</tr></tbody></table>
</div></div>
<div class="header parbase section">



    <a name="main-pars_header_1260543892"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="FederatedDataAccessFDA">
                    Federated Data Access (FDA)
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_430745646"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Microsoft Azure Synapse Analytics</td>
<td>&nbsp;</td>
</tr><tr><td>Amazon Redshift<br>
</td>
<td><p>&nbsp;</p>
</td>
</tr><tr><td>Oracle</td>
<td><ul>
<li>11g</li>
<li>12c<br>
</li>
<li>18c</li>
</ul>
</td>
</tr><tr><td>PostgreSQL</td>
<td><ul>
<li>9.4.x<br>
</li>
<li>9.5.x</li>
<li>9.6.x</li>
<li>10.x</li>
<li>11.x</li>
</ul>
</td>
</tr><tr><td>SQL Server<br>
</td>
<td><ul>
<li>2012 SP1 and SP2</li>
<li>2014</li>
<li>2016</li>
<li>2017</li>
</ul>
</td>
</tr><tr><td>MySQL</td>
<td><ul>
<li>5.7<br>
</li>
</ul>
</td>
</tr><tr><td>Teradata</td>
<td><ul>
<li>15.0<br>
</li>
<li>15.10</li>
<li>16</li>
<li>16.20</li>
</ul>
</td>
</tr><tr><td>Netezza</td>
<td><ul>
<li>7.2</li>
</ul>
</td>
</tr><tr><td>Sybase</td>
<td><ul>
<li>IQ 16</li>
<li>ASE 15.7</li>
</ul>
</td>
</tr><tr><td>SAP HANA</td>
<td><ul>
<li>version 1 SP12 or above</li>
</ul>
</td>
</tr><tr><td>Hadoop via HiveSQL</td>
<td><ul>
<li>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</li>
<li>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</li>
<li>Cloudera CDH6.x</li>
</ul>
</td>
</tr><tr><td>Snowflake</td>
<td>&nbsp;</td>
</tr></tbody></table>
</div></div>
<div class="header parbase section">



    <a name="main-pars_header_349986245"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="ClientConsoleoperatingsystems">
                    Client Console operating systems
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_990452260"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Windows Server<br>
</td>
<td><ul>
<li>2012</li>
<li>2016</li>
</ul>
</td>
</tr><tr><td>Windows</td>
<td><ul>
<li>8</li>
<li>10 (recommended for Japanese instances)</li>
</ul>
</td>
</tr></tbody></table>
</div></div>
<div class="header parbase section">



    <a name="main-pars_header_1143336137"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="MobileSDK">
                    Mobile SDK
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_862052127"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Android</td>
<td valign="top"><ul>
<li>7.x</li>
<li>8.x&nbsp;</li>
<li>9.0&nbsp;</li>
</ul>
<p>with mobile SDK build 1.0.27.</p>
</td>
</tr><tr><td>iOS</td>
<td valign="top"><ul>
<li>iOS 9</li>
<li>iOS 10</li>
<li>iOS 11</li>
<li>iOS 12</li>
<li>iOS 13</li>
</ul>
<p>with&nbsp;mobile SDK build 1.0.26,&nbsp;compatible with 32 and 64-bit versions.</p>
</td>
</tr></tbody></table>
</div></div>
<div class="header parbase section">



    <a name="main-pars_header_2054797177"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="Browsers">
                    Browsers
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="table parbase section">





    <a name="main-pars_table_583837044"></a>
    <div class="noHeader"><table width="100%" cellspacing="0" cellpadding="1" border="1">
<tbody><tr><td>Internet Explorer<br />
</td>
<td><ul>
<li>11</li>
</ul>
</td>
</tr><tr><td>Microsoft Edge</td>
<td><ul>
<li>Latest version</li>
</ul>
</td>
</tr><tr><td>Firefox</td>
<td><ul>
<li>Latest version&nbsp;</li>
</ul>
</td>
</tr><tr><td>Chrome</td>
<td><ul>
<li>Latest version&nbsp;</li>
</ul>
</td>
</tr><tr><td>Safari</td>
<td><ul>
<li>Latest version</li>
</ul>
</td>
</tr></tbody></table>
</div></div>
<div class="header parbase section">



    <a name="main-pars_header_578261395"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="ExperienceCloudintegrations">
                    Experience Cloud integrations
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="text parbase section">

    <a name="main-pars_text_1362496704"></a>
    
        
            <div class="text"><p>For integrations with Adobe solutions, <a disablelinktracking="false" href="https://docs.adobe.com/content/help/en/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations">refer to this section</a>.</p>
</div>
        
    
    

</div>
<div class="header parbase section">



    <a name="main-pars_header_783347623"></a>
    
        

        

        
            
            
            
            
            
            
            <div class="header  header-top">
                <h2 id="Morelikethis">
                    More like this
                </h2>
                
                
                    
                
            </div>
            <!-- for Cascading Toc -->
            
                
            
        
    

</div>
<div class="text parbase section">

    <a name="main-pars_text_1467587621"></a>
    
        
            <div class="text"><ul>
<li><a href="https://docs.adobe.com/content/help/en/campaign-classic/using/release-notes/latest-release.html">Campaign Classic Release notes</a>&nbsp;</li>
<li><a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html">Installation Guide</a>&nbsp;</li>
<li><a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Deprecated features and systems</a>&nbsp;</li>
<li><a href="https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html">Build upgrade procedure</a></li>
<li><a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html">Campaign Classic Compatibility matrix for 19.0 release</a></li>
<li><a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-1.html">Campaign Classic Compatibility matrix for 19.1 release</a></li>
</ul>
</div>
        
