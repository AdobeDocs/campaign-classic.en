---
title: Migration of technical users to Adobe Developer console
description: Learn how to migrate Campaign technical operators to Technical account on Adobe Developer console
feature: Technote
role: Admin
exl-id: 1a409daf-57be-43c9-a3d9-b8ab54c88068
---
# Migration of Campaign technical operators to Adobe Developer Console {#migrate-tech-users-to-ims}

As part of the effort to reinforce security and authentication process, starting with Campaign Classic v7.3.5, the authentication process to Campaign Classic is being improved. Technical operators should now use the [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe recommends to perform this migration in Campaign v7.3.5 to be able to migrate smoothly to Campaign v8.**

A technical operator is a Campaign user profile which has been explicitly created for API integration. This article details the steps required to migrate a technical operator to a technical account via the Adobe Developer console.

## Are you impacted?{#ims-impacts}

If you are making API calls from a system external to Campaign into either your Campaign Marketing instance or the Real-Time Message Center instance, Adobe highly recommends you to migrate the technical operator(s) to technical account(s) through the Adobe Developer Console as detailed below.

This change is applicable starting Campaign Classic v7.3.5 (and latest [IMS migration compatible versions](#ims-versions-tech)) and is **mandatory** to move to Adobe Campaign v8.

## Migration process {#ims-migration-procedure}

Follow the below steps to create technical account(s) within the Adobe Developer Console, and then use those newly created accounts to be able to change the authentication methods for all of your external systems making API calls in Adobe Campaign.

An overview of the steps are:

* Creating a project within the Adobe Developer Console
* Assigning the appropriate API's to the newly created project
* Granting the needed Campaign Product Profiles to the project
* Updating your APIs to use the newly created technical account credentials
* Remove the legacy technical operators from your Campaign instance


### IMS migration compatible versions {#ims-versions-tech}

 A prerequisite for this migration is to upgrade your environment to one of the following product version:

* Campaign v7.3.5 (recommended)
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

These Campaign versions are detailed in the [Release Notes](../../rn/using/latest-release.md).

### Prerequisites for the migration{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Campaign Hosted and Managed Services customers

    For API calls into the Message Center instance(s), the product profile (mentioned below) should be created during the upgrade to Campaign v7.3.5 (or other [IMS migration compatible version](#ims-versions-tech)), or during provisioning of the instance. Note that f you do not see the product profile, please reach out to your Transition Manager or Customer Support to get the product profile created before starting the IMS migration. This product profile is named:

    `campaign - <your campaign marketing instance> - messagecenter`

    If you have already been using IMS based authentication for user access to Campaign then the product profiles needed for the API calls should already exist within the Admin Console. If you use a custom operator group within Campaign for the API calls to the Marketing instance, you must create that product profile within the Admin Console.

    For other cases, you must reach out to your Adobe Transition Manager (for Managed Services users) or to Adobe Customer Care (for other Hosted users), so that Adobe technical teams can migrate your existing Operator groups and Named rights to the Product Profiles within the Admin Console.

* Campaign On-Premise and Hybrid customers

    For API calls into the Message Center instance(s), you must create a product profile named:

    `campaign - <your campaign instance> - messagecenter`

    If you have already been using IMS based authentication for user access to Campaign then the product profiles needed for the API calls should already exist within the Admin Console. If you use a custom operator group within Campaign for the API calls to the Marketing instance, you must create that product profile within the Admin Console.

    You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### Step 1 - Create your Campaign Project within the Adobe Developer Console {#ims-migration-step-1}

Integrations are created as part of a **Project** within Adobe Developer Console. Learn more about Projects in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}. 

You can use any project previously created by you or you can create a new project. The steps to create a project are detailed in the [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. You can find key steps below

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

To create a new project, click **Create new project** from the main screen in the Adobe Developer Console.

![](assets/New-Project.png) 

You can use the **Edit project** button to rename this project. 


### Step 2 - Add APIs to your project {#ims-migration-step-2}

From the newly created project screen, add in the API's needed to be able to use this project as a Technical Account for your API calls to Adobe Campaign.

To add APIs to your project, follow these steps:

1. Click on **Add API** to select the APIs to add to your project. 
    ![](assets/do-not-translate/ims-updates-01.png) 
1. Select and add the Adobe Campaign API to your Project by checking the box in the upper right corner of Adobe Campaign card which appears when you hover the mouse over the card
    ![](assets/do-not-translate/ims-updates-02.png) 
1. Click **Next** at the bottom of the screen.

### Step 3 - Select the authentication type  {#ims-migration-step-3}

In the **Configure API** screen, select the authentication type needed. **OAuth Server-to-Server** Authentication is required for this project. Ensure it is selected and click **Next** at the bottom of the screen.

![](assets/do-not-translate/ims-updates-03.png) 

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Step 4 - Select the product profiles {#ims-migration-step-4}

As described in the prerequisites section you must assign the appropriate product profiles to be used by the project. In this step, you must select the product profile or profiles to be used by the technical account being created. 

If this technical account is used to make API calls to the Message Center instance, make sure to select the Adobe product profile, ending with messagecenter, for the Marketing Instance associated to the Message Center.

For API calls to the Marketing instance(s) select the product profile corresponding to the instance and Operator Group, for example `campaign - <your campaign marketing instance> - Admin`.

Once the needed product profiles have been selected click on **Save configured API** at the bottom of the screen.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Step 5 - Add the I/O management API to your project {#ims-migration-step-5}


From the project screen, click the **[!UICONTROL + Add to Project]** and choose **[!UICONTROL API]** in the upper left of the screen to be able to add the I/O Management API to this project.

![](assets/do-not-translate/ims-updates-04.png) 

In the **Add an API** screen, scroll down to find the **I/O Management API** card. Select it by clicking the checkbox that appears when you hover over the card. Then click **Next** at the bottom of the screen.

![](assets/do-not-translate/ims-updates-05.png) 


In the **Configure API** screen, the OAuth Server-to-Server authentication is already existing. Click **Save configured API** at the bottom of the screen.


![](assets/do-not-translate/ims-updates-06.png) 

This takes you back to the Project screen within the I/O Management API of the newly created project. Click on the project name in the breadcrumbs at the top of the screen to be taken back to the main Project Details page.


### Step 6 - Verify the project setup {#ims-migration-step-6}

Review your project to ensure it looks similar to the below with the **I/O Management API** and **Adobe Campaign API** visible in the Products and Services section and **OAuth Server-to-Server** in the Credentials section.

![](assets/do-not-translate/ims-updates-07.png) 


### Step 7 - Validate your configuration {#ims-migration-step-7}

To try out the connection, follow the steps detailed in the [Adobe Developer Console credentials guide](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} for generating an access token and copy the Sample cURL command provided. You can create a soap call using these credentials to test that you can authenticate and connect to the Adobe Campaign instance(s) correctly. We recommend doing this validation prior to making all of the changes to the third-party API integrations.

### Step 8 - Update the third-party API Integrations {#ims-migration-step-8}

You must now update off of the API Integrations making calls into Adobe Campaign to use the newly created Technical Account. 

For details on API integration steps, please refer to the code samples below.

>[!BEGINTABS]

>[!TAB SOAP Call]

```

curl --location --request POST 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: xtk:queryDef#ExecuteQuery' \
--header 'Authorization: Bearer eyJhw' \
--data-raw '<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'

```

>[!TAB  SampleCode Java]

```javascript

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import com.google.gson.Gson;
import com.google.gson.JsonObject;
 
import com.google.gson.JsonSyntaxException;
import org.apache.hc.client5.http.classic.methods.HttpPost;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.io.entity.StringEntity;
 
 
public class TAAccessToken {
    public static void main(String[] args) throws IOException {
        String accessToken = null;
        CloseableHttpClient httpClient = HttpClients.createDefault();
        try {
            HttpPost httpPost = new HttpPost("https://ims-na1.adobelogin.com/ims/token/v3");
 
            // Request headers
            httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded");
 
            String clientId = "<client_id>";
            String clientSecret = "<client_secret>";
            String scopes = "<scopes>";
 
            // Define the request body
            String requestBody = "client_id="+clientId+"&client_secret="+clientSecret+"&grant_type=client_credentials&scope="+scopes+"";
            StringEntity requestEntity = new StringEntity(requestBody);
            httpPost.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClient.execute(httpPost);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
                int responseCode = response.getCode();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String lineImsToken;
                    StringBuilder responseImsToken = new StringBuilder();
                    while ((lineImsToken = bufferedReader.readLine()) != null) {
                        responseImsToken.append(lineImsToken);
                    }
 
                    String jsonString = responseImsToken.toString();
 
                    try {
                        Gson gson = new Gson();
                        JsonObject jsonObject = gson.fromJson(jsonString, JsonObject.class);
 
                        // Get the value of a specific key
                        accessToken = jsonObject.get("access_token").getAsString();
                    }
                    catch (JsonSyntaxException | NullPointerException e) {
                        System.err.println("Error parsing JSON: " + e.getMessage());
                        e.printStackTrace();
                    }
                    System.out.println("Response Code: " + responseCode);
                    System.out.println("Response Body: " + accessToken);
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClient.close();
        }
 
        CloseableHttpClient httpClientSoap = HttpClients.createDefault();
        try {
            HttpPost httpPostSoap = new HttpPost("https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp");
 
            // Request headers
            httpPostSoap.addHeader("Content-Type", "text/xml; charset=utf-8");
            httpPostSoap.addHeader("SOAPAction", "xtk:queryDef#ExecuteQuery");
            httpPostSoap.addHeader("Authorization", "Bearer "+accessToken);
 
            // Request body
            String xmlData = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n" +
                    "<soap:Envelope xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\">\n" +
                    "  <soap:Body>\n" +
                    "    <ExecuteQuery xmlns=\"urn:xtk:queryDef\">\n" +
                    "            <sessiontoken></sessiontoken>\n" +
                    "            <entity>\n" +
                    "                <queryDef schema=\"nms:recipient\" operation=\"select\">\n" +
                    "                    <!-- fields to retrieve -->\n" +
                    "                    <select>\n" +
                    "                        <node expr=\"@lastName\"/>\n" +
                    "                        <node expr=\"@email\"/>\n" +
                    "                        <node expr=\"@firstName\"/>\n" +
                    "                    </select>\n" +
                    "                    <!-- condition on email -->\n" +
                    "                    <!-- <where><condition expr=\"@email= '\''joh@com.com'\''\"/>\n" +
                    "                </where> -->\n" +
                    "                </queryDef>\n" +
                    "            </entity>\n" +
                    "        </ExecuteQuery>\n" +
                    "  </soap:Body>\n" +
                    "</soap:Envelope>";
            StringEntity requestEntity = new StringEntity(xmlData);
            httpPostSoap.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClientSoap.execute(httpPostSoap);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String line;
                    while ((line = bufferedReader.readLine()) != null) {
                        System.out.println(line);
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClientSoap.close();
        }
 
    }
}

```

>[!TAB SampleCodePython]

```python

import requests
 
oauth_url = 'https://ims-na1.adobelogin.com/ims/token/v3'
data = {
    'grant_type': 'client_credentials',
    'scope': '<scopes>',
    'client_id': '<client_id>',
    'client_secret': '<client_secret>'
}
 
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
}
response = requests.post(oauth_url, data=data, headers=headers)
response = response.json()
access_token = response['access_token']
 
 
url = 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp'
headers = {
    'Content-Type': 'text/xml; charset=utf-8',
    'SOAPAction': 'xtk:queryDef#ExecuteQuery',
    'Authorization': 'Bearer '+access_token
}
xml_data = '''<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'''
response = requests.post(url, headers=headers, data=xml_data)

```

>[!ENDTABS]

For more information, refer to [Adobe Developer Console authentication documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Below are sample SOAP calls showing the before and after migration calls for the third party systems.

Once the migration process is achieved and validated, the Soap Calls are updated as below:

* Before the migration: there was no support for Technical account access token.

    ```sql
    POST /nl/jsp/soaprouter.jsp HTTP/1.1
    Host: localhost:8080
    Content-Type: application/soap+xml;
    SOAPAction: "nms:rtEvent#PushEvent"
    charset=utf-8
    
    <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:PushEvent>
            <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
            <urn:domEvent>
                <!--You may enter ANY elements at this point-->
                <rtEvent type="type" email="name@domain.com"/>
            </urn:domEvent>
        </urn:PushEvent>
    </soapenv:Body>
    </soapenv:Envelope>
    ```

* After the migration: there is support for Technical account access token. The access token is expected to be supplied in `Authorization` header as Bearer token. Usage of session token should be ignored here, as shown in the below soap call sample.

    ```sql
    POST /nl/jsp/soaprouter.jsp HTTP/1.1
    Host: localhost:8080
    Content-Type: application/soap+xml;
    SOAPAction: "nms:rtEvent#PushEvent"
    charset=utf-8
    Authorization: Bearer <IMS_Technical_Token_Token>
    
    <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:PushEvent>
            <urn:sessiontoken></urn:sessiontoken>
            <urn:domEvent>
                <!--You may enter ANY elements at this point-->
                <rtEvent type="type" email="name@domain.com"/>
            </urn:domEvent>
        </urn:PushEvent>
    </soapenv:Body>
    </soapenv:Envelope>
    ```



### Step 9 - (optional) Update the technical account operator within the Campaign Client Console {#ims-migration-step-9}

This step is optional and only available within the Marketing Instance(s), not within any Message Center instance. If specific folder permissions or named rights have been defined for the Technical Operator not via the assigned Operator Group(s). You would now need to update the newly created Technical Account user in the Admin Console to grant the folder permissions or named rights required.

Note that the Technical Account user will NOT exist in Adobe Campaign until at least one API call is made to the Campaign Instance, at which time IMS will create the user within Campaign. If you are unable to locate the technical users within Campaign, ensure you have been able to successfully send an API call as outlined [in Step 7](#ims-migration-step-7).

1. To apply the changes needed for the new Technical Account User, locate them within the Campaign Client Console by email address. This email address was created during the Project Creation and Authentication steps above. 

    You can locate this email address by clicking on the **OAuth Server-to-Server** heading in the **Credentials** section of the Project.

    ![](assets/do-not-translate/ims-updates-07.png) 

    In the **Credentials details** tab, scroll down to locate the **Technical Account Email** and click the **Copy** button.

    ![](assets/do-not-translate/ims-updates-08.png) 

1. You now need to update the newly created technical operator in Adobe Campaign Client Console. You must apply the existing technical operator folder permissions to the new technical operator.

    To update this operator, follow these steps:

    1. From Campaign Client Console explorer, browse to the **Administration > Access Management > Operators**.
    1. Access the existing technical operator used for APIs.
    1. Browse to the folder permissions, and check rights.
    1. Apply the same permissions to the newly created technical operator. This operator's email is the **Technical Account Email** value copied earlier.
    1. Save your changes.


>[!CAUTION]
>
>The new technical operator must have made at least one API call to be added to Campaign Client Console.
>

### Step 10 - Remove the old technical operator from Adobe Campaign {#ims-migration-step-10}

Once you have migrated all of the third-party systems to use the new Technical Account with IMS Authentication you can delete the old technical operator from the Campaign Client Console. 

You do this by logging into the Campaign Client Console, navigating to **Administration > Access Management > Operators** and locating the old Technical Users and deleting them.
