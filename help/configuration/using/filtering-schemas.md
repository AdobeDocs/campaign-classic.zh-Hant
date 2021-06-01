---
product: campaign
title: 篩選方案
description: 篩選方案
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 篩選結構{#filtering-schemas}

## 系統篩選器{#system-filters}

您可以根據特定使用者的權限，篩選結構存取權。 系統篩選器可讓您使用&#x200B;**readAccess**&#x200B;和&#x200B;**writeAccess**&#x200B;參數，管理結構中詳細實體的讀取和寫入權限。

>[!NOTE]
>
>此限制僅適用於非技術使用者：具有相關權限或使用工作流程的技術使用者將能夠擷取和更新資料。

* **readAccess**:提供對架構資料的只讀訪問。

   **警告**  — 所有連結的表都必須使用相同的限制設定。此設定可能會影響效能。

* **writeAccess**:提供對架構資料的寫入訪問。

這些篩選器是在結構的主&#x200B;**element**&#x200B;層級輸入，如下列範例所示，可以形成以限制存取。

* 限制寫入權限

   在此，該篩選器用於不具有ADMINISTRATION權限的操作員不允許對架構的WRITE權限。 這表示只有管理員對此結構描述的實體具有寫權限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制讀取和寫入權限：

   在此，該篩選器用於禁止所有運算子對架構的「讀取」和「寫入」權限。 僅&#x200B;**internal**&#x200B;帳戶，以運算式&quot;$(loginId)!=0」，則具有這些權限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用來定義條件的可能&#x200B;**expr**&#x200B;屬性值為TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運算子都具有架構的讀取和寫入權限。

## Protect內建結構{#protecting-built-in-schemas}

預設情況下，內建結構僅可對具有「管理」權限的操作員使用「寫入」權限進行訪問：

* ncm:publishing
* nl：監視
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
* xtk:image
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
* xtk:strings
* xtk:xslt

>[!IMPORTANT]
>
>**xtk:sessionInfo**&#x200B;架構的讀取和寫入權限僅可由Adobe Campaign例項的內部帳戶存取。

## 修改內置架構{#modifying-system-filters-of-built-in-schemas}的系統篩選器

您仍可以修改現成可用結構的系統篩選器，這些架構預設會因與舊版的相容性問題而受到保護。

>[!NOTE]
>
>不過，Adobe建議您不要修改預設參數，以保證最佳安全性。

1. 為相關結構建立擴充功能，或開啟現有擴充功能。
1. 在主要元素中新增子元素&#x200B;**`<sysfilter name="<filter name>" _operation="delete"/>`**，以刪除來源架構中相同之下的篩選器應用程式。
1. 您也可以新增新篩選器，如[系統篩選器](#system-filters)中所述。
