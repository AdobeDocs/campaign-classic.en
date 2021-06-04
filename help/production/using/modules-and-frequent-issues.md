---
product: campaign
title: Modules and frequent issues
description: Modules and frequent issues
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
---
# Modules and frequent issues{#modules-and-frequent-issues}

Here is a list of modules impacted by frequent issues:

<table> 
 <thead> 
  <tr> 
   <th> Module </th> 
   <th> Execution scope </th> 
   <th> Troubleshooting </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Execution of an export process<br /> </td> 
   <td> The operator who scheduled this export needs to re-launch it. Either delta or full re-launch.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Execution of an import process<br /> </td> 
   <td> The operator who scheduled this export needs to re-launch it. Check the database for duplicates.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Reading of the bounce mail box<br /> </td> 
   <td> Check this module if bounce mails are no longer forwarded.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Delivers emails<br /> </td> 
   <td> Check this module if mails are no longer being sent.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Maintains MTA connection statistics<br /> </td> 
   <td> Check this module if mails are no longer being sent.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Log writing<br /> </td> 
   <td> If some logs are missing in the log files, check to make sure that the module is using port 6666. Refer to <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">List of open ports</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Consolidating and retrieving tracking logs<br /> </td> 
   <td> Check this module if tracking logs aren't forwarded anymore.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracking log writing and purging server<br /> </td> 
   <td> Check this module if tracking logs aren't forwarded anymore and there are no traces of logs in the files on the server. Refer to <a href="../../production/using/tracking-logs-issues.md" target="_blank">Tracking logs issues</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Startup and monitoring instance<br /> </td> 
   <td> Check this module if no processes start.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Application server (HTTP and SOAP)<br /> </td> 
   <td> Check this module if the console and web connections don't work and trigger an <strong>xtk:session</strong> type error<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controls workflow instance execution.<br /> </td> 
   <td> If you encounter any problems, restart this module. If necessary, apply the procedure to increase precision of logs detailed in the <a href="../../production/using/log-precision.md" target="_blank">Log precision</a> section.<br /> </td> 
  </tr> 
 </tbody> 
</table>
