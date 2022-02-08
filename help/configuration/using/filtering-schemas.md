---
product: campaign
title: 篩選方案
description: 篩選方案
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 篩選結構{#filtering-schemas}

![](../../assets/v7-only.svg)

## 系統篩選器 {#system-filters}

您可以根據特定用戶的權限篩選對特定用戶的架構訪問。 系統篩選器允許您使用 **讀取訪問** 和 **寫訪問** 參數。

>[!NOTE]
>
>此限制僅適用於非技術用戶：具有相關權限或使用工作流的技術用戶將能夠檢索和更新資料。

* **讀取訪問**:提供對架構資料的只讀訪問。

   **警告**  — 所有連結表都必須設定相同的限制。 此配置會影響效能。

* **寫訪問**:提供對架構資料的寫訪問。

這些篩選器是在主 **元素** 架構的級別和（如以下示例所示）可以形成為限制訪問。

* 限制WRITE權限

   此處，該篩選器用於禁止在沒有ADMINISTRATION權限的情況下對運算子的架構具有WRITE權限。 這意味著只有管理員才對此架構描述的實體具有寫權限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制讀權限和寫權限：

   此處，篩選器用於禁止所有運算子對架構的READ和WRITE權限。 僅 **內部** 帳戶，由表達式「$(loginId)！」表示=0&quot;，具有這些權限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   可能 **EXPR** 用於定義條件的屬性值為TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運算子都對架構具有讀和寫權限。

## Protect內置架構 {#protecting-built-in-schemas}

預設情況下，只有具有ADMINISTRATION權限的運算子才能使用WRITE權限訪問內置架構：

* ncm：發佈
* nl：監視
* nms：日曆
* xtk：生成器
* xtk：連接
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk：實體原始
* xtk：格式
* xtk:funcList
* xtk：融合
* xtk：影像
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk：導航樹
* xtk:operatorGroup
* xtk：包
* xtk:queryDef
* xtk：資源菜單
* xtk：權限
* xtk：架構
* xtk：指令碼上下文
* xtk:spec檔案
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk：字串
* xtk:xslt

>[!IMPORTANT]
>
>對的READ和WRITE權限 **xtk:sessionInfo** 模式僅可由Adobe Campaign實例的內部帳戶訪問。

## 修改內置架構的系統篩選器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改現成架構的系統篩選器，這些架構預設受到保護，原因是與舊版本的相容性問題。

>[!NOTE]
>
>但是，Adobe建議您不要修改預設參數以確保最佳安全性。

1. 為相關架構建立擴展或開啟現有擴展。
1. 添加子元素 **`<sysfilter name="<filter name>" _operation="delete"/>`** 在主元素中刪除源架構中相同下的篩選器應用程式。
1. 如果願意，可以添加新篩選器，如中所述 [系統篩選器](#system-filters)。
