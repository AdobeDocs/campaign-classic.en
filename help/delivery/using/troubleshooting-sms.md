---
solution: Campaign Classic
product: campaign
title: SMS troubleshooting
description: Learn more how to troubleshoot SMS channel
audience: delivery
content-type: reference
topic-tags: configuring-channels
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
---
# SMS Troubleshooting {#troubleshooting-sms}

## Conflict between different external accounts {#external-account-conflict}

If the instance has multiple SMS external accounts, you must check that problems are not caused by a conflict between external accounts.

Adobe Campaign treats external accounts as unrelated entities.

If you have multiple accounts, follow this procedure to isolate the external account causing problems:

1. Disable all external accounts.
1. Enable one external account.
1. Try to reproduce the problem.
1. If the initial problem does not always appear, do a reasonable amount of tries before concluding.
1. If the problem does not appear with that single account, disable it and restart to step 2 on the next account.

Once you checked every account individually, there are 2 possible scenarios:

* **The problem appeared on one or several accounts**

  In this case, you can apply other troubleshooting procedures on each account individually. It is best to disable other accounts while diagnosing an account to reduce network traffic and the number of logs.

* **The problem did not appear when only one account is active at any time**

  You have a conflict between accounts. As mentioned before, Adobe Campaign treats accounts individually, but the provider may treat them as a single account.

  * You are using different login/password combinations between all your accounts.
    You will have to contact the provider to diagnose potential conflicts on their side.

  * Some of the external accounts share the same login/password combination.
    The provider has no way to tell from which external account the `BIND PDU` is coming from, so they treat all connections from the multiple accounts as a single one. They might have routed MO and SR randomly over the two accounts, causing issues.
    If the provider supports multiple short codes for the same login/password combination, you will have to ask them where to put that short code in the `BIND PDU`. Note that this piece of information has to be put inside the `BIND PDU`, and not in `SUBMIT_SM`, since the `BIND PDU` is the only place that will allow routing MOs correctly.
    See the [Information in each kind of PDU](../../delivery/using/sms-protocol.md#information-pdu) section above to know which field is available in the `BIND PDU`, usually you add the short code in `address_range`, but that requires special support from the provider. Contact them to know how they expect to route multiple short codes independently.
    Adobe Campaign supports handling multiple short codes on the same external account.

## Issue with external account in general {#external-account-issues}

* Investigate whether connector has been changed recently and by whom (check External Accounts as a group).

  ```
  select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",

  (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",

  (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",

  N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"

  from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
  ```

* Investigate (in /postupgrade directory) whether system was upgraded and when
* Investigate whether any packages affecting SMS might have been upgraded recently (/var/log/dpkg.log).

## Issue with mid-sourcing (hosted){#issue-mid-sourcing}

* If the problem happens on a mid-sourcing environment, make sure that the delivery and broad logs are properly created and updated on the mid-sourcing server. If that's not the case, this is not an SMS issue.

* If everything works on the mid server and SMS are properly sent, but the marketing instance is not properly updated, you might have a mid-synchronization issue.

## Issue when connecting to the provider {#issue-provider}

* If the `BIND PDU` returns a non-zero `command_status` code, ask the provider for more information.

* Check that the network is properly configured so the TCP connection can be made to the provider.

* Ask the provider to check that they properly added the IPs to the allowlist of the Adobe Campaign instance.

* Check **External account** settings. Ask the provider the value of the fields.

* If the connection is successful but unstable, check the [Issue with unstable connections](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) section.

* If connection issues are difficult to diagnose, a network capture can provide information. Make sure that the network capture runs simultaneously while the problem appears for it can be analyzed efficiently. You should also note the exact time at which the problem appears.

## Issues with unstable connection {#issues-unstable-connection}

A connection is considered unstable if any of the following happens:

* The connection lasts for less than 1 hour. Adobe Campaign Classic transmitter connections are an exception due to the way the Adobe Campaign Classic MTA works.

* The provider sends `UNBIND PDU`s.

* `enquire_link` times out, either on the Adobe Campaign side or on the provider side. You might see `ENQUIRE_LINK_RESP` with a non-zero error code in that case.

* There are a lot of `BIND PDU`s. There should not be more than a few during a day, depending on the number of connections. More than 1 BIND PDU per hour should be alerting.

How to fix connection stability problems:

* Unstable connections are rarely the root cause, it's often the result of another problem triggering a disconnect. Finding the root cause is the priority.

* Enable verbose SMPP traces. You will need them to see what is happening when the connection restarts.

* If the provider sends `BIND PDU`s, something might be wrong. Ask your provider why `UNBING` is sent.

* Taking a network capture is sometimes the only way to see how the connection is closed.

* If the provider closes the connections by sending either a `TCP FIN` or a `TCP RST packet`, ask your provider more information.

* If the provider closes the connection after sending a clean error such as `DELIVER_SM_RESP` with an error code, they must fix their connector otherwise that will prevent other kinds of messages from being transmitted and will trigger MTA throttling. This is especially important in transceiver mode where closing the connection impacts both MT and SR.

## Issue when sending a MT (regular SMS sent to an end-user){#issue-MT}

* Check that the connection is stable. An SMPP connection should stay up for at least 1 hour continuously except for transmitters on Adobe Campaign Classic. See the section [Issue with unstable connections](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* If restarting the MTA makes sending MT working again for a small period of time, you probably have throttling due to an unstable connection. See the section [Issue with unstable connections](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Check that the broad log is present and in the correct status with the correct dates. If it's not, this might be a delivery or delivery preparation issue.

* Check that the MTA actually processes the message. If it's not the case, this might not be a SMS issue.

* Check that the SMS connector is actually bound with the provider's equipment. Ask the provider for feedback to make sure all systems are communicating properly. See `BIND_TRANSMITTER` and `BIND_TRANSCEIVER PDU`s for information about the bind process. You may need to enable SMPP traces for proper troubleshooting.

* With the SMPP traces enabled, check that the `SUBMIT_SM PDU` is containing the right information.

* Check that the provider responds with a `SUBMIT_SM_RESP PDU` with a "OK" value (code 0). Make sure that the PDU arrives with a reasonable delay: anything longer than 1 second must be discussed with the provider, it usually arrives in less than 100ms.

* If all these steps work, you can be confident that the problem is on the provider side. They will have to do the troubleshooting on their platform.

* If it works but throughput is inconsistent, try adjusting the sending window and lowering the MT throughput. You will need to work with the provider to adjust that. Adobe Campaign can send messages very quickly so performance problems may arise on the provider's equipment.

## MT are duplicated (the same SMS is sent multiple times in a row){#duplicated-MT}

Duplicates are often caused by retries. It's normal to have duplicates when retrying messages, you should try instead to remove the root cause of retries.

* If you see duplicates sent exactly 60 seconds apart, it's probably a problem on the provider side, they don't send a `SUBMIT_SM_RESP` quickly enough.

* If you see many `BIND/UNBIND`, you have an unstable connection. See the[Issue with unstable connections](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) section for solutions before attempting to solve duplicate messages issues.

Lowering the amount of duplicates when there is a retry:

* Lower the sending window. The sending window should be big enough to cover for `SUBMIT_SM_RESP` latency. Its value represents the maximum number of messages that can be duplicated if an error happens while the window is full.

## Issue when processing SR (delivery receipts) {#issue-process-SR}

* You will need SMPP traces enabled to do any kind of SR troubleshooting.

* Check that the `DELIVER_SM PDU` is coming from the provider and that it is well formed.

* Check that Adobe Campaign replies with a successful `DELIVER_SM_RESP PDU` in a timely manner. On Adobe Campaign Classic, this guarantees that the SR has been inserted into the `providerMsgId` table for deferred processing by the SMS process.

If the `DELIVER_SM PDU` is not successfully acknowledged, then you should check the following:

* Check regex related to id extraction and error processing in the **External account**. You may need to validate them against the content of the `DELIVER_SM PDU`.

* Check that errors are properly provisioned in the `broadLogMsg` table.

If the `DELIVER_SM PDU` has been acknowledged by the Adobe Campaign Classic extended SMPP connector but the broadLog is not updated properly, check the ID reconciliation process described in the section [Matching MT, SR and broadlog entries](../../delivery/using/sms-protocol.md#matching-mt).

If you fixed everything but some invalid SR are still in the provider's buffers, you can skip them by using the "Invalid ID acknowledge count" option. This should be used with care and reset to 0 as quickly as possible after the buffers are clean.

## Issue when processing MO (and blacklisting/auto reply){#issue-process-MO}

* Enable SMPP traces during tests. If you don't enable TLS, you should do a network capture when troubleshooting MO to check that PDUs contain the correct information and are properly formatted.

* When capturing network traffic or analyzing SMPP traces, be sure to capture the whole conversation with the MO and its reply MT if a reply is configured.

* If the MO (`DELIVER_SM PDU`) doesn't appear in the traces, the problem is on the provider side. They will have to do troubleshooting on their platform.

* If the `DELIVER_SM PDU` appears, check that it's acknowledged by Adobe Campaign with a successful `DELIVER_SM_RESP PDU` (code 0). This RESP guarantees that all the processing logic has been applied by Adobe Campaign (auto reply and allow/denylist). If it's not the case, search for an error message in the SMS process logs.

* If automatic replies are enabled, check that the `SUBMIT_SM` has been sent to the provider. If not, it's guaranteed to find an error message in the SMS process logs.

* If the `SUBMIT_SM MT PDU` containing the reply is found in the traces but the SMS does not arrive to the mobile phone, you will have to contact the provider for assistance on troubleshooting.

## Issue during delivery preparation not excluding quarantined recipients (quarantined by the auto reply feature) {#issue-delivery-preparation}

* Check that the phone number format is exactly the same in the quarantine table and in the delivery log. If it's not, refer to this [section](../../delivery/using/sms-protocol.md#automatic-reply) if you are having issues with the plus prefix of the international phone number format.

* Check short codes. Exclusions can happen if the short code of the recipient is either the same as defined in the external account or if it's empty (empty = any shortcode). If only one short code is used for the whole Adobe Campaign instance, it's easier to leave all **short code** fields empty.

## Encoding issues {#encoding-issues}

**Step 1: Get in touch with the provider**

Contact them and see what's wrong with them. They should be able to tell you if the problem is on their side or on Adobe Campaign side. If the problem is in Adobe Campaign, they should be able to tell you exactly what field is incorrect.

**Step 2: Know what's in your message**

Unicode allows many variants for look-alike characters and Adobe Campaign cannot handle them all.

The most common source of problems is a copy-paste from a word processor, that changes usual characters to typographically correct versions: spaces changed to non-breaking spaces, double quotes changed to opening and closing quotes, minus signs changed to various kinds of hyphens , etc.

Don't copy-paste your message when testing, always type it directly in the interface.

With hexadecimal, you can tell the difference between similar characters. A lower-case L, a upper-case I, O, 0, all different types of quotes, non-latin encodings or even different types of spaces can all look the same or even not be displayed at all.

To convert unicode to hexadecimal, you can use online tools such as the [Unicode code converter](https://r12a.github.io/app-conversion/) website. Type in your text, make sure there is no PII such as phone numbers and click **Convert**. You will see the hexadecimal values at the bottom (UTF-32 zone).

When opening tickets about encoding problems, whether with the provider or [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), always include a hexadecimal version of what you type and what you see.

**Step 3: Know what you should send**

Determine the encoding you expect to be used and search online for its character table. Check that the characters you intend to send are actually available in the target code page. Check that the `data_coding` field is correct and matches what you and the provider expect.

**Step 4: Know what you actually sent**

You will need the debug output of the connector in order to see exactly what bytes you send to the provider. Encoding problems appear in `SUBMIT_SM PDU`s, so be sure to capture them. Send very distinct messages that are easy to find in the log.

Send different kinds of special characters when testing. For example, GSM7 encoding has extended characters that are very distinct in their hexadecimal form, they are easy to spot since they don't appear in any other encoding.

## Elements to include when communicating about a SMS issue {#element-include}

Whenever you seek assistance on a SMS issue, whether it's opening a support ticket to Adobe Campaign, to the SMS provider, or any kind of communication about the issue, you will need to include the following information to be sure that it will be properly qualified. Properly qualified issues are key to solving problems faster.

* **Enable verbose SMPP messages** when the problem appears. Most SMS problems are impossible to solve without this.

* If the problem is related to SMS traffic, contact the provider first. Their platform is best suited for efficient diagnosis of SMS traffic problems in real time.

* Include a brief but factual description of the problem.

* Include a description of the expected result.

* Include the feedback from the provider.

* Include relevant logs and/or network captures. When doing captures, make sure to reproduce the problem during the capture.

* If you include logs, traces or captures, pinpoint the exact location in the file when the problem appears.

* If you reference messages, PDUs or logs, clearly state their timestamp to make them easier to find.

* Try to reproduce the problem on a test environment. If you are unsure about a setting, try it on the test environment and check the result with the SMPP traces. It's usually better to report problems replicated on test environments than directly reporting problems on production environments.

* Include any change or tweaks made on the platform. Also, include any change that the provider may have done on their side.

### Network capture {#network-capture}

A network capture is not always needed, usually verbose SMPP messages are enough. Here are some guidelines that will help you determine if a network capture is needed:

* Connection issues, but the verbose messages don't show any `BIND_RESP PDU`.

* Unexplained disconnections with no error message, the usual behavior of the connector when it detects a low-level protocol error.

* The provider complains about the unbind/disconnection process.

* Encoding issues in optional TLV fields.

* Traffic is suspected to be mixed between different connections.

In all other situations, try to analyze verbose SMPP messages first and request a network capture only if information is missing in the verbose logs.

In some cases, capturing network traffic is not needed. Here are the most common situations:

* TLS enabled: By definition, TLS traffic is encrypted so it cannot be captured.

* Performance issues: Logs contain all the needed information to trace performance issues.

* Timing issues (`retry timing`, `enquire_link` period, throughput capping,etc.)

* SR parsing and processing: verbose logs give much more context and a better presentation.

* MO processing (automatic replies, quarantine).

* Errors not involving actual SMPP traffic: Delivery preparation, Message Center API issues, workflow issues, etc.

## Enabling SMPP traces {#enabling-smpp-traces}

New connector supports extended logging through traces: SMPP. Traces are output in the MTA log, not on the standard output.

**Enabling per external account (preferred method)**

1. In the **External account**, check **Enable verbose SMPP traces in the log file**.
1. Wait 10 minutes to let the server reload external accounts.

It should be active now.

**Enabling in configuration**

In the `config-instance.xml` file, set the following parameters:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Checking the number of open connections on a container {#open-connections}

To check the number of open connections on a container, you can use this command:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

This will list the number of connections opened for a given port. Here we are using the port 3600.

Result should be as follows:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 opened connections for the sms process and 2 per mta child with 5 children.
