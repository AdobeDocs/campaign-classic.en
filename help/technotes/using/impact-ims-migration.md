---
title: Update Campaign interface after IMS migration
description: Learn how to activate Adobe Identity Management System migration interface impacts
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
---
# Update Campaign interface after IMS migration {#impact-ims-migration}

Once you have [migrated your Campaign technical operators to Developer Console](ims-migration.md) and [transitioned to IMS for end-user authentication](migrate-users-to-ims.md), the last step is to enable the user interface and API restrictions to remove options and capabilities which are specific to native authentication. This update is available starting Campaign v7.4.1.

## Enable IMS restrictions {#ims-restrictions}

To finalize your migration to Adobe Identify Management System (IMS), you must block new native user creation, native user login, and API access for native operators. Your environment is then secured and standardized.

As a Managed Cloud Service/Hosted user, contact Adobe to enable this restriction, and associated updates in the product user interface.

As an on-premise/hybrid user, follow these steps:

1. Browse to the `<imsConfig>` section of your instance configuration file.
1. To enable the UI restrictions, update the `nonIMSOperatorMgmtInClientConsoleRestricted` option, inside the `nonIMSOperatorMgmtInClientConsole` element, to `true`, as below:


    ```xml
    <serverConf>
    <shared>
        <imsConfig>
            <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
        </imsConfig>
    </shared>
    </serverConf>
    ```

1. To enable the API restrictions, update the `disableAPI` option, inside the `nonIMSAuthnAPI` element, to `true`, as below:

    ```xml
    <serverConf>
    <shared>
        <imsConfig>
            <nonIMSAuthnAPI disableAPI="true">
                ...
            </nonIMSAuthnAPI>
        </imsConfig>
    </shared>
    </serverConf>
    ```

Note that a few operators are allowed to connect to Adobe Campaign with a native authentication. These technical operators are enabled by default and must not be modified. To allow this exception, these technical operators are added to the allow-list by default. You can find this list in the `<imsConfig>` section of your instance configuration file, in the `allowOperator` option inside the `nonIMSAuthnAPI` element.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

If you need to add an operator to the allowlist, add a new `allowOperator` element with the operator's name. For example, if you want to add a new operator with the name `test`, update this section as follows:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Impacts in the user interface {#ims-impacts}

Once the migration is finalized, and restrictions have been applied as described below, the following changes are applied to the product and its user interface.

### Operator management {#manage-admin}

You can no longer create, edit, update, or delete operators with native authentication from the client console. 

As a consequence, these actions have been disabled in the client console.

The administration of operators is centralized in the Adobe Admin Console, and the following tasks are now be managed exclusively through this console. Learn how to create users and assign permissions in [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Unavailable options {#unavailable-migration}

After the migration, the following tasks are no longer be available in the client console:

* Use the [Merge Selected lines option](../../platform/using/updating-data.md#merge-data) to merge operators.

* Update the following fields for your operators:
    * Name
    * Password
    * Label
    * Email

* [Reset your Campaign password](../../production/using/lost-password.md)

* Edit the XML source of the operators

* Duplicate operators.


>[!MORELIKETHIS]
>
>* [Migration of end-users to IMS](migrate-users-to-ims.md)
>* [Migration of technical operators to Adobe Developer console](ims-migration.md)
>* [Adobe Campaign Classic v7 latest release notes](../../rn/using/latest-release.md)
>* [What is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
