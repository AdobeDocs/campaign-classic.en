# Campaign Classic v7 FAQ Consolidation - Summary of Changes

## Overview
This document summarizes the consolidation of Campaign Classic v7 FAQ pages, focusing on v7-specific content and redirecting users to the comprehensive Campaign v8 FAQ for common topics.

## Changes Made

### 1. New File Created

**`platform/using/faq-campaign-classic-v7.md`** - A new consolidated FAQ focused exclusively on Campaign Classic v7-specific topics:

- **v7 Architecture & Deployment**
  - Hosting models (On-premise, Hosted, Hybrid)
  - Differences between deployment types
  - Migration from on-premise/hybrid to Managed Services
  
- **Build Upgrades (v7 specific)**
  - What is a build upgrade
  - How to check v7 version
  - Upgrade process for on-premise vs hosted customers
  
- **v7-Specific Configuration**
  - Language selection (fixed at instance creation in v7)
  - Security zones configuration (on-premise/hybrid)
  - LDAP integration (on-premise/hybrid only)
  - Security best practices for on-premise
  - Client console cache clearing
  
- **Migration Guidance**
  - Should I migrate from v7 to v8?
  - Key considerations for migration
  
- **Getting Help**
  - Links to v7 documentation
  - Prominent redirect to Campaign v8 Comprehensive FAQ for common topics

### 2. Updated File

**`platform/using/faq-build-upgrade.md`** - Updated to clarify it's v7-specific:
- Changed title to include "(Campaign Classic v7)"
- Added note at the top redirecting users to v8 Comprehensive FAQ for common questions
- Kept existing detailed content about build upgrade process (still relevant for v7 on-premise/hybrid customers)

### 3. Updated TOC

**`TOC.md`** - Simplified FAQ section from 12 pages to 2 pages:

**Before:**
```
+ Frequently Asked Questions {#faq}
     + [Top questions](platform/using/common-questions.md)
     + [Global concepts](platform/using/faq-key-concepts.md)
     + [Build upgrade](platform/using/faq-build-upgrade.md)
     + [Privacy](platform/using/privacy-faq.md)
     + [Audiences](platform/using/faq-audiences.md)
     + [Design messages](platform/using/faq-designing.md)
     + [Send messages](platform/using/faq-messages.md)
     + [Workflows](platform/using/faq-workflows.md)
     + [Configuration](platform/using/faq-campaign-config.md)
     + [Reports](platform/using/faq-reporting.md)
     + [Development](platform/using/faq-developers.md)
```

**After:**
```
+ Frequently Asked Questions {#faq}
     + [Campaign Classic v7 Specific FAQ](platform/using/faq-campaign-classic-v7.md)
     + [Build upgrade](platform/using/faq-build-upgrade.md)
```

### 4. Deleted Files

The following 10 FAQ files were removed as their content is now either:
- Consolidated in the new v7-specific FAQ, OR
- Covered comprehensively in the Campaign v8 FAQ

**Deleted files:**
1. `platform/using/common-questions.md` - General questions covered in v8 FAQ
2. `platform/using/faq-key-concepts.md` - General concepts covered in v8 FAQ
3. `platform/using/privacy-faq.md` - Privacy topics covered in v8 FAQ
4. `platform/using/faq-audiences.md` - Audience management covered in v8 FAQ
5. `platform/using/faq-designing.md` - Message design covered in v8 FAQ
6. `platform/using/faq-messages.md` - Sending messages covered in v8 FAQ
7. `platform/using/faq-workflows.md` - Workflows covered in v8 FAQ
8. `platform/using/faq-campaign-config.md` - General config covered in v8 FAQ
9. `platform/using/faq-reporting.md` - Reporting covered in v8 FAQ
10. `platform/using/faq-developers.md` - Developer topics covered in v8 FAQ

## Rationale

### Why These Changes?

1. **Campaign v8 has a comprehensive FAQ** covering all common Campaign topics (workflows, deliveries, audiences, personalization, reporting, etc.)

2. **Avoid content duplication** - No need to maintain the same answers in both v7 and v8 documentation

3. **Focus v7 docs on v7-specific topics:**
   - On-premise and hybrid deployment (v8 is cloud-only)
   - v7 architecture and hosting models
   - v7-specific configurations (LDAP, security zones)
   - Build upgrade process for on-premise/hybrid customers
   - Migration considerations from v7 to v8

4. **Better user experience** - Clear signposting to comprehensive v8 FAQ for common questions, with v7 FAQ focused on what's unique to v7

## Topics Redirected to v8 Comprehensive FAQ

The following topics are now directed to the Campaign v8 Comprehensive FAQ:

- **Getting Started**: Download Campaign, connect to Campaign, user interface basics, permissions
- **Profiles and Audiences**: Create recipients, import profiles, targeting, lists, deduplication
- **Message Design**: Email design, templates, personalization, multilingual messages
- **Testing and Sending**: Delivery analysis, proofs, approval process, tracking, reports
- **Workflows**: Creating workflows, monitoring, automation, data import
- **Campaign Settings**: CRM connectors, external databases (FDA), tracking setup
- **Reporting**: Creating reports, cubes, descriptive analysis
- **Developers**: Data model, schemas, APIs, packages
- **Privacy**: GDPR, consent management, data deletion

## Link to Campaign v8 Comprehensive FAQ

All redirects point to:
**https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html**

This comprehensive FAQ includes 200+ questions organized by topic with expandable answers, search functionality, and extensive cross-linking.

## Next Steps

1. **Review the new v7-specific FAQ** to ensure all v7-unique content is covered
2. **Test the links** to the v8 Comprehensive FAQ
3. **Consider adding a banner/note** to other v7 pages mentioning the comprehensive v8 FAQ for common questions
4. **Update any internal links** that pointed to the deleted FAQ pages

## Benefits

✅ **Reduced maintenance** - Only one comprehensive FAQ to maintain for common topics  
✅ **Clearer user journey** - v7 users know where to go for v7-specific vs. general questions  
✅ **Better content quality** - Focus v7 docs on what makes v7 unique  
✅ **Easier migration path** - Clear guidance on v7 vs. v8 differences  
✅ **Simplified navigation** - 2 FAQ pages instead of 12  

## Files Modified

- **Created**: `platform/using/faq-campaign-classic-v7.md`
- **Updated**: `platform/using/faq-build-upgrade.md`, `TOC.md`
- **Deleted**: 10 FAQ files (listed above)

---

**Date**: December 1, 2025  
**Prepared by**: AI Assistant for Alice Simonet Nkouka

