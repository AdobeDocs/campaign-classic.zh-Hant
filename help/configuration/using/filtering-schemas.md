---
title: 篩選結構
seo-title: 篩選結構
description: 篩選結構
seo-description: null
page-status-flag: never-activated
uuid: 04a90785-3084-42fd-85af-77bc28687579
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 64d4c5b8-db0b-4287-8d30-4bf09878a401
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 篩選結構{#filtering-schemas}

## 系統篩選器 {#system-filters}

您可以根據特定使用者的權限來篩選結構存取權。 系統篩選器可讓您使用readAccess和writeAccess參數，管理在結構描述中詳細描述的 **實體的讀****取和寫入權限** 。

>[!NOTE]
>
>此限制僅適用於非技術使用者：具有相關權限或使用工作流程的技術使用者將能夠擷取和更新資料。

* **readAccess**:提供對架構資料的只讀訪問。

   **警告** -所有連結的表格都必須使用相同的限制設定。 此配置可影響效能。

* **writeAccess**:提供對架構資料的寫訪問。

這些篩選器是在方案的主 **要元素級別中輸入** ，而且如下列範例所示，可形成以限制存取。

* 限制寫入權限

   在這裡，篩選器用於在未具有ADMINISTRATION權限的情況下禁止操作員對架構的WRITE權限。 這表示只有管理員才對此架構描述的實體具有寫權限。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制讀取和寫入權限：

   在這裡，篩選器用於禁止所有運算子對架構的READ和WRITE權限。 僅內 **部** 帳戶，以運算式&quot;$(loginId)!=0」，具有這些權限。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   用於 **定義條件** 的可能expr屬性值為TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運算子都具有架構的讀取和寫入權限。

## 保護內建結構 {#protecting-built-in-schemas}

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
>Adobe Campaign例項的內 **部帳戶只能存取xtk:sessionInfo** 架構的READ和WRITE權限。

## 修改內建結構描述的系統篩選器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改現成可用架構的系統篩選器，這些架構由於與舊版的相容性問題而預設受到保護。

>[!NOTE]
>
>不過，Adobe建議您不要修改預設參數，以確保最佳安全性。

1. 建立相關架構的擴充功能或開啟現有的擴充功能。
1. 在主要元素中添 **`<sysfilter name="<filter name>" _operation="delete"/>`** 加子元素，以刪除來源模式中相同項下篩選器的應用程式。
1. 如果您喜歡，可以新增篩選，如「系統」篩選 [中所述](#system-filters)。

