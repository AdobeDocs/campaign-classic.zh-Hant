---
solution: Campaign Classic
product: campaign
title: 篩選綱要
description: 篩選綱要
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# 篩選結構{#filtering-schemas}

## 系統過濾器{#system-filters}

您可以根據特定使用者的權限來篩選結構存取權。 系統過濾器使用&#x200B;**readAccess**&#x200B;和&#x200B;**writeAccess**&#x200B;參數，管理結構描述中詳細實體的讀寫權限。

>[!NOTE]
>
>此限制僅適用於非技術使用者：具有相關權限或使用工作流程的技術使用者將能夠擷取和更新資料。

* **readAccess**:提供對架構資料的只讀訪問。

   **警告** -所有連結的表格都必須使用相同的限制設定。此配置可影響效能。

* **writeAccess**:提供對架構資料的寫訪問。

這些篩選器是在方案的主&#x200B;**element**&#x200B;級別輸入的，並且如以下示例所示，可以形成以限制訪問。

* 限制寫入權限

   在這裡，篩選器用於在未具有ADMINISTRATION權限的情況下禁止操作員對架構的WRITE權限。 這表示只有管理員才對此架構描述的實體具有寫權限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制讀取和寫入權限：

   在這裡，篩選器用於禁止所有運算子對架構的READ和WRITE權限。 僅&#x200B;**internal**&#x200B;帳戶，由運算式&quot;$(loginId)表示！=0」，具有這些權限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用於定義條件的可能&#x200B;**expr**&#x200B;屬性值為TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運算子都具有架構的讀取和寫入權限。

## Protect內置結構{#protecting-built-in-schemas}

預設情況下，內置結構只能對具有ADMINISTRATION權限的操作員使用WRITE權限訪問：

* ncm：發佈
* nl：監控
* nms:calendar
* xtk:builder
* xtk：連接
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk：影像
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk：字串
* xtk:xslt

>[!IMPORTANT]
>
>**xtk:sessionInfo**&#x200B;架構的READ和WRITE權限僅能由Adobe Campaign實例的內部帳戶訪問。

## 修改內置結構{#modifying-system-filters-of-built-in-schemas}的系統篩選器

您仍然可以修改現成可用架構的系統篩選器，這些架構由於與舊版的相容性問題而預設受到保護。

>[!NOTE]
>
>不過，Adobe建議您不要修改預設參數，以確保最佳安全性。

1. 建立相關架構的擴充功能或開啟現有的擴充功能。
1. 在主要元素中添加子元素&#x200B;**`<sysfilter name="<filter name>" _operation="delete"/>`**，以刪除源模式中相同項下篩選器的應用程式。
1. 如果您喜歡，可以添加新過濾器，如[系統過濾器](#system-filters)中所述。

