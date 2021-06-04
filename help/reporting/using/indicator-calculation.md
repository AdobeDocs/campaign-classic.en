---
product: campaign
title: Indicator calculation
description: Indicator calculation
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
---
# Indicator calculation {#indicator-calculation}

## User activities {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Opens<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Sum of all @totalClicks with a URL primary key equal to 1.<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Sum of all @totalClicks with a URL type equal to "Email click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Sum of all @totalClicks with a URL type equal to "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

This report is based on the **[!UICONTROL Consolidated tracking]** table (nms:trackingStats). This aggregate table is used for performance reasons when displaying reports, in the place of the **[!UICONTROL Recipient tracking logs]** table (nms:trackingLogRcp) and it is not calculated in real-time. The table is generated a few minutes after the tracking logs are retrieved. If the indicators are up-to-date, the results will be the same as for the indicators of the **Tracking indicators** report. The @totalclicks indicator expresses the total number of clicks over a 5-minute period.

## Non-deliverables and bounces {#non-deliverables-and-bounces-1}

**Breakdown by error type**

This report is based on the **[!UICONTROL Delivery and tracking statistics]** table (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Total number of processed messages<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Sum of messages with a status equal to "Ready", "Sent" or "Failed".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> User unknown<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "User unknown". <br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Unreachable <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "Unreachable". <br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rejected<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "Rejected". <br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Invalid domain<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "Invalid domain". <br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Account disabled<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "Account disabled".<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox full<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Count of all messages with a status equal to "Failed" and a reason equal to "Inbox full". <br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Errors<br /> </td> 
   <td> @value<br /> </td> 
   <td> Number of failed messages for this type of error.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="Value of the error type")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contribution<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of errors of this type compared to the total number of error messages.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Breakdown<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of errors of this type compared to the total number of processed messages.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Breakdown by domain**

The second part of the report details the breakdown of failed messages by internet domain as opposed to error type. The formula linked to the **Error** indicator (@value) in this case is: Count(@status=2 and @domain="Value of the domain name"), i.e. a count of all messages with a failed status for this domain.

## Browsers {#browsers-1}

This report is based on the **[!UICONTROL Internet Browser Statistics]** table (nms:userAgentsStats).

