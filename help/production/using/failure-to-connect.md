---
solution: Campaign Classic
product: campaign
title: Failure to connect
description: Failure to connect
audience: production
content-type: reference
topic-tags: troubleshooting
---

# Failure to connect{#failure-to-connect}

The reasons for a connection problem can be multiple and depend on various contexts.

You can try the following tests and if the connection failure persists, please contact the **Adobe Campaign support**.



<table> 
 <thead> 
  <tr> 
   <th>Checks<br /> </th> 
   <th>Resolution<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td>Do you have Internet access from your computer?</td> 
   <td>Check that you can connect to websites on the Internet (for example). If you cannot connect, the problem is on your machine. Contact your system administrator.</td>
  </tr>
  <tr> 
   <td>Can you connect to the server hosting Adobe Campaign via another service?</td> 
   <td>Connect to the server via SSH or any other means. If this is not possible, your host company has a problem. Contact their system administrator.</td>
  </tr>
  <tr> 
   <td>Does the Web server respond?</td> 
   <td>Connect to the Adobe Campaign server access URL using a Web browser: <b>http(s):// &lt;urlserver&gt;</b>. If it does not respond, the web server is stopped on the machine. Contact the system administrator of your host company in order to restart the service.</td>
  </tr>
  <tr> 
   <td>Has Adobe Campaign been correctly integrated?</td> 
   <td>Log on to the: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. The server should return the following type of message:

      <pre>
      	<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      </pre>
 If you do not obtain this result, check in your Web server configuration that integration is taken into account.</td>
  </tr>
  <tr> 
   <td>Has the Adobe Campaign Web module been launched?</td> 
   <td>Connect to the following URL: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>
* If you obtain a Tomcat Java error:

Is the JAVA integration correctly performed? Adobe Campaign requires a SUN JDK.

It is integrated in the file [path of application]/nl6/customer.sh

* If you obtain a blank page:
Has the Adobe Campaign Web module started up? You should obtain:
<pre>
nlserver pdump
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
[...]
web@default (27515) - 55.2 Mb
[...]
</pre>
* If not, restart it using the following command:
<pre>        
nlserver start web
</pre>
</td>
</tr>
  <tr>
  	<td>Check the general configuration of the security zones.</td>
  	<td>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones)</td>
  </tr>
 </tbody> 
</table>
