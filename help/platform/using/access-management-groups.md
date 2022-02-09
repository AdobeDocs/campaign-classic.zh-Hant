---
product: campaign
title: 建立和管理運算子組
description: 瞭解如何授予對操作員組的訪問權限
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 建立和管理運算子組 {#operator-groups}

![](../../assets/common.svg)

通過 **[!UICONTROL Administration > Access management > Operator groups]** 的子菜單。

## 建立新運算子組 {#creating-a-new-operator-group}

要建立新運算子組，請應用以下步驟：

1. 按一下 **[!UICONTROL New]** 的子菜單。 **[!UICONTROL New]**。
1. 在下部窗口中，從 **[!UICONTROL General]** 頁籤，在相應欄位中輸入該組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下 **[!UICONTROL Content]** 的子菜單。
1. 按一下 **[!UICONTROL Add]** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。
1. 按一下下拉清單或位於右側的資料夾 **[!UICONTROL Folder]** 欄位以查找要與此組關聯的指定權限或運算子。
1. 選擇要添加的權限或運算子，然後按一下 **[!UICONTROL OK]** 驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此操作以添加其他權限或運算子。

1. 按一下 **[!UICONTROL Save]** 按鈕，將組添加到清單中。

## 預設組 {#default-groups}

預設運算子組為：

1. **[!UICONTROL Administrator]**

   此組中的運算子對實例具有完全訪問權限。 管理員是可以訪問介面中技術最先進的用戶。 他們握住 **[!UICONTROL Administration]** 確保平台已全部設定。

   此組包含以下命名權限：

   * **[!UICONTROL ADMINISTRATION]**:執行/建立/編輯/刪除任何對象（如工作流、交付、指令碼等）的權限。

1. **[!UICONTROL Delivery operators]**

   此組中的操作員負責管理交貨：它們允許訪問建立和準備交貨所需的主要資源（市場活動類型、交貨映射、預設模板、個性化塊等）。

   此組包含以下命名權限：

   * **[!UICONTROL PREPARE DELIVERIES]**:建立、編輯和啟動交付分析，
   * **[!UICONTROL START DELIVERIES]**:批准先前分析的交貨的權利。

1. **[!UICONTROL Campaign managers]**

   此組中的操作員可以管理市場營銷活動：它允許您訪問連結到市場活動（計畫、計畫、工作流、預算等）的對象。 在 **[!UICONTROL Campaign]** (可選的Adobe Campaign模組)。

   此組包含以下命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹（前提是您對相關分支具有編輯權限）,
   * **[!UICONTROL WORKFLOW]**:有權使用工作流。
   >[!NOTE]
   >
   >此組不允許操作員開始交貨。

1. **[!UICONTROL Content contributors]**

   此組中的運算子可以訪問以下框架中的「內容」資料夾： **[!UICONTROL Content management]** (可選的Adobe Campaign模組)。 此組不授予任何附加權利。

1. **[!UICONTROL Access to reports]**

   此組保留給外部操作員，以便通過Web訪問訪問傳遞報告。

1. **[!UICONTROL Workflow execution]**

   通過此組，您可以分配操作員管理與市場活動無關的工作流的權利。

1. **[!UICONTROL Workflow supervisors]**

   此組中的操作員在有關市場活動工作流的警報時收到電子郵件通知。

1. 本地/中央管理

   這些組允許您使用 **[!UICONTROL Distributed marketing]** (可選的Adobe Campaign模組)。

1. **[!UICONTROL Offer managers]**

   此組中的運算子可以建立和維護聘用。 有關此的詳細資訊，請參閱此 [頁](../../interaction/using/operator-profiles.md)。
此組包含以下命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹（前提是您對相關分支具有編輯權限）,
   * **[!UICONTROL EDIT FOLDERS]**:更改資料夾屬性（如內部名稱、標籤、關聯影像、子資料夾順序等）的權限。
