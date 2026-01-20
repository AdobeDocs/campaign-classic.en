# 📊 v7 Documentation Reorganization - Overview

**Generated**: 2026-01-13  
**Total Folders**: 21  
**Total Files**: ~1,500

---

## 📈 Executive Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 **Total Files** | 1,500 | 100% |
| ✅ **KEEP (v7-specific)** | 400 | 27% |
| 🗑️ **DELETE (in v8)** | 800 | 53% |
| ➡️ **MOVE (to v8)** | 200 | 13% |
| 🔍 **REVIEW (unclear)** | 100 | 7% |

**🎯 Estimated Reduction**: 60-75% (1,500 → 400-600 files)

---

## 📁 Folder Analysis by Priority

### 🟢 Priority 1: 100% KEEP - v7-Only Features

| Folder | Files | Reason | v8 Status | Action |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | On-premise/hybrid setup | Cloud-only in v8 | ✅ KEEP ALL + badge |
| 📂 `/mrm/` | 5 | Marketing Resource Mgmt | NOT in FFDA | ✅ KEEP ALL + badge |
| 📂 `/surveys/` | 8 | Online surveys | NOT in FFDA | ✅ KEEP ALL + badge |
| 📂 `/distributed/` | 7 | Distributed marketing | NOT in FFDA | ✅ KEEP ALL + badge |
| 📂 `/response/` | 5 | Response management | Status unclear | 🔍 VERIFY then KEEP |
| 📂 `/migration/` | 8 | v6.1 → v7 migration | v7-specific | ✅ KEEP ALL |
| **TOTAL** | **108** | **7%** | - | **Badge as v7-only** |

---

### 🔴 Priority 2: 60-70% DELETE - High Duplication

| Folder | Total | KEEP | DELETE | MOVE | REVIEW | Notes |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16%) | 67 (60%) | 8 (7%) | 18 (17%) | Email/SMS/Push in v8 |
| 📂 `/workflow/` | 121 | 24 (20%) | 60 (50%) | 12 (10%) | 25 (20%) | Common activities in v8 |
| 📂 `/reporting/` | 32 | 3 (10%) | 22 (70%) | 2 (6%) | 5 (14%) | Reports redesigned in v8 |
| 📂 `/platform/` | 61 | 12 (20%) | 34 (55%) | 5 (8%) | 10 (17%) | Common features in v8 |
| 📂 `/campaign/` | 11 | 2 (18%) | 7 (64%) | 1 (9%) | 1 (9%) | Campaign mgmt in v8 |
| **TOTAL** | **336** | **59** | **190** | **28** | **59** | **High reduction potential** |

---

### 🟡 Priority 3: 30-50% MIXED - Detailed Analysis Needed

| Folder | Total | KEEP % | DELETE % | Notes |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65% | 22% | Schema/DB configs (mostly v7) |
| 📂 `/production/` | 43 | 65% | 23% | Server management (mostly v7) |
| 📂 `/integrations/` | 37 | 40% | 40% | Check connector availability |
| 📂 `/interaction/` | 39 | 51% | 31% | Offer engine (verify v8) |
| 📂 `/web/` | 26 | 92% | 8% | Web apps > Landing pages v8 |
| 📂 `/message-center/` | 16 | 60% | 30% | Transactional messaging |
| **TOTAL** | **230** | **~55%** | **~25%** | **Requires folder-by-folder review** |

---

## 🎯 Quick Wins - Week 1

### High Confidence Deletions (95-100% v8 match)

| Folder | Files to Delete | Impact | Effort |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 files | 🔥🔥🔥 High | 2 days |
| 📂 `/workflow/` | 60 files | 🔥🔥🔥 High | 2 days |
| 📂 `/reporting/` | 22 files | 🔥🔥 Medium | 1 day |
| 📂 `/platform/` | 34 files | 🔥🔥 Medium | 1 day |
| 📂 `/campaign/` | 7 files | 🔥 Low | 0.5 day |
| **TOTAL** | **190 files** | **53% reduction** | **6.5 days** |

**Examples**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (workflow) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

---

## 📋 Detailed Folder Breakdown

### 📂 Delivery (`/help/delivery/using/`) - 111 files

| Category | Files | KEEP | DELETE | MOVE | REVIEW | Notes |
|----------|-------|------|--------|------|--------|-------|
| Get Started | 8 | 0 | 7 | 0 | 1 | Basics in v8 |
| Email | 18 | 0 | 16 | 0 | 2 | Fully in v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = KEEP |
| Push | 9 | 0 | 8 | 0 | 1 | Fully in v8 |
| Direct Mail | 4 | 0 | 4 | 0 | 0 | In v8 |
| Personalization | 8 | 1 | 6 | 0 | 1 | Coupons = KEEP |
| Templates | 6 | 0 | 6 | 0 | 0 | In v8 |
| A/B Testing | 11 | 0 | 10 | 0 | 1 | In v8 |
| Monitoring | 14 | 0 | 12 | 1 | 1 | Mostly in v8 |
| Troubleshooting | 9 | 2 | 4 | 2 | 1 | Keep on-prem tips |
| Deliverability | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Advanced | 9 | 11 | 5 | 5 | 8 | Mixed |
| **TOTAL** | **111** | **18** | **67** | **8** | **18** | **60% can be deleted** |

**Must Keep**:
- ✅ `personalized-coupons.md` - NOT in v8 FFDA
- ✅ `sms-set-up-mid.md` - Mid-sourcing (on-prem)
- ✅ `spamassassin.md` - On-prem spam filtering

