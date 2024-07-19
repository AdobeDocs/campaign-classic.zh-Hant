---
product: campaign
title: 管理工作流程許可權
description: 瞭解如何管理工作流程許可權
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---

# 管理工作流程許可權{#managing-rights}



如果不是管理員，Adobe Campaign操作員需要存取許可權才能建立、執行或修改工作流程。

一般而言，執行工作流程的操作員需要存取包含各種活動（收件者、收件者清單、訂閱、傳遞等）期間所使用資料的檔案，並可能需要存取其子檔案。

它們也必須對應至已命名的許可權，這些許可權必須與它們會影響的工作流程執行的動作（收件者匯入、檔案存取、融合、SQL指令碼執行等）一致。

如需管理操作員與許可權的詳細資訊，請參閱此[區段](../../platform/using/access-management.md)。

## 操作者群組 {#operator-groups-wf}

下列運運算元群組與工作流程相關聯：

* **[!UICONTROL Workflow execution]**&#x200B;群組可讓您控制目標工作流程的執行與核准：名為許可權的工作流程已對應至此群組的運運算元。 除了資料檔案的存取權之外，工作流程上的所有動作都需要它。 依預設，**[!UICONTROL Workflow execution]**&#x200B;群組對標準目標工作流程檔案和工作流程範本具有唯讀存取權。 此群組中的操作者也擁有擱置核准檔案的讀寫存取權。
* **[!UICONTROL Workflow supervisors]**&#x200B;群組可讓操作員管理工作流程核准。
* 用於存取行銷活動工作流程的&#x200B;**[!UICONTROL Operation Managers]**&#x200B;群組。

## 已命名的權限 {#named-rights}

只有已命名許可權的工作流程才特定於工作流程：它可讓您建立、啟動和停止工作流程。 已命名許可權必須具備工作流程檔案的讀取許可權才能適用。 若要進行目標工作流程，必須在&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;檔案上讀取許可權。

## 工作流程執行帳戶 {#workflow-execution-account}

您可以設定要在工作流程範本層級使用的執行帳戶。 執行帳戶可讓您將授權直接對應至工作流程，而不考慮Adobe Campaign運運算元開始執行。 依預設，每個工作流程都會以啟動工作流程的運運算元的許可權執行。

若要將執行帳戶對應至工作流程，請前往工作流程範本清單，然後以滑鼠右鍵按一下連結至工作流程的範本。 選擇&#x200B;**[!UICONTROL Action > Change execution account...]**，然後選取要使用的帳戶。
