---
title: 稽核記錄
seo-title: 稽核記錄
description: 稽核記錄
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 稽核記錄{#audit-trail}

在Adobe Campaign中，您可 **[!UICONTROL Audit trail]** 以存取實例中所做變更的完整記錄。

**[!UICONTROL Audit trail]** 即時擷取在Adobe Campaign例項中發生的動作和事件的完整清單。 它包含自助式方式，可存取資料記錄，以協助回答下列問題：您的工作流程發生了什麼，以及誰上次更新了工作流程，或您的使用者在執行個體中做了什麼。

>[!NOTE]
>
>Adobe Campaign不會審核在使用者權限、範本、個人化或促銷活動中所做的變更。\
>稽核記錄只能由執行個體的管理員管理。

稽核記錄包含三個元件：

* **結構審計線索**:檢查活動和對方案所做的最後修改。

   有關方案的詳細資訊，請參閱本 [頁](../../configuration/using/data-schemas.md)。

* **工作流程稽核記錄**:檢查對工作流所做的活動和最後修改，另外，檢查工作流的狀態，例如：

   * 開始
   * 暫停
   * 停止
   * 重新啟動
   * 清除等於「清除」歷史記錄的操作
   * 在模擬模式中模擬與動作相等的啟動
   * 喚醒與操作相等立即執行暫掛任務
   * 無條件停止
   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   有關如何監控工作流程的詳細資訊，請參閱專 [用章節](../../workflow/using/monitoring-workflow-execution.md)。

* **選項審核跟蹤**:檢查活動和對選項所做的最後修改。

   有關選項的詳細資訊，請參閱本 [頁](../../installation/using/configuring-campaign-options.md)。

## 訪問審核跟蹤 {#accessing-audit-trail}

若要存取您實例的 **[!UICONTROL Audit trail]** :

1. 存取您 **[!UICONTROL Explorer]** 實例的功能表。
1. 在功能表 **[!UICONTROL Administration]** 下，選取 **[!UICONTROL Audit]** 。

   ![](assets/audit_trail_1.png)

1. 窗 **[!UICONTROL Audit trail]** 口隨即開啟，其中包含實體清單。 Adobe Campaign會稽核工作流程、選項和結構描述的建立、編輯和刪除動作。

   選取其中一個實體，以進一步瞭解最後修改。

   ![](assets/audit_trail_2.png)

1. 該窗 **[!UICONTROL Audit entity]** 口提供有關所選實體的更詳細資訊，如：

   * **[!UICONTROL Type]** :工作流、選項或結構。
   * **[!UICONTROL Entity]** :活動的內部名稱。
   * **[!UICONTROL Modified by]** :上次修改此實體的最後一個人員的使用者名稱。
   * **[!UICONTROL Action]** :上次對此實體執行的動作為「已建立」、「已編輯」或「已刪除」。
   * **[!UICONTROL Modification date]** :上次對此實體執行動作的日期。
   程式碼區塊會提供您實體中確切變更內容的詳細資訊。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>根據預設，保留期為180天 **[!UICONTROL Audit logs]** 。 要瞭解有關如何更改保留期的詳細資訊，請參閱本 [頁](../../production/using/database-cleanup-workflow.md#deployment-wizard)。

## 啟用／停用稽核記錄 {#enable-disable-audit-trail}

例如，如果您想要在資料庫中儲存一些空間，您就可以針對特定活動輕鬆啟用或停用稽核記錄。

若要這麼做：

1. 存取您 **[!UICONTROL Explorer]** 實例的功能表。
1. 在功能表 **[!UICONTROL Administration]** 下，依序選 **[!UICONTROL Platform]** 取 **[!UICONTROL Options]** 。

   ![](assets/audit_trail_4.png)

1. 根據要激活／停用的圖元，選擇以下選項之一：

   * 對於工作流： **[!UICONTROL XtkAudit_Workflows]**
   * 對於結構： **[!UICONTROL XtkAudit_DataSchema]**
   * 對於選項： **[!UICONTROL XtkAudit_Option]**
   * 針對每個實體： **[!UICONTROL XtkAudit_Enable_All]**
   ![](assets/audit_trail_5.png)

1. 如果 **[!UICONTROL Value]** 要啟用實體，請將變更為1；若要停用實體，請變更為0。

   ![](assets/audit_trail_6.png)

1. 按一下 **[!UICONTROL Save]** .

