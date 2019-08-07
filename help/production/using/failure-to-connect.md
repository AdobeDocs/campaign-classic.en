---
title: Failure to connect
seo-title: Failure to connect
description: Failure to connect
seo-description: 
page-status-flag: never-activated
uuid: 272d533f-38b1-4e0e-9c79-dcf560b027e8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 7420180f-7c63-488e-81fc-a5cf0c723e82
index: y
internal: n
snippet: y
---

# Failure to connect{#failure-to-connect}

The reasons for this can be multiple and depend on various contexts.

Check the general configuration of the security zones.

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Check the following information:

1. **Network checks**

    * Do you have Internet access from your computer?

      Check that you can connect to websites on the Internet (for example). If you cannot connect, the problem is on your machine. Contact your system administrator.
    
    * Can you connect to the server hosting Adobe Campaign via another service?

      Connect to the server via SSH or any other means. If this is not possible, your host company has a problem. Contact their system administrator.

1. **Checks on Web server side** (IIS/apache/etc.)

    * Does the Web server respond?

      Connect to the Adobe Campaign server access URL using a Web browser: **http(s)://&lt;URLSERVER&gt;**. If it does not respond, the web server is stopped on the machine. Contact the system administrator of your host company in order to restart the service.
    
    * Has Adobe Campaign been correctly integrated?

      Log on to the: **http(s):// `<urlserver>  /r/test </urlserver>`** URL. The server should return the following type of message

      ```    
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```    
    
      If you do not obtain this result, check in your Web server configuration that integration is taken into account.

1. **Checks on the Adobe Campaign side**

    * Has the Adobe Campaign Web module been launched?

      Connect to the following URL: **http(s):// `<urlserver jsp="" logon.jsp="" nl="" strong="" />`**

        * If you obtain a Tomcat Java error:

          Is the JAVA integration correctly performed? Adobe Campaign requires a SUN JDK.

          It is integrated in the file **[path of application]/nl6/customer.sh**
        
        * If you obtain a blank page:

          Has the Adobe Campaign Web module started up? You should obtain:

          ```        
          nlserver pdump
          HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) dated DD/MM/YYYY
          [...]
          web@default (27515) - 55.2 Mb
          [...]
          ```        
        
          If not, restart it using the following command:

          ```        
          nlserver start web
          ```

          >[!NOTE]
          >
          >If you obtain a response of the following type when you list the Adobe Campaign modules:   
          > **nlserver pdump** 
          >HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) dated DD/MM/YYYY No tasks You must restart the entire Adobe Campaign application. To do this, use the following commands:   

          >
          >    
          >    
          >    * If you have root or administrator access: 
          >    * If not, then in the Adobe Campaign account: 
          >    
          >    
          >      **nlserver watchdog -svc -noconsole **
          >    
          >    
          >

