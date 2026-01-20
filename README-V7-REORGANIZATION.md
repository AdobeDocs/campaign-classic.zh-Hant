---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7檔案重組套件

**2提示pour analyzer et réorganizer la doc v7 → v8**

&#x200B;---

## 📁個影格

### 🔍個提示（指示）

| Fichier | 說明 | 輸出 |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | 分析資料夾索引標籤avec %相符 | `[folder]-detailed-analysis.md` |

&#x200B;---

## 🚀使用率

### ⃣1️組合值（tous les資料夾）

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génere** ：
- 📊執行摘要（統計全域）
- 📁分析des 21個資料夾
- 🎯排列優先順序
- ✅個動作專案
- ⚠️風險
- 📈個量度

**尾部** ：~50-60頁Markdown

&#x200B;---

### ⃣2️分析資料夾

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génere** ：
- 📊統計資料夾
- 📋 Tableau détaillé organisé comme Experience League
- 🔗個連線可修剪專案(v7 + Experience League)
- 📈 Jusqu&#39;à 3符合v8 par fichier avec %
- 📄重新擷取檔案par檔案
- 🎯重組計畫
- ✅個傾印追蹤的核取方塊

**尾部** ：~30-40頁Markdown

&#x200B;---

## 📊範例輸出

### 提示1 （概觀）

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### 提示2 （詳細資料夾）

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

&#x200B;---

## 🎯工作流程建議

### 塞曼尼1：總合值1. Exécuter **提示1** → Obtenir `v7-reorganization-overview.md`2. 優先識別碼資料夾3. 合作夥伴平均利益關係人

### 塞曼尼2-4 ：分析戴爾1. 優先傾印資料夾：   - Exécuter **提示2**   - 取得者`[folder]-detailed-analysis.md`   - Valider les designs   - 評論者減少動作

### Semaine 5+ ：執行1. supprimer les fichiers identifiers (DELETE)2. Badger les fichiers v7-only (KEEP)3. 移轉者內容Manquant (MOVE)4. 檢閱者比較模糊(REVIEW)

&#x200B;---

## 💡個提示

### 傾倒提示- ✅影印機/整合式提示字元- ✅ Ne pas修飾元格式- ✅ Adapter seulement le chemin du資料夾（提示2）

### 傾倒更多輸出- 📝 Output en Markdown (pas HTML)- 🔗個連絡人可卡因自動設定- ✅個傾印追蹤的核取方塊- 📊統計和百分比- 🎨表情符號圖示

### 傾印「分析」- 🎯 Commencer par les gros資料夾（傳遞、工作流程）- ⚡優先順序快速獲勝（95-100%相符）- 🔍檢閱者手冊les cas ambigus （&lt;70%相符）- ✅驗證器avec SME前衛隱藏大量

&#x200B;---

## ⚠️重要

### 前衛1. ✅ Vérifier l&#39;équivalent v82. ✅ Vérifier qui&#39;il n&#39;y a pas de contentu v7特定3. ✅ Mettre à jour `redirects.csv`4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers v7-only1. ✅ Ajouter un badge au début du fichier2. ✅ Expliquer pourquoi測試僅限v73. ✅個連線限制v8

&#x200B;---

## 🆘支援

**問題**？
- 提示ne fonctionne pas → Vérifier les chemins des repos
- Demander un résumé的輸出字串→長
- 貝松助教→ Ping l&#39;équipe doc

&#x200B;---

**Derniere mise à jour** ： 2026-01-13

