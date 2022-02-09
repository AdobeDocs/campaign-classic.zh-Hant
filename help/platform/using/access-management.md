---
product: campaign
title: 開始使用權限
description: 瞭解如何授予對市場活動功能的訪問權限
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 6%

---

# 開始使用權限{#access-management}

![](../../assets/common.svg)

Adobe Campaign允許您定義和管理分配給各種運算子的權限。 這些是授權或拒絕的一組權利和限制：

* 訪問某些功能（通過指定權限）,
* 訪問某些記錄，
* 建立、修改和/或刪除記錄（活動、聯繫人、市場活動、組等）。

權限應用於操作員配置檔案或操作員組。

它們由與操作員與Adobe Campaign的連接模式相連結的安全參數完成。 有關中安全區的詳細資訊 [此頁](../../installation/using/security-zones.md)。

可以向用戶授予兩種權限類型：

* 您可以定義屬性權限的運算子組，然後將運算子與一個或多個組關聯。 這使您能夠重新使用權限並使操作員配置檔案更加一致。 它還方便了配置檔案的管理和維護。 組建立和管理在 [此部分](access-management-groups.md)。

* 您可以直接將命名權限屬性給用戶，在某些情況下，會使通過組分配的權限超負荷。 此等權利於 [此頁](access-management-named-rights.md)。

>[!NOTE]
>
>開始定義權限之前，Adobe建議您閱讀 [安全配置核對表](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。

瞭解如何授予訪問權限和在以下部分中設定權限：

* [建立運算子](access-management-operators.md)

* [定義組](access-management-groups.md)

* [添加命名權限](access-management-named-rights.md)

* [管理市場活動資料夾訪問](access-management-folders.md)

* [訪問權限矩陣](access-management-named-rights.md#access-rights-matrix)


另請參閱:

* [管理工作流的權限](../../workflow/using/managing-rights.md)
* [管理分佈式市場營銷的權限](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [管理交互模組的權限](../../interaction/using/operator-profiles.md)
* [篩選對架構的訪問](../../configuration/using/filtering-schemas.md)
* [限制PI視圖](../../configuration/using/restricting-pii-view.md)
