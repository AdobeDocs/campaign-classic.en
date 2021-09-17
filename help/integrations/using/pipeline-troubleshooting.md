---
product: campaign
title: Configuring the integration
description: Configuring the integration
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
---
# Pipeline troubleshooting {#pipeline-troubleshooting}

![](../../assets/common.svg)

**Pipelined fails with error "No task corresponds to the mask pipelined@<&nbsp;instance&nbsp;>"**

Your version of Adobe Campaign Classic does not support the pipeline.

1. Check if the [!DNL pipelined] element is present in the config file. If not, it means it's not supported.
1. Upgrade to Campaign 20.3 or [!DNL Gold Standard] 11.

**Pipelined fails with '' aurait dû commencer par `[` ou `{` (iRc=16384)"**

The **NmsPipeline_Config** option is not set. It's actually a JSON parsing error.
Set the JSON config in the option **NmsPipeline_Config**. See "routing option" in this page.

**Pipelined fails with "the subject must be a valid organization or client"**

The Organization identifier configuration is not valid.

1. Check that the IMSOrgId is set in the serverConf.xml.
1. Look for an empty IMSOrgId in the instance config file that can override the default. If so, remove it.
1. Check that the IMSOrgId matches that of the customer in the Experience Cloud.

**Pipelined fails with "invalid key"**

The @authPrivateKey parameter of the instance config file is incorrect.

1. Check that the authPrivateKey is set.
1. Check that the authPrivateKey: starts with @, ends with =, and is about 4000 characters long.
1. Look for the original key and check that it is: in RSA format, 4096 bits long, and starts with `-----BEGIN RSA PRIVATE KEY-----`.
<br> If necessary, re-create the key and register it on Adobe Analytics.
1. Check that the key was encoded within the same instance as [!DNL pipelined]. <br>If necessary, redo the encoding using the sample JavaScript or workflow.

**Pipelined fails with "unable to read the token during authentication"**

The private key has an invalid format.

1. Run the steps for key encryption on this page.
1. Check that the key is encrypted on the same instance.
1. Check that the authPrivateKey in the config file matches the generated key. <br>Make sure to use OpenSSL to generate the key pair. PuttyGen for example, does not generate the proper format.

**Pipelined fails with "is no longer allowed to get access token"**

The logs should be as follows:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

This error message means that the authentication is configured using the legacy Omniture base OAuth. Refer to the [Configuring Adobe I/O for Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) documentation to upgrade your authentication.

**No triggers are retrieved**

When the [!DNL pipelined] process is running and no triggers are retrieved:

1. Make sure that the trigger is active in Analytics and is generating events.
1. Make sure that the [!DNL pipelined] process is running.
1. Look for errors in the [!DNL pipelined] log.
1. Look for errors in the [!DNL pipelined] status page. trigger-discarted, trigger-failures should be zero.
1. Check that the trigger name is configured in the **[!UICONTROL NmsPipeline_Config]** option. If there is a doubt, use the wildcard option.
1. Check that Analytics has an active trigger and is generating events. There could be a delay of a few hours after the configuration is made in Analytics before it's active.

**Events are not linked to a customer**

When some events are not linked to a customer:

1. Check that the reconciliation workflow is running, if applicable.
1. Check that the event contains a customer ID.
1. Make a query on the customer table using the customer ID.
1. Check the frequency of the customer import. New customers are imported into Adobe Campaign with a workflow.

**Latency in events processing**

When the Analytics timestamp is much older than the creation date of the event in Campaign.

Generally, a trigger can take 15-90 minutes to launch a marketing campaign. This varies depending on the implementation of data collection, load on the pipeline, custom configuration of the defined trigger, and the workflow in Adobe Campaign.

1. Check if the [!DNL pipelined] process has been running.
1. Look for errors in pipelined.log that can cause retries. Fix the errors, if applicable.
1. Check the [!DNL pipelined] status page for the queue size. If the queue size is large, improve the performance of the JS.
1. Since a delay seems to increase with volume, configure the triggers on Analytics using fewer messages.

**Upgrading stage instances from legacy authentication to Adobe IO authentication**

Changing the integration authentication on your stage instance will not affect the configuration of your production instance. You can choose to upgrade your stage instance then update the authentication to Adobe IO and test your triggers on your stage instance. 

Your production instance will continue to use the legacy authentication and will be unaffected by this change.
