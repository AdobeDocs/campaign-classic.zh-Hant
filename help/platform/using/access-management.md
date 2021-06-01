---
product: campaign
title: 開始使用權限
description: 了解如何授與Campaign功能的存取權
feature: 存取管理
role: Business Practitioner, Administrator
level: Beginner
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---

# 開始使用權限{#access-management}

Adobe Campaign可讓您定義及管理指派給各種運算子的權限。 這些是授權或拒絕的一組權限和限制：

* 存取特定功能（透過具名權限）,
* 訪問某些記錄，
* 建立、修改和/或刪除記錄（動作、聯絡人、促銷活動、群組等）。

權限會套用至運算子設定檔或運算子群組。

這些參數是由連結至操作員與Adobe Campaign之連線模式的安全參數所完成。 有關[此頁](../../installation/using/security-zones.md)中安全區域的詳細資訊。

您可以授予使用者兩種權限：

* 您可以定義運算子群組，將其權限歸因於該群組，然後將運算子與一或多個群組關聯。 這可讓您重複使用權限，並讓運算子設定檔更加一致。 它還促進了配置檔案的管理和維護。 群組建立和管理顯示在[此部分](access-management-groups.md)中。

* 您可以直接將已命名的權限歸因給使用者，在某些情況下，會使透過群組分配的權限過載。 這些權限顯示在[此頁面](access-management-named-rights.md)中。

>[!NOTE]
>
>開始定義權限之前，Adobe建議您閱讀[安全配置檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。

在以下章節了解如何授予存取權和設定權限：

* [建立運算子](access-management-operators.md)

* [定義群組](access-management-groups.md)

* [新增已命名的權限](access-management-named-rights.md)

* [管理Campaign資料夾存取](access-management-folders.md)

* [訪問權限矩陣](access-management-named-rights.md#access-rights-matrix)


另請參閱：

* [管理工作流程的權限](../../workflow/using/managing-rights.md)
* [管理分散式行銷的權限](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [管理互動模組的權限](../../interaction/using/operator-profiles.md)
* [篩選結構存取權](../../configuration/using/filtering-schemas.md)
* [限制PI檢視](../../configuration/using/restricting-pii-view.md)
