---
product: campaign
title: 建立及管理操作員群組
description: 瞭解如何授與操作員群組的存取權
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---

# 建立及管理操作員群組 {#operator-groups}



運運算元群組是透過 **[!UICONTROL Administration > Access management > Operator groups]** 樹狀結構中的節點。

## 建立新的運運算元群組 {#creating-a-new-operator-group}

若要建立新的運運算元群組，請套用下列步驟：

1. 按一下 **[!UICONTROL New]** 群組清單右側的按鈕，或以滑鼠右鍵按一下清單並選擇 **[!UICONTROL New]**.
1. 在區段下方的視窗中，從 **[!UICONTROL General]** 索引標籤中，在對應欄位中輸入此群組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下 **[!UICONTROL Content]** 標籤定義此群組的授權。
1. 按一下 **[!UICONTROL Add]** 按鈕以選取要與群組產生關聯的指定權利或操作者。
1. 按一下下拉式清單或 **[!UICONTROL Folder]** 欄位，找出要與此群組建立關聯的指定許可權或操作者。
1. 選取要新增的許可權或運運算元，然後按一下 **[!UICONTROL OK]** 以進行驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此作業以新增其他許可權或操作者。

1. 按一下 **[!UICONTROL Save]** 按鈕以將群組新增至清單。

## 預設群組 {#default-groups}

預設運運算元群組為：

1. **[!UICONTROL Administrator]**

   此群組中的運運算元具有此執行個體的完整存取權。 管理員是可存取介面中最技術部分的使用者。 他們持有 **[!UICONTROL Administration]** 角色並確保平台已全部設定。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL ADMINISTRATION]**：執行/建立/編輯/刪除任何物件的權利，例如工作流程、傳送、指令碼等

1. **[!UICONTROL Delivery operators]**

   此群組中的運運算元負責管理傳送：他們可讓您存取建立和準備傳送所需的主要資源（行銷活動型別、傳送對應、預設範本、個人化區塊等）。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL PREPARE DELIVERIES]**：直接建立、編輯和開始傳送分析，
   * **[!UICONTROL START DELIVERIES]**：核准先前分析的傳送的權利。

1. **[!UICONTROL Campaign managers]**

   此群組中的操作員可以管理行銷活動：它可讓您存取連結至行銷活動的物件（計畫、方案、工作流程、預算等） 在的架構內 **[!UICONTROL Campaign]** (選擇性Adobe Campaign模組)。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL INSERT FOLDERS]**：將資料夾插入Adobe Campaign樹狀結構的權利（前提是您擁有相關分支的編輯許可權），
   * **[!UICONTROL WORKFLOW]**：使用工作流程的權利。

   >[!NOTE]
   >
   >此群組不會讓操作者開始傳遞。

1. **[!UICONTROL Content contributors]**

   此群組中的操作員可在的框架記憶體取內容資料夾 **[!UICONTROL Content management]** (選擇性Adobe Campaign模組)。 此群組不會授予任何其他權利。

1. **[!UICONTROL Access to reports]**

   此群組是保留給外部操作者，以透過Web存取存取傳遞報告。

1. **[!UICONTROL Workflow execution]**

   此群組可讓您指派操作員管理與行銷活動無關的工作流程許可權。

1. **[!UICONTROL Workflow supervisors]**

   若出現行銷活動工作流程相關警示，此群組中的操作員會收到電子郵件通知。

1. 本機/中央管理

   這些群組可讓您使用 **[!UICONTROL Distributed marketing]** (選擇性Adobe Campaign模組)。

1. **[!UICONTROL Offer managers]**

   此群組中的運運算元可以建立和維護優惠方案。 如需詳細資訊，請參閱此 [頁面](../../interaction/using/operator-profiles.md).
此群組包含下列已命名的許可權：

   * **[!UICONTROL INSERT FOLDERS]**：將資料夾插入Adobe Campaign樹狀結構的權利（前提是您擁有相關分支的編輯許可權），
   * **[!UICONTROL EDIT FOLDERS]**：變更資料夾屬性的權利，例如內部名稱、標籤、關聯的影像、子資料夾順序等。
