---
product: campaign
title: Configure the pipeline
description: Learn how to configure the pipeline for Campaign - Triggers integration
feature: Triggers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
---
# Configure the pipeline {#configuring-pipeline}

Authentication parameters such as the customer ID, the private key, and the authentication endpoint are configured in the instance configuration files.

The list of triggers to be processed is configured in an option in JSON format.

The triggers are used for targeting by a campaign workflow that sends emails. The campaign is set up so that a customer that has both trigger events receives an email.

## Prerequisites {#prerequisites}

Before starting this configuration, please check you have:

* An Adobe Developer project
* A valid Organization ID - To find your Organization ID, refer to [this page](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* A Developer access to your Organization
* A valid triggers configuration in Adobe Analytics

Authentication is required since pipeline is hosted in the Adobe Experience Cloud. It uses an authentication which is supported for via an Adobe Developer Project.

## Step 1: Create/update your Adobe Developer Project {#creating-adobe-io-project}

You must enable your organization with Adobe Developer Account Tokens for the Triggers integration.

Learn how to create your Adobe Technical account in [this page](../../integrations/using/oauth-technical-account.md). Note that you need to select **[!UICONTROL Adobe Analytics]** while adding API to the Adobe Developer credential.

## Step 2: Configure the pipeline option {#configuring-nmspipeline}

Once the authentication is set, the pipeline will retrieve the events. It only processes triggers that are configured in Adobe Campaign. The trigger must have been generated from Adobe Analytics and pushed to the pipeline which will only process triggers that are configured in Adobe Campaign.

The option can also be configured with a wildcard in order to catch all triggers regardless of the name.

1. In Adobe Campaign, access the options menu under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** in the **[!UICONTROL Explorer]**.

1. Select the **[!UICONTROL NmsPipeline_Config]** option.

1. In the **[!UICONTROL Value (long text)]** field, you can paste the following JSON code, which specifies two triggers. Make sure to remove comments.

    ```json
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

    ```json
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

### Set the Consumer parameter {#consumer-parameter}

The pipeline works like a supplier and consumer model. Messages are consumed only for an individual consumer: each consumer gets its own copy of the messages.

The **Consumer** parameter identifies the instance as one of these consumers. The identity of the instance will call the pipeline. You can fill it with the instance name which can be found on the Monitoring page of the Client Console.

The pipeline service keeps track of the messages retrieved by each consumer. Using different consumers for different instances allows you to make sure that every message is sent to each instance.

### Pipeline option recommendations {#pipeline-option-recommendation}

To configure Pipeline option, you should follow these recommendations:

* Add or edit triggers under **[!UICONTROL Triggers]**.
* Make sure the JSON is valid. 
* The **Name** parameter corresponds to the trigger ID. A wildcard "*" will catch all triggers.
* The **Consumer** parameter corresponds to the name of the calling instance or application.
* the `pipelined`process also supports the "aliases" topic.
* You should always restart `pipelined`process after making changes.

## (optional) Step 3: Additional configuration {#step-optional}

You can change some internal parameters as per your load requirements but make sure to test them before applying them to your production environment.

The list of optional parameters is:

|  Option | Description  |
|:-:|:-:|
|  appName(Legacy) |  AppID of the OAuth application registered in the Legacy Oath application where the public key was uploaded. For more on this, refer to this [page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
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

The `pipelined` process needs to be started automatically.

For this, set the `<`pipelined`>` element in the config file to autostart="true":

```sql
 <pipelined autoStart="true" ... "/>
```

### Pipelined process restart {#pipelined-process-restart}

A restart is required for the changes to take effect:

```sql
nlserver restart pipelined@instance
```

## Step 4: Validation {#step-validation}

To validate the pipeline setup for provisioning, follow the steps below:

* Make sure the `pipelined` process is running.
* Check the `pipelined.log` for pipeline connection logs.
* Verify the connection and if pings are received. Hosted customers can use the Monitoring from the Client Console.
