---
product: campaign
title: 稽核軌跡
description: 瞭解如何使用Campaign稽核軌跡監控您的執行個體
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---

# 稽核軌跡{#audit-trail}



在Adobe Campaign中 **[!UICONTROL Audit trail]** 可讓您存取執行個體中所做變更的完整歷史記錄。

**[!UICONTROL Audit trail]** 即時擷取在Adobe Campaign例項中發生之動作和事件的完整清單。 功能包括自助式存取歷史資料記錄，以協助回答下列問題：您的工作流程發生什麼事、上次更新者是誰，或您的使用者在執行個體中做了什麼。

>[!NOTE]
>
>Adobe Campaign不會稽核使用者許可權、範本、個人化或行銷活動中所做的變更。\
>稽核軌跡只能由執行個體的管理員管理。

稽核軌跡包含三個元件：

* **結構描述稽核軌跡**：檢查活動和對結構描述所做的最後修改。

  如需結構描述的詳細資訊，請參閱本節 [頁面](../../configuration/using/data-schemas.md).

* **工作流程稽核軌跡**：檢查活動和對工作流程進行的最後修改，另外檢查工作流程的狀態，例如：

   * 開始
   * 暫停
   * 停止
   * 重新啟動
   * 清除等於動作清除歷史記錄
   * 模擬在模擬模式下等於動作「開始」的專案
   * 立即喚醒等於動作執行擱置中的工作
   * 無條件停止

  如需工作流程的詳細資訊，請參閱本 [頁面](../../workflow/using/about-workflows.md).

  如需如何監視工作流程的詳細資訊，請參閱 [專用區段](../../workflow/using/monitoring-workflow-execution.md).

* **選項稽核軌跡**：檢查活動及對選項進行的最後修改。

  如需選項的詳細資訊，請參閱本節 [頁面](../../installation/using/configuring-campaign-options.md).

## 存取稽核軌跡 {#accessing-audit-trail}

若要存取執行個體的 **[!UICONTROL Audit trail]** ：

1. 存取 **[!UICONTROL Explorer]** 執行個體的功能表。
1. 在 **[!UICONTROL Administration]** 功能表，選取 **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. 此 **[!UICONTROL Audit trail]** 視窗會開啟，其中含有您的實體清單。 Adobe Campaign將稽核工作流程、選項和結構的建立、編輯和刪除動作。

   選取其中一個實體以深入瞭解最後的修改。

   ![](assets/audit_trail_2.png)

1. 此 **[!UICONTROL Audit entity]** 視窗會提供所選實體的詳細資訊，例如：

   * **[!UICONTROL Type]** ：工作流程、選項或結構描述。
   * **[!UICONTROL Entity]** ：活動的內部名稱。
   * **[!UICONTROL Modified by]** ：上次修改此實體之人員的使用者名稱。
   * **[!UICONTROL Action]** ：此實體上執行的最後一個動作，已建立、已編輯或已刪除。
   * **[!UICONTROL Modification date]** ：此實體上個動作執行的日期。

   程式碼區塊會針對實體中的確切變更提供詳細資訊。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>根據預設，保留期間設為180天 **[!UICONTROL Audit logs]** . 若要瞭解如何變更保留期的詳細資訊，請參閱本 [頁面](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## 啟用/停用稽核軌跡 {#enable-disable-audit-trail}

例如，如果您想在資料庫上節省一些空間，可以輕鬆地為特定活動啟用或停用稽核軌跡。

若要這麼做：

1. 存取 **[!UICONTROL Explorer]** 執行個體的功能表。
1. 在 **[!UICONTROL Administration]** 功能表，選取 **[!UICONTROL Platform]** 則 **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. 根據您想要啟動/取消啟動的實體，選取下列選項之一：

   * 針對工作流程： **[!UICONTROL XtkAudit_Workflows]**
   * 針對結構描述： **[!UICONTROL XtkAudit_DataSchema]**
   * 若為選項： **[!UICONTROL XtkAudit_Option]**
   * 對於每個實體： **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 變更 **[!UICONTROL Value]** 設為1 （如果要啟用實體）或0 （如果要停用）。

   ![](assets/audit_trail_6.png)

1. 按一下 **[!UICONTROL Save]** .
