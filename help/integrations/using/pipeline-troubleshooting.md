---
title: Configuring the integration
seo-title: Configuring the integration
description: Configuring the integration
seo-description: 
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
---

# Pipeline troubleshooting {#pipeline-troubleshooting}

**Pipelined fails with error "No task corresponds to the mask pipelined@"**

Your version of Adobe Campaign Classic does not support the pipeline.

1. Check if the [!DNL pipelined] element is present in the config file. If not, it means it's not supported.
1. Upgrade to version 6.11 build 8705 or later.

**Pipelined fails with '' aurait dû commencer par `[` ou `{` (iRc=16384)"**

The **NmsPipeline_Config** option is not set. It's actually a JSON parsing error.
Set the JSON config in the option **NmsPipeline_Config**. See "routing option" in this page.

**Pipelined fails with "the subject must be a valid organization or client"**

The IMSOrgid configuration is not valid.

1. Check that the IMSOrgId is set in the serverConf.xml.
1. Look for an empty IMSOrgId in the instance config file that can override the default. If so, remove it.
1. Check that the IMSOrgId matches that of the customer in the Experience Cloud.

**Pipelined fails with "invalid key"**

The @authPrivateKey parameter of the instance config file is incorrect.

1. Check that the authPrivateKey is set.
1. Check that the authPrivateKey: starts with @, ends with =, and is about 4000 characters long.
1. Look for the original key and check that it is: in RSA format, 4096 bits long, and starts with -----BEGIN RSA PRIVATE KEY-----.
<br> If necessary, re-create the key and register it on Adobe Analytics. Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Check that the key was encoded within the same instance as [!DNL pipelined]. <br>If necessary, redo the encoding using the sample JavaScript or workflow.

**Pipelined fails with "unable to read the token during authentication"**

The private key has an invalid format.

1. Run the steps for key encryption on this page.
1. Check that the key is encrypted on the same instance.
1. Check that the authPrivateKey in the config file matches the generated key. <br>Make sure to use OpenSSL to generate the key pair. PuttyGen for example, does not generate the proper format.

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
Annexes

**How to use the Key encryption JavaScript**

Run a JavaScript to encrypt the private key. It is required for the pipeline configuration.

Here is a code sample that you can use to run the cryptString function:

```

/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))

```

On the server, execute the Javascript:

```

nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js

```

Copy and paste the encoded key from the output to the console.