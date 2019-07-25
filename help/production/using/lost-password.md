---
title: Lost password
seo-title: Lost password
description: Lost password
seo-description: 
page-status-flag: never-activated
uuid: d430ed98-2887-4274-9e5c-ca879c4c7ebe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: f5d9930f-0e9e-4bc1-becb-cf7b94e5dd7f
index: y
internal: n
snippet: y
---

# Lost password{#lost-password}

 You can change or recover a lost password.

There are two possible scenarios:

* Password lost by an Adobe Campaign operator.

  In this case, you can change the password of the operator concerned. To do this, connect via an operator with administrator rights, right-click on an operator, select **Actions** > **Reset password** and set the operator's new password. We recommend that operators change their password when they first reconnect.

  ![](assets/operator-passwd.png)

* **Internal** password loss (on-premise customers only).

  If the **internal** password is lost, you must reinitialize it. To do this, apply the following procedure:

    1. Edit the **/usr/local/neolane/nl6/conf/serverConf.xml** file.
    1. Go to the **internalPassword** line.

       ```    
       <!-- XTK authentication mode internalPassword : Password of internal account -->
        <xtk internalPassword="myPassword"/>
       ```

    1. Delete the string in quotes, in this case: **myPassword**

       You thus obtain the following line:

       ```    
       !-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword=""/
       ```

    1. Save changes and close the file.
    1. Configure the new password. To do this, enter the following commands:

       ```    
       nlserver config -internalpassword
       HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of dd/mm/yyyy
       Enter current password.
       Password: (empty)
       Enter the new password.
       Password: 
       Confirmation 
       ```

    1. You can now use your new password to connect in **Internal** mode.

