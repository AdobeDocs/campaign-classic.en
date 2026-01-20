# PROMPT 2: Analyse Détaillée d'un Folder

**Génère un rapport Markdown détaillé pour UN folder avec % de match**

---

## 📋 COPIER CE PROMPT

```markdown
# v7 Folder Detailed Analysis with Match Percentages

Generate detailed Markdown analysis for a specific v7 folder with v8 match percentages.

## TARGET FOLDER
📁 **Analyze**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

## REPOSITORIES
- **v7**: /Users/florentvignes/Documents/GitHub/campaign-classic.en/
- **v8**: /Users/florentvignes/Documents/GitHub/campaign.en/
- **v8 Web**: /Users/florentvignes/Documents/GitHub/campaign-web.en/

---

## OUTPUT FORMAT: Complete Markdown Report

Generate this structure:

### HEADER
\`\`\`markdown
# 📊 v7 Folder Analysis: Delivery

**Folder**: `/help/delivery/using/`  
**Generated**: 2026-01-13  
**Total Files**: XXX

---

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 **Total Files** | XXX | 100% |
| ✅ **KEEP** | XX | XX% |
| 🗑️ **DELETE** | XX | XX% |
| ➡️ **MOVE** | XX | XX% |
| 🔍 **REVIEW** | XX | XX% |

**Reorganization Impact**: XX files to delete (XX% reduction)

---
\`\`\`

### COMPLETE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

Organized by category (like Experience League):

### 🚀 Get Started

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 1 | [about-email-channel.md](file:///Users/.../about-email-channel.md) | [campaign-web/v8/email](https://experienceleague.adobe.com/en/docs/campaign-web/v8/email) | 95% | - | - | - | - | Email basics fully in v8 | 🗑️ DELETE |
| 2 | [communication-channels.md](file:///...) | [campaign-web/v8/msg](https://...) | 85% | [campaign/v8/send](https://...) | 75% | - | - | Channel overview in v8 | 🗑️ DELETE |
| 3 | [steps-about-delivery-creation-steps.md](file:///...) | [campaign-web/v8/msg/gs-deliveries](https://...) | 90% | - | - | - | - | Delivery process in v8 | 🗑️ DELETE |

### 📧 Email

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 4 | [creating-an-email-delivery.md](file:///...) | [campaign-web/v8/email/create-email](https://...) | 95% | - | - | - | - | Email creation fully documented | 🗑️ DELETE |
| 5 | [email-parameters.md](file:///...) | [campaign-web/v8/email/configure-and-send](https://...) | 85% | [campaign/v8/send/email](https://...) | 70% | - | - | Settings in v8 | 🗑️ DELETE |
| 6 | [defining-the-email-content.md](file:///...) | [campaign-web/v8/email/edit-content](https://...) | 90% | - | - | - | - | Content editing in v8 | 🗑️ DELETE |

### 📱 SMS

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 7 | [sms-channel.md](file:///...) | [campaign-web/v8/msg/send-sms](https://...) | 90% | - | - | - | - | SMS basics in v8 | 🗑️ DELETE |
| 8 | [sms-send.md](file:///...) | [campaign-web/v8/msg/send-sms](https://...) | 95% | - | - | - | - | SMS sending in v8 | 🗑️ DELETE |
| 9 | **[sms-set-up-mid.md](file:///...)** | NONE | 0% | - | - | - | - | **Mid-sourcing setup (on-prem only)** | ✅ **KEEP** |
| 10 | [sms-protocol.md](file:///...) | [campaign/v8/send/sms/smpp](https://...) | 60% | - | - | - | - | Advanced SMPP, check v8 depth | 🔍 REVIEW |

### 🔔 Push Notifications

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 11 | [about-mobile-app-channel.md](file:///...) | [campaign-web/v8/push](https://...) | 90% | - | - | - | - | Push basics in v8 | 🗑️ DELETE |
| 12 | [create-notifications-ios.md](file:///...) | [campaign/v8/send/push/push-ios](https://...) | 95% | - | - | - | - | iOS push fully documented | 🗑️ DELETE |
| 13 | [create-notifications-android.md](file:///...) | [campaign/v8/send/push/push-android](https://...) | 95% | - | - | - | - | Android push fully documented | 🗑️ DELETE |

### 📮 Direct Mail

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 14 | [about-direct-mail-channel.md](file:///...) | [campaign/v8/send/direct-mail](https://...) | 90% | - | - | - | - | Direct mail basics in v8 | 🗑️ DELETE |
| 15 | [creating-a-direct-mail-delivery.md](file:///...) | [campaign/v8/send/direct-mail/create](https://...) | 95% | - | - | - | - | Creation process in v8 | 🗑️ DELETE |

### 🎯 Personalization

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 16 | **[personalized-coupons.md](file:///...)** | NONE | 0% | - | - | - | - | **Coupons NOT in v8 FFDA** | ✅ **KEEP** |
| 17 | [about-personalization.md](file:///...) | [campaign-web/v8/personalization](https://...) | 95% | - | - | - | - | Personalization fully in v8 | 🗑️ DELETE |
| 18 | [personalization-fields.md](file:///...) | [campaign-web/v8/personalization/personalize](https://...) | 95% | - | - | - | - | Fields fully documented | 🗑️ DELETE |

### 📋 Templates & Seeds

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 19 | [about-templates.md](file:///...) | [campaign-web/v8/msg/delivery-template](https://...) | 90% | - | - | - | - | Templates in v8 | 🗑️ DELETE |
| 20 | [about-seed-addresses.md](file:///...) | [campaign/v8/send/test-and-send](https://...) | 95% | - | - | - | - | Seeds fully in v8 | 🗑️ DELETE |

### 🧪 A/B Testing

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 21 | [a-b-testing-use-case.md](file:///...) | [campaign-web/v8/msg/send-to-subscribers](https://...) | 85% | - | - | - | - | A/B testing in v8 | 🗑️ DELETE |
| 22 | [configuring-a-b-testing.md](file:///...) | [campaign-web/v8/msg/send-to-subscribers](https://...) | 90% | - | - | - | - | Configuration in v8 | 🗑️ DELETE |

### 🚀 Delivery Process

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 23 | [steps-create-and-identify-the-delivery.md](file:///...) | [campaign-web/v8/msg/gs-deliveries](https://...) | 90% | - | - | - | - | Creation steps in v8 | 🗑️ DELETE |
| 24 | [check-before-sending.md](file:///...) | [campaign-web/v8/msg/gs-deliveries](https://...) | 85% | - | - | - | - | Pre-send checks in v8 | 🗑️ DELETE |
| 25 | [sending-messages.md](file:///...) | [campaign-web/v8/msg/gs-deliveries](https://...) | 90% | - | - | - | - | Sending process in v8 | 🗑️ DELETE |

### 📊 Monitoring

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 26 | [about-delivery-monitoring.md](file:///...) | [campaign-web/v8/msg/delivery-logs](https://...) | 85% | - | - | - | - | Monitoring in v8 | 🗑️ DELETE |
| 27 | [delivery-dashboard.md](file:///...) | [campaign-web/v8/msg/delivery-logs](https://...) | 90% | - | - | - | - | Dashboard in v8 | 🗑️ DELETE |
| 28 | [about-message-tracking.md](file:///...) | [campaign-web/v8/msg/track-and-monitor](https://...) | 95% | - | - | - | - | Tracking fully in v8 | 🗑️ DELETE |

### 🔧 Troubleshooting

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 29 | [understanding-delivery-failures.md](file:///...) | [campaign/v8/send/delivery-failures](https://...) | 85% | - | - | - | - | Failures documented in v8 | 🗑️ DELETE |
| 30 | [delivery-troubleshooting.md](file:///...) | [campaign/v8/send/delivery-failures](https://...) | 70% | - | - | - | - | Good tips, migrate missing content | ➡️ MOVE |
| 31 | [troubleshooting-sms.md](file:///...) | [campaign/v8/send/sms](https://...) | 65% | - | - | - | - | SMS-specific issues, migrate | ➡️ MOVE |

### 📬 Deliverability

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | v8 Match 3 | % | Notes | Action |
|---|---------|------------|---|------------|---|------------|---|-------|--------|
| 32 | [about-deliverability.md](file:///...) | [campaign/v8/send/deliverability](https://...) | 90% | - | - | - | - | Deliverability in v8 | 🗑️ DELETE |
| 33 | **[spamassassin.md](file:///...)** | NONE | 0% | - | - | - | - | **On-premise spam filtering** | ✅ **KEEP** |
| 34 | [inbox-rendering.md](file:///...) | [campaign/v8/send/email-rendering](https://...) | 95% | - | - | - | - | Rendering in v8 | 🗑️ DELETE |

[... Continue for ALL files in folder ...]

---
\`\`\`

### FILE-BY-FILE DETAILED RECAP
\`\`\`markdown
## 📄 Detailed File Recap

### File #1: about-email-channel.md

**Category**: Get Started  
**v7 Path**: `/help/delivery/using/about-email-channel.md`  
**File**: [Open in v7](file:///Users/.../about-email-channel.md)

#### v8 Matches

1. **🥇 Primary Match**: `campaign-web/v8/email/` - **95% match**
   - **URL**: https://experienceleague.adobe.com/en/docs/campaign-web/v8/email
   - **Coverage**: Email channel basics, capabilities, overview
   - **Gaps**: None significant
   - **Quality**: Equivalent or better in v8

2. **🥈 Secondary Match**: `campaign/v8/send/email.md` - **85% match**
   - **URL**: https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/email
   - **Coverage**: Technical email details
   - **Gaps**: Less user-friendly than Web UI docs

#### Content Analysis

**Main Topics**:
- ✅ Email channel introduction
- ✅ Email capabilities and features
- ✅ Best practices for email
- ✅ Email channel overview

**v7-Specific Content**: None

**v8 Coverage**:
- ✅ **Fully covered**: All main topics (100%)
- ⚠️ **Partially covered**: None
- ❌ **Not covered**: None

#### Decision: 🗑️ DELETE

**Reasoning**:  
Email channel basics are comprehensively documented in Campaign Web v8 with equivalent or better coverage. The v8 documentation is more current and user-friendly. No v7-specific content present.

**Action**:
- ✅ Confirm v8 path is comprehensive
- ✅ Add to deletion list
- ✅ Update redirects.csv: `/delivery/about-email-channel` → `https://experienceleague.adobe.com/en/docs/campaign-web/v8/email`

