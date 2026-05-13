---
product: campaign
title: 篩選結構描述
description: 篩選結構描述
feature: Custom Resources
role: Developer
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
TQID: https://experienceleague.adobe.com/-EcD9suVVxnqRIgsLdaADQ7T0CIMw1CzSnoqJqNe8xs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 1%

---

# 篩選結構{#filtering-schemas}

## 系統篩選器 {#system-filters}

您可以根據特定使用者的許可權，篩選其結構描述存取權。 系統篩選器可讓您使用&#x200B;**readAccess**&#x200B;和&#x200B;**writeAccess**&#x200B;引數，管理結構描述中詳述之實體的讀取和寫入許可權。

>[!NOTE]
>
>此限制僅適用於非技術使用者：具有相關許可權或使用工作流程的技術使用者將能夠擷取和更新資料。

* **readAccess**：提供對結構描述資料的唯讀存取權。

  **警告** — 所有連結資料表都必須設定相同的限制。 此設定可能會影響效能。

* **writeAccess**：提供結構描述資料的寫入許可權。

這些篩選器是在結構描述的主要&#x200B;**元素**&#x200B;層級輸入的，如下列範例所示，可以形成以限制存取。

* 限制寫入許可權

  在此，篩選器是用來在沒有ADMINISTRATION許可權的情況下禁止操作員在結構描述上使用WRITE許可權。 這表示只有管理員擁有此結構描述所說明之實體的寫入許可權。

  ```
  <sysFilter name="writeAccess">      
   <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
  </sysFilter>
  ```

* 限制讀取和寫入許可權：

  在此處，篩選器用於禁止所有運運算元在結構描述上同時具有讀取和寫入許可權。 只有&#x200B;**internal**&#x200B;帳戶(由運算式&quot;$(loginId)!=0&quot;表示)具有這些許可權。

  ```
  <sysFilter name="readAccess"> 
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  
  <sysFilter name="writeAccess">  
   <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
  </sysFilter>
  ```

  用來定義條件的可能的&#x200B;**expr**&#x200B;屬性值是TRUE或FALSE。

>[!NOTE]
>
>如果未指定篩選器，則所有運運算元都將具有結構描述的讀取和寫入許可權。

## 保護內建方案 {#protecting-built-in-schemas}

依預設，只有具備管理員許可權的運運算元才可透過寫入許可權存取內建方案：

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
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
>**xtk:sessionInfo**&#x200B;結構描述的讀取和寫入許可權只能由Adobe Campaign執行個體的內部帳戶存取。

## 修改內建綱要的系統篩選器 {#modifying-system-filters-of-built-in-schemas}

由於舊版的相容性問題，您仍然可以修改現成可用的結構描述的系統篩選器，這些篩選器預設是受保護的。

>[!NOTE]
>
>不過，Adobe建議您不要修改預設引數來保證最佳安全性。

1. 為相關結構描述建立擴充功能，或開啟現有的擴充功能。
1. 在主元素中新增子元素&#x200B;**`<sysfilter name="<filter name>" _operation="delete"/>`**，以刪除原始結構描述中相同專案下的篩選器應用程式。
1. 您也可以新增篩選器，如[系統篩選器](#system-filters)所詳述。
