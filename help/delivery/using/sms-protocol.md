---
product: campaign
title: SMS connector protocol and settings
description: Learn more on the SMS connector and how to configure it
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# SMS connector protocol and settings {#sms-connector-protocol}

>[!NOTE]
>
>Through this document, all references to details about the protocol, field names and values refer to the [SMPP 3.4 specification](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

As part of the transition from Campaign v7 to v8, the Campaign Classic documentation set has been streamlined and reorganized. Common features are now available exclusively in the Campaign v8 documentation set. To learn more about SMS connector settings, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

## Overview {#overview}

SMS might be limited to sending short text messages with no formatting but its simplicity makes it a valuable communication channel.

There are two main ways to send an SMS:

* Send it manually from a phone, the usual way to communicate directly between people.
* Send it from the internet, the way Adobe Campaign send messages. For that, you need a SMS service provider that connects the internet to the mobile network.
Adobe Campaign uses the SMPP protocol to send SMS to a service provider.

This document will walk you through the connection set up between Adobe Campaign and a SMPP provider.

SMPP providers can sometimes deviate from the official specification but the SMS connector in Adobe Campaign provides many options to adapt its behavior for it to be compatible with most providers.

>[!IMPORTANT]
>
>Setting up a connection to a new provider may require some technical skills, knowledge of TCP, binary, hexadecimal representation and text encodings. It will also require active cooperation with the provider.

## SMPP protocol {#smpp-protocol}

Adobe Campaign Classic supports the SMPP protocol version 3.4. This is a widespread protocol that allows sending SMS to a provider (SMSC) and receiving SMS as well as receipts. For more on this, refer to the [SMPP documentation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

The network equipment on the SMS service provider side is often called the SMSC.

### SMPP connections {#smpp-connections}

Adobe Campaign connects to the network equipment of the SMS service provider via TCP. The SMPP protocol sets permanent TCP connections from Adobe Campaign to the provider. TCP connections are always initiated by Adobe Campaign, even to receive messages.
SMPP opens 1 or 2 TCP connections, depending on its mode. All connections are always initiated by Adobe Campaign.

The SMPP protocol can work in two modes:

* **Transmitter+receiver (or TX+RX)**: two separate TCP connections are used for transmitting and receiving messages.
* **Transceiver (or TRX)**: a single TCP connection is used for transmitting and receiving messages.

>[!NOTE]
>
> Adobe Campaign Classic only supports the TX+RX mode. This limitation is due to its technical architecture.

### SMPP PDU {#smpp-pdu}

SMPP transmission units ("packets") are called PDUs. A **PDU** contains a command, a status, a sequence number and data.

Each PDU must be acknowledged by an `SMPP RESP PDU` (synchronous response). Requests may be pipelined: the sender can send many commands without waiting for `RESP`, the number of requests that may be pipelined at any time is called the window. `RESP PDU` may arrive in any order, unrelated to the order of their corresponding initiator PDU.

In the separated **Transmitter+receiver** mode, the connection used depends on the kind of message transmitted. The transmitter connection is used for MT, and the receiver connection is used for MO and SR. Requests and responses for each kind of message are sent over the same TCP connection.

For example, when sending an MT, the transmitter connection is used and the `RESP` that acknowledges the MT is also sent through the transmitter channel. When you receive an MO (or an SR), the receiver connection is used to receive the MO and to send the `RESP` that acknowledges the MO.

![](assets/do-not-localize/sms_protocol_1.png)

In Adobe Campaign Classic, to link SR with their corresponding MT, an ID is returned by the SMSC with the `SUBMIT_SM_RESP` and `DELIVER_SM` steps. The identifier is stored in the `providerId` field of the `nms::providerMsgId` table and is linked to `broadLogId` and `deliveryId`. This matching operation is done by the SMS process when writing to the database.

A successful `SUBMIT_SM_RESP PDU` triggers the "sent" message status in the sending log while a successful `DELIVER_SM (SR) PDU` triggers the "received" message status.

### Security aspects {#security-aspects}

The protocol itself is not encrypted. Most providers implement a variant of IP on allowlist so Adobe Campaign server IP addresses have to be declared to the provider.

Adobe Campaign supports passing a login and a password during the bind phase. It also supports SMPP over TLS. It should be noted that certificates are required for proper security. While the SMPP connector allows bypassing certificate checks, it should only be used for testing since TLS without certificates provides a significantly lower level of security.

The connector uses the default certificates provided by the system `openssl` library. Usually it's provided by the `/etc/ssl/certs` directory on Debian. This directory is provided by the "ca-certificates" package by default but it may be customized.

### Information in each kind of PDU {#information-pdu}

Each kind of PDU has distinct fields that carry different pieces of information. These PDU are detailed in the [SMPP 3.4 specification](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Each section below describes both the PDU and its synchronous response (`*_RESP PDU`). All PDUs must be acknowledged by a corresponding `RESP`, this is a mandatory part of the specification.

PDUs can have optional fields. Only the most common fields are described here. Refer to the [SMPP 3.4 specification](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) for more information.

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

This PDU is used to initiate a connection to the SMSC. **Transmitter**, **Receiver** and **Transceiver** modes only change the kind of SMS allowed to be transferred over this connection, specifically:

| Mode | Kinds of SMS allowed  |
|:-:|:-:|
| Transmitter | MT |
| Receiver | MO + SR |
| Transceiver | MT + MO + SR |

Notable fields in a `BIND_* PDU`:

* **system_id**: Login used for authentication. Set in the external account.

* **password**: Password used for authentication. Set in the external account.

* **system_type**: Required to be set at a specific value for some providers. Set in the external account, available in all versions. Often distinguishes between different types of contracts, channels, countries, etc.

* **addr_ton** and **addr_npi**: Required by some providers. Set by the `Bind TON` and `Bind NPI` settings in the external account.

* **address_range**: Required by some providers. Most of the time, this is a list of shortcodes allowed on this connection. Set in the external account.

`BIND_*_RESP` has no specific field, it confirms whether the connection was successful or not.

#### UNBIND {#unbind}

This PDU must be sent by the system before disconnecting. It must wait the matching `UNBIND_RESP` PDU before closing the connection.

Conforming SMSC must not close the connection, the TCP connection is controlled by the Adobe Campaign connector.

#### SUBMIT_SM {#submit-sm}

This PDU sends a MT to the SMSC. Its response PDU gives the ID of the MT.

Notable fields in a `SUBMIT_SM` PDU:

* **service_type**: required by some providers. Set in the delivery properties.

* **source_addr_ton** and **source_addr_npi**: indicates what kind of source address is transmitted. The meaning of these fields is standardized, but since some providers use it differently, you should ask the provider for its correct value. Set in the external account.

* **source_addr**: the source address / oADC of the MT. It will be displayed on the mobile phone. Set in the external account and the delivery, the value in the delivery takes precedence over the value of the external account.

* **dest_addr_ton** and **dest_addr_npi**: indicates what kind of destination address is transmitted (e.g. local or international format). The meaning of these fields is standardized, but since some providers use it differently, you should ask the provider for its correct value. Set in the external account.

* **destination_addr**: recipient address, phone number or MSISDN.

* **esm_class**: used to tell if UDH is used or not in the text field. Enabled automatically by the connector for split SMS if the `message_payload` mode is not used.

* **priority_flag**: priority of this message over others. This is tied to the priority of the delivery itself.

* **validity_period**: timestamp after which no retry should be attempted. Set in the delivery itself.

* **registered_delivery**: tells whether a SR is requested or not. Adobe Campaign always sets this flag except for automatic replies. For multipart messages, the flag is only set for the first part. All versions have the same behavior.

* **data_coding**: indicates the encoding used in the text field. See the [SMS text encoding](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"} (Campaign v8 documentation) section for more information.

* **short_message**: the text of the message. If UDH is used, this also contains the UHD header.

Adobe Campaign supports these optional fields:

* **dest_addr_subunit**: used to specify the target of the SMS: flash, mobile or SIM card. Set in the delivery properties.

* **message_payload**: when enabled in the external account, long messages will be sent in a single PDU and the text will be transmitted in this field rather than the `short_message` field.

#### SUBMIT_SM_RESP {#submit-sm-resp}

This PDU will contain the ID of the MT. This is useful to match it with incoming SR.

>[!IMPORTANT]
>
>Many providers transmit the MT ID in hexadecimal. Make sure that you set the **ID format in MT acknowledgement** setting correctly in the external account.

Some providers send `SUBMIT_SM_RESP` after sending the SR. To account for that behavior, Adobe Campaign waits 30 seconds before replying **Invalid message ID** to a SR with an unknown ID.

#### DELIVER_SM {#delivery-sm}

This PDU is sent by the SMSC to Adobe Campaign. It contains either a MO or a SR.

Most fields have the same meaning as their `SUBMIT_SM` counterpart. Here is the list of useful fields:

* **source_addr**: source address of the MO/SR. Usually this is a phone number.

* **destination_addr**: short code that received the MO or the SR.

* **esm_class**: used to tell if the PDU is a MO or a SR.

* **short_message**: text of the message. For SR, this contains data described in the Appendix B of the SMPP protocol specification. See [SR error management](sms-protocol.md#sr-error-management) for more details.

Adobe Campaign is able to read message ID in the `receipted_message_id` optional field with some configuration.

#### DELIVER_SM_RESP {#deliver-sm-resp}

This PDU is sent by Adobe Campaign to acknowledge SR and MO.

Adobe Campaign Classic acknowledges SR and MO once they have been inserted into the database. Some processing errors can happen even if a successful `DELIVER_SM_RESP` PDU has been sent. This limitation is caused by the software architecture of Adobe Campaign Classic.

#### ENQUIRE_LINK {#enquire-links}

This PDU is only used to check that the connection is live. Its frequency should be set according to the provider's needs.

The default 60 seconds should match most configurations set in the external account.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

This PDU acknowledges that the connection is alive.

### Multipart SMS (long SMS) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign only supports multipart SMS or long SMS for sending. UDH and `message_payload` are not supported for incoming SMS (MO), meaning that MO are limited to 160 characters.

### Throughput capping and windowing {#throughput-capping}

Most providers require a throughput limit for each SMPP connection. This can be achieved by setting a number of SMS in the external account. Note that throughput throttling happens per connection, the total effective throughput is the limit per connection multiplied by the total number of connections. This is detailed in the [Simultaneous connections](sms-protocol.md#connection-settings) section.

To reach maximum possible throughput, you will need to fine tune the maximum sending window. The sending window is the number of `SUBMIT_SM PDU`s that can be sent without waiting for a `SUBMIT_SM_RESP`. See the [Sending window setting](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"} (Campaign v8 documentation) section for more details.

### SR and error management ("Appendix B") {#sr-error-management}

The SMPP protocol defines standard synchronous errors in `RESP PDU`s, but it does not define error codes for SR. Each provider uses their own error codes with their meaning.

A recommendation is made in the Appendix B section of the [SMPP protocol specification](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (page 167), but this does not list the actual error codes nor their meaning.

To adapt to error management, the broadlog message system of Adobe Campaign has been leveraged to properly provision errors and their severity (hard, soft, etc.).

As mentioned above, there are two different kinds of errors:

* synchronous replies in the `SUBMIT_SM_RESP` that happen immediately after the message was sent to the SMSC
* receipts that may come much later when the mobile received the message or when the message timed out. In that case the error is found in a SR.

When a SR is received, status and error can be found in its `short_message` field (example for Appendix B conforming implementations). The `short_message` field of the PDU is often called the **text field** since it contains text in MT. In case of SR, it contains technical information plus a sub-field named **Text**. These 2 fields are different and `short_message` actually contains the **Text** field and other information.

Adobe Campaign Classic connectors (except Extended SMPP) use a hardcoded behavior that depends on the selected provider. Generic SMPP only distinguishes between success and error, with no detail. Delivery log may contain some information which is not guaranteed.

#### SR text field format {#sr-text-field-format}

The specification recommends using this format for the SR text field. It is a list of subfields, space-separated with a colon to separate the field name and its value. Field names are case insensitive.

Example of a SR text field matching the Appendix B recommendation:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

The id field is the ID received in the `SUBMIT_SM_RESP PDU`, the acknowledge of the MT.

`sub` and `dlvrd` are supposed to count the amount of delivered parts and delivered messages, but this is not used by Adobe Campaign since the broadlog system gives a better, and more integrated information.

`submit date` and `done date` fields are indicative timestamps of when the MT was sent and when the SR was sent by the mobile. Expect some problems with time zones or even wrong timestamps given by mobiles with incorrect date set.

The stat field is important since it tells the status of the message. The only important status are `DELIVRD`, `UNDELIV` and `REJECTD`. The `DELIVRD` status indicates a success, the other two indicate an error. Other values are possible, but they are usually intermediate notifications e.g. the MT reached the mobile carrier, but not the mobile phone. These intermediate notifications are ignored by Adobe Campaign.

The err field contains the provider-specific error code. The provider has to give a table of possible error codes along with their meaning to be able to interpret this value.

Finally, the text field usually contains the beginning of the text of the MT. This is ignored by Adobe Campaign and some providers don't transmit it to avoid PII leakage and network bandwidth consumption. It can be used during troubleshooting to spot the SR matching a test MT more easily by reading this field.

### Example of SR processing in Adobe Campaign Classic Extended generic SMPP {#sr-processing}

This example displays the case of an implementation following the Appendix B recommendation, default values in the external account, and a successful SMS MT.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

First, the `id extraction` regex is applied to extract the ID and reconcile it with the corresponding MT.

Then, the `status extraction` regex and `error code extraction` regex are applied to extract these fields and are appended to the string.

The broadlog message is constructed with this information, and the original unaltered string is appended for reference:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

The message is then normalized, removing the MESSAGE part to be able to match multiple messages with the same stat and err codes.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

If the message is not already provisioned in the broadlog message table, a new entry will be created, using the whole message as **firstText** and the normalized message. Then, the connector uses the success and `error` regex to determine if it was a success or a failure:

* If it matches the `success` regex, it will be considered as a success.

* If it matches the `error` regex, the message is qualified as an error.

* If none of these two regex match, the SR is ignored. It might be an intermediate notification, which is not handled by Adobe Campaign.

By default, all errors are provisioned as soft errors. This means that hard errors must be provisioned by hand.

## SMPP external account parameters {#SMPP-parameters-external}

Each implementation of the SMPP protocol has many variations. To improve compatibility and adaptability, many settings are available to change the behavior of the SMPP connector. This section describes every parameter and its effects on the connector.

### General parameters and routing {#general-parameters-routing}

**Limit MTA instances for this account**

It is possible to set a limit to the number of MTA instances allowed to connect to the SMPP provider. When checked, you can specify how many MTAs can be used at most.

This option allows finer control over the number of connections, see [Simultaneous connections](sms-protocol.md#connection-settings).

If you set a value higher than the number of running MTAs, all MTAs will run as normal: this option is only a limit and cannot spawn additional MTAs.

If you need to precisely control the number of connections, e.g. provider requirement, it is recommended to always set this option even if the current deployment has the right number of MTAs running. If additional MTAs are added afterwards, the connection limit will still be respected.

### Connection settings {#connection-settings}

#### SMSC implementation name {#smsc-implementation-name}

Sets the name of the SMSC implementation. It should be set to the name of your provider. Contact the administrator or the deliverability team to know what to add in this field. The role of this field is described in the [SR error management](sms-protocol.md#sr-error-management) section.

>[!NOTE]
>
>Engagement of Deliverability team is based on contract, and customers should contact their Adobe representative for information related to Deliverability engagement.

#### Number of MTA child connections {#number-mta-child}

In Adobe Campaign Classic, it defines the number of connections per MTA child.

The Adobe Campaign Classic Extended SMPP connector can control the number of connections per MTA child. To control the global limit of connections, you will have to limit the number of MTA child processes, which often means having a dedicated mid-sourcing platform for SMS.

For Adobe Campaign Classic, there can be a different number of receiver and transmitter connections:

* **Transmitter connections = Number of MTA child connections * number of MTA child processes * number of MTAs (if auto-reply is set) * number of MTA child connections**
 
As suggested above, the Adobe Campaign Classic SMS process opens more transmitter connections if auto-reply is enabled. These extra connections are used to send the automatic replies.

* **Receiver connections = Number of MTA child connections**

If you set up automatic replies, the SMS process will open transmitter/receiver pairs, increasing the number of transmitter connections. If you did not set up any automatic reply, it will open only receiver connections.

#### Enable TLS over SMPP {#enable-TLS}

Use TLS to connect to the provider. The connection will be encrypted. The TLS connection is managed by the OpenSSL library anything applicable to OpenSSL will be true for this connection.

#### Enable verbose SMPP traces in the log file {#enable-verbose-log-file}

This setting dumps all SMPP traffic in log files. It's often required to adjust parameters during initial setup. This must be enabled when troubleshooting the connector and compared to the traffic seen by the provider.

In Adobe Campaign Classic, log output is in the MTA log for MT-related traffic and in the SMS log for MO and SR-related traffic.

### Receiver connection setting {#receiver-connection}

This section is only visible in separated **transmitter+receiver** mode.

#### Use different parameters for the receiver {#receiver-parameters}

When the box is unchecked, the same settings are used for transmitter and receiver.

When the box is checked, settings in the **Connection settings** section will apply to the transmitter and settings in the **Receiver connection** settings will apply to the receiver.

**Receiver server, port, account, password, system type**

These settings apply to the receiver when in transmitter+receiver mode. They work like the transmitter part, see above for more details.

### SMPP channel settings {#smpp-channel-settings}

#### Store incoming MO in the database {#incoming-mo-storing}

When enabled, incoming MO will be stored in the inSMS table of the database. This table can be queried using the query activity of any workflow.

Adobe Campaign Classic always stores all MOs in the inSMS database so this option is not available.

#### Enable Real-time KPI updates during SR processing {#real-time-kpi}

When enabled, KPIs will be updated in real-time on the main delivery page when receiving error SR.

The drawback can be low performance because of the database contention it generates. If disabled, statistics are updated by the **syncfromexec** workflow, running every 20 minutes.

Adobe Campaign Classic has an entirely different mechanism for KPIs so this option is not available.

#### Short code {#short-code}

Indicates the main short code of the account. If multiple short codes are used for this account or if the short code is unknown, leave this field empty.

Specifying short code is helpful for two features:

* The preview will display the short code if no source number is provided. It will reflect the real behavior on the mobile phone.

* The denylist setting of the auto reply feature only sends to quarantine the user for a specific short code.

### SMSC specifics {#SMSC-specifics}

These settings are advanced settings which adapt the Adobe Campaign connector to most SMPP implementation peculiarities.

#### Skip TLS certificate check {#skip-tls}

When TLS is enabled, skip all certificate checks.

When checked, the connection is not secure anymore, it should not be enabled in production.

It can useful for debugging or test purposes.

You can choose between three different values for the certificate validation:

* Full certification check (including the hostname), default.
* Skip the hostname verification.
* Skip the certificate verification.

#### Regex applied to determine successful/error status {#regex-applied}

When messages with an unknown stat/err field combination are encountered, these regex are applied on the stat field to determine whether the SR was a success or an error. SR with stat values that don't match any of these regexes are ignored.

By default, stat values that begin with `DELIV`, e.g. `DELIVRD` in the [Appendix B](sms-protocol.md#sr-error-management), will be considered as successfully delivered and all stat values that match errors, e.g. `REJECTED`, `UNDELIV`, are considered errors.

#### ID format in MT acknowledgement {#id-format-mt}

This indicates the format of the ID returned in the `message_id` field of the `SUBMIT_SM_RESP PDU`.

* **Do not modify**: The ID is stored as-is in the database, as ASCII-encoded text. No pre-processing nor filtering occurs.

* **Decimal number**: The ID is expected to be a decimal number in ASCII form. Leading and trailing spaces and leading zeros are removed when this setting is used.

* **Hexadecimal number**: The ID is expected to be a hexadecimal number in ASCII form, with no leading 0x nor trailing h. The ID is then converted to a decimal number before being stored in the database.

* **Hexadecimal string**: The ID is expected to be an ASCII-encoded text that is itself a string of bytes encoded as hexadecimal. For example, in the PDU you will find `0x34 0x31 0x34 0x32 0x34 0x33`, which translates to ASCII "414243". This string is then decoded as a hexadecimal string of bytes and you obtain "ABC" as a result: you will store the ID "ABC" in the database.

#### ID format in SR {#id-format-sr}

This indicates the format of the ID captured by the `Extraction` regex of the ID in the SR. Values have the same meaning and the same behavior as the format in MT above.

**SR ID or error code in optional field**

>[!NOTE]
>
>Only available in the Adobe Campaign Classic Extended SMPP connector.

If checked, the content of optional fields will be appended to the text processed by regexes above. The text will have the format `0xTAG:VALUE`, `0xTAG` being the 4-digit hexadecimal value of the tag in upper case e.g. `0x002E`.

For example, you might want to capture the ID in the `receipted_message_id` field. For this, enable this checkbox and the following text will be added to the status:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

In this example, 0x001E is the tag of the optional field and the UUID is the value of the field.

In order to capture this value, you may now set the following regex in the Extraction regex of the ID in the SR field:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>You can only capture optional fields that have text (ASCII/UTF-8) values. Specifically, binary fields cannot be captured reliably with the current regex system.

**Service ID tag**

Allows to add a custom TLV. This field sets the tag portion. The value can be customized per delivery in the **Service or program ID** value in the advanced parameters of the delivery.

This setting only allows adding one TLV option per message.

### Automatic reply sent to the MO {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic and in a hybrid architecture, applying auto-reply for the extended SMPP connector requires to add write access for the mid operator on the **External account** folder.

This feature allows to quickly reply text to MO and handle per-short code sending to denylist.

The **Keyword** and **Short code** columns define conditions to trigger the auto reply. If both fields match, the MO is sent and the additional action is triggered. To specify a wildcard, you should leave the field empty. Keyword matches against the first alphanumeric word in the MO text, ignoring punctuation and leading spaces. It means that the **Keyword** field cannot contain spaces and must be a single word.

The **Keyword** setting is a prefix. For example, if you specify "AD", it will match "AD", "ADAPT" and "ADOBE". If you have multiple keywords with a common prefix, you need to pay attention to the order since keywords are processed from top to bottom.

The **Reply** column is the text to reply. No personalization is available in this field. If you leave this field empty, no message will be replied but the additional action will be triggered anyway.

The **Additional action** column provides an extra action when both **Keyword** and **Short code** match, empty short code matches all short codes. You can send to quarantine or remove from quarantine, value none replies to the text. If you specify an **Additional action** but leave the **Reply** field empty, the action will be executed but no reply will be sent. Quarantine is applied only for the specified short code, or all short codes if the field is left empty.

>[!IMPORTANT]
>
>The send full phone number setting has an impact on the behavior of automatic reply quarantine mechanism: if send full phone number is not checked, the phone number put in quarantine will be prefixed by a plus sign ("+") to make it compatible with the international phone number format.

All entries in the table are processed in the specified order, until one rule matches. If multiple rules match a MO, only the topmost rule will be applied.

## SMS delivery template parameters {#sms-delivery-template-parameters}

Some parameters may be set per delivery template.

### Delivery parameters {#delivery-parameters}

#### Transmission mode {#transmission-mode}

This field indicates the kind of SMS you wish to transfer: normal or flash messages, storing on the mobile or the SIM card.

This setting is transmitted in the `dest_addr_subunit` optional field in the `SUBMIT_SM PDU`.

* **Unspecified** sends no optional field in the PDU.

* **Flash** sets the value to 1. It sends a flash message that pops up on the mobile and is not stored in memory.

* **Normal** sets the value to 0. It sends a normal message.

* **Save on mobile** sets the value to 2. It tells the phone to store the SMS in internal memory.

* **Save on terminal** sets the value to 3. It tells the phone to store the SMS in the SIM card.

#### Validity period {#validity-period}

The validity period is transmitted in the `validity_period` field of the `SUBMIT_SM PDU`. The date is always formatted as an absolute UTC time format, the date field will end with "00+".

## Extended generic SMPP connector {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Arrows represent data flows.

When sending delivery parts, the MTA spawns MTA children. The number of MTA child processes is dynamic and depends on a configuration in serverConf.xml. Each MTA child instantiates the connector `CSmppConnectorWorker` which connects to the SMPP provider. Connections are kept alive as long as the MTA child is kept alive, also configurable in serverConf.xml.

The SMS process only processes SR, it connects to the provider and leaves the connection open. The process reconnects every 10 minutes to reload new settings, this is normal operation.

### Matching MT, SR and broadlog entries {#matching-mt}

An intermediate table `nmsProviderMsgId` is used to store MT and SR data temporarily before being committed asynchronously to the broadlog.

`nmsProviderMsgId` table has 3 groups of columns:

* Columns updated when a MT is sent and acknowledged: `iBroadLogId`, `iDeliveryId`

* Columns updated when a SR is received: `iMsgId`, `iStatus`

* Columns that are always updated: `tsCreated`, `sProviderId`

When both MT and SR finished processing, you should have complete lines, with both broadlog information and status information.

Here, `iMsgId` is linked to `nmsBroadLogMsg` table, indicating the full status/error message.

The SMS process checks for complete lines every minute, then processes them asynchronously:

* The complete line is read.
* SMS process computes the name of the broadlog table based on the delivery mapping.
* SMS process updates the broadlog table with the message ID and the status.

**Throughput and parallel connections**

Each MTA child creates a configurable amount of connections, so limiting the number of MTA child will limit the number of connections. Because the correlation between MTA child processes and traffic is correlated, this can be somewhat controlled but still a bit unpredictable.
