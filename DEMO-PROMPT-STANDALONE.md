# 🚀 DEMO PROMPT - v7 to v8 Documentation Analysis

**Copy-paste this entire prompt into Cursor/ChatGPT to analyze any v7 folder**

---

## 📋 THE PROMPT (COPY FROM HERE) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

---

## 🎯 DEMO INSTRUCTIONS

### Step 1: Show the Prompt
1. Open this file (`DEMO-PROMPT-STANDALONE.md`)
2. Scroll to "THE PROMPT" section
3. Say: *"This is our automated analysis prompt"*

### Step 2: Copy the Prompt
1. Select everything from "# Campaign v7 Documentation Analysis" to the end
2. Copy to clipboard
3. Say: *"I just copy the entire prompt..."*

### Step 3: Paste & Execute
1. Open Cursor
2. Paste the prompt
3. Say: *"...and paste it into Cursor"*
4. Hit Enter

### Step 4: Show Results
1. Wait for generation (~30-60 seconds)
2. Scroll through the generated report
3. Highlight key sections:
   - 📊 Summary stats
   - 📋 File-by-file table
   - ✅ Must Keep section
   - 🗑️ Quick Wins
   - 🎯 Execution Plan

### Step 5: Wow Moment
1. Show the markdown preview
2. Point out:
   - *"111 files analyzed automatically"*
   - *"67 files safe to delete (60% reduction)"*
   - *"18 v7-specific files identified"*
   - *"Complete execution plan with timelines"*

---

## 💡 DEMO TIPS

### Make it Interactive
**Ask the audience**: *"Which folder should we analyze?"*
- delivery ✅ (111 files - impressive)
- workflow ✅ (121 files - even bigger)
- web ✅ (26 files - quick demo)
- reporting ✅ (32 files - fast)

### Customize on the Fly
**Show flexibility**: Change the folder path in the prompt:
```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Highlight Key Features
1. **Automation**: *"No manual work needed"*
2. **Accuracy**: *"Uses v8 documentation for comparison"*
3. **Actionable**: *"Ready-to-execute plan with checkboxes"*
4. **Smart**: *"Identifies v7-specific features automatically"*

### Time Comparison
**Before**: *"Manual analysis = 2-3 days per folder"*  
**After**: *"Automated analysis = 30 seconds per folder"*

**ROI**: *"21 folders × 2 days = 42 days → 15 minutes"*

---

## 📊 EXPECTED OUTPUT PREVIEW

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

---

## 🎬 DEMO SCRIPT

**Opening**:
> "Today I'll show you how we automated v7 documentation reorganization using AI. This used to take weeks, now it takes minutes."

**Problem**:
> "We have 1,500+ v7 documentation files. Many are duplicated in v8. We need to identify what to keep, delete, or migrate."

**Solution**:
> "We created a smart prompt that analyzes any folder and generates actionable recommendations."

**Demo**:
> "Let me show you. I'll analyze the 'delivery' folder with 111 files..."
> 
> [Copy prompt, paste, execute]
> 
> "...and in 30 seconds, we get a complete analysis."

**Results**:
> "Look at this:
> - 67 files to delete (60% reduction)
> - 18 v7-specific files identified
> - 8 files to migrate
> - Complete 3-week execution plan
> 
> All automated. All accurate."

**Close**:
> "This same process works for all 21 folders. What used to take 6 weeks now takes 15 minutes."

---

## 🚀 READY TO DEMO!

**Just**:
1. Open this file
2. Copy the prompt
3. Paste into Cursor
4. Show the magic ✨

**Total demo time**: 3-5 minutes  
**Wow factor**: 🔥🔥🔥

