---
product: campaign
title: Use named rights to set up permissions
description: Learn how to use named rights to set up permissions
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
TQID: https://experienceleague.adobe.com/GApH-ZtovMX--PzISD-Pvafo3pfcbG-OqHzp5kCvcNQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Use named rights to set up permissions{#named-rights}

By default, Adobe Campaign proposes a set of named rights that let you define the authorizations assigned to operators and groups of operators. These rights can be edited from the **[!UICONTROL Administration > Access management > Named rights]** node of the tree. 

![](assets/s_ncs_admin_named_rights.png)

These rights are as follows:

* **[!UICONTROL ADMINISTRATION]**: Operators with the **[!UICONTROL ADMINISTRATION]** right has full access on the instance. Admin users can execute/create/edit/delete any object such as workflow, delivery, scripts, etc.

   >[!IMPORTANT]
   >
   >**After migrating to IMS:** Once you migrate to Adobe Identity Management System (IMS), any Product Profile or Named Right containing the word "admin" in its name (such as "Administrators", "admin", "admins", etc.) will automatically grant access to Campaign Control Panel. We recommend avoiding the use of "admin" in Named Right or Role names unless you intend for those users to have Control Panel access. Learn more about [IMS migration](../../technotes/using/migrate-users-to-ims.md) and [managing Control Panel access](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: You can set multiple approval steps within workflows and deliveries to ensure that the current state has been approved by an assigned operator or group. Users with the **[!UICONTROL APPROVAL ADMINISTRATION]** right can set approval steps and also assign an operator or operator group who should approve those steps.

   >[!IMPORTANT]
   >
   >**After migrating to IMS:** Product Profiles or Named Rights containing the word "admin" (such as "Approval Administrator") will grant access to Campaign Control Panel. Learn more about [IMS migration](../../technotes/using/migrate-users-to-ims.md) and [managing Control Panel access](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL CENTRAL]**: Right for central management (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Right to delete folders. With this right, users are allowed to delete folders from the explorer view.

* **[!UICONTROL EDIT FOLDERS]**: Right to alter folder properties such as internal name, label, associated image, sub folder order, etc.

* **[!UICONTROL EXPORT]**: Users can export data out of their Adobe Campaign instances into a file on server or local machine using the **[!UICONTROL EXPORT]** workflow activity.

* **[!UICONTROL FILES ACCESS]**: Right to read and write access for files via a script which can be written in the **[!UICONTROL JavaScript]** workflow activity to read/write files on a server.

* **[!UICONTROL IMPORT]**: Right for generic data import. **[!UICONTROL IMPORT]** allows you to import data into any other table whereas the **[!UICONTROL RECIPIENT IMPORT]** right allows to import into the recipient table only.

* **[!UICONTROL INSERT FOLDERS]**: Right to insert folders. Users with the **[!UICONTROL INSERT FOLDERS]** right can create new folders in the folder tree in explorer view.

* **[!UICONTROL LOCAL]**: Right for local management (Distributed Marketing).

* **[!UICONTROL MERGE]**: Right to merge the selected records into one. If recipients exist as duplicates, the **[!UICONTROL MERGE]** right allows user to select the duplicates and merge them into a primary recipient.

* **[!UICONTROL PREPARE DELIVERIES]**: Right to create, edit and save a delivery. Users with the **[!UICONTROL PREPARE DELIVERIES]** right can also start the delivery analysis process.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Right to collect and delete privacy data. For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: Right to execute commands in various programming languages.

* **[!UICONTROL RECIPIENT IMPORT]**: Right to import recipients. Users with the **[!UICONTROL RECIPIENT IMPORT]** right can import a local file into recipient table.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Right to execute any SQL command directly on the database.

* **[!UICONTROL START DELIVERIES]**: Right to approve previously analyzed deliveries. After the delivery analysis, delivery will pause at various approval steps and will need to be approved to resume. Users with the **[!UICONTROL START DELIVERIES]** right are allowed to approve deliveries.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Right to write your own SQL scripts using the SQL Data Management activity, in order to create and populate work tables. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html){target="_blank"}.

* **[!UICONTROL WORKFLOW]**: Right to execute workflows. Without this right, users cannot start, stop or restart workflows.

* **[!UICONTROL WEBAPP]**: Right to use web applications.

>[!NOTE]
>
>This list can differ depending on the add-ons installed on the platform.

## Access rights matrix {#access-rights-matrix}

Default groups and named rights allow operators to access certain folders in the navigation hierarchy, and grant read, write, and delete permissions.

Adobe Campaign access rights matrix is available [here](/help/platform/using/assets/access-rights-matrix.pdf).

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
