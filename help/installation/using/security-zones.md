---
solution: Campaign Classic
product: campaign
title: Configure security zones
description: Learn how to configure security zones
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
---

# Define security zones (on-premise){#defining-security-zones}

Each operator needs to be linked to a zone to log on to an instance and the operator IP must be included in the addresses or address sets defined in the security zone. Security zone configuration is carried out in the configuration file of the Adobe Campaign server.

Operators are linked to a security zone from its profile in the console, accessible in the **[!UICONTROL Administration > Access management > Operators]** node. [Learn more](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>This procedure is restricted to **on-premise** deployments. 
>
>As a **hosted** customer, if you can access [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), you can use the Security Zone self service interface. [Learn more](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Other **hybrid/hosted** customers need to reach out to Adobe support team to add IP to the allow list.
>

## Create security zones {#creating-security-zones}

A zone is defined by:

* one or more ranges of IP addresses (IPv4 and IPv6)
* a technical name associated to each range of IP addresses

Security zones are interlocked, which means that defining a new zone within another zone reduces the number of operators who can log on to it while increasing the rights assigned to each operator.

Zones must be defined during server configuration, in the **serverConf.xml** file. All the parameters available in the **serverConf.xml** are listed in [this section](../../installation/using/the-server-configuration-file.md).

Each zone defines rights, such as:

* HTTP connection rather than HTTPS
* Error display (Java errors, JavaScript, C++, etc.)
* Report and webApp preview
* Authentication via login / password
* Non-secure connection mode

>[!NOTE]
>
>**Each operator must be linked to a zone**. If the IP address of the operator belongs to the range defined by the zone, the operator can log on to the instance.  
>The operator's IP address may be defined in several zones. In this case, the operator receives the **set** of available rights for each zone.

The out-of-the-box **serverConf.xml** file includes three zones: **public, VPN, and LAN**.

>[!NOTE]
>
>**The out-of-the-box configuration is secure**. However, before migrating from an earlier version of Adobe Campaign, it may be necessary to temporarily reduce security in order to migrate and approve the new rules.

Example of how to define a zone in the **serverConf.xml** file:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

All of the rights defining a zone are as follows:

* **allowDebug**: enables a webApp to be executed in "debug" mode
* **allowEmptyPassword**: authorizes a connection to an instance without a password
* **allowHTTP**: a session can be created without using the HTTPS protocol
* **allowUserPassword**: the session token can have the following form "`<login>/<password>`"
* **sessionTokenOnly**: the security token is not required in the connection URL
* **showErrors**: errors on the server side are forwarded and displayed

>[!IMPORTANT]
>
>In a zone definition, each attribute with the **true** value reduces security.

When using Message Center, if there are several execution instances, you need to create an additional security zone with the **sessionTokenOnly** attribute defined as **true**, wherein only the necessary IP addresses are to be added. For more on configuring instances, refer to [this document](../../message-center/using/creating-a-shared-connection.md).

## Best practices for security zones {#best-practices-for-security-zones}

In the definition of the **lan** security zone, it's possible to add an IP address mask defining technical access. This add will enable access to all the instances hosted on the server.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>

```

We recommend defining IP address ranges directly in the configuration file dedicated to the instance for operators who access only a specific instance.

In the **`config-<instance>.xml`** file:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>

```

## Sub networks and proxies in a security zone {#sub-networks-and-proxies-in-a-security-zone}

The **proxy** parameter can be used in a **subNetwork** element to specify proxy use in a security zone.

When a proxy is referenced and a connection enters via this proxy (visible via the HTTP X-Forwarded-For header), the verified zone is that of the clients of the proxy and not that of the proxy.

>[!IMPORTANT]
>
>If a proxy is configured and it is possible to override it (or it if does not exist), the IP address that will be tested will be able to be falsified.
>
>In addition, relays are now generated like proxies. You can therefore add the IP address 127.0.0.1 to the list of proxies in your security zone configuration.
>
>For example: " `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`".

Various cases can occur:

* A sub-network is directly referenced in the security zone and no proxy is configured: users of the sub-network can directly connect to the Adobe Campaign server.

  ![](assets/8101_proxy1.png)

* A proxy is specified for a sub-network in the security zone: users from this sub-network can access the Adobe Campaign server via this proxy.

  ![](assets/8101_proxy2.png)

* A proxy is included in a security zone sub-network: users that have access through this proxy, regardless of their origin, can access the Adobe Campaign server.

  ![](assets/8101_proxy3.png)

The IP addresses of proxies that are likely to access the Adobe Campaign server must be entered in both the **`<subnetwork>`** concerned and the first level subnetwork **`<subnetwork name="all"/>`**. For example, here for a proxy whose IP address is 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Link a security zone to an operator {#linking-a-security-zone-to-an-operator}

Once zones are defined, each operator must be linked to one of them to be able to log on to an instance and the IP address of the operator must be included in the addresses or range of addresses referenced in the zone.

The technical configuration of the zones is carried out in the configuration file of the Campaign Server: **serverConf.xml**.

Prior to this, you must start by configuring the out-of-the-box **[!UICONTROL Security zone]** enumeration to link a label to the internal name of the zone defined in the **serverConf.xml** file.

This configuration is done in the Campaign explorer:

1. Click the **[!UICONTROL Administration > Platform > Enumerations]** node.
1. Select the **[!UICONTROL Security zone (securityZone)]** system enumeration.

   ![](assets/enum_securityzone.png)

1. For each security zone defined in the configuration file of the server, click the **[!UICONTROL Add]** button. 
1. In the **[!UICONTROL Internal name]** field, enter the name of the zone defined in the **serverConf.xml** file. It corresponds to the **@name** attribute of the `<securityzone>`  element. Enter the label linked to the internal name in the  **Label**field.

   ![](assets/enum_addsecurityvalue.png)

1. Click OK and save the modifications.

Once the zones are defined and the **[!UICONTROL Security zone]** enumeration is configured, you need to link each operator to a security zone:

1. Click the **[!UICONTROL Administration > Access management > Operators]** node.
1. Select the operator whom you want to link a security zone to, and click the **[!UICONTROL Edit]** tab.
1. Go to the **[!UICONTROL Access rights]** tab and click the **[!UICONTROL Edit access parameters...]** link.

   ![](assets/zone_operator.png)

1. Select a zone from the **[!UICONTROL Authorized connection zone]** drop-down list

   ![](assets/zone_operator_selection.png)

1. Click **[!UICONTROL OK]** and save the modifications to apply these changes.



## Recommendations

* Make sure that your reverse proxy in not allowed in subNetwork. If it is the case, **all** traffic will be detected as coming from this local IP, so will be trusted.

* Minimize the use of sessionTokenOnly="true":

  * Warning: If this attribute is set to true, the operator can be exposed to a **CRSF attack**.
  * In addition, the sessionToken cookie is not set with an httpOnly flag, so some client-side javascript code can read it.
  * However Message Center on multiple execution cells needs sessionTokenOnly: create a new security zone with sessionTokenOnly set to "true" and add **only the needed IP(s)** in this zone.

* When possible, set all allowHTTP, showErrors to be false (not for localhost) and check them.

  * allowHTTP = "false": forces operators to use HTTPS
  * showErrors = "false": hides technical errors (including SQL ones). It prevents displaying too much information, but reduces the capability for the marketer to solve mistakes (without asking for more information from an administrator)

* Set allowDebug to true only on IPs used by marketing users/administrators who need to create (in fact preview) surveys, webApps and reports. This flag allows these IPs to get relay rules displayed and to debug them.

* Never set allowEmptyPassword, allowUserPassword, allowSQLInjection to true. These attributes are only here to allow a smooth migration from v5 and v6.0:

  * **allowEmptyPassword** lets operators have an empty password. If this is the case for you, notify all your operators to ask them to set a password with a deadline. Once this deadline has passed, change this attribute to false.

  * **allowUserPassword** lets operators send their credentials as parameters (so they will be logged by apache/IIS/proxy). This feature was used in the past to simplify API usage. You can check in your cookbook (or in the specification) whether some third-party applications use this. If so, you have to notify them to change the way they use our API and as soon as possible remove this feature.

  * **allowSQLInjection** lets the user perform SQL injections by using an old syntax. As soon as possible carry out the corrections described in [this page](../../migration/using/general-configurations.md) to be able to set this attribute to false. You can use /nl/jsp/ping.jsp?zones=true to check your security zone configuration. This page displays the active status of security measures (computed with these security flags) for the current IP.

* HttpOnly cookie/useSecurityToken: refer to **sessionTokenOnly** flag.

* Minimize IPs added to the allow list: Out of the box, in security zones, we have added the 3 ranges for private networks. It is unlikely that you will use all of these IP addresses. So keep only the ones that you need.

* Update webApp/internal operator to be only accessible in localhost.