---

### File #9: sms-set-up-mid.md

**Category**: SMS  
**v7 Path**: `/help/delivery/using/sms-set-up-mid.md`  
**File**: [Open in v7](file:///Users/.../sms-set-up-mid.md)

#### v8 Matches

1. **❌ No Match**: NONE - **0% match**
   - **Reason**: Mid-sourcing server setup is on-premise/hybrid specific
   - **v8 Status**: Cloud-only, no mid-sourcing setup needed

#### Content Analysis

**Main Topics**:
- ⚠️ Mid-sourcing server installation
- ⚠️ SMS connector configuration on mid-sourcing
- ⚠️ Network setup between marketing and mid-sourcing
- ⚠️ nlserver configuration

**v7-Specific Content**: 
- ✅ **100% v7-specific**: On-premise/hybrid architecture
- ✅ **Mid-sourcing**: Not applicable in v8 cloud
- ✅ **Server setup**: v7 only

**v8 Coverage**:
- ❌ **Not covered**: Mid-sourcing setup (not applicable in cloud)

#### Decision: ✅ KEEP

**Reasoning**:  
This file documents mid-sourcing server setup which is specific to v7 on-premise and hybrid deployments. v8 is cloud-only and handles mid-sourcing automatically. This content is essential for v7 users.

**Action**:
- ✅ Keep in v7 documentation
- ✅ Add v7-only badge: "This feature is specific to Campaign Classic v7 on-premise and hybrid deployments."
- ✅ Update intro with note about v8 difference

---

[... Continue detailed recap for ALL files ...]

---
\`\`\`

### REORGANIZATION RECOMMENDATIONS
\`\`\`markdown
## 🎯 Reorganization Recommendations

### Proposed Hierarchical Structure

Instead of flat folder, organize by category:

\`\`\`
/help/delivery/
├── get-started/
│   ├── about-email-channel.md (DELETE - in v8)
│   ├── communication-channels.md (DELETE - in v8)
│   └── steps-about-delivery-creation-steps.md (DELETE - in v8)
│
├── email/
│   ├── creating-an-email-delivery.md (DELETE - in v8)
│   ├── email-parameters.md (DELETE - in v8)
│   └── [15 more files...]
│
├── sms/
│   ├── sms-channel.md (DELETE - in v8)
│   ├── sms-set-up-mid.md (KEEP - v7 only)
│   └── [5 more files...]
│
├── push/
│   └── [7 files - mostly DELETE]
│
├── direct-mail/
│   └── [3 files - all DELETE]
│
├── personalization/
│   ├── personalized-coupons.md (KEEP - not in v8 FFDA)
│   └── [6 more files - DELETE]
│
├── templates-seeds/
│   └── [8 files - all DELETE]
│
├── a-b-testing/
│   └── [9 files - all DELETE]
│
├── delivery-process/
│   └── [8 files - all DELETE]
│
├── monitoring/
│   └── [12 files - all DELETE]
│
├── troubleshooting/
│   ├── delivery-troubleshooting.md (MOVE then DELETE)
│   ├── troubleshooting-sms.md (MOVE then DELETE)
│   └── [5 more files...]
│
├── deliverability/
│   ├── spamassassin.md (KEEP - v7 only)
│   └── [6 more files - mostly DELETE]
│
└── advanced/
    └── [8 files - mixed]
\`\`\`

### Benefits of This Structure

1. **✅ Better Navigation**: Logical grouping by feature
2. **✅ Clear Progression**: Get Started → Specific Channels → Advanced
3. **✅ Easier Maintenance**: Related files together
4. **✅ Experience League Alignment**: Matches online structure

---
\`\`\`

### ACTION PLAN
\`\`\`markdown
## ✅ Execution Plan

### Phase 1: Quick Deletions (Week 1)

**High Confidence Deletions** (85-100% v8 match):

- [ ] **Email** (15 files)
  - [ ] about-email-channel.md → campaign-web/v8/email
  - [ ] creating-an-email-delivery.md → campaign-web/v8/email/create-email
  - [ ] email-parameters.md → campaign-web/v8/email/configure-and-send
  - [ ] [... list all 15 ...]

- [ ] **SMS** (4 files)
  - [ ] sms-channel.md → campaign-web/v8/msg/send-sms
  - [ ] sms-send.md → campaign-web/v8/msg/send-sms
  - [ ] [... list all 4 ...]

- [ ] **Push** (7 files)
  - [ ] [... list all 7 ...]

- [ ] **Direct Mail** (3 files)
  - [ ] [... list all 3 ...]

[Continue for all categories...]

**Total Phase 1**: 67 files to delete

---

### Phase 2: Content Migration (Week 2)

**Files to Migrate to v8 First**:

- [ ] **delivery-troubleshooting.md**
  - Migrate to: `/campaign/v8/send/delivery-failures.md`
  - Content: Troubleshooting tips sections 3, 5, 7
  - Effort: 2 hours

- [ ] **troubleshooting-sms.md**
  - Migrate to: `/campaign/v8/send/sms/sms.md`
  - Content: SMPP error codes, timeout handling
  - Effort: 1 hour

[List all 8 files to migrate...]

**Total Phase 2**: 8 files migrated, then deleted from v7

---

### Phase 3: v7-Specific Badging (Week 2)

**Files to Keep with v7-Only Badge**:

- [ ] **personalized-coupons.md**
  - Badge: "Coupons are not available in Campaign v8 Enterprise (FFDA) deployments"
  - Link to: v8 limitations page

- [ ] **sms-set-up-mid.md**
  - Badge: "Mid-sourcing server setup is specific to Campaign v7 on-premise/hybrid deployments"
  - Note: "Campaign v8 is cloud-only"

- [ ] **spamassassin.md**
  - Badge: "SpamAssassin integration is specific to Campaign v7 on-premise deployments"
  - Note: "Campaign v8 uses cloud-based spam filtering"

[List all files to badge...]

**Total Phase 3**: 18 files badged

---

### Phase 4: Manual Review (Week 3)

**Files Requiring Validation**:

- [ ] **sms-protocol.md** (60% match)
  - Action: Compare SMPP protocol depth in v8
  - If v8 sufficient: DELETE
  - If gaps: KEEP or MOVE

- [ ] **generating-personalized-pdf-documents.md** (65% match)
  - Action: Verify PDF generation docs in v8
  - Check: Does v8 cover all use cases?

[List all review items...]

**Total Phase 4**: 18 files reviewed and decided

---
\`\`\`

### METRICS
\`\`\`markdown
## 📊 Success Metrics

### Quantitative Goals

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| **Files Deleted** | 67 (60%) | - | ⏳ Pending |
| **Files Kept** | 18 (16%) | - | ⏳ Pending |
| **Files Migrated** | 8 (7%) | - | ⏳ Pending |
| **Files Reviewed** | 18 (17%) | - | ⏳ Pending |
| **Reduction %** | 67% | - | ⏳ Pending |

### Quality Checks

- [ ] All deleted files have v8 equivalent (verified)
- [ ] All kept files have v7-only badge
- [ ] All migrated content integrated in v8
- [ ] No broken links remain
- [ ] redirects.csv updated
- [ ] TOC.md updated
- [ ] Stakeholder approval obtained

---
\`\`\`

---

## END OF REPORT

Generate this complete markdown report for the specified folder.

Include:
- ✅ Summary statistics
- ✅ Complete analysis table organized by category
- ✅ Multiple v8 matches per file with %
- ✅ Detailed file-by-file recap
- ✅ Reorganization recommendations
- ✅ Execution plan with checkboxes
- ✅ Success metrics

Make all links clickable (v7 files + Experience League URLs).
```

---

## USAGE

1. **Copy the entire prompt above**
2. **Replace folder path**:
   ```
   📁 **Analyze**: /Users/.../help/[YOUR-FOLDER]/using/
   ```
3. **Paste into Cursor**
4. **Run analysis**
5. **Get complete Markdown report**
6. **Save as**: `[folder]-detailed-analysis.md`

---

## FOLDER EXAMPLES

Try with:
- `/help/delivery/using/` (111 files)
- `/help/workflow/using/` (121 files)
- `/help/platform/using/` (61 files)
- `/help/web/using/` (26 files)

---

## OUTPUT PREVIEW

The report will be ~30-40 pages of detailed Markdown with:
- Summary stats
- Complete table with all files
- Up to 3 v8 matches per file
- Match percentages
- Detailed file recaps
- Reorganization plan
- Action items

Perfect for execution! ✅

