---
product: campaign
title: Technote - Adobe Campaign system upgrades
description: Adobe Campaign system upgrade
hide: yes
hidefromtoc: yes
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
---
# Adobe Campaign 2023 environment upgrades {#ac-system-upgrade}

Campaign infrastructure relies on third-party systems which must be regularly updated with the latest versions and fixes. These updates are mandatory to ensure continuity of service and secure Campaign environments from security risks. In addition, a Campaign upgrade is required to ensure compatibility with third-party system changes.

As a **Hosted or Managed Cloud Services customer**, Adobe informs you about these upgrades when they are needed. You will be required to upgrade your environments in accordance with the recommendations to ensure compliance.

As an **On-premise or Hybrid customer**, Adobe highly recommends that you to upgrade your system and Campaign versions according to the same calendar. 

For security reasons, you must [install the latest Campaign build](#ac-upgrade), and then upgrade your [operating system](#os-upgrade) and/or your [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>For any questions about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). See also the [Build upgrade FAQ](../../platform/using/faq-build-upgrade.md).
>

## Campaign build upgrade {#ac-upgrade}

**Are you impacted?**

If you are impacted by the [operating system upgrade](#os-upgrade) and/or the [database system upgrade](#pg-upgrade) detailed below, you must upgrade your Campaign environments to [the latest 7.3.2 version](../../rn/using/latest-release.md#release-7-3-2), which is compatible with these systems.

**How to update?**

* As a hosted or Managed Cloud Services customer, Adobe will contact you and upgrade your Campaign version.
* As a hybrid customer, Adobe will inform you of the scheduled build upgrade dates for your mid-sourcing environment. You must also upgrade your marketing environment to that same version.
* As an on-premise customer, you are requested to upgrade your Campaign environments to the latest 7.3.2 build. 


## Operating system upgrade {#os-upgrade}

**Are you impacted?**

If you are running Campaign on a Debian operating system, to benefit from latest Debian security updates, you need to move your Campaign infrastructure to **Debian 11**. Note that security support for Debian 9 will be available until June 30, 2023.

**How to update?**

* As a hosted or Managed Cloud Services customer, Adobe will contact you and upgrade your environment.
* As a hybrid customer, Adobe will inform you of the scheduled upgrade dates for your mid-sourcing environment. If your marketing environment is also running on Debian, you must upgrade it to Debian 11 too.
* As an on-premise customer, you are requested to upgrade your environments to Debian 11. 

## Database system upgrade {#pg-upgrade}

**Are you impacted?**

If your database system for Campaign is PostgreSQL, to benefit from latest PostgreSQL innovations and security updates, you need to upgrade to **PostgreSQL 14**. Note that PostgreSQL 11 will reach End Of Life on November 9, 2023.

**How to update?**

* As a hosted or Managed Cloud Services customer, Adobe will contact you and upgrade your database system from PostgreSQL 11 to PostgreSQL 14.
* As a hybrid customer, if your marketing database system is PostgreSQL, you must upgrade it to PostgreSQL 14.
* As an on-premise customer, you are requested to upgrade your database system to PostgreSQL 14. 


## Useful links

* [Upgrade your environment](../../production/using/build-upgrade.md)
* [Build upgrade FAQ](../../platform/using/faq-build-upgrade.md)
* [Download the latest Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Make the new Client Console available to users](../../installation/using/client-console-availability-for-windows.md)
