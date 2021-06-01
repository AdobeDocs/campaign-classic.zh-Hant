---
product: campaign
title: 稽核軌跡
description: 稽核軌跡
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# 稽核軌跡{#audit-trail}

在Adobe Campaign中，**[!UICONTROL Audit trail]**&#x200B;可讓您存取在執行個體中所做變更的完整歷史記錄。

**[!UICONTROL Audit trail]** 即時擷取在您的Adobe Campaign例項中發生之動作和事件的完整清單。其中包括自助式存取資料記錄，以協助回答下列問題：工作流程的變更，以及上次更新工作流程的使用者，或您的使用者在例項中執行的動作。

>[!NOTE]
>
>Adobe Campaign不會稽核使用者權限、範本、個人化或促銷活動中所做的變更。\
>稽核軌跡只能由執行個體的管理員管理。

稽核軌跡包含三個元件：

* **結構稽核軌跡**:檢查活動以及上次對您的結構完成的修改。

   如需結構的詳細資訊，請參閱此[page](../../configuration/using/data-schemas.md)。

* **工作流程稽核軌跡**:檢查活動和上次對工作流程完成的修改，此外，還檢查工作流程的狀態，例如：

   * 開始
   * 暫停
   * 停止
   * 重新啟動
   * 清理 與「清除」歷史記錄相等
   * 在模擬模式下模擬與「啟動」(Start)操作相等
   * 喚醒與「立即執行掛起任務」操作相等
   * 無條件停止

   如需工作流程的詳細資訊，請參閱此[page](../../workflow/using/about-workflows.md)。

   有關如何監視工作流的詳細資訊，請參閱[專用區段](../../workflow/using/monitoring-workflow-execution.md)。

* **選項稽核軌跡**:勾選活動，以及上次對選項完成的修改。

   有關選項的詳細資訊，請參閱此[page](../../installation/using/configuring-campaign-options.md)。

## 訪問審核跟蹤{#accessing-audit-trail}

若要存取執行個體的&#x200B;**[!UICONTROL Audit trail]** :

1. 存取執行個體的&#x200B;**[!UICONTROL Explorer]**&#x200B;功能表。
1. 在&#x200B;**[!UICONTROL Administration]**&#x200B;功能表下，選取&#x200B;**[!UICONTROL Audit]** 。

   ![](assets/audit_trail_1.png)

1. 隨即開啟&#x200B;**[!UICONTROL Audit trail]**&#x200B;窗口，其中包含實體清單。 Adobe Campaign會稽核工作流程、選項和結構的建立、編輯和刪除動作。

   選取其中一個實體，以進一步了解上次修改。

   ![](assets/audit_trail_2.png)

1. **[!UICONTROL Audit entity]**&#x200B;窗口為您提供有關所選實體的更詳細資訊，例如：

   * **[!UICONTROL Type]** :工作流程、選項或結構。
   * **[!UICONTROL Entity]** :活動的內部名稱。
   * **[!UICONTROL Modified by]** :上次修改此實體的最後一個人員的用戶名。
   * **[!UICONTROL Action]** :上次對此實體執行的操作，即「已建立」、「已編輯」或「已刪除」。
   * **[!UICONTROL Modification date]** :對此實體執行的上次操作的日期。

   程式碼區塊會提供您實體中確切變更項目的詳細資訊。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>根據預設，**[!UICONTROL Audit logs]**&#x200B;的保留期間設為180天。 若要進一步了解如何變更保留期，請參閱此[page](../../production/using/database-cleanup-workflow.md#deployment-wizard)。

## 啟用/禁用審核跟蹤{#enable-disable-audit-trail}

例如，如果您想要在資料庫中儲存一些空間，則可以輕鬆啟動或停用特定活動的稽核軌跡。

若要這麼做：

1. 存取執行個體的&#x200B;**[!UICONTROL Explorer]**&#x200B;功能表。
1. 在&#x200B;**[!UICONTROL Administration]**&#x200B;功能表下，依序選取&#x200B;**[!UICONTROL Platform]**&#x200B;和&#x200B;**[!UICONTROL Options]** 。

   ![](assets/audit_trail_4.png)

1. 根據要激活/停用的實體，選擇以下選項之一：

   * 對於工作流：**[!UICONTROL XtkAudit_Workflows]**
   * 結構描述：**[!UICONTROL XtkAudit_DataSchema]**
   * 對於選項：**[!UICONTROL XtkAudit_Option]**
   * 對於每個實體：**[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 如果要啟用實體，請將&#x200B;**[!UICONTROL Value]**&#x200B;變更為1；如果要停用實體，則變更為0。

   ![](assets/audit_trail_6.png)

1. 按一下 **[!UICONTROL Save]**。
