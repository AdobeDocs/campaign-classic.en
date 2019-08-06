---
title: Connection thresholds
seo-title: Connection thresholds
description: Connection thresholds
seo-description: 
page-status-flag: never-activated
uuid: 35fc05c7-2056-4712-bd52-f6501daa4f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 67b715d6-27d6-4b7b-bba6-ad6b9db83061
index: y
internal: n
snippet: y
---

# Connection thresholds{#connection-thresholds}

For heavily loaded servers, the connection threshold might be exceeded. In any event, it is useful to find out why.

There are three different thresholds:

1. The Web connection threshold, configured in your web server. To modify it, contact your system administrator.
1. The database connection threshold. To modify it, contact your database administrator.
1. The Adobe Campaign connection threshold, available in two places:

    * Tomcat side: all queries actually arriving on the Adobe Campaign Tomcat client.

      This threshold is configured in the **nl6/tomcat-7/conf/server.xml** file. The **maxThreads** attribute lets you increase the threshold of the number of queries processed at a time. It can be changed to 250, for instance.

      ```    
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

    * Database: set of all connections open at the same time on the database by a process.

      This threshold is configured in the file **nl6/conf/serverConf.xml**. The **maxCnx** attribute located in **datasource pool** lets you increase the threshold of queries processed simultaneously.

      ```    
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

