---
title: Using the local approval activity
seo-title: Using the local approval activity
description: Using the local approval activity
seo-description: 
page-status-flag: never-activated
uuid: db1d2b96-9797-480d-8a58-10c9071e7551
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: c3abf796-999d-4dad-942d-3572b6f50a04
index: y
internal: n
snippet: y
---

# Using the local approval activity{#using-the-local-approval-activity}

The **Local approval** activity integrated into a targeting workflow lets you set up a recipient approval process before the delivery is sent.

>[!CAUTION]
>
>To use this function, you need to purchase the Distributed Marketing module, which is a Campaign option. Please check your license agreement.

To set up this use case, we created the following targeting workflow:

![](assets/local_validation_workflow.png)

The main steps of the local approval process are:

1. The population resulting from targeting can be limited thanks to a **Split** type activity using a data distribution model. 

   ![](assets/local_validation_intro_1.png)

1. The **Local approval** activity then takes over and sends a notification email to each local supervisor. The activity is pended until each local supervisor approves the recipients assigned to them.

   ![](assets/local_validation_intro_4.png)

1. Once the approval deadline is reached, the workflow starts again. In this example, the **Delivery** activity starts and the delivery is sent to the approved targets.

   >[!NOTE]
   >
   >Once the deadline is reached, recipients who haven't been approved are excluded from targeting.

   ![](assets/local_validation_intro_6.png)

1. A few days later, the second **Local approval** type activity sends a notification email to each local supervisor with a summary of the actions carried out by their contacts (clicks, opens, etc.). 

   ![](assets/local_validation_intro_5.png)

## Step 1: Creating the data distribution template {#step-1--creating-the-data-distribution-template-}

The data distribution template lets you limit the population resulting from targeting based on data grouping while enabling you to assign each value to a local supervisor. In this example, we have defined the **Email address domain** field as a distribution field and assigned a domain to each local supervisor

