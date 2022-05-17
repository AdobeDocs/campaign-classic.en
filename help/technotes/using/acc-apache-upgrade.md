---
product: campaign
title: Technote - Adobe Campaign - Apache version security update
description: Adobe Campaign - Apache version security update
hide: yes
hidefromtoc: yes
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
---
# Adobe Campaign - Apache version security update {#apache-update}

>[!CAUTION]
>This article applies to: Campaign Classic v7 Managed Services customers, Campaign v8 customers and Campaign Standard customers.

Adobe Campaign works with 3rd party tools, and compatibility is updated on a regular basis, in order to implement supported versions only, and benefit from the latest fixes and improvements. 

Adobe Campaign includes Apache Tomcat which acts as the entry point in the application server via HTTP, and is integrated with Apache Web server. The Apache Software Foundation has released Apache HTTP Server 2.4.53. This version addresses vulnerabilities which may allow a remote attacker to take control of an affected system. Learn more in [Apache 2.4.53 annoucement](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

The Adobe Campaign team will conduct the Apache version security upgrade activity by **June 15, 2022** to mitigate this Apache vulnerability and make your instance environment more secure. This upgrade applies to all Campaign Classic v7 Managed Services customers, Campaign v8 and Campaign Standard customers running on a vulnerable version of Apache HTTP Server. If you are impacted, Adobe already contacted you to inform you about this upgrade.

This upgrade is expected to run automatically outside of your normal business hours for you to continue using the Campaign service without any disruption. 

Your non-production instance(s) will be upgraded by our teams first before we upgrade your production instance(s). Since this is an automatic upgrade process owned by Adobe, there is no action required from your side. However, if you experience any issues, please contact [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).   


>[!NOTE]
>This upgrade requires to restart the Apache web server. The downtime will not exceed 10 minutes within the time slot mentioned below.
> 
  
## Frequently Asked Questions {#apache-faq}

* **Why is this a mandatory upgrade?**

    The current Apache version is vulnerable and has a potential security threat. It is important for your Campaign instance(s) to be upgraded to the latest applicable Apache version to address the security risk. 

* **Which customers are targeted for security upgrades?**

    All the customers using Campaign environments implemented on older Apache versions are upgraded to the latest applicable Apache version.

* **What is the expected downtime?**

    The expected downtime is under 10 minutes.  

* **Are there any actions required by the customer for this security upgrade?** 
    
    No actions is required since the security upgrade will run automatically. 

* **What is the impact on the running campaigns/workflows during the maintenance window?**

    During the maintenance window, the workflow and mail services will both be stopped, and the scheduled activities will not be running. Any ongoing activities or running processes will be on halt during the downtime until the server restarts. Once the activity is completed and the server is restarted, all services will resume.

* **What validations need to be run by the customers?** 
    
    No specific testing is needed for this security upgrade. In case any issue is observed, please reach out to [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Can I request a change in Date/Time to the scheduled security upgrade slot?** 
    
    Since this is a security fix, we strongly recommend you adapt to the existing schedule.  


For any other question, you can reach out to [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).
