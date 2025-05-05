---
product: campaign
title: 稽核軌跡
description: 瞭解如何使用Campaign稽核軌跡監控您的執行個體
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3d1ed85dcafc5afc4088db98c09d78fb7e9c0a39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# 稽核軌跡{#audit-trail}

>[!INFO]
>
>在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/audit-trail)中進一步瞭解稽核軌跡功能。

在Adobe Campaign中，**[!UICONTROL Audit trail]**&#x200B;可讓您存取執行個體中所做變更的完整歷史記錄。

**[!UICONTROL Audit trail]**&#x200B;可以即時擷取Adobe Campaign執行個體中發生之動作和事件的完整清單。 功能包括自助式存取歷史資料記錄，以協助回答下列問題：您的工作流程發生什麼事、上次更新者是誰，或您的使用者在執行個體中做了什麼。

>[!NOTE]
>
>Adobe Campaign不會稽核使用者許可權、範本、個人化或行銷活動中所做的變更。\
>稽核軌跡只能由執行個體的管理員管理。

![](assets/audit_trail_2.png)

+++ 深入瞭解稽核軌跡可用實體

* **結構描述稽核軌跡**：可讓您探索對結構描述所做的變更，以及識別進行這些修改的人和發生時間。

  如需結構描述的詳細資訊，請參閱此[頁面](../../configuration/using/data-schemas.md)。

* **工作流程稽核軌跡**&#x200B;會追蹤與工作流程相關的所有動作，包括：

   * 開始
   * 暫停
   * 停止
   * 重新啟動
   * 清除等於動作清除歷史記錄
   * 模擬在模擬模式下等於動作「開始」的專案
   * 立即喚醒等於動作執行擱置中的工作
   * 無條件停止

  如需工作流程的詳細資訊，請參閱此[頁面](../../workflow/using/about-workflows.md)。

  如需如何監視工作流程的詳細資訊，請參閱[專屬區段](../../workflow/using/monitoring-workflow-execution.md)。

* **選項稽核軌跡**&#x200B;可讓您檢查活動和對選項進行的最後修改。

  如需選項的詳細資訊，請參閱此[頁面](../../installation/using/configuring-campaign-options.md)。

* **傳遞稽核軌跡**&#x200B;可讓您檢查活動和對傳遞進行的最後修改。

  如需傳遞的詳細資訊，請參閱此[頁面](../../delivery/using/communication-channels.md)。

* **外部帳戶**&#x200B;可讓您檢查對外部帳戶所做的修改，這些修改由技術流程（如技術工作流程或行銷活動工作流程）使用。

  如需外部帳戶的詳細資訊，請參閱此[頁面](../../installation/using/external-accounts.md)。

* **傳遞對應**&#x200B;可讓您監視活動以及最近對傳遞對應所做的修改。

  如需傳遞對應的詳細資訊，請參閱此[頁面](../../configuration/using/target-mapping.md)。

* **網頁應用程式**&#x200B;可讓您檢查在Campaign V8中對網頁表單所做的修改，這些修改用於建立具有輸入和選擇欄位的頁面，並且可能包含來自資料庫的資料。

  如需網頁應用程式的詳細資訊，請參閱此[頁面](../../web/using/about-web-applications.md)。

* **選件**&#x200B;可讓您檢查活動和對您的選件進行的最後修改。

  如需優惠方案的詳細資訊，請參閱此[頁面](../../interaction/using/interaction-and-offer-management.md)。

* **操作員**&#x200B;可讓您監視活動以及最近對操作員所做的修改。

  如需運運算元的詳細資訊，請參閱此[頁面](../../platform/using/access-management-operators.md)。

+++