For more on creating a data distribution template, refer to [Limiting the number of subset records per data distribution](../../workflow/using/using-the-local-approval-activity.md#limiting-the-number-of-subset-records-per-data-distribution).

1. To create the data distribution template, go to the **Resources > Campaign management > Data distribution** node and click **New**.

   ![](assets/local_validation_data_distribution_1.png)

1. Select the **General** tab.

   ![](assets/local_validation_data_distribution_2.png)

1. Enter the **Label** and the **Distribution context**. In this example, we have selected the **Recipient** targeting schema and the **Email domain** field as a distribution field. The list of recipients will be broken down by domain.
1. In the **Distribution type** field, select how the target limitation value will be expressed in the **Distribution** tab. Here, we have chosen **Percentage**.
1. In the **Approval storage** field, enter the storage schema of the approvals that match the targeting schema in use. Here we are going to use the default storage schema: **Local approval of recipients**.
1. Then click the **Advanced parameters** link.

   ![](assets/local_validation_data_distribution_3.png)

1. Keep the **Approve the targeted messages** option checked so that all recipients are pre-selected from the list of recipients to approve.
1. In the **Delivery label** field, we've left the default expression (compute string of the delivery). The standard label of the delivery will be used in the feedback notification.
1. In the **Grouping field** section, we have selected the **Gender** field as a grouping field for displaying recipients in the approval and feedback notifications.
1. In the **Edit targeted messages** section, we've selected the **Edit recipients** web application and the **recipientId** parameter. In the approval and feedback notifications, recipients will be clickable and will point towards the URL of the web application. The additional URL parameter will be **recipientId**.
1. Then click the **Distribution** tab. For each domain, enter the following fields:

   ![](assets/local_validation_data_distribution_4.png)

    * **Value**: enter the value of the domain name. 
    * **Percentage / Fixed**: for each domain, enter the max. number of recipients you want to send the delivery to. In this example, we want to limit the delivery to 10% per domain.
    * **Label**: enter the label of the domain to be displayed in the approval and feedback notifications.
    * **Group or operator**: select the operator or group of operators assigned to the domain.

      >[!CAUTION]
      >
      >Make sure the operators have been assigned the appropriate rights.

## Step 2: Creating the targeting workflow {#step-2--creating-the-targeting-workflow}

To set up this use case, we created the following targeting workflow:

![](assets/local_validation_workflow.png)

The following activities were added:

* Two **Query** activities,
* One **Intersection** activity,
* One **Split** activity,
* One **Local approval** activity,
* One **Delivery** activity,
* One **Wait** activity,
* A second **Local approval** activity,
* One **End** activity.

### Queries, Intersection and Split {#queries--intersection-and-split}

Upstream targeting is made up of two queries, one intersection and one split. The population resulting from targeting can be limited using a **Split** activity using a data distribution template.

For more on configuring a split activity, refer to [Split](../../workflow/using/split.md). The creation of a data distribution template is detailed in [Limiting the number of subset records per data distribution](../../workflow/using/using-the-local-approval-activity.md#limiting-the-number-of-subset-records-per-data-distribution).

If you do not want to limit the population from the query, you do not have to use the **Query**, **Intersection**, and **Split** activities. In this case, complete the data distribution template in the first **Local approval** activity.

1. In the **Record count limitation** section, select the **Limit the selected records** option and click the **Edit** link.

   ![](assets/local_validation_split_1.png)

1. Select the **Keep only the first records after sorting** option and click **Next**.

   ![](assets/local_validation_split_1bis.png)

1. In the **Sort columns** section, add the field which the sort is applied to. Here, we have chosen the **Email** field. Click **Next**.

   ![](assets/local_validation_split_2.png)

1. Select the **By data distribution** option, select the distribution template created previously (refer to [Step 1: Creating the data distribution template](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-)) and click **Finish**.

   ![](assets/local_validation_split_3.png)

In the distribution template, we have chosen to limit the population to 10% per grouping value, which coincides with the values displayed in the workflow (340 as an input and 34 as an output).

![](assets/local_validation_intro_1.png)

### Approval notification {#approval-notification}

The **Local approval** activity lets you send a notification to each local supervisor.

For more on configuring the **Local approval** activity, refer to [Local approval](../../workflow/using/local-approval.md).

![](assets/local_validation_workflow_2.png)

The following fields need to be entered:

1. In the **Action to execute** section, select the **Target approval notification** option.
1. In the **Distribution context** section, select the **Specified in the transition** option.

   If you don't want to limit the targeted population, select the **Explicit** option here and enter the distribution template created previously in the **Data distribution** field. 

1. In the **Notification** section, select the delivery template and the subject to be used for the notification email. Here, we have chosen the default template: **Local approval notification**.
1. In the **Approval schedule** section, we've kept the default approval deadline (3 days) and added a reminder. The delivery will leave 3 days after the start of approval. Once the approval deadline has been reached, recipients who haven't been approved aren't taken into account by targeting.

The notification email sent by the **Local approval** activity to local supervisors is as follows: 

![](assets/local_validation_intro_2.png)

### Wait {#wait}

The wait activity lets you postpone the start of the second local approval activity that will send the delivery feedback notification. In the **Duration** field, we have entered the **5d** value (5 days). The actions performed by recipients for 5 days following the sending of the delivery will be included in the feedback notification.

![](assets/local_validation_workflow_3.png)

### Feedback notification {#feedback-notification}

The second **Local approval** activity lets you send a delivery feedback notification to each local supervisor.

![](assets/local_validation_workflow_4.png)

The following fields need to be entered.

1. In the **Action to execute** section, choose **Delivery feedback report**.
1. In the **Delivery** section, choose **Specified in the transition**. 
1. In the **Notification** section, select the delivery template and the subject to be used for the notification email.

Once the deadline configured in the wait activity is reached, the second **Local approval** type activity sends the following notification email to each local supervisor:

![](assets/local_validation_intro_3.png)

### Approval tracking by the administrator {#approval-tracking-by-the-administrator}

Each time the local approval activity starts, an approval task is created. The administrator can control each of these approval tasks.

Go to the targeting workflow of your campaign and click the **Local approval tasks** tab.

![](assets/local_validation_admin_1.png)

The list of local approval tasks can also be accessed via the **Approval tasks** tab of the data distribution template.

![](assets/local_validation_admin_2.png)

Select the task you want to monitor and click the **Detail** button. The **General** tab of the local approval task lets you view information on the task. If necessary, you can alter the approval and the reminder dates.

![](assets/local_validation_admin_3.png)

This tab shows the following information:

* the label of the task and its ID
* the distribution template used
* the number of targeted messages
* the linked workflow and campaign
* the task schedule

The **Distribution** tab for the task lets you view the approval logs, their status, the number of messages targeted, the approval date, as well as the operator who approved the delivery.

![](assets/local_validation_admin_4.png)

Select an approval log and click the **Detail** button to display more information. The **General** tab of the local approval log lets you view general log information. You can also change the approval status.

![](assets/local_validation_admin_5.png)

This tab shows the following information:

* the linked approval task
* the approval status (**Approved** or **Pending**)
* the distribution template used
* the local supervisor who approved and the approval date
* the number of messages targeted and approved

The **Targeted** tab of the approval log displays the list of targeted recipients and their approval status. You can change this status if necessary. 

![](assets/local_validation_admin_6.png)

