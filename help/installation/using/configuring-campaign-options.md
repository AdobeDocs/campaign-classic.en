---
title: Configuring Campaign options
seo-title: Configuring Campaign options
description: Configuring Campaign options
seo-description: 
page-status-flag: never-activated
uuid: 3a1b21b9-7840-435d-9c41-4bdfd97d15ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: de6d08d4-4356-43ac-985b-d2047fc644f8
index: y
internal: n
snippet: y
---

# Configuring Campaign options{#configuring-campaign-options}

The **Administration / Platform / Options** node allows you to configure Adobe Campaign options.

Some of them are built-in when installing Campaign, and others can be added manually when needed. Available options vary according to the packages installed with your instance.

## Delivery {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Deliverability_LastBroadLogMsgDate</strong><br /> </td> 
   <td> Date of the last broadLogMsg retrieved from the deliverability instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Deliverability_LastBroadLogMsgSent</strong><br /> </td> 
   <td> Date of the last broadLogMsg sent to the deliverability instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DmRendering_cuid</strong><br /> </td> 
   <td> Delivery reports identifier. Please contact support to obtain your identifier.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DmRendering_SeedTargets</strong><br /> </td> 
   <td> List of schemas for which you want to use test addresses for Inbox Rendering. (element names are separated with commas) E.g.: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBilling_MainActionThreshold</strong><br /> </td> 
   <td> Minimum number of recipients in order for a delivery to be considered as the main one in the billing report.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_DefaultProvider</strong><br /> </td> 
   <td> Default routing service provider for the new templates.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_LogsPerTransac</strong><br /> </td> 
   <td> Number of BroadLogs that are created for a delivery at once.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_MaxDelayPerTransac</strong><br /> </td> 
   <td> Insertion (into table) of logs (broadLogs) per transactions : number of rows to process per batch.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_MidAnalyzeBatchSize</strong><br /> </td> 
   <td> Grouping size of delivery parts when analyzing mid-sourcing deliveries.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_MsgValidityDuration</strong><br /> </td> 
   <td> Default delivery period for a delivery (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_RegexRules</strong><br /> </td> 
   <td> Regular expressions for normalizing delivery messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_RemoveBlackList</strong><br /> </td> 
   <td> Entering "1" as the value lets you exclude recipients who no longer wish to be contacted.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_RemoveDuplicatesRecipients</strong><br /> </td> 
   <td> Entering "1" as the value lets you automatically ignore doubles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Nms_DefaultRcpSchema</strong><br /> </td> 
   <td> Adobe Campaign uses a "Nms_DefaultRcpSchema" global variable to dialog with the default recipient database (nms:recipient).<br /> The option value must correspond to the name of the schema which matches the external recipient table.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_ErrorAddressMasks</strong><br /> </td> 
   <td> Lets you define the syntax of the Error address used when replying to a message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_FromAddressMasks</strong><br /> </td> 
   <td> Lets you define the syntax of the From address used when sending a message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_MaxRetry</strong><br /> </td> 
   <td> Maximum number of retries during analysis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_PublishingScript</strong><br /> </td> 
   <td> Publication script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_NoCountBroadLogMsgPush</strong><br /> </td> 
   <td> Disable the broadLogMsg count for push messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDeliveryWizard_ShowDeliveryWeight</strong><br /> </td> 
   <td> Display the message weight in the delivery wizard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_DefaultErrorAddr</strong><br /> </td> 
   <td> Default 'error' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_DefaultFromAddr</strong><br /> </td> 
   <td> Default 'from' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_DefaultReplyToAddr</strong><br /> </td> 
   <td> Default 'reply' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_ExpOrganization</strong><br /> </td> 
   <td> Common name of the customer. Used in some warning messages displayed to the recipients.<br /> "You are receiving this message because you have been in contact with ***** or an affiliated company. To no longer receive messages from *****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_FromName</strong><br /> </td> 
   <td> Default 'from' email label at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_ReplyToName</strong><br /> </td> 
   <td> Default 'reply' email label at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_RetryCount</strong><br /> </td> 
   <td> Period between two retries of an email message (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsEmail_RetryPeriod</strong><br /> </td> 
   <td> Period of retries for email messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsForecast_MsgWeightFormula</strong><br /> </td> 
   <td> Formula used to calculate the weighting of a message for a provisional delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsInmail_WhitelistEmails</strong><br /> </td> 
   <td> List of authorized forwarding email addresses (from the inbound mail processing module). The addresses have to be separated by commas (or * to allow all). E.g. xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsNPAI_EmailMaxError</strong><br /> </td> 
   <td> On channel "email"(use as default) : Maximal number of errors that is accepted, for SOFT errors during sending before putting the recipient into quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsNPAI_EmailSignificantErrorDelay</strong><br /> </td> 
   <td> On channel "email"(use as default) : Minimal period to spent since the previous referenced SOFT error, before taking into account a new SOFT error.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsNPAI_MobileMaxError</strong><br /> </td> 
   <td> On channel "mobile" : Maximal number of errors that is accepted, for SOFT errors during sending before putting the recipient into quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsNPAI_MobileSignificantErrorDelay</strong><br /> </td> 
   <td> On channel "mobile" : Minimal period to spent since the previous referenced SOFT error, before taking into account a new SOFT error.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkEmail_Characters</strong><br /> </td> 
   <td> Valid characters for an email address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_MirrorPageUrl</strong><br /> </td> 
   <td> URL of the mirror page server (by default, should be identical to NmsTracking_ServerUrl).<br /> It is the default value of email deliveries when the URL is not specified in the routing definition.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsPaper_SenderLine1</strong><br /> </td> 
   <td> Line 1 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsPaper_SenderLine3</strong><br /> </td> 
   <td> Line 3 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsPaper_SenderLine4</strong><br /> </td> 
   <td> Line 4 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsPaper_SenderLine6</strong><br /> </td> 
   <td> Line 6 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsPaper_SenderLine7</strong><br /> </td> 
   <td> Line 7 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsSMS_Priority</strong><br /> </td> 
   <td> Parameters of sent SMS messages: information transmitted to the SMS gateway to indicate the message priority.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsSMS_RetryCount</strong><br /> </td> 
   <td> Number of retries when sending SMS messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsSMS_RetryPeriod</strong><br /> </td> 
   <td> Period during which retries of SMS messages will be performed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkEmail_Characters</strong><br /> </td> 
   <td> Valid characters for an email address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsMidSourcing_LogsPeriodHour</strong><br /> </td> 
   <td> Allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed. See <a href="../../platform/using/accessing-an-external-database.md#cloud-messaging---fda-synchronization">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsMidSourcing_PrepareFlow</strong><br /> </td> 
   <td> Maximum number of calls in MidSourcing session, which can be run in parallel (3 by default).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NMS_ActivateOwnerConfirmation</strong><br /> </td> 
   <td> Lets you allow the operator in charge of the delivery to confirm the send, if a specific operator or group of operators is designated for starting a delivery in the delivery's properties.<br /> To do this, activate the option by entering "1" as the value. To deactivate this option, enter "0".<br /> The send confirmation process will then function as default: only the operator or group of operators designated for the send in the delivery properties (or an administrator) will be able to confirm and carry out the send. See <a href="../../campaign/using/setting-up-marketing-campaigns.md#starting-an-online-delivery">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsMTA_Alert_Delay</strong><br /> </td> 
   <td> Custom delay (in minutes) after which a delivery is considered as 'delayed', default being 30 minutes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkBarcode_SpecialChar</strong><br /> </td> 
   <td> Enable/Disable support for special characters for Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsLine_AESKey</strong><br /> </td> 
   <td> AES key used in the 'lineImage' servlet to encode the URLs (LINE channel).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsWebSegments_LastStates</strong><br /> </td> 
   <td> Name of the option which contains the web segments and their states.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsUserAgentStats_LastConsolidation</strong><br /> </td> 
   <td> Last consolidation date for <strong>NmsUserAgent</strong> statistics.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_Restrict_EditXML</strong> </td> 
   <td> Add this option with the "0" value to disable the edition of deliveries' XML code (right-click / <strong>Edit XML source</strong> or <strong>CTRL + F4</strong> shortcut).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Resources {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>NcmRessourcesDir</strong><br /> </td> 
   <td> Location of resources for publication in the Adobe Campaign client console. See <a href="../../delivery/using/formatting.md#image-referencing">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NcmRessourcesDirPreview</strong><br /> </td> 
   <td> Location of resources for previewing in the Adobe Campaign client console. See <a href="../../delivery/using/formatting.md#image-referencing">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_DefaultIgnoredImage</strong><br /> </td> 
   <td> List of URL masks for the images skipped during upload.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_ImagePublishing</strong> </td> 
   <td> Configuration of image uploading. The values can be none / tracking / script / list (can be overridden by operator's optional settings). </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_ImageSubDirectory</strong><br /> </td> 
   <td> Folder in which the images on the server are to be stored.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_LogoPath</strong><br /> </td> 
   <td> Space to display logos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NcmPublishingDir</strong><br /> </td> 
   <td> Root folder for publications.<br /> For more on HTML and Text contents generation, refer to <a href="../../delivery/using/using-a-content-template.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkImageUrl</strong><br /> </td> 
   <td> Lets you define the server on which the images used in the deliveries are stored to enable the browser to get them.<br /> For build versions &lt;= 5098, we use the URL of the images that were uploaded onto the instance.<br /> For build versions &gt; 5098, we use instead the delivery's public URL or the <strong>XtkFileRes_Public_URL</strong> option's URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_MediaInstance</strong><br /> </td> 
   <td> Lets you configure the instance name for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_MediaPassword</strong><br /> </td> 
   <td> Lets you configure the password for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsDelivery_MediaServers</strong><br /> </td> 
   <td> Lets you configure the media URL(s) for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsBroadcast_MsgWebValidityDuration</strong><br /> </td> 
   <td> Default validity duration for online resources of a delivery (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkFileRes_Public_URL</strong><br /> </td> 
   <td> New URL for public resource files.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Campaign &amp; workflow management {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>CrmMarketingActivityWindow</strong><br /> </td> 
   <td> Marketing history shown for this number of months.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsOperation_Duration</strong><br /> </td> 
   <td> Default validity period of a campaign (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsOperation_LimitConcurrency</strong><br /> </td> 
   <td> Maximum number of delivery/workflow/hypothesis/simulation jobs that can be processed at a time, started by operationMgt workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsOperation_OperationMgtDebug</strong><br /> </td> 
   <td> Allows you to monitor the <a href="../../workflow/using/campaign.md">operationMgt</a> technical workflow execution. When activated (value "1"), the execution information are logged in the workflow audit logs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsOperation_TimeRange</strong><br /> </td> 
   <td> Time period for targeting and extraction conditions in scheduled mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Workflow_AnalysisThreshold</strong><br /> </td> 
   <td> Number of affected records after which table statistics are automatically recomputed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkReport_Logo</strong><br /> </td> 
   <td> Logo to be displayed in the top right-hand corner of the reports exported.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_PausedWorkflowPeriod</strong><br /> </td> 
   <td> Number of days to wait between checks for paused workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCampaign_Activate_OwnerConfirmation</strong><br /> </td> 
   <td> Activate the deliveries validation by the owner of the operation by entering "1" as the value. To deactivate this option, enter "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsAsset_JavascriptExt</strong><br /> </td> 
   <td> Additional JS library to load in workflow's activity "Marketing resource notifications".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Security {#security}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>XtkAcceptOldPasswords</strong><br /> </td> 
   <td> (Install compatibility mode:build&gt;6000) If the "1" is entered, this option activates the compatibility mode for stored passwords. Changing this option prevents the use of old passwords stored in the database.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkKey</strong><br /> </td> 
   <td> This key is used to encrypt most passwords in the database. (external accounts, LDAP password...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_Allow_PrivilegeEscalation</strong><br /> </td> 
   <td> If 1 is selected, this option to allow privilegeEscalation in javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_Disable_ControlsOnFileDownload</strong><br /> </td> 
   <td> If 1 is selected, this option disable ACL controls during a file download (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_Disable_JSFileSandboxing</strong><br /> </td> 
   <td> If 1 is selected, this option disable the file sandboxing within Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_SaveOptions_AllowNonAdmin</strong><br /> </td> 
   <td> If set to 'true', authorized non-admin operator to update the xtkOption values through the deployment wizard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSecurity_Unsafe_DecryptString</strong><br /> </td> 
   <td> If 1 is selected, this option allow to use decryptString to decrypt some passwords.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkTraceDeleteLogin</strong><br /> </td> 
   <td> Enter the "1" value to trace the deletion of elements with Audit trail information in the mData, through the modification of its "modified by" field before the deletion of the record.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Message Center {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>MC_EnrichmentCustomJs</strong><br /> </td> 
   <td> JavaScript library to be personalized for enriching events. Must contain the implementation of these two functions:<br /> 
    <ul> 
     <li> <p><strong>enrichRtEvents(aiEventId);</strong>: enriches and saves events in the database (where <strong>aiEventId</strong> corresponds to the table of real time events processed).</p> </li> 
     <li> <p><strong>enrichBatchEvents(aiEventId);</strong>: enriches and saves events in the database (where <strong>aiEventId</strong> corresponds to the ID table of batch events processed).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_LastUpdateFromBL</strong><br /> </td> 
   <td> Date of the last event status update via delivery logs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RoutingCustomJs</strong><br /> </td> 
   <td> JavaScript library to be personalized for routing events. Must contain the implementation of these two functions:<br /> 
    <ul> 
     <li> <p><strong>dispatchRtEvent(iEventId);</strong>: returns the internal name of the transactional message selected to process the real time event (where <strong>iEventId</strong> corresponds to the ID of the real time event processed).</p> </li> 
     <li> <p><strong>dispatchBatchEvent(iEventId);</strong>: returns the internal name of the transactional message selected to process the batch event (where <strong>iEventId</strong> corresponds to the ID of the batch event processed).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgDeliveryTimeAlert</strong><br /> </td> 
   <td> Alert threshold of average sending time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgDeliveryTimeWarning</strong><br /> </td> 
   <td> Warning threshold for average sending time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgProcessTimeAlert</strong><br /> </td> 
   <td> Alert threshold for the average processing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgProcessTimeWarning</strong><br /> </td> 
   <td> Warning threshold for the average processing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgQueueAlert</strong><br /> </td> 
   <td> Alert threshold for the average number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgQueueTimeAlert</strong><br /> </td> 
   <td> Alert threshold for average queuing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgQueueTimeWarning</strong><br /> </td> 
   <td> Warning threshold for average queuing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventAvgQueueWarning</strong><br /> </td> 
   <td> Warning threshold for the average number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventErrorAlert</strong><br /> </td> 
   <td> Alert threshold for processing errors of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventErrorWarning</strong><br /> </td> 
   <td> Warning threshold for processing errors of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventMaxQueueAlert</strong><br /> </td> 
   <td> Alert threshold for maximum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventMaxQueueWarning</strong><br /> </td> 
   <td> Warning threshold for maximum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventMinQueueAlert</strong><br /> </td> 
   <td> Alert threshold for minimum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventMinQueueWarning</strong><br /> </td> 
   <td> Warning threshold for minimum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventQueueAlert</strong><br /> </td> 
   <td> Threshold before critical condition for the queue of pending real time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventQueueWarning</strong><br /> </td> 
   <td> Threshold before warning for the queue of pending real time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventThroughputAlert</strong><br /> </td> 
   <td> Alert threshold for real-time event throughput.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_RtEventThroughputWarning</strong><br /> </td> 
   <td> Warning threshold for real-time event throughput.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsMessageCenter_RoutingBatchSize</strong><br /> </td> 
   <td> Size of the regrouping for the event routing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>MC_LastRtEventStat</strong><br /> </td> 
   <td> Update pointer of RtEvent status (last date until when the data was retrieved).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsLine_MessageCenterURL</strong><br /> </td> 
   <td> Message Center server URL used to send welcome messages (LINE channel).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Database {#database}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>NmsCleanup_LastCleanup</strong><br /> </td> 
   <td> Defines the last time the cleanup process was run.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_BroadLogPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which broadlog are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_EventHistoPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which the event history is erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_EventPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which events are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_EventStatPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which the event statistics are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_PropositionPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which propositions are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_QuarantineMailboxFull</strong><br /> </td> 
   <td> Lets you define the delay after which the quarantines are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_RecycledDeliveryPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which recycled deliveries are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_RejectsPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which rejects are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_TrackingLogPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which tracking logs are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_TrackingStatPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which tracking statistics is erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_VisitorPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which visitors are erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsCleanup_WorkflowResultPurgeDelay</strong><br /> </td> 
   <td> Lets you define the delay after which workflow results is erased from the database.<br /> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcCapabilities_AzureDw</strong><br /> </td> 
   <td> Azure SQL Datawarehouse connector options.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcOptions_TableSpaceIndex</strong><br /> </td> 
   <td> Name of the tablespace intended to contain the indexes of the Adobe Campaign standard tables.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcOptions_TableSpaceUser</strong><br /> </td> 
   <td> Name of the tablespace intended to contain the data of the standard Adobe Campaign tables.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcOptions_TableSpaceWork</strong><br /> </td> 
   <td> Name of the tablespace intended to contain the data of the Adobe Campaign work tables.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcOptions_TableSpaceWorkIndex</strong><br /> </td> 
   <td> Name of the tablespace intended to contain the indexes of the Adobe Campaign work tables.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcTimeZone</strong><br /> </td> 
   <td> Time zone of the Adobe Campaign's instance. See <a href="../../installation/using/configuring-campaign-options.md#configuration" target="_blank">Configuration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcUseNChar</strong><br /> </td> 
   <td> Are the database's string fields defined with NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcUseTimeStampWithTZ</strong><br /> </td> 
   <td> Do the database's 'datetime' fields store timezone info?<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkDatabaseId</strong><br /> </td> 
   <td> ID of the database. Begins by 'u' for Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkInstancePrefix</strong><br /> </td> 
   <td> Prefix added to internal names generated automatically.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkQuery_Schema_LineCount</strong><br /> </td> 
   <td> Maximum number of results returned by a query on xtk:schema and xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkSequence_AutoGeneration</strong><br /> </td> 
   <td> All customized schemas, created after this time, with autopk="true" and without the attribute "pkSequence" will get an auto-geneated sequence "auto_ 
    <schemanamespace> 
     <schemaname>
       _seq. 
      <br /> 
     </schemaname> 
    </schemanamespace></td> 
  </tr> 
  <tr> 
   <td> <strong>NlMigration_KeepFolderStructure</strong><br /> </td> 
   <td> During migration, the tree structure is automatically reorganized based on the new version standards.<br /> This option allows you to disable the automatic migration of the navigation tree. If you use it, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.<br /> 
    <ul> 
     <li> <p><strong>Data type:</strong> Integer</p> </li> 
     <li> <p><strong>Value (text)</strong>: 1 </p> </li> 
    </ul> This option should only be used if the out-of-the-box navigation tree has undergone too many changes.<br /> For more on this, refer to <a href="../../migration/using/specific-configurations-in-v5-11.md#adobe-campaign-v7-tree-structure">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsLastErrorStatCoalesce</strong><br /> </td> 
   <td> Last processing date of the <strong>NmsEmailErrorStat</strong> table cleanup.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostUpgradeLastError</strong><br /> </td> 
   <td> Information concerning the error that occurred in the Postupgrade, following the syntax below:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occurred + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkCleanup_NoStats</strong><br /> </td> 
   <td> Enter the "1" value so that the update of statistics is not performed through the cleanup workflow.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>AEMResourceTypeFilter</strong><br /> </td> 
   <td> Types of AEM resources that can be used in Adobe Campaign. Values must be separated by commas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>nmsPipeline_config</strong><br /> </td> 
   <td> Lets you configure Experience Cloud Triggers. Data type is "long text" and must be in JSON format. See .<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</strong><br /> </td> 
   <td> This option is used when importing data from a third-party system through a CRM connector. Enabling the option lets you collect only objects modified since the last import. This option has to be manually created and populated as below: 
    <ul> 
     <li> <p><strong>Internal name</strong>: LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p><strong>Value (field)</strong>: date of the last import, with the yyyy/MM/dd hh:mm:ss format. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TNT_EdgeServer</strong><br /> </td> 
   <td> Adobe Target server used for the integration. This option is already selected by default. This value corresponds to the Adobe Target Domain Server, followed by the value /m2. For example: tt.omtrdc.net/m2.<br /> See <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TNT_TenantName</strong><br /> </td> 
   <td> Adobe Target Organization name. This value corresponds to the name of the Adobe Target Client.<br /> See <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AAM_DataSourceId</strong><br /> </td> 
   <td> Option used for the integration with Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AAM_DestinationId</strong><br /> </td> 
   <td> Option used for the integration with Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcCapabilities_Teradata</strong><br /> </td> 
   <td> Teradata connector options.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>WdbcCapabilities_Hive</strong><br /> </td> 
   <td> Hive connector options.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Offers {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>NmsCoupons_MaxPerTransac</strong><br /> </td> 
   <td> Number of coupons that are updated per SQL transaction.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsInteraction_LastPropositionSynchControl_</strong><br /> </td> 
   <td> '+ [proposition's schema] + "_" + extAccountSource.@executionInstanceId + [proposition's schema] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsInteraction_LastPropositionSynchExec_</strong><br /> </td> 
   <td> '+ [ proposition's schema] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsInteraction_SynchWorkflowIds</strong><br /> </td> 
   <td> Synchronization workflow tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsInteraction_UseDaemon</strong><br /> </td> 
   <td> Enable/disable asynchronous proposition writing ("0" to disable, "1" to enable).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsModule_CouponsEnabled</strong><br /> </td> 
   <td> Lets you enable coupons.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>NmsExecutionInstanceId</strong><br /> </td> 
   <td> Execution instance identifier.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_CustomerId</strong><br /> </td> 
   <td> Customer identifier used when sending the billing report.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_IntranetURL</strong><br /> </td> 
   <td> Internal base URL to access the application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_LastPostUpgrade</strong><br /> </td> 
   <td> Build number of the AC instance before the last upgrade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsServer_URL</strong><br /> </td> 
   <td> Base URL of the public web application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkPassUnknownSQLFunctionsToRDBMS</strong><br /> </td> 
   <td> Lets you continue using old undeclared SQL functions after migrating. We strongly recommend against using this option due to the security risks it introduces.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>NmsTracking_Available</strong><br /> </td> 
   <td> Option that lets you activate tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_ClickFormula</strong><br /> </td> 
   <td> Tracked-URL calculation script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_ExtAccount</strong><br /> </td> 
   <td> Lets you define the tracking server's external account.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_Instance</strong><br /> </td> 
   <td> Lets you define the instance name on the tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_LastConsolidation</strong><br /> </td> 
   <td> Last time the tracking information has been consolidated with new data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_OpenFormula</strong><br /> </td> 
   <td> Open URL computation script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_Password</strong><br /> </td> 
   <td> Password for the tracking sever<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_Pointer</strong><br /> </td> 
   <td> The pointer keeps track of the last messsage events that were processed through their IDs and date.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_SecureServerUrl</strong><br /> </td> 
   <td> Secure URL of the frontal tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_ServerUrl</strong><br /> </td> 
   <td> URL of the frontal tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_ServerUrlList</strong><br /> </td> 
   <td> List of the URLs used to contact the tracking servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_UserAgentRules</strong><br /> </td> 
   <td> Browser-identification rule set.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_WebFormula</strong><br /> </td> 
   <td> Script used to compute Web tracking tags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_WebTrackingDelivery</strong><br /> </td> 
   <td> Name of the virtual delivery designed for web tracking management.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>NmsTracking_WebTrackingMode</strong><br /> </td> 
   <td> Lets you define the web tracking mode.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## GDPR {#gdpr}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Privacy_Request_ConfirmDeletePending</strong><br /> </td> 
   <td> If option 1 is selected, you have to confirm manually the deletion in the interface in a second step. Otherwise, data will be deleted without confirmation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Privacy_Request_ConfirmDeletePendingDelay</strong><br /> </td> 
   <td> Delay between request waits for deleting confirmation and request is cancelled.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Privacy_Request_MaxErrorAllowed</strong><br /> </td> 
   <td> The maximum number of error allowed when processing/deleting a privacy request.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Privacy_Request_PurgeDelay</strong><br /> </td> 
   <td> Delay between request is created on the queue and request data is deleted.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>XtkLdap_Active</strong><br /> </td> 
   <td> Enable LDAP server to be used to authenticate users and provide authorizations to users.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_AppLogin</strong><br /> </td> 
   <td> Application login to contact the server for various searches.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_AppPassword</strong><br /> </td> 
   <td> Encrypted password for the application login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_AutoOperator</strong><br /> </td> 
   <td> Enable automatic creation of operators and rights in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_DN</strong><br /> </td> 
   <td> Computation formula for LDAP DN based on login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_DNSearch</strong><br /> </td> 
   <td> Enable DN search in directory.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_DNSearchBase</strong><br /> </td> 
   <td> Search base.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_DNSearchFilter</strong><br /> </td> 
   <td> DN search filter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_DNSearchScope</strong><br /> </td> 
   <td> Search scope.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_Mechanism</strong><br /> </td> 
   <td> Authentication type used to contact the LDAP server (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_Rights</strong><br /> </td> 
   <td> Enable synchronization of authorizations and groups from LDAP directory to named rights in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_RightsAttr</strong><br /> </td> 
   <td> LDAP attribute containing the authorization name.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_RightsBase</strong><br /> </td> 
   <td> Search base.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_RightsFilter</strong><br /> </td> 
   <td> Search filter for user authorizations.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_RightsMask</strong><br /> </td> 
   <td> Expression to extract the names of the Adobe Campaign rights from the LDAP authorizations.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_RightsScope</strong><br /> </td> 
   <td> Search scope.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkLdap_Server</strong><br /> </td> 
   <td> LDAP server address (it is possible to specify a port by specifying ':' as the separator).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web forms {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>XtkUseScrollBar</strong><br /> </td> 
   <td> Value set to 1 will allow Scroll bar addition to detail forms.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkWebForm_Instance</strong><br /> </td> 
   <td> Instance to be used for web form invalidation in 'other server(s)' mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkWebForm_Password</strong><br /> </td> 
   <td> Password of the instance to be used for web form invalidation in 'other server(s)' mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkWebForm_ServersMode</strong><br /> </td> 
   <td> Option that lets you specify the invalidation mode of web forms: local by default, uses tracking servers if the option is 'tracking' and uses a personalized list with the 'other server(s)' option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>XtkWebForm_ServersURLs</strong><br /> </td> 
   <td> Personalized address list of servers to be contacted for web form invalidation ('other server(s)' mode).<br /> </td> 
  </tr> 
 </tbody> 
</table>

