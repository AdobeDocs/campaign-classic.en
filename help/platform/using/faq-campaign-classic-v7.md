---
product: campaign
title: Campaign Classic FAQ
description: Questions specific to Adobe Campaign Classic v7 architecture, deployment, and features
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
---
# Campaign Classic v7 FAQ {#campaign-classic-v7-faq}

This FAQ addresses questions specific to Adobe Campaign Classic v7 architecture, deployment models, and v7-specific features.

**For comprehensive answers to common Campaign questions** (workflows, deliveries, audiences, reporting, personalization, etc.), please refer to the [**Campaign v8 Comprehensive FAQ**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, which provides detailed answers organized by topic.

## Campaign Classic v7 Architecture & Deployment {#v7-architecture}

### What are the hosting models available in Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 offers three deployment models:

* **Hosted (Managed Services)** - Fully managed by Adobe on Adobe infrastructure
* **On-premise** - Installed and managed on your own infrastructure
* **Hybrid** - Mid-sourcing architecture with mix of cloud and on-premise components

Each deployment model has different capabilities and management responsibilities. The availability of modules, options, and configurations depends on your deployment type.

[Click here to learn more](../../installation/using/hosting-models.md) about hosting models and their differences.

**Note:** Campaign v8 is exclusively available as Managed Cloud Services. [Learn about Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### What are the differences when working on-premise vs. in a hosted environment? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 comes with a set of modules and options. The availability of these modules and their configuration depends on the [type of deployment](../../installation/using/hosting-models.md) of your installation: hosted (Managed Services), hybrid or on-premise.

Key differences:

* **On-premise** - Full control over installation, infrastructure, and configuration. Requires internal IT resources for maintenance, upgrades, and security.
* **Hosted/Managed Services** - Infrastructure and maintenance managed by Adobe. Automatic upgrades and enhanced security. Limited direct server access.
* **Hybrid** - Combines benefits of both models. Marketing instance hosted by Adobe, execution/mid-sourcing managed separately.

[Click here for the full capability matrix](../../installation/using/capability-matrix.md).

### How do I migrate from on-premise/hybrid to Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Migrating to Adobe Managed Services provides improved scalability, security, and reduced IT overhead. It's often a stepping stone before transitioning to Campaign v8.

**Key points:**

* No automated migration tool available - manual planning and execution required
* Adobe Professional Services support highly recommended
* Benefits include cloud infrastructure, automatic security patches, expert support, and easier path to v8
* Migration involves due diligence, environment audit, data cleanup, stage migration, and production cutover

**Getting started:** Contact your Adobe representative to assess your environment and develop a detailed migration plan with Adobe Professional Services.

Learn more about [migrating to Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Build Upgrades (Campaign Classic v7) {#build-upgrades-v7}

### What is a build upgrade in Campaign Classic v7? {#what-is-a-build-upgrade-v7}

A Build Upgrade is when the Adobe Campaign Classic v7 software is updated to the latest secure build number, yet stays in the same major/minor build level. For example: Campaign Classic v7 build 9026 to Campaign v7 build 9032.

Adobe Campaign is regularly updated. Minor versions are released with new features, improvements and fixes. In addition, builds with cumulative fixes only are periodically released.

Learn more [in this section](../../rn/using/rn-overview.md).

### How can I upgrade Campaign Classic v7 to the latest version? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic uses a range of technology to deliver value. This combination of technologies requires you to upgrade your Campaign Classic v7 instance(s) regularly to ensure the most up-to-date versions are being used to deliver superior security, stability, and performance.

**For hosted customers:** You automatically benefit from Campaign yearly upgrade with the latest stable version. Adobe manages the upgrade process and coordinates timing with you.

**For on-premise/hybrid customers:** You are responsible for performing upgrades. Adobe strongly recommends upgrading at least once per year.

[Read this section](../../production/using/build-upgrade.md) to learn how to update your environment and read [Build Upgrade FAQ](../../platform/using/faq-build-upgrade.md) for detailed questions on this specific topic.

### What is the latest version of Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

The latest Campaign Classic v7 version, including new features and documentation, is detailed in the latest [Release Notes](../../rn/using/latest-release.md).

### How do I know which version of Campaign Classic v7 I am running? {#how-do-i-know-which-version-v7}

Check your version and build number from the **[!UICONTROL Help > About...]** menu in the Adobe Campaign Client console. The **[!UICONTROL About]** box contains detailed information on the version and build you are running for both the console and the server.

Learn more [in this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Is a build upgrade the same as a version upgrade? {#is-build-upgrade-same-as-version-upgrade}

No. A build upgrade is an incremental update within a given major version, whereas a version upgrade is a change from one major version to another. Build upgrades are straightforward and typically do not involve major architectural, technical, or data model changes.

Version upgrades (e.g., v7 to v8) usually come with significant technical changes and may require configuration changes or partial re-implementation depending on your customizations.

## Campaign Classic v7 Configuration {#v7-configuration}

### Can I change the language of Campaign Classic v7 interface? {#can-i-change-language-v7}

Campaign Classic v7 language is selected when creating the instance. **You cannot change it afterwards.**

Adobe Campaign v7 user interface is available in 4 languages: English, French, German and Japanese. The client console and the server must be set with the same language. Each Campaign Classic v7 instance can only run in one language.

For English, when installing Campaign v7, you can select either US English or UK English: they differ on date and time formats.

[Learn more in this section](../../installation/using/creating-an-instance-and-logging-on.md).

**Note:** Campaign v8 Web UI allows users to change their interface language independently. [Learn more](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### How can I configure security zones in Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

The Security Zones self-service interface can be used to manage entries in the VPN Security Zone configuration of an Adobe Campaign Classic v7 deployment. This is primarily relevant for on-premise and hybrid deployments.

Read [this section](../../installation/using/security-zones.md) to learn about security zones in Campaign v7.

[Click here to learn more](https://helpx.adobe.com/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} about the Security Zone self-service UI.

**Note:** Hosted/Managed Services customers should contact Adobe to configure security zones.

### Can Adobe Campaign Classic v7 integrate with LDAP? {#can-campaign-classic-integrate-with-ldap}

Yes. As an **on-premise/hybrid customer**, you can integrate Campaign Classic v7 with your LDAP directory for centralized authentication and user management.

This integration allows:

* Users to authenticate against your corporate LDAP directory
* Centralized user and rights management
* Automatic synchronization of user groups and permissions
* Single sign-on capabilities

[Click here to learn how](../../installation/using/connecting-through-ldap.md) to set up LDAP integration in Campaign Classic v7.

**Note:** LDAP integration is available for on-premise and hybrid deployments. Hosted customers use Adobe IMS for authentication.

### What are security best practices for on-premise deployments? {#security-best-practices-on-premise}

On-premise and hybrid deployments require additional security configuration and hardening compared to hosted environments.

**Key security areas:**

* Network security and firewall configuration
* Database access and security
* Operating system hardening
* File permissions and access controls
* Security zones configuration
* Encryption (data at rest and in transit)
* User access management
* Regular security patching
* Audit logging and monitoring

Read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html){target="_blank"} to discover key elements to check regarding security configuration and hardening for on-premise deployments.

### How do I clear the client console cache? {#how-do-i-clear-console-cache}

Clearing the Campaign client console cache resolves many common display and functionality issues. The cache stores local configuration files that can sometimes become corrupted or outdated.

**When to clear cache:**

* New branding elements not displaying correctly
* Export/import functions failing unexpectedly
* Interface elements not updating after configuration changes
* Performance issues or slow console response
* After upgrading to a new client console version

**How to clear cache:**

1. **Soft Cache Clear (try this first):**
   * Open the Campaign client console
   * Go to **[!UICONTROL File]** menu
   * Select **[!UICONTROL Clear the local cache...]**
   * Confirm the action when prompted
   * Restart the client console

2. **Hard Cache Clear (if soft clear doesn't resolve the issue):**
   * Perform Soft Cache Clear first
   * Logout and close the client console completely
   * Navigate to:
     * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
     * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Delete all XML files named `nlclient-config-<alphanumerical value>.xml` and associated folders
   * **Important:** Do NOT delete `nlclient_cnx.xml` file
   * Restart client console

Learn more in [Campaign client console documentation](../../platform/using/launching-adobe-campaign.md).

## Getting Help {#getting-help}

### Where can I find more information about Campaign Classic v7? {#where-to-find-more-info-v7}

**Documentation and resources:**

* [Campaign Classic v7 Documentation](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html){target="_blank"} - Complete documentation
* [Campaign Classic v7 Release Notes](../../rn/using/latest-release.md) - Latest release information
* [Campaign Classic Compatibility Matrix](../../rn/using/compatibility-matrix.md) - Supported systems and versions
* [Campaign Classic Tutorials](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html){target="_blank"} - Video tutorials

**For common Campaign questions:**

Please refer to the [**Campaign v8 Comprehensive FAQ**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"} which provides detailed answers on:

* Getting Started with Campaign
* Profiles and Audiences
* Message Design and Delivery
* Workflows and Automation
* Reporting and Analytics
* Campaign Settings and Configuration
* Developer Resources
* Privacy and Compliance

**Community and support:**

* [Campaign Community Forums](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe Support](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Control Panel (Hosted customers)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html){target="_blank"}

### Should I migrate from Campaign Classic v7 to Campaign v8? {#should-i-migrate-to-v8}

Campaign v8 is Adobe's strategic platform, ideal for organizations needing high-volume campaigns, modern web UI, cloud-native benefits, and long-term support. Campaign Classic v7 will reach End of Support in the coming years.

**Consider migrating to Campaign v8 if you:**

* Handle large data volumes or experience performance issues
* Want to reduce IT overhead and infrastructure management (v8 is Managed Cloud Services only)
* Need modern UI and Adobe Experience Platform integration
* Want future-proof technology with automatic updates
* Are currently on hosted/managed services (easier migration path)

**Important considerations:**

* Campaign v8 is exclusively available as Managed Cloud Services (no on-premise/hybrid options)
* Requires planning for migration of customizations and integrations
* FFDA architecture brings performance but requires some workflow/API adaptations

**Next steps:** Contact your Adobe representative to assess migration readiness and access migration tools.

Learn more:

* [Campaign v8 Overview](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Transition from Campaign Classic v7 to v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Campaign v8 Comprehensive FAQ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**For detailed answers to common Campaign questions on workflows, deliveries, audiences, reporting, personalization, and more**, visit the [Campaign v8 Comprehensive FAQ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.
