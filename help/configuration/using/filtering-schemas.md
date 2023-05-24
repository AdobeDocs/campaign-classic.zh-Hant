---
product: campaign
title: 篩選方案
description: 篩選方案
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 篩選結構{#filtering-schemas}

## 系統篩選器 {#system-filters}

您可以根據特定使用者的許可權，篩選其結構描述存取權。 系統篩選器可讓您使用管理結構描述中詳述之實體的讀取和寫入許可權 **readAccess** 和 **writeAccess** 引數。

>[!NOTE]
>
>此限制僅適用於非技術使用者：具有相關許可權或使用工作流程的技術使用者將能夠擷取和更新資料。

* **readAccess**：提供對結構描述資料的唯讀存取權。

   **警告**  — 所有連結的表格都必須設定相同的限制。 此設定會影響效能。

* **writeAccess**：提供對結構描述資料的寫入許可權。

這些篩選器輸入在主要 **元素** 如下列範例所示，可形成架構的層級和來限制存取。

* 限制寫入許可權

   在此，篩選器用於在沒有ADMINISTRATION許可權的情況下禁止操作員在結構描述上執行WRITE許可權。 這表示只有管理員擁有此結構描述所說明之實體的寫入許可權。

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* 限制讀取和寫入許可權：

   在此，篩選器用於禁止所有運運算元在結構描述上同時具有讀取和寫入許可權。 僅限 **內部** 帳號，由運算式「$(loginId)」表示！=0」擁有這些許可權。

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   可能 **運算式** 用來定義條件的屬性值是TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運運算元都將具有結構描述的讀取和寫入許可權。

## Protect內建結構描述 {#protecting-built-in-schemas}

依預設，只有具備管理員許可權的運運算元才可透過寫入許可權存取內建結構描述：

* ncm：發佈
* nl：monitoring
* nms：calendar
* xtk：builder
* xtk：連線
* xtk：dbInit
* xtk：entityBackupNew
* xtk：entityBackupOriginal
* xtk：entityOriginal
* xtk：form
* xtk：funcList
* xtk：fusion
* xtk：image
* xtk：javascript
* xtk：jssp
* xtk：jst
* xtk：navtree
* xtk：operatorGroup
* xtk：package
* xtk：queryDef
* xtk：resourceMenu
* xtk：rights
* xtk：schema
* xtk：scriptContext
* xtk：specFile
* xtk：sql
* xtk：sqlSchema
* xtk：srcSchema
* xtk：strings
* xtk：xslt

>[!IMPORTANT]
>
>的讀取和寫入許可權 **xtk：sessionInfo** 結構描述只能由Adobe Campaign執行個體的內部帳戶存取。

## 修改內建結構描述的系統篩選器 {#modifying-system-filters-of-built-in-schemas}

您仍然可以修改現成可用的結構描述的系統篩選器，由於與舊版本的相容性問題，這些結構描述預設是受保護的。

>[!NOTE]
>
>不過，Adobe建議您不要修改預設引數來保證最佳安全性。

1. 為相關結構描述建立擴充功能，或開啟現有擴充功能。
1. 新增子元素 **`<sysfilter name="<filter name>" _operation="delete"/>`** 元素來刪除原始結構描述中相同專案下的篩選器應用程式。
1. 您也可以新增篩選器，詳情請參閱 [系統篩選器](#system-filters).
