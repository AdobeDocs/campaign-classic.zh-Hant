---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀示範提示 — v7到v8檔案分析

**複製並貼上此整個提示到Cursor/ChatGPT以分析任何v7資料夾**

---

## 📋提示（從此處複製） ⬇️

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

## 🎯個示範指示

### 步驟1：顯示提示
1. 開啟這個檔案(`DEMO-PROMPT-STANDALONE.md`)
2. 捲動到「提示」區段
3. 說： *「這是我們的自動分析提示」*

### 步驟2：複製提示
1. 選取從「# Campaign v7檔案分析」到結尾的所有專案
2. 複製到剪貼簿
3. 說： *「我只是複製整個提示……」*

### 步驟3：貼上並執行
1. 開啟游標
2. 貼上提示
3. 說： *「……並貼到Cursor「*」
4. 點選Enter

### 步驟4：顯示結果
1. 等待產生（~30-60秒）
2. 捲動產生的報表
3. 反白主要區段：
   - 📊摘要統計資料
   - 📋個檔案逐個資料表
   - ✅必須保留區段
   - 🗑️個快速成功
   - 🎯執行計畫

### 步驟5： Wow時刻
1. 顯示Markdown預覽
2. 指出：
   - *「111個檔案已自動分析」*
   - *&quot;67個檔案可安全刪除（減少60%）&quot;*
   - 已識別&#x200B;*「18個v7特定檔案」*
   - *「使用時間表完成執行計畫」*

---

## 💡個示範提示

### 使其成為互動式
**詢問對象**： *「我們應該分析哪個資料夾？」*
- 傳遞✅ （111個檔案 — 令人印象深刻）
- 工作流程✅ （121個檔案 — 甚至更大）
- 網頁✅ （26個檔案 — 快速示範）
- 報告✅ （32個檔案 — 快速）

### 即時自訂
**顯示彈性**：變更提示中的資料夾路徑：

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### 強調主要功能
1. **自動化**： *「不需要手動工作」*
2. **準確度**： *「使用v8檔案進行比較」*
3. **可操作**： *「使用核取方塊準備執行計畫」*
4. **Smart**： *「自動識別v7特定功能」*

### 時間比較
**Before**： *&quot;手動分析=每個資料夾2-3天&quot;*\
**After**： *&quot;自動分析=每個資料夾30秒&quot;*

**ROI**： *&quot;21個資料夾× 2天= 42天→ 15分鐘&quot;*

---

## 📊預期的輸出預覽

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

## 🎬示範指令碼

**正在開啟**：
> 「今天，我將展示如何使用AI來自動化v7檔案重組。 這過去需要數週，現在只需要數分鐘。」

**問題**：
> 「我們有1,500多個v7檔案檔案。 許多在v8中重複。 我們需要識別要保留、刪除或移轉的專案。」

**解決方案**：
> 「我們已建立智慧型提示，可分析任何資料夾並產生可操作的建議。」

**示範**：
> 「我來給你們看看。 我將分析包含111個檔案的「傳送」資料夾……」
> 
> [複製提示，貼上，執行]
> 
> 「……30秒內，我們將獲得完整分析。」

**個結果**：
> 「看看這個：
> - 要刪除67個檔案（減少60%）
> - 已識別18個v7專屬檔案
> - 8個要移轉的檔案
> - 完成3週執行計畫
> 
> 全部自動化。 一切準確。」

**關閉**：
> 「同樣的程式適用於所有21個資料夾。 過去需要6週的時間，現在需要15分鐘。」

---

## 🚀已準備好進行示範！

**Just**：
1. 開啟此檔案
2. 複製提示
3. 貼上至游標
4. 顯示魔術✨

**總示範時間**： 3-5分鐘\
**Wow因子**： 🔥🔥🔥

