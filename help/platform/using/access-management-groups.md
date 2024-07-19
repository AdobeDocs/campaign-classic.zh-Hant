---
product: campaign
title: 建立及管理操作員群組
description: 瞭解如何授與操作員群組的存取權
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# 建立及管理操作員群組 {#operator-groups}

>[!NOTE]
>
>這些程式僅適用於使用原生驗證連線到Campaign的運運算元。 如需Adobe IMS驗證資訊，請參閱[此檔案](https://helpx.adobe.com/tw/enterprise/using/user-groups.html)。

運運算元群組是透過樹狀結構中的&#x200B;**[!UICONTROL Administration > Access management > Operator groups]**&#x200B;節點所建立。

## 建立新的運運算元群組 {#creating-a-new-operator-group}

若要建立新的運運算元群組，請套用下列步驟：

1. 按一下群組清單右側的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，或用滑鼠右鍵按一下清單，然後選擇&#x200B;**[!UICONTROL New]**。
1. 在區段下方視窗中，從&#x200B;**[!UICONTROL General]**&#x200B;索引標籤，在對應欄位中輸入此群組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下&#x200B;**[!UICONTROL Content]**&#x200B;標籤以定義此群組的授權。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選取要與群組建立關聯的指定許可權或運運算元。
1. 按一下下拉式清單或&#x200B;**[!UICONTROL Folder]**&#x200B;欄位右側的資料夾，以尋找要與此群組關聯的指定許可權或操作者。
1. 選取要新增的許可權或運運算元，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此作業以新增其他許可權或操作者。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕，將群組新增至清單。

## 預設群組 {#default-groups}

預設運運算元群組為：

1. **[!UICONTROL Administrator]**

   此群組中的運運算元具有此執行個體的完整存取權。 管理員是可存取介面中最技術部分的使用者。 他們持有&#x200B;**[!UICONTROL Administration]**&#x200B;角色，並確認平台已全部設定。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL ADMINISTRATION]**：執行/建立/編輯/刪除任何物件的權利，例如工作流程、傳遞、指令碼等

1. **[!UICONTROL Delivery operators]**

   此群組中的運運算元負責管理傳送：他們可讓您存取建立和準備傳送所需的主要資源（行銷活動型別、傳送對應、預設範本、個人化區塊等）。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL PREPARE DELIVERIES]**：有權建立、編輯和開始傳遞分析，
   * **[!UICONTROL START DELIVERIES]**：核准先前分析的傳遞的許可權。

1. **[!UICONTROL Campaign managers]**

   此群組中的操作員可以管理行銷活動：它可讓您存取連結至行銷活動的物件（計畫、方案、工作流程、預算等） 在&#x200B;**[!UICONTROL Campaign]**&#x200B;的架構中(選擇性的Adobe Campaign模組)。

   此群組包含下列已命名的許可權：

   * **[!UICONTROL INSERT FOLDERS]**：將資料夾插入Adobe Campaign樹狀結構的許可權（前提是您擁有相關分支的編輯許可權），
   * **[!UICONTROL WORKFLOW]**：使用工作流程的權利。

   >[!NOTE]
   >
   >此群組不會讓操作者開始傳遞。

1. **[!UICONTROL Content contributors]**

   此群組中的運運算元可以存取&#x200B;**[!UICONTROL Content management]**&#x200B;架構內的內容資料夾(選擇性的Adobe Campaign模組)。 此群組不會授予任何其他權利。

1. **[!UICONTROL Access to reports]**

   此群組為外部操作員保留，以便針對特定操作員啟用「行銷活動控制面板」中的「報表」、「排程」和「論壇」圖示。

1. **[!UICONTROL Workflow execution]**

   此群組可讓您指派操作員管理與行銷活動無關的工作流程許可權。

1. **[!UICONTROL Workflow supervisors]**

   若出現行銷活動工作流程相關警示，此群組中的操作員會收到電子郵件通知。

1. 本機/中央管理

   這些群組可讓您使用&#x200B;**[!UICONTROL Distributed marketing]** (選擇性的Adobe Campaign模組)。

1. **[!UICONTROL Offer managers]**

   此群組中的運運算元可以建立和維護優惠方案。 如需詳細資訊，請參閱此[頁面](../../interaction/using/operator-profiles.md)。
此群組包含下列已命名的許可權：

   * **[!UICONTROL INSERT FOLDERS]**：將資料夾插入Adobe Campaign樹狀結構的許可權（前提是您擁有相關分支的編輯許可權），
   * **[!UICONTROL EDIT FOLDERS]**：變更資料夾屬性的權利，例如內部名稱、標籤、關聯的影像、子資料夾順序等。
