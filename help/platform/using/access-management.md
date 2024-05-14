---
product: campaign
title: 開始使用權限
description: 瞭解如何授與Campaign功能的存取權
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 5%

---

# 開始使用權限{#access-management}


>[!CAUTION]
>
>從Campaign Classicv7.3.1開始，所有運運算元都應該使用 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"} 以連線至Campaign。
>
>為了強化安全性和驗證程式，Adobe Campaign強烈建議您將所有現有的操作員驗證模式從登入/密碼原生驗證移轉至AdobeIdentity Management系統(IMS)。 瞭解如何在中移轉您的操作員 [此頁面](../../technotes/using/migrate-users-to-ims.md).
> 
>移轉後，請注意下一節不再適用。  瞭解如何在中使用Adobe IMS設定許可權 [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hant){target="_blank"}.


Adobe Campaign可讓您定義並管理指派給各種運運算元的許可權。 這些是一組授權或拒絕的許可權和限制：

* 存取特定功能（透過已命名的許可權），
* 存取特定記錄，
* 建立、修改及/或刪除記錄（動作、連絡人、行銷活動、群組等）。

這些許可權適用於操作員設定檔或操作員群組。

它們是透過連結至操作員與Adobe Campaign的連線模式的安全引數完成的。 有關中安全性區域的詳細資訊 [此頁面](../../installation/using/security-zones.md).

您可授予使用者兩種型別的許可權：

* 您可以定義您賦予許可權的運運算元群組，然後將運運算元與一或多個群組建立關聯。 這可讓您重複使用許可權，並讓運運算元設定檔更加一致。 它也能促進設定檔的管理和維護。 群組的建立和管理會顯示在 [本節](access-management-groups.md).

* 您可以將已命名的許可權直接歸因於使用者，在某些情況下，這會使透過群組配置的許可權過載。 這些許可權會顯示在 [此頁面](access-management-named-rights.md).

>[!NOTE]
>
>開始定義許可權之前，Adobe建議您先閱讀 [安全性設定檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html).

在以下章節中瞭解如何授與存取權並設定許可權：

* [建立運算子](access-management-operators.md)

* [定義群組](access-management-groups.md)

* [新增已命名的許可權](access-management-named-rights.md)

* [管理Campaign資料夾存取權](access-management-folders.md)

* [存取許可權矩陣](access-management-named-rights.md#access-rights-matrix)


另請參閱：

* [管理工作流程的許可權](../../workflow/using/managing-rights.md)
* [管理分散式行銷的許可權](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [管理互動模組的許可權](../../interaction/using/operator-profiles.md)
* [篩選結構描述的存取權](../../configuration/using/filtering-schemas.md)
* [限制PI檢視](../../configuration/using/restricting-pii-view.md)
