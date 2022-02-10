---
product: campaign
title: 稽核軌跡
description: 瞭解如何使用市場活動審核跟蹤來監視實例
feature: Audit Trail, Monitoring
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# 稽核軌跡{#audit-trail}

![](../../assets/v7-only.svg)

在Adobe Campaign, **[!UICONTROL Audit trail]** 允許您訪問在實例中所做的更改的完整歷史記錄。

**[!UICONTROL Audit trail]** 即時捕獲在您的Adobe Campaign實例中發生的操作和事件的綜合清單。 它包括訪問資料歷史的自助式方法，以幫助回答以下問題：您的工作流發生了什麼，上次更新工作流的人員或用戶在實例中做了什麼。

>[!NOTE]
>
>Adobe Campaign不審核在用戶權限、模板、個性化或市場活動中所做的更改。\
>審核跟蹤只能由實例的管理員管理。

審核跟蹤包括三個元件：

* **架構審核跟蹤**:檢查活動和對方案所做的最後修改。

   有關架構的詳細資訊，請參閱 [頁](../../configuration/using/data-schemas.md)。

* **工作流審核跟蹤**:檢查活動和對工作流所做的最後修改，另外檢查工作流的狀態，例如：

   * 開始
   * 暫停
   * 停止
   * 重新啟動
   * 清理 它等於「清除」(Purge)歷史記錄
   * 在模擬模式下模擬與動作「開始」相等
   * 喚醒，此喚醒等於立即執行掛起的任務
   * 無條件停止

   有關工作流的詳細資訊，請參閱 [頁](../../workflow/using/about-workflows.md)。

   有關如何監視工作流的詳細資訊，請參閱 [專用段](../../workflow/using/monitoring-workflow-execution.md)。

* **選項審核跟蹤**:檢查活動和對選項所做的最後修改。

   有關選項的詳細資訊，請參閱 [頁](../../installation/using/configuring-campaign-options.md)。

## 訪問審核跟蹤 {#accessing-audit-trail}

訪問實例 **[!UICONTROL Audit trail]** :

1. 訪問 **[!UICONTROL Explorer]** 的子菜單。
1. 在 **[!UICONTROL Administration]** 菜單，選擇 **[!UICONTROL Audit]** 。

   ![](assets/audit_trail_1.png)

1. 的 **[!UICONTROL Audit trail]** 窗口。 Adobe Campaign將審核工作流、選項和架構的建立、編輯和刪除操作。

   選擇其中一個實體以瞭解有關上次修改的詳細資訊。

   ![](assets/audit_trail_2.png)

1. 的 **[!UICONTROL Audit entity]** 窗口將提供有關所選實體的更詳細資訊，如：

   * **[!UICONTROL Type]** :工作流、選項或方案。
   * **[!UICONTROL Entity]** :活動的內部名稱。
   * **[!UICONTROL Modified by]** :上次修改此實體的最後一個人的用戶名。
   * **[!UICONTROL Action]** :上次對此實體執行的操作（建立、編輯或刪除）。
   * **[!UICONTROL Modification date]** :對此實體執行的上次操作的日期。

   代碼塊將為您提供有關實體中更改內容的詳細資訊。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>預設情況下，保留期設定為180天 **[!UICONTROL Audit logs]** 。 要瞭解有關如何更改保留期的詳細資訊，請參閱此 [頁](../../production/using/database-cleanup-workflow.md#deployment-wizard)。

## 啟用/禁用審核跟蹤 {#enable-disable-audit-trail}

例如，如果要在資料庫上節省一些空間，則可以輕鬆激活或停用特定活動的審核跟蹤。

若要這麼做：

1. 訪問 **[!UICONTROL Explorer]** 的子菜單。
1. 在 **[!UICONTROL Administration]** 菜單，選擇 **[!UICONTROL Platform]** 然後 **[!UICONTROL Options]** 。

   ![](assets/audit_trail_4.png)

1. 根據要激活/停用的實體，選擇以下選項之一：

   * 對於工作流： **[!UICONTROL XtkAudit_Workflows]**
   * 對於架構： **[!UICONTROL XtkAudit_DataSchema]**
   * 對於選項： **[!UICONTROL XtkAudit_Option]**
   * 對於每個實體： **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 更改 **[!UICONTROL Value]** 如果要啟用實體，則為1；如果要禁用實體，則為0。

   ![](assets/audit_trail_6.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。
