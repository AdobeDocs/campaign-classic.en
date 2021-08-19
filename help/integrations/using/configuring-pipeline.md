---
product: campaign
title: Configuring the pipeline
description: Learn how to configure the pipeline
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
---
# Configuring pipeline {#configuring-pipeline}

![](../../assets/common.svg)

Authentication parameters such as the customer ID, the private key, and the authentication endpoint are configured in the instance configuration files.
The list of triggers to be processed is configured in an option in JSON format.
The triggers are used for targeting by a campaign workflow that sends emails. The campaign is set up so that a customer that has both trigger events receives an email.

>[!CAUTION]
>
>In case of Hybrid deployment, ensure that pipeline is configured on a mid-instance.

## Prerequisites {#prerequisites}

Before starting this configuration, please check you are using:

* Minimum, one of the following Adobe Campaign builds:
  * 19.1.8.9039
  * 19.1.4.9032 - Gold Standard 11
  * 20.2.4.9187
  * 20.3.1 
* Adobe Analytics Standard version

You will also need:

* Adobe I/O project authentication
* a valid IMSOrgID, the identifier of the Experience Cloud customer with Adobe Analytics added
* a Developer access to the IMS Org
* triggers configuration done in Adobe Analytics

## Authentication and configuration files {#authentication-configuration}

Authentication is required since pipeline is hosted in the Adobe Experience Cloud.
It uses a pair of public and private keys. This process has the same function as a user/password but is more secure.
Authentication is supported for the Marketing Cloud via Adobe I/O Project.

## Step 1: Creating/updating Adobe I/O Project {#creating-adobe-io-project}

For Hosted customers, you can create a customer care ticket to enable your organization with Adobe I/O Technical Account Tokens for the Triggers integration.

For On Premise customers, refer to the [Configuring Adobe I/O for Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) page. Note that you need to select **[!UICONTROL Adobe Analytics]** while adding API to the Adobe I/O credential.

## Step 2: Configuring NmsPipeline_Config pipeline option {#configuring-nmspipeline}

Once the authentication is set, pipeline will retrieve the events. It will only process triggers that are configured in Adobe Campaign. The trigger must have been generated from Adobe Analytics and pushed to the pipeline which will only process triggers that are configured in Adobe Campaign.
The option can also be configured with a wildcard in order to catch all triggers regardless of the name.

1. In Adobe Campaign, access the options menu under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** in the **[!UICONTROL Explorer]**.

1. Select the **[!UICONTROL NmsPipeline_Config]** option.

1. In the **[!UICONTROL Value (long text)]** field, you can paste the following JSON code, which specifies two triggers. You need to make sure to remove comments.

    ```
    {
    "topics": [ // list of "topics" that the pipelined is listening to.
       {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
            "triggers": [ // Array of triggers.
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
    }
    ```

1. You can also choose to paste the following JSON code which catches all triggers.

    ```
    {
    "topics": [
      {
        "name": "triggers",
        "consumer":  "customer_dev",
        "triggers": [
          {
            "name": "*",
            "jsConnector": "cus:pipeline.js"
          }
        ]
      }
    ]
    }
    ```

### The Consumer parameter {#consumer-parameter}

The pipeline works like a supplier and consumer model. Messages are consumed only for an individual consumer: each consumer gets its own copy of the messages.

The **Consumer** parameter identifies the instance as one of these consumers. The identity of the instance will call the pipeline. You can fill it with the instance name which can be found on the Monitoring page of the Client Console.

The pipeline service keeps track of the messages retrieved by each consumer. Using different consumers for different instances allows you to make sure that every message is sent to each instance.

### Pipeline option recommendations {#pipeline-option-recommendation}

To configure Pipeline option, you should follow these recommendations:

* Add or edit triggers under **[!UICONTROL Triggers]**, you should not edit the rest.
* Make sure the JSON is valid. You can use a JSON Validator, refer to this [website](http://jsonlint.com/) for example.
* "name" corresponds to the trigger ID. A wildcard "*" will catch all triggers.
* "Consumer" corresponds to the name of the calling instance or application.
* Pipelined also supports the "aliases" topic.
* You should always restart pipelined after making changes.

## Step 3: Optional configuration {#step-optional}

You can change some internal parameters as per your load requirements but make sure to test them before putting them into production.

The list of optional parameters can be found below:

|  Option | Description  |
|:-:|:-:|
|  appName(Legacy) |  AppID of the OAuth application registered in the Legacy Oath application where the public key was uploaded. For more on this, refer to this [page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(Legacy)  |  URL to get gateway tokens. Default: ```https://api.omniture.com``` |
|  authPrivateKey(Legacy) |  The private key, public part uploaded in the Legacy Oath application, AES encrypted with the XtkKey option: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy)  | Disable authentication, connecting without gateway tokens will only be accepted by some development Pipeline endpoints. |
| discoverPipelineEndpoint  |  URL to find the Pipeline Services endpoint to be used for this tenant. Default: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec  |  Period between two dumps of the internal state process in ```var/INSTANCE/pipelined.json.``` <br> Internal state is also accessible on-demand here: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint  |  Disable the detection of the PipelineServicesEndpoint to force it |
| monitorServerPort  | The pipelined process will listen on this port to provide the internal state process here: ```http://INSTANCE:PORT/pipelined/status```. <br>Default is 7781  |
|  pointerFlushMessageCount |  When this number of messages is processed, the offsets will be saved in the database. <br> Default is 1000 |
|  pointerFlushPeriodSec | After this period, the offsets will be saved in the database. <br>Default is 5 (secs) |
| processingJSThreads  | Number of dedicated threads processing messages with custom JS connectors. <br> Default is 4  |
|  processingThreads | Number of dedicated threads processing messages with built-in code. <br>Default is 4  |
| retryPeriodSec  |  Delay between retries in case of processing errors. <br>Default is 30 (secs) |
| retryValiditySec  | Discard the message if it is not successfully processed after this period (too many retries). <br>Default is 300 (secs)  |

### Pipelined process auto-start {#pipelined-process-autostart}

The pipelined process needs to be started automatically.

For this, set the <&nbsp;pipelined&nbsp;> element in the config file to autostart="true":

```
 <pipelined autoStart="true" ... "/>
```

### Pipelined process restart {#pipelined-process-restart}

A restart is required for the changes to take effect:

```
nlserver restart pipelined@instance
```

## Step 4: Validation {#step-validation}

To validate the pipeline setup for provisioning, follow the steps below:

* Make sure the [!DNL pipelined] process is running.
* Check the pipelined.log for pipeline connection logs.
* Verify the connection and if pings are received. Hosted customers can use the Monitoring from the Client Console.
