# PROMPT 1: Vue d'Ensemble - Tous les Folders v7

**Génère un rapport Markdown avec vue d'ensemble de tous les dossiers v7**

---

## 📋 COPIER CE PROMPT

```markdown
# v7 Documentation Reorganization - Overview Report

Generate a comprehensive overview of all v7 documentation folders with reorganization recommendations.

## REPOSITORIES
- **v7**: /Users/florentvignes/Documents/GitHub/campaign-classic.en/
- **v8**: /Users/florentvignes/Documents/GitHub/campaign.en/
- **v8 Web**: /Users/florentvignes/Documents/GitHub/campaign-web.en/

---

## TASK: Analyze ALL v7 Folders

Analyze these main v7 documentation folders:
- `/help/campaign/using/`
- `/help/campaign-opt/using/`
- `/help/configuration/using/`
- `/help/delivery/using/`
- `/help/distributed/using/`
- `/help/installation/using/`
- `/help/integrations/using/`
- `/help/interaction/using/`
- `/help/message-center/using/`
- `/help/migration/using/`
- `/help/mrm/using/`
- `/help/platform/using/`
- `/help/production/using/`
- `/help/reporting/using/`
- `/help/response/using/`
- `/help/rn/using/`
- `/help/social/using/`
- `/help/surveys/using/`
- `/help/technotes/using/`
- `/help/web/using/`
- `/help/workflow/using/`

---

## OUTPUT FORMAT: Markdown Report

Generate complete Markdown report with this structure:

### HEADER
\`\`\`markdown
# 📊 v7 Documentation Reorganization Overview

**Generated**: 2026-01-13  
**Total Folders Analyzed**: 21  
**Total Files**: ~X,XXX

---

## 📈 Executive Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 **Total Files** | X,XXX | 100% |
| ✅ **KEEP (v7-specific)** | XXX | XX% |
| 🗑️ **DELETE (in v8)** | XXX | XX% |
| ➡️ **MOVE (to v8)** | XXX | XX% |
| 🔍 **REVIEW (unclear)** | XXX | XX% |

**Estimated Reduction**: XX-XX% (X,XXX → XXX files)

---
\`\`\`

### FOLDER-BY-FOLDER ANALYSIS
\`\`\`markdown
## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content

| Folder | Files | Reason | v8 Status | Action |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | ~75 | On-premise/hybrid setup | Not in v8 | ✅ KEEP ALL + badge |
| 📂 `/mrm/` | ~5 | MRM not in FFDA | Exists but not FFDA | ✅ KEEP ALL + badge |
| 📂 `/surveys/` | ~8 | Surveys not in FFDA | Exists but not FFDA | ✅ KEEP ALL + badge |
| 📂 `/distributed/` | ~7 | Distributed marketing | Not in v8 FFDA | ✅ KEEP ALL + badge |
| 📂 `/response/` | ~5 | Response management | Status unclear | 🔍 REVIEW status |

**Total**: ~100 files (XX%)

---

### 🔴 60-70% DELETE - High Duplication

| Folder | Files | Keep | Delete | Reason |
|--------|-------|------|--------|--------|
| 📂 `/delivery/` | 111 | 18 (16%) | 67 (60%) | Standard features in v8 |
| 📂 `/workflow/` | 121 | 24 (20%) | 60 (50%) | Common activities in v8 |
| 📂 `/reporting/` | 32 | 3 (10%) | 22 (70%) | Reports in v8 |
| 📂 `/platform/` | 61 | 12 (20%) | 34 (55%) | Common features in v8 |
| 📂 `/campaign/` | 11 | 2 (15%) | 7 (60%) | Campaign mgmt in v8 |

**Total Deletions**: ~190 files

---

### 🟡 30-50% MIXED - Needs Analysis

| Folder | Files | Keep | Delete | Move | Review |
|--------|-------|------|--------|------|--------|
| 📂 `/configuration/` | 69 | 45 (65%) | 15 (22%) | 5 | 4 |
| 📂 `/production/` | 43 | 28 (65%) | 10 (23%) | 3 | 2 |
| 📂 `/integrations/` | 37 | 15 (40%) | 15 (40%) | 5 | 2 |
| 📂 `/interaction/` | 39 | 20 (51%) | 12 (31%) | 4 | 3 |
| 📂 `/web/` | 26 | 24 (92%) | 2 (8%) | 0 | 0 |

**Requires Manual Review**: ~11 files

---
\`\`\`

### DETAILED BREAKDOWN BY FOLDER
\`\`\`markdown
## 📋 Detailed Folder Breakdown

### 📂 Campaign (`/help/campaign/using/`)

**Total Files**: 11  
**v8 Equivalent**: `/campaign/campaigns/` + `/campaign-web/v8/campaigns/`

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 2 | 18% | v7-specific campaign features |
| 🗑️ DELETE | 7 | 64% | Campaign management in v8 |
| ➡️ MOVE | 1 | 9% | Best practices missing in v8 |
| 🔍 REVIEW | 1 | 9% | Check v8 coverage |

**Key Files**:
- ✅ `providers-stocks-and-budgets.md` - MRM related (KEEP)
- 🗑️ `about-marketing-campaigns.md` - Fully in v8 (DELETE)
- ➡️ `marketing-campaign-monitoring.md` - Good tips (MOVE)

**Recommendation**: Delete 7 files, keep 2, migrate 1

---

### 📂 Delivery (`/help/delivery/using/`)

**Total Files**: 111  
**v8 Equivalent**: `/campaign/send/` + `/campaign-web/v8/email/`, `/msg/`, `/send/`

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 18 | 16% | Coupons, spamassassin, mid-sourcing |
| 🗑️ DELETE | 67 | 60% | Email, SMS, Push in v8 |
| ➡️ MOVE | 8 | 7% | Troubleshooting tips |
| 🔍 REVIEW | 18 | 17% | Partial v8 coverage |

**Key v7-Specific Files**:
- ✅ `personalized-coupons.md` - Not in v8 FFDA
- ✅ `spamassassin.md` - On-prem only
- ✅ `sms-set-up-mid.md` - Mid-sourcing setup

**Recommendation**: High-value folder, significant reduction possible (60%)

---

### 📂 Workflow (`/help/workflow/using/`)

**Total Files**: 121  
**v8 Equivalent**: `/campaign/automation/workflow/` + `/campaign-web/v8/workflows/`

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 24 | 20% | MRM, on-prem configs |
| 🗑️ DELETE | 60 | 50% | Common activities in v8 |
| ➡️ MOVE | 12 | 10% | Best practices, patterns |
| 🔍 REVIEW | 25 | 20% | Mixed content |

**Quick Wins** (safe deletions):
- 🗑️ `query.md` - Query activity fully in v8
- 🗑️ `split.md` - Split activity fully in v8
- 🗑️ `enrichment.md` - Enrichment fully in v8
- 🗑️ `about-workflows.md` - Workflow basics in v8

**Recommendation**: Large folder, ~60 easy deletions

---

### 📂 Installation (`/help/installation/using/`)

**Total Files**: 75  
**v8 Equivalent**: NONE (v8 is cloud-only)

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 71 | 95% | On-premise/hybrid setup |
| 🗑️ DELETE | 4 | 5% | Generic docs in v8 |
| ➡️ MOVE | 0 | 0% | - |
| 🔍 REVIEW | 0 | 0% | - |

**100% v7-Specific Content**:
- Server installation
- Database setup
- nlserver configuration
- Network configuration
- Security zones

**Recommendation**: Keep almost everything, add v7-only badges

---

### 📂 MRM (`/help/mrm/using/`)

**Total Files**: 5  
**v8 Equivalent**: `/campaign/automation/mrm/` (exists but NOT in FFDA)

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 5 | 100% | MRM not in v8 FFDA |
| 🗑️ DELETE | 0 | 0% | - |
| ➡️ MOVE | 0 | 0% | - |
| 🔍 REVIEW | 0 | 0% | - |

**All Files v7-Specific** (keep for FFDA users):
- `about-marketing-resource-management.md`
- `controlling-costs.md`
- `creating-and-managing-tasks.md`
- `discussion-forums.md`
- `managing-marketing-resources.md`

**Recommendation**: Keep all, add badges

---

### 📂 Surveys (`/help/surveys/using/`)

**Total Files**: 8  
**v8 Equivalent**: `/campaign-web/v8/` (exists but NOT in FFDA)

| Status | Count | % | Details |
|--------|-------|---|---------|
| ✅ KEEP | 8 | 100% | Surveys not in v8 FFDA |
| 🗑️ DELETE | 0 | 0% | - |
| ➡️ MOVE | 0 | 0% | - |
| 🔍 REVIEW | 0 | 0% | - |

**Recommendation**: Keep all, add badges

---

[Continue for ALL 21 folders...]

---
\`\`\`

### PRIORITIZATION MATRIX
\`\`\`markdown
## 🎯 Reorganization Priorities

### Priority 1: High Impact, Low Risk (Week 1)

| Folder | Files to Delete | Impact | Risk | Effort |
|--------|----------------|--------|------|--------|
| 📂 `/delivery/` | 67 | 🔥🔥🔥 High | ✅ Low | 2 days |
| 📂 `/workflow/` | 60 | 🔥🔥🔥 High | ✅ Low | 2 days |
| 📂 `/reporting/` | 22 | 🔥🔥 Medium | ✅ Low | 1 day |
| 📂 `/platform/` | 34 | 🔥🔥 Medium | ✅ Low | 1 day |

**Total Impact**: ~183 files deleted (XX% reduction)

---

### Priority 2: Validation Required (Week 2)

| Folder | Action | Effort |
|--------|--------|--------|
| 📂 `/installation/` | Badge all as v7-only | 1 day |
| 📂 `/mrm/` | Badge all as v7-only | 2 hours |
| 📂 `/surveys/` | Badge all as v7-only | 2 hours |
| 📂 `/distributed/` | Badge all as v7-only | 2 hours |

**Total Impact**: ~100 files badged

---

### Priority 3: Content Migration (Week 3)

| Folder | Files to Migrate | Destination | Effort |
|--------|------------------|-------------|--------|
| 📂 `/delivery/` | 8 troubleshooting | v8/send/ | 1 day |
| 📂 `/workflow/` | 12 best practices | v8/workflows/ | 2 days |
| 📂 `/platform/` | 5 advanced patterns | v8/dev/ | 1 day |

**Total Impact**: 25 files migrated then deleted

---

### Priority 4: Manual Review (Week 4)

| Folder | Files | Focus |
|--------|-------|-------|
| 📂 `/configuration/` | 4 | Check schema/DB docs |
| 📂 `/integrations/` | 2 | Verify connector status |
| 📂 `/interaction/` | 3 | Check offer engine |
| 📂 `/response/` | 5 | Verify feature status |

**Total Impact**: 14 files reviewed

---
\`\`\`

### ACTION SUMMARY
\`\`\`markdown
## ✅ Action Summary

### Immediate Actions (High Confidence)

#### 🗑️ DELETE (~280 files - 60% of deletable content)
- [ ] `/delivery/`: 67 files → Standard features in v8
- [ ] `/workflow/`: 60 files → Common activities in v8
- [ ] `/reporting/`: 22 files → Reports in v8
- [ ] `/platform/`: 34 files → Common features in v8
- [ ] `/campaign/`: 7 files → Campaign mgmt in v8
- [ ] Other folders: ~90 files

#### ✅ KEEP + BADGE (~180 files - v7-specific)
- [ ] `/installation/`: 71 files → On-premise
- [ ] `/mrm/`: 5 files → Not in FFDA
- [ ] `/surveys/`: 8 files → Not in FFDA
- [ ] `/distributed/`: 7 files → Not in FFDA
- [ ] `/configuration/`: 45 files → Schema/DB configs
- [ ] Other v7-specific: ~44 files

#### ➡️ MOVE THEN DELETE (~40 files)
- [ ] Best practices from `/workflow/`: 12 files
- [ ] Troubleshooting from `/delivery/`: 8 files
- [ ] Advanced patterns from `/platform/`: 5 files
- [ ] Other valuable content: ~15 files

#### 🔍 REVIEW (~50 files)
- [ ] `/response/`: Verify feature status
- [ ] `/integrations/`: Check connector availability
- [ ] `/interaction/`: Verify offer engine coverage
- [ ] Partial matches: ~35 files

---

### Estimated Timeline

| Phase | Duration | Outcome |
|-------|----------|---------|
| **Week 1**: High-impact deletions | 5 days | ~280 files deleted |
| **Week 2**: Badging v7-specific | 3 days | ~180 files badged |
| **Week 3**: Content migration | 4 days | ~40 files migrated |
| **Week 4**: Manual review | 3 days | ~50 files decided |

**Total**: 4 weeks  
**Result**: ~1,500 → ~400 files (73% reduction)

---
\`\`\`

### RISK ASSESSMENT
\`\`\`markdown
## ⚠️ Risk Assessment

### Low Risk (Proceed with Confidence)

| Folder | Action | Risk Level | Mitigation |
|--------|--------|------------|------------|
| 📂 `/delivery/` | Delete 67 files | 🟢 Low | v8 comprehensive |
| 📂 `/workflow/` | Delete 60 files | 🟢 Low | Activities in v8 |
| 📂 `/reporting/` | Delete 22 files | 🟢 Low | Reports in v8 |

### Medium Risk (Validate Samples)

| Folder | Action | Risk Level | Mitigation |
|--------|--------|------------|------------|
| 📂 `/platform/` | Delete 34 files | 🟡 Medium | Check 3-5 samples |
| 📂 `/integrations/` | Mixed actions | 🟡 Medium | Verify connectors |

### High Risk (Manual Review Required)

| Folder | Action | Risk Level | Mitigation |
|--------|--------|------------|------------|
| 📂 `/response/` | Status unclear | 🔴 High | Verify in v8 first |
| 📂 `/configuration/` | Mixed content | 🔴 High | Schema expert review |

---
\`\`\`

### RECOMMENDATIONS
\`\`\`markdown
## 💡 Recommendations

### 1. Quick Wins First
Start with `/delivery/` and `/workflow/` folders:
- High file count (181 files)
- Clear duplication with v8
- Low risk
- 40% of total reduction

### 2. Parallel Workstreams
- **Stream 1**: Delete duplicates (weeks 1-2)
- **Stream 2**: Badge v7-specific (weeks 1-2)
- **Stream 3**: Migrate content (week 3)
- **Stream 4**: Manual review (week 4)

### 3. Validation Process
Before deleting:
1. ✅ Confirm v8 equivalent exists
2. ✅ Check no v7-specific mentions
3. ✅ Validate with SME (for first 3-5 per folder)
4. ✅ Update redirects.csv

### 4. Communication
- **Week 0**: Share overview with stakeholders
- **Week 1**: Daily progress updates
- **Week 2**: Mid-point review
- **Week 4**: Final validation

### 5. Rollback Plan
- Keep deleted files in git history
- Maintain list of deletions
- Can restore if needed

---
\`\`\`

### METRICS & TRACKING
\`\`\`markdown
## 📊 Success Metrics

### Quantitative Goals
- ✅ **Reduction**: 60-75% (1,500 → 400-600 files)
- ✅ **Timeline**: Complete in 4 weeks
- ✅ **Quality**: Zero broken links
- ✅ **Coverage**: All v7-specific content badged

### Progress Tracking

| Week | Files Deleted | Files Badged | Files Migrated | Cumulative % |
|------|---------------|--------------|----------------|--------------|
| 1 | 280 | 0 | 0 | 19% |
| 2 | 0 | 180 | 0 | 31% |
| 3 | 0 | 0 | 40 | 34% |
| 4 | 50 | 0 | 0 | 37% |
| **Total** | **330** | **180** | **40** | **37%** reduction |

---
\`\`\`

---

## END OF REPORT

Generate this complete markdown report analyzing all 21 v7 folders.

Include:
- ✅ Executive summary with totals
- ✅ Folder-by-folder breakdown
- ✅ Detailed analysis for each folder
- ✅ Prioritization matrix
- ✅ Action items with checkboxes
- ✅ Risk assessment
- ✅ Recommendations
- ✅ Success metrics

Make it:
- 📊 Data-driven with numbers
- 🎯 Actionable with clear next steps
- 📝 Complete for all folders
- ✅ Ready to present to stakeholders
```

---

## USAGE

1. **Copy the entire prompt above**
2. **Paste into Cursor**
3. **Run analysis**
4. **Get complete Markdown report**
5. **Save as**: `v7-reorganization-overview.md`

---

## OUTPUT PREVIEW

The report will be ~50-60 pages of detailed Markdown covering all 21 folders with:
- Executive summary
- Folder analysis
- Prioritization
- Action items
- Timeline
- Risks
- Metrics

Perfect for stakeholder presentations! 📊

