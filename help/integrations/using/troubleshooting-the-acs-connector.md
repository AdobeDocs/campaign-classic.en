---
product: campaign
title: Troubleshooting the ACS Connector
description: Troubleshooting the ACS Connector
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
---
# Troubleshooting the ACS Connector{#troubleshooting-the-acs-connector}

Depending on your implementation, you can face several common issues.

* **What are the UI differences between Campaign Standard and Campaign v7?**

  Campaign Standard and Campaign v7 work in a very similar way. Most concepts are the same but in some cases, the approach can differ slightly. Here a some of the concepts that might differ in the context of the ACS Connector:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> recipients (or any other profile dimension)<br /> </td> 
   <td> profiles<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> campaign workflows, targeting workflows<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> operations<br /> </td> 
   <td> campaigns<br /> </td> 
  </tr> 
  <tr> 
   <td> web applications<br /> </td> 
   <td> landing pages<br /> </td> 
  </tr> 
  <tr> 
   <td> custom table and schema extension<br /> </td> 
   <td> custom resource and resource extension<br /> </td> 
  </tr> 
  <tr> 
   <td> seed members<br /> </td> 
   <td> test profiles<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **The recipients of my Campaign v7 instance are not synchronized or visible to Campaign Standard.**

  This case can happen for different reasons:

    * Recipients were just created or updated in Campaign v7. The synchronization triggers every 15 minutes. Meaning that updated or newly created recipients will be visible in Campaign Standard after the next synchronization.
    * Your implementation can have been set to only synchronize recipients from specific folders. Recipients from other folders are not synchronized.
    * The recipient can be synchronized but not visible in Campaign Standard. Check the folder rights mapping.

* **I don't find the profile fields I need to base my query on in Campaign Standard.**

  By default, 20 fields from the nms:recipient table are synchronized with Campaign Standard. Refer to the detailed list of synchronized fields. Any additional field you need to retrieve in Campaign Standard must be mapped and configured by your consultant.

  To make sure the field you want to use is available, you can check the profile resource definition from **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

  Besides, all data attached to recipients and stored in tables related to nms:recipients are not synchronized by default to Campaign Standard.

  To still be able to use related data, you can perform your targeting in Campaign v7 and add additional data as explained in the [Synchronizing audiences](../../integrations/using/synchronizing-audiences.md) section, or you can refer to your consultant to explore customization possibilities.

* **I am using another profile dimension than the default nms:recipient in Campaign v7, how can I synchronize them with Campaign Standard?**

  Campaign Standard uses a unique targeting resource which is named **profiles**. The basic implementation of the Campaign Standard Connect feature provides a default mapping between Campaign v7 recipients and Campaign Standard profiles.

  If you use another profile dimension in Campaign v7, or if you use several ones, they all must be mapped with Campaign Standard profiles. Refer to your consultant to address this particular need.

* **I want to share a list of profiles with Campaign Standard through a workflow but cannot find my audience in Campaign Standard**.

  Audiences can be found in the **[!UICONTROL Audiences]** menu in Campaign Standard. They have the label specified in the **[!UICONTROL List update]** activity in your Campaign v7 workflow. They are subject to the folder mapping defined during the implementation.

  The first thing to check is whether the workflow has finished without error. If you notice an error on the **[!UICONTROL List update]** activity, it means that the synchronization with Campaign Standard may have failed. To be able to see more details about what went wrong, go to **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. This folder contains synchronization workflows triggered by the **[!UICONTROL List update]** activity execution.

  Also, make sure that the **[!UICONTROL Share with ACS]** option is checked in the **[!UICONTROL List update]** activity and that the workflow was correctly executed.

  Note that recipients profiles contained in the list must have been synchronized with Campaign Standard prior to the workflow execution. Once shared with Campaign Standard, recipients of the list are reconciliated with Campaign Standard profiles, meaning that they must exist there. Recipients from the list that cannot be reconciliated with profiles in Campaign Standard are ignored.

  If you share a list made of profiles and if none are synchronized with Campaign Standard, it creates an empty Query audience in Campaign Standard that cannot be used.

* **I received a notification telling me that a synchronization workflow is in error state. What should I do?**

  Check the external account configuration in both Campaign Standard and Campaign v7 by testing the connection:

    * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
    * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **I have no security group available when mapping folders between Campaign v7 and Campaign Standard.**

  You need to first synchronize your security groups from **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. This action checks the security groups available in Campaign Standard. Once synchronized, you can find the security groups when configuring the folder mapping.

* **I cannot edit a profile, an audience or a landing page in Campaign Standard. What does it mean?**

  Resources synchronized from Campaign v7 are in read-only mode in Campaign Standard, to ensure data consistency. If you need to edit one of these elements, you can do it in Campaign v7 and then replicate the change in Campaign Standard.
