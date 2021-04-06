---
solution: Campaign Classic
product: campaign
title: Configuring Campaign options
description: Learn how to configure Campaign options
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
---
# List of Campaign Classic options{#configuring-campaign-options}

The **[!UICONTROL Administration / Platform / Options]** node allows you to configure Adobe Campaign options.

>[!NOTE]
>
>Modifying or updating Adobe Campaign options can be performed by experts users only.

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
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Date of the last broadLogMsg retrieved from the deliverability instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Date of the last broadLogMsg sent to the deliverability instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Delivery reports identifier. Please contact support to obtain your identifier.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> List of schemas for which you want to use test addresses for Inbox Rendering. (element names are separated with commas) E.g.: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Lets you allow the operator in charge of the delivery to confirm the send, if a specific operator or group of operators is designated for starting a delivery in the delivery's properties.</p><p> To do this, activate the option by entering "1" as the value. To deactivate this option, enter "0".</p><p> The send confirmation process will then function as default: only the operator or group of operators designated for the send in the delivery properties (or an administrator) will be able to confirm and carry out the send. See <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">this section</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign uses a "Nms_DefaultRcpSchema" global variable to dialog with the default recipient database (nms:recipient).<br /> The option value must correspond to the name of the schema which matches the external recipient table.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Minimum number of recipients in order for a delivery to be considered as the main one in the billing report.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Default routing service provider for the new templates.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Number of BroadLogs that are created for a delivery at once.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Insertion (into table) of logs (broadLogs) per transactions : number of rows to process per batch.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Grouping size of delivery parts when analyzing mid-sourcing deliveries.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Default delivery period for a delivery (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Regular expressions for normalizing delivery messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Entering "1" as the value lets you exclude recipients who no longer wish to be contacted.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Entering "1" as the value lets you automatically ignore doubles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Lets you define the syntax of the Error address used when replying to a message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Lets you define the syntax of the From address used when sending a message.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Lets you define a timeout limit (in seconds) for getting a response from the server when retrieving an image downloaded from a personalized URL and attached to an email. If this value is exceeded, the message cannot be sent. The default value is 60 seconds.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Lets you define the maximum size (in bytes) allowed for an image downloaded from a personalized URL and attached to an email. The default value is 100,000 bytes. When sending a proof and downloading the image(s) to process the email, if the size of an image exceeds this value or if there is a downloading issue, an error will be displayed in the Delivery logs and the proof delivery will fail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Lets you set a maximum number of attachments in an email or transactional email template. If this value is exceeded, a warning will be displayed in the delivery analysis logs or when publishing the transactional email template. The default value is 1 attachment.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Maximum number of retries during analysis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Publication script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Disable the broadLogMsg count for push messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Display the message weight in the delivery wizard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Default 'error' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Default 'from' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Default 'reply' email address at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Common name of the customer. Used in some warning messages displayed to the recipients.<br /> "You are receiving this message because you have been in contact with ***** or an affiliated company. To no longer receive messages from *****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Default 'from' email label at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Default 'reply' email label at instance's level used for email delivery if left empty by user.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Period between two retries of an email message (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Period of retries for email messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formula used to calculate the weighting of a message for a provisional delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> List of authorized forwarding email addresses (from the inbound mail processing module). The addresses have to be separated by commas (or * to allow all). E.g. xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> AES key used in the 'lineImage' servlet to encode the URLs (LINE channel).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> On channel "email"(use as default) : Maximal number of errors that is accepted, for SOFT errors during sending before putting the recipient into quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> On channel "email"(use as default) : Minimal period to spent since the previous referenced SOFT error, before taking into account a new SOFT error.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> On channel "mobile" : Maximal number of errors that is accepted, for SOFT errors during sending before putting the recipient into quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> On channel "mobile" : Minimal period to spent since the previous referenced SOFT error, before taking into account a new SOFT error.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Maximum number of calls in MidSourcing session, which can be run in parallel (3 by default).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Custom delay (in minutes) after which a delivery is considered as 'delayed', default being 30 minutes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>This option is used by the <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> technical workflow when counting the number of running deliveries.</p>It allows you to define the number of days above which deliveries with inconsistent status will be excluded from the count of running deliveries.</p><p>By default, the value is set to “7", meaning that inconsistent deliveries older than 7 days will be excluded.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Line 1 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Line 3 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Line 4 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Line 6 of the sender's address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Line 7 of the sender's address.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> URL of the mirror page server (by default, should be identical to NmsTracking_ServerUrl).<br /> It is the default value of email deliveries when the URL is not specified in the routing definition.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parameters of sent SMS messages: information transmitted to the SMS gateway to indicate the message priority.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Number of retries when sending SMS messages.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Period during which retries of SMS messages will be performed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Last consolidation date for <span class="uicontrol">NmsUserAgent</span> statistics.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Name of the option which contains the web segments and their states.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Enable/disable support for special characters for Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Valid characters for an email address.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Add this option with the "0" value to disable the edition of deliveries' XML code (right-click / <span class="uicontrol">Edit XML source</span> or <span class="uicontrol">CTRL + F4</span> shortcut).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

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
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Location of resources for publication in the Adobe Campaign client console. See <a href="../../delivery/using/formatting.md#image-referencing">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Location of resources for previewing in the Adobe Campaign client console. See <a href="../../delivery/using/formatting.md#image-referencing">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> List of URL masks for the images skipped during upload.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuration of image uploading. The values can be none / tracking / script / list (can be overridden by operator's optional settings). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Folder in which the images on the server are to be stored.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Space to display logos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Root folder for publications.<br /> For more on HTML and Text contents generation, refer to <a href="../../delivery/using/using-a-content-template.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Lets you define the server on which the images used in the deliveries are stored to enable the browser to get them.<br /> For build versions &lt;= 5098, we use the URL of the images that were uploaded onto the instance.<br /> For build versions &gt; 5098, we use instead the delivery's public URL or the <span class="uicontrol">XtkFileRes_Public_URL</span> option's URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Lets you configure the instance name for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Lets you configure the password for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Lets you configure the media URL(s) for image uploading.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Default validity duration for online resources of a delivery (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
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
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Marketing history shown for this number of months.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Default validity period of a campaign (in seconds).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximum number of delivery/workflow/hypothesis/simulation jobs that can be processed at a time, started by operationMgt workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Allows you to monitor the <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> technical workflow execution. When activated (value "1"), the execution information are logged in the workflow audit logs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Time period for targeting and extraction conditions in scheduled mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Number of affected records after which table statistics are automatically recomputed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo to be displayed in the top right-hand corner of the reports exported.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Number of days to wait between checks for paused workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Activate the deliveries validation by the owner of the operation by entering "1" as the value. To deactivate this option, enter "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Install compatibility mode: build&gt;6000) When activated (value “1”), this option allows the use of old passwords stored in the database for the connexion to external accounts or to the instance.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> This key is used to encrypt most passwords in the database. (external accounts, LDAP password...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> If 1 is selected, this option to allow privilegeEscalation in javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> If 1 is selected, this option disable ACL controls during a file download (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> If 1 is selected, this option disable the file sandboxing within Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> If set to 'true', authorized non-admin operator to update the xtkOption values through the deployment wizard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> If 1 is selected, this option allow to use decryptString to decrypt some passwords.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
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
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> JavaScript library to be personalized for enriching events. Must contain the implementation of these two functions:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriches and saves events in the database (where <span class="uicontrol">aiEventId</span> corresponds to the table of real time events processed).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriches and saves events in the database (where <span class="uicontrol">aiEventId</span> corresponds to the ID table of batch events processed).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Date of the last event status update via delivery logs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript library to be personalized for routing events. Must contain the implementation of these two functions:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : returns the internal name of the transactional message selected to process the real time event (where <span class="uicontrol">iEventId</span> corresponds to the ID of the real time event processed).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : returns the internal name of the transactional message selected to process the batch event (where <span class="uicontrol">iEventId</span> corresponds to the ID of the batch event processed).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Alert threshold of average sending time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Warning threshold for average sending time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Alert threshold for the average processing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Warning threshold for the average processing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Alert threshold for the average number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Alert threshold for average queuing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Warning threshold for average queuing time of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Warning threshold for the average number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Alert threshold for processing errors of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Warning threshold for processing errors of real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Alert threshold for maximum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Warning threshold for maximum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Alert threshold for minimum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Warning threshold for minimum number of queued real-time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Threshold before critical condition for the queue of pending real time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Threshold before warning for the queue of pending real time events.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Alert threshold for real-time event throughput.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Warning threshold for real-time event throughput.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Size of the regrouping for the event routing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Update pointer of RtEvent status (last date until when the data was retrieved).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Defines the last time the cleanup process was run.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which broadlog are erased from the database.</p><p>This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Lets you define the delay after which the event history is erased from the database.</p><p>
   This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Lets you define the delay after which events are erased from the database.</p><p>This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Lets you define the delay after which the event statistics are erased from the database.</p><p>This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Lets you define the delay after which propositions are erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Lets you define the delay after which the quarantines are erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which recycled deliveries are erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which rejects are erased from the database.</p><p>This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which tracking logs are erased from the database.</p><p>This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Lets you define the delay after which tracking statistics is erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which visitors are erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Lets you define the delay after which workflow results is erased from the database.</p><p> This option is automatically created once the delay is modified within the interface. If you modify the value from the options list, it should be expressed in seconds.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse connector options.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Lets you affect Unconditional Stop behavior on all the workflows and PostgreSQL database queries according to the following potential values:<ul>
    <li><p>0 – default: stops workflow process, no impact on the database<p></li>
    <li><p>1 -  pg_cancel_backend: stops workflow process and cancels query in the database<p></li>
    <li><p>2 – pg_terminate_backend: stops workflow process and terminates query in the database<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Name of the tablespace intended to contain the data of the Adobe Campaign standard tables.<br />See <a href="../../installation/using/creating-and-configuring-the-database.md">Creating and configuring the database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Name of the tablespace intended to contain the indexes of the Adobe Campaign standard tables.<br />See <a href="../../installation/using/creating-and-configuring-the-database.md">Creating and configuring the database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Name of the tablespace intended to contain the data of the Adobe Campaign work tables.<br />See <a href="../../installation/using/creating-and-configuring-the-database.md">Creating and configuring the database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Name of the tablespace intended to contain the indexes of the Adobe Campaign work tables.<br />See <a href="../../installation/using/creating-and-configuring-the-database.md">Creating and configuring the database</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Allows you to configure a separate database for working tables on Microsoft SQL Server, in order to optimize backups and replication. The option corresponds to the name of the temporary database: Work tables will be written in this database if specified. Example: 'tempdb.dbo.' (note that the name must end with a dot). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Read more</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Time zone of the Adobe Campaign's instance. See <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Are the database's string fields defined with NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Do the database's 'datetime' fields store timezone info?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID of the database. Begins by 'u' for Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefix added to internal names generated automatically.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximum number of results returned by a query on xtk:schema and xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> All customized schemas, created after this time, with autopk="true" and without the attribute "pkSequence" will get an auto-geneated sequence "auto_ 
    &lt;schemanamespace> 
     &lt;schemaname>
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> During migration, the tree structure is automatically reorganized based on the new version standards.<br /> This option allows you to disable the automatic migration of the navigation tree. If you use it, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Data type:</span> Integer</p> </li> 
     <li> <p> <span class="uicontrol">Value (text)</span> : 1 </p> </li> 
    </ul> This option should only be used if the out-of-the-box navigation tree has undergone too many changes.<br /> For more on this, refer to <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Last processing date of the <span class="uicontrol">NmsEmailErrorStat</span> table cleanup.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Information concerning the error that occurred in the Postupgrade, following the syntax below:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occurred + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
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
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Types of AEM resources that can be used in Adobe Campaign. Values must be separated by commas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Lets you configure Experience Cloud Triggers. Data type is "long text" and must be in JSON format. See <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">How to use Experience Cloud Triggers with Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> This option is used when importing data from a third-party system through a CRM connector. Enabling the option lets you collect only objects modified since the last import. This option has to be manually created and populated as below: 
    <ul> 
     <li> <p> <span class="uicontrol">Internal name</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Value (field)</span> : date of the last import, with the yyyy/MM/dd hh:mm:ss format. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Adobe Target server used for the integration. This option is already selected by default. This value corresponds to the Adobe Target Domain Server, followed by the value /m2. For example: tt.omtrdc.net/m2.<br /> See <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target Organization name. This value corresponds to the name of the Adobe Target Client.<br /> See <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">this section</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Option used for the integration with Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Option used for the integration with Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata connector options.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Number of coupons that are updated per SQL transaction.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [proposition's schema] + "_" + extAccountSource.@executionInstanceId + [proposition's schema] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ proposition's schema] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Synchronization workflow tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Enable/disable asynchronous proposition writing ("0" to disable, "1" to enable).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Execution instance identifier.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Customer identifier used when sending the billing report.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Internal base URL to access the application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Build number of the AC instance before the last upgrade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> Base URL of the public web application server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Option that lets you activate tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Tracked-URL calculation script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Lets you define the tracking server's external account.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Lets you define the instance name on the tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Last time the tracking information has been consolidated with new data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Open URL computation script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Password for the tracking sever<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> The pointer keeps track of the last messsage events that were processed through their IDs and date.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Secure URL of the frontal tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL of the frontal tracking server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> List of the URLs used to contact the tracking servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Browser-identification rule set.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script used to compute Web tracking tags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Name of the virtual delivery designed for web tracking management.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Lets you define the web tracking mode.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Privacy {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Option name </th> 
   <th> Description </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> If option 1 is selected, you have to confirm manually the deletion in the interface in a second step. Otherwise, data will be deleted without confirmation.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Delay between request waits for deleting confirmation and request is cancelled.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> The maximum number of error allowed when processing/deleting a privacy request.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Enable LDAP server to be used to authenticate users and provide authorizations to users.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Application login to contact the server for various searches.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Encrypted password for the application login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Enable automatic creation of operators and rights in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Computation formula for LDAP DN based on login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Enable DN search in directory.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Search base.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN search filter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Search scope.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Authentication type used to contact the LDAP server (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Enable synchronization of authorizations and groups from LDAP directory to named rights in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> LDAP attribute containing the authorization name.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Search base.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Search filter for user authorizations.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expression to extract the names of the Adobe Campaign rights from the LDAP authorizations.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Search scope.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
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
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Value set to 1 will allow Scroll bar addition to detail forms.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instance to be used for web form invalidation in 'other server(s)' mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Password of the instance to be used for web form invalidation in 'other server(s)' mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option that lets you specify the invalidation mode of web forms: local by default, uses tracking servers if the option is 'tracking' and uses a personalized list with the 'other server(s)' option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Personalized address list of servers to be contacted for web form invalidation ('other server(s)' mode).<br /> </td> 
  </tr> 
 </tbody> 
</table>