**Global statistics**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitors<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Total number of targeted recipients for this browser who clicked in a delivery at least once.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Page views<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Total number of clicks on delivery links using this browser, for all deliveries.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Usage rate<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of visitors for this browser compared to the total number of visitors.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistics per browser**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Usage rate<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Percentage of the number of visitors per day using this browser compared to the number of visitors measured on the day with the most visits.<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Global rate<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of visitors for this version compared to the total number of visitors using all browsers.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relative weight<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of visitors for this version compared to the total number of visitors using this browser.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sharing to social networks {#sharing-to-social-networks-1}

This report is based on the **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats), and **[!UICONTROL Web tracking]** (nms:webTrackingLog) tables.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Number of messages to deliver<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Total number of messages processed during the delivery analysis.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Number of successful deliveries<br /> </td> 
   <td> @success<br /> </td> 
   <td> Number of messages processed successfully <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Sum of all @totalClicks for which the URL category equals "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Shares**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Number of shares<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Total number of messages shared on this social network.<br /> </td> 
   <td> Sum(iIf([url/@category]="Value of the social network type",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Breakdown<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Percentage of the number of shares on this social network compared to the total number of shares.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Sharing rate<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Number of shares on this network compared to the number of messages to deliver.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Opens**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Number of opens <br /> </td> 
   <td> @open<br /> </td> 
   <td> Total number of tracking lines in the web tracking table.<br /> </td> 
   <td> Count<br /> </td> 
  </tr> 
  <tr> 
   <td> Breakdown<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Percentage of the number of opens on this social network compared to the total number of opens.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Rate of opens<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Number of opens on this social network compared to the total number of messages to deliver.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistics on sharing activities {#statistics-on-sharing-activities-1}

This report is based on the **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats), and **[!UICONTROL Web tracking]** (nms:webTrackingLog) tables. 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> New contacts<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Count of the number of visitors linked to a recipient.<br /> </td> 
   <td> Formula: count(@id)<br /> Filter: @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Opens<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Count of all @ids with a URL type equal to "Open".<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Shares<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL category included in 'email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'<br /> Count of all @totalClicks with a URL category that equals "email", "facebook", "twitter", "delicious", "digg", "google" or "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Operating systems {#operating-systems-1}

This report is based on the **[!UICONTROL Internet Browser Statistics]** table (nms:userAgentsStats).

**Global statistics**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitors<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Daily average of the total number of recipients targeted by the operating system who clicked in a delivery at least once.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pages viewed<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Daily average of the total number of clicks on the delivery links per operating systems for all deliveries.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Usage rate<br /> </td> 
   <td> -<br /> </td> 
   <td> Breakdown of visitors per operating system compared to the total number of visitors.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistics per operating system**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Usage rate<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Percentage of the number of visitors per day on this operating system compared to the number of visitors measured on the day with the most visits.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Global rate<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of visitors per version compared to the total number of visitors on all operating systems.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relative rate<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of visitors per version compared to the total number of visitors using this operating system.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Subscription tracking {#subscription-tracking-1}

This report is based on the **[!UICONTROL Services]** table (nms:service). 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Registered<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Count of registered people on the previous day.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Subscriptions<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> count of subscriptions (@action = 1) on the previous day.<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Unsubscriptions<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> count of unsubscriptions (action = 0) on the previous day.<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolution<br /> </td> 
   <td> -<br /> </td> 
   <td> Number of subscriptions minus the number of unsubscriptions. The rate is calculated in relation to the total number of subscribers.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Loyalty<br /> </td> 
   <td> -<br /> </td> 
   <td> Subscriber loyalty rate for the related period.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking indicators {#tracking-indicators-1}

This report is based on the **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) and **[!UICONTROL Consolidated tracking]** (nms:trackingStats) tables. 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messages to deliver<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Count of the number of broadLogs after target analysis.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Success<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Count of messages for which the "seed address" field equals "No" and with a status equal to "Taken into account by the service provider" or "Sent" or "Received on the mobile".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinct opens on the population reached<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolation of the number of distinct opens for all emails based on the number of distinct opens for emails in html format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Sum of opens on the population reached<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolation of the total number of opens for all emails based on the total number of opens of emails in html format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks on the unsubscription link<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Count of all @ids with a URL category equal to "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks on the link to the mirror page<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Count of all @ids with a URL category equal to "Mirror page".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Estimation of forwards<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Difference between the number of distinct people and the number of distinct recipients who clicked in the email at least once.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Sends<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Count of the messages for which the "seed address" field equals "No" and with a status equal to "taken into account by the recipient" or "Sent" or "Received on mobile".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Complaints<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Count of messages with a status equal to "Failed" and a reason equal to "address on denylist".<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Opens<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Count of all @broadLog-ids in all tracking logs.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Distinct count of @broadLog-ids with a URL type equal to "Email click". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Raw reactivity<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of the number of recipients who clicked in a delivery at least once compared to the number of recipients who opened a delivery at least once.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinct clicks on the population reached<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Count of all @source-ids with a URL category equal to "Email click".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Cumulated clicks<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Count of all @ids with a URL category that equals "Email click".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Recipient clicks<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Distinct count of the @broadLog-ids with a URL type that equals "Email click".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Estimated reactivity<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio of the number of recipients who clicked in a delivery at least once compared to the estimate of recipients who opened the delivery at least once.<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Visited pages<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Count of all @ids with a URL type equal to "Web" or "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 or [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Count of all @ids with a URL type equal to "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Total amount<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Sum of webTrackingLog/@amounts with a URL type equal to "Transaction". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Average transaction amount<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio of the total amount compared to the number of transactions.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Items<br /> </td> 
   <td> @article<br /> </td> 
   <td> Sum of webTrackingLog/@articles with a URL type that equals "Transaction".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Average number of items per transaction<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio of the number of items compared to the number of transactions.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Average amount per message<br /> </td> 
   <td> -<br /> </td> 
   <td> Ratio of the total amount compared to the number of messages to deliver.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> Email<br /> </td> 
   <td> @email<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Sum of all @totalClicks with a URL category that equals "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URLs and click streams {#urls-and-click-streams-1}

This report is based on the **[!UICONTROL Delivery]** table (nms:delivery). 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reactivity<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Ratio of the number of targeted recipients who clicked in a delivery at least once compared to the estimated number of targeted recipients who opened a delivery at least once.<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinct clicks<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Ratio of the number of distinct people who clicked in a delivery at least once compared to the number of messages delivered with success.<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Cumulated clicks<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Ratio of the total number of clicks by targeted recipients compared to the number of messages delivered with success.<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Count of all @totalClicks with a URL primary key different from 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage of the number of clicks compared to the total number of cumulated clicks.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Delivery summary {#delivery-summary-1}

This report is based on the **[!UICONTROL Delivery]** table (nms:delivery). 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Initial population<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Total number of recipients targeted by the delivery.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messages rejected by the rule<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Number of addresses ignored during the analysis in keeping with typology rules: address not specified, quarantined, on denylist, etc.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messages to deliver<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Total number of messages to deliver after delivery analysis.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Success<br /> </td> 
   <td> @success<br /> </td> 
   <td> Number of messages processed with success.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Errors<br /> </td> 
   <td> @error<br /> </td> 
   <td> Total number of errors cumulated during deliveries and automatic bounce processing.<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> New quarantines<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Number of quarantined addresses following a delivery fail (user unknown, invalid domain).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot clicks {#hot-clicks-1}

This report is based on the Delivery(nms:delivery) and **[!UICONTROL Consolidated tracking]** (nms:trackingStats) tables.

This report shows the message content (HTML and/or text) with, on each link, the percentage of clicks on links. Personalization blocks unsubscription links and mirror page links are taken into account in the total cumulated clicks but are not displayed in the report.

## Tracking statistics {#tracking-statistics-1}

This report is based on the **[!UICONTROL Delivery]** table (nms:delivery). 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Sum of all @totalClicks with a URL type that equals "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Sum of all @totalClicks with a URL type that equals "Email click".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Open<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Sum of all @totalClicks with a URL primary key that equals 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Delivery statistics {#delivery-statistics-1}

This report is based on the **[!UICONTROL Delivery and tracking statistics]** table (nms:deliveryLogStats). 

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Emails processed<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Total number of messages with a status that equals "Ready", "Sent" or "Failed".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br /> </td> 
   <td> @success<br /> </td> 
   <td> Number of messages processed successfully.<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Hard bounces<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Total number of messages with a status that equals "Failed" and a reason that equals "User unknown".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Soft bounces<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Total of all messages with a status that equals "Failed" and a reason that equals "unreachable", "inbox full", "invalid domain", "disabled account", "not connected" or "rejected"<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Opens<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Total number of @broadLog-ids in the tracking logs.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clicks<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Total number of @source-ids for which the URL category equals "Email click". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Unsubscriptions<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Total number of @ids for which the URL category equals "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Breakdown of opens {#breakdown-of-opens-1}

This report is based on **Deliveries** (nms:delivery) and **Tracking logs** (nms:trackingLogRcp) tables.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Field name</strong> <br /> </th> 
   <th> <strong>Indicator description</strong> <br /> </th> 
   <th> <strong>Indicator calculation formula</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Opens<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Sum of all @id with a URL primary key equal to 1 (open). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Other indicators {#other-indicators}

The **Sent** indicator (@sent), accessed via the **Deliveries (nms:delivery) > Indicators** node corresponds to the total number of SMS sent to the service provider. This indicator is only used for SMS deliveries and must not be used for other types of deliveries (not to be confused with the **@success** and **@processed** indicators).

## Indicator synchronization {#indicator-synchronization}

If you experience desynchronization or inconsistency for certain indicators, select the concerned delivery in the Adobe Campaign explorer, right-click and choose **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Click **[!UICONTROL Next]**, then click **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Tracking opens {#tracking-opens-}

In order for Adobe Campaign to detect message opens, the recipient must download the images in the email. HTML and Multipart/Alternative emails include a 0 pixel image, which enable you to detect messages which have been opened. Since messages in text format do not include any images, it is impossible to detect whether they have been opened or not. Values calculated based on message opens are always estimates, due to the error margin linked to image display.

## Targeted persons / recipients {#targeted-persons---recipients}

In some reports, Adobe Campaign differentiates targeted persons and targeted recipients.

Targeted recipients are all the recipients whom the delivery was sent to.

The number of persons includes targeted recipients plus all persons whom the email was forwarded to. Each time there is an open or a click in a new browser (which the message has not yet been opened in), another person is added to the statistics.

For instance, if you receive an email (sent by Adobe Campaign) at work and open or click in it, you will be counted as a targeted recipient (i.e. recipient=1, person=1). If you forward this email to two friends, the number of targeted recipients will still equal one, while the number of persons will equal three. Value 3 coincides with each open/click in a new browser.
