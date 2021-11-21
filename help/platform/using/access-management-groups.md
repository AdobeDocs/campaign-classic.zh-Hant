---
product: campaign
title: 建立和管理運算子群組
description: 了解如何授予運算子群組的存取權
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 建立和管理運算子群組 {#operator-groups}

![](../../assets/common.svg)

運算子群組是透過 **[!UICONTROL Administration > Access management > Operator groups]** 節點。

## 建立新運算子組 {#creating-a-new-operator-group}

要建立新的運算子組，請應用以下步驟：

1. 按一下 **[!UICONTROL New]** 按鈕，或按一下右鍵該清單並選擇 **[!UICONTROL New]**.
1. 在下部窗口中，從 **[!UICONTROL General]** 頁簽，在相應欄位中輸入此組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下 **[!UICONTROL Content]** 頁簽，定義此組的授權。
1. 按一下 **[!UICONTROL Add]** 按鈕，選擇要與組關聯的指定權限或運算子。
1. 按一下下拉式清單，或位於 **[!UICONTROL Folder]** 欄位，以找到要與此組關聯的指定權限或操作員。
1. 選取要新增的權限或運算子，然後按一下 **[!UICONTROL OK]** 以驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此操作以添加其他權限或運算子。

1. 按一下 **[!UICONTROL Save]** 按鈕將組添加到清單中。

## 預設群組 {#default-groups}

預設運算子組為：

1. **[!UICONTROL Administrator]**

   此群組中的運算子可完整存取執行個體。 管理員是可存取介面中最技術部分的使用者。 他們拿著 **[!UICONTROL Administration]** 角色，並確定平台皆已設定。

   此群組包含下列命名權限：

   * **[!UICONTROL ADMINISTRATION]**:執行/建立/編輯/刪除任何物件（例如工作流程、傳送、指令碼等）的權限。

1. **[!UICONTROL Delivery operators]**

   此群組中的運算子負責管理傳送：它們可讓您存取建立和準備傳送所需的主要資源（行銷活動類型、傳送對應、預設範本、個人化區塊等）。

   此組包含以下命名權限：

   * **[!UICONTROL PREPARE DELIVERIES]**:建立、編輯和開始傳遞分析，
   * **[!UICONTROL START DELIVERIES]**:核准先前分析的傳送的權限。

1. **[!UICONTROL Campaign managers]**

   此群組中的運算子可以管理行銷活動：它可讓您存取連結至促銷活動（計畫、方案、工作流程、預算等）的物件 在 **[!UICONTROL Campaign]** (選用的Adobe Campaign模組)。

   此組包含以下命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹的權利（前提是您擁有相關分支的編輯權利）,
   * **[!UICONTROL WORKFLOW]**:使用工作流程的權限。
   >[!NOTE]
   >
   >此群組不會讓運算子開始傳送。

1. **[!UICONTROL Content contributors]**

   此群組中的運算子可以在 **[!UICONTROL Content management]** (選用的Adobe Campaign模組)。 此組不授予任何附加權利。

1. **[!UICONTROL Access to reports]**

   此群組會保留給外部運算子，以透過Web存取存取存取傳送報表。

1. **[!UICONTROL Workflow execution]**

   此群組可讓您指派運算子管理與促銷活動無關之工作流程的權利。

1. **[!UICONTROL Workflow supervisors]**

   此群組中的運算子會收到電子郵件通知，以防與促銷活動工作流程有關的警報發生。

1. 本地/中央管理

   這些群組可讓您使用 **[!UICONTROL Distributed marketing]** (選用的Adobe Campaign模組)。

1. **[!UICONTROL Offer managers]**

   此群組中的運算子可以建立及維護選件。 有關詳細資訊，請參閱 [頁面](../../interaction/using/operator-profiles.md).
此組包含以下命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹的權利（前提是您擁有相關分支的編輯權利）,
   * **[!UICONTROL EDIT FOLDERS]**:更改資料夾屬性的權限，如內部名稱、標籤、關聯影像、子資料夾順序等。
