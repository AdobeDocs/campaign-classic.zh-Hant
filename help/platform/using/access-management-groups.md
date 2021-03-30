---
solution: Campaign Classic
product: campaign
title: 建立和管理運算元群組
description: 瞭解如何授與營運商群組的存取權
feature: 存取管理
role: 業務從業人員、管理員
level: 初學者
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# 建立和管理運算子組{#operator-groups}

操作員組是通過樹中的&#x200B;**[!UICONTROL Administration > Access management > Operator groups]**&#x200B;節點建立的。

## 建立新的運算元群組{#creating-a-new-operator-group}

若要建立新的運算元群組，請套用下列步驟：

1. 按一下組清單右側的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，或按一下右鍵清單並選擇&#x200B;**[!UICONTROL New]**。
1. 在下方窗口的&#x200B;**[!UICONTROL General]**&#x200B;頁籤中，在相應欄位中輸入此組的名稱和說明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 按一下&#x200B;**[!UICONTROL Content]**&#x200B;頁籤以定義此組的授權。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選擇指定的右側或要與組關聯的運算子。
1. 按一下下拉清單或&#x200B;**[!UICONTROL Folder]**&#x200B;欄位右側的資料夾，以找到要與此組關聯的指定權限或運算子。
1. 選擇要添加的權限或運算子，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以驗證。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重複此操作以添加其他權限或運算子。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕，將群組新增至清單。

## 預設群組{#default-groups}

預設運算元群組為：

1. **[!UICONTROL Administrator]**

   此群組中的運算子擁有執行個體的完整存取權。 管理員是可存取介面中最具技術含量的使用者。 他們負責&#x200B;**[!UICONTROL Administration]**&#x200B;角色，並確保平台已全部設定。

   此群組包含下列指名的權限：

   * **[!UICONTROL ADMINISTRATION]**:執行／建立／編輯／刪除任何物件（例如工作流程、傳送、指令碼等）的權利。

1. **[!UICONTROL Delivery operators]**

   此群組的運算子負責管理傳送：它們可存取建立和準備傳送所需的主要資源（促銷活動類型、傳送對應、預設範本、個人化區塊等）。

   此群組包含下列命名權限：

   * **[!UICONTROL PREPARE DELIVERIES]**:直接建立、編輯和開始傳送分析，
   * **[!UICONTROL START DELIVERIES]**:核准先前分析的傳送。

1. **[!UICONTROL Campaign managers]**

   此群組中的運算子可以管理行銷促銷活動：它可讓您存取連結至促銷活動的物件（計畫、方案、工作流程、預算等） 在&#x200B;**[!UICONTROL Campaign]**(可選Adobe Campaign模組)框架內。

   此群組包含下列命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹的權利（前提是您對相關分支具有編輯權限）,
   * **[!UICONTROL WORKFLOW]**:使用工作流程。
   >[!NOTE]
   >
   >此群組不會讓運算子開始傳送。

1. **[!UICONTROL Content contributors]**

   此群組中的運算子可存取&#x200B;**[!UICONTROL Content management]**(選用的Adobe Campaign模組)架構內的「內容」資料夾。 此群組不授予任何額外權利。

1. **[!UICONTROL Access to reports]**

   此群組會保留給外部運算子，以透過Web存取存取來存取傳送報表。

1. **[!UICONTROL Workflow execution]**

   此群組可讓您指派營運商管理與促銷活動無關之工作流程的權利。

1. **[!UICONTROL Workflow supervisors]**

   此群組中的運算子會收到電子郵件通知，以防發生促銷活動工作流程的警報。

1. 本地／中央管理

   這些組可讓您使用&#x200B;**[!UICONTROL Distributed marketing]**(可選的Adobe Campaign模組)。

1. **[!UICONTROL Offer managers]**

   此群組中的運算子可建立及維護選件。 有關此問題的詳細資訊，請參閱此[頁](../../interaction/using/operator-profiles.md)。
此群組包含下列命名權限：

   * **[!UICONTROL INSERT FOLDERS]**:將資料夾插入Adobe Campaign樹的權利（前提是您對相關分支具有編輯權）,
   * **[!UICONTROL EDIT FOLDERS]**:有權更改資料夾屬性，如內部名稱、標籤、關聯的影像、子資料夾順序等。