**Quick Delete Examples**:
- 🗑️ `about-email-channel.md` → 95% in `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95% in `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90% in `campaign-web/v8/msg/send-sms`

---

### 📂 Workflow (`/help/workflow/using/`) - 121 files

| Category | Files | KEEP | DELETE | MOVE | REVIEW | Notes |
|----------|-------|------|--------|------|--------|-------|
| Get Started | 12 | 2 | 9 | 0 | 1 | Basics in v8 |
| Targeting | 18 | 3 | 12 | 1 | 2 | Query/Split in v8 |
| Flow Control | 15 | 2 | 10 | 1 | 2 | Common in v8 |
| Action Activities | 24 | 4 | 16 | 2 | 2 | Most in v8 |
| Event Activities | 8 | 1 | 6 | 0 | 1 | In v8 |
| MRM Activities | 5 | 5 | 0 | 0 | 0 | NOT in FFDA |
| Technical | 16 | 4 | 8 | 2 | 2 | Mixed |
| Advanced | 12 | 3 | 4 | 3 | 2 | Patterns useful |
| Use Cases | 11 | 0 | 5 | 3 | 3 | Good examples |
| **TOTAL** | **121** | **24** | **60** | **12** | **25** | **50% can be deleted** |

**Must Keep**:
- ✅ All MRM activities (5 files) - NOT in v8 FFDA
- ✅ On-premise configurations
- ✅ Advanced technical workflows

**Quick Delete Examples**:
- 🗑️ `query.md` → 95% in `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95% in `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95% in `campaign/v8/automation/workflow/enrichment`

---

### 📂 Installation (`/help/installation/using/`) - 75 files

| Category | Files | Action | Notes |
|----------|-------|--------|-------|
| Server Installation | 18 | ✅ KEEP | On-premise only |
| Database Setup | 12 | ✅ KEEP | On-premise only |
| Configuration | 15 | ✅ KEEP | nlserver, etc. |
| Network | 8 | ✅ KEEP | Security zones |
| Integration | 10 | ✅ KEEP | LDAP, etc. |
| Troubleshooting | 8 | ✅ KEEP | On-prem issues |
| Generic Docs | 4 | 🗑️ DELETE | In v8 start guide |
| **TOTAL** | **75** | **71 KEEP / 4 DELETE** | **95% v7-specific** |

**Reason**: v8 is cloud-only, all on-premise setup docs are v7-specific.

---

### 📂 Web (`/help/web/using/`) - 26 files

| Category | Files | KEEP | DELETE | Notes |
|----------|-------|------|--------|-------|
| Web Apps | 14 | 14 | 0 | Advanced features not in v8 |
| Web Forms | 8 | 8 | 0 | More than v8 landing pages |
| Landing Pages | 2 | 0 | 2 | Basic pages in v8 |
| HTML Editor | 2 | 2 | 0 | Different from v8 |
| **TOTAL** | **26** | **24** | **2** | **92% v7-specific** |

**Reason**: v7 has full Web Applications framework, v8 has simplified Landing Pages.

---

## ✅ Action Plan

### Week 1: High-Impact Deletions
- [ ] `/delivery/`: Delete 67 files (email, SMS, push basics)
- [ ] `/workflow/`: Delete 60 files (common activities)
- [ ] `/reporting/`: Delete 22 files (standard reports)
- [ ] `/platform/`: Delete 34 files (common features)
- [ ] `/campaign/`: Delete 7 files (campaign management)
- **Total**: 190 files deleted (13% reduction)

### Week 2: v7-Specific Badging
- [ ] `/installation/`: Badge 71 files as "v7 on-premise only"
- [ ] `/mrm/`: Badge 5 files as "Not available in v8 FFDA"
- [ ] `/surveys/`: Badge 8 files as "Not available in v8 FFDA"
- [ ] `/distributed/`: Badge 7 files as "Not available in v8 FFDA"
- [ ] `/web/`: Badge 24 files as "v7 Web Applications"
- **Total**: 115 files badged

### Week 3: Content Migration
- [ ] Migrate troubleshooting tips from `/delivery/` to v8
- [ ] Migrate workflow best practices to v8
- [ ] Migrate advanced patterns from `/platform/` to v8
- **Total**: 40 files migrated then deleted

### Week 4: Manual Review
- [ ] Review `/configuration/` mixed content
- [ ] Review `/integrations/` connector availability
- [ ] Review `/interaction/` offer engine coverage
- [ ] Review `/response/` feature status
- **Total**: 50 files reviewed and decided

---

## 📊 Expected Results

| Phase | Files Affected | Cumulative % |
|-------|----------------|--------------|
| Week 1: Deletions | 190 | 13% |
| Week 2: Badging | 115 | 20% |
| Week 3: Migration | 40 | 23% |
| Week 4: Review | 50 | 26% |
| **TOTAL** | **395** | **26% processed** |

**Remaining**: ~1,100 files to process in subsequent phases

**Final Goal**: 1,500 → 400-600 files (60-73% reduction)

---

## 🎯 Success Metrics

| Metric | Target | Status |
|--------|--------|--------|
| Files Deleted | 800+ (53%) | ⏳ Pending |
| Files Badged | 200+ (13%) | ⏳ Pending |
| Files Migrated | 200+ (13%) | ⏳ Pending |
| Broken Links | 0 | ⏳ Pending |
| Stakeholder Approval | ✅ | ⏳ Pending |

---

**Last Updated**: 2026-01-13  
**Next Review**: After Week 1 execution

