---
product: campaign
title: Failure to connect
description: Failure to connect
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
---
# Failure to connect{#failure-to-connect}

The reasons for a connection problem can be multiple and depend on various contexts.

You can try the following tests and if the connection failure persists, please contact the [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



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
<td>Log on to the: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. The server should return the following type of message: &lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/>
If you do not obtain this result, check in your Web server configuration that integration is taken into account.</td>
</tr>
<tr> 
<td>Connect to the following URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>If you obtain a Tomcat Java error, check if the JAVA integration is correctly performed. It is integrated in the file [path of application]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Connect to the following URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>If you obtain a blank page, check if the Adobe Campaign Web module is started. The command nlserver pdump should return Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY. If not, restart the module with the command nlserver start web</td>
</tr>
<tr>
<td>Check the general configuration of the security zones.</td>
<td>For more on configuring security zones, refer to <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>this section.</a></td>
</tr>
<tr>
<td>The command nlserver pdump returns <b>No tasks</b></td>
<td>You must restart the entire Adobe Campaign application. To do this, use the following command: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
