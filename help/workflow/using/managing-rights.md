---
product: campaign
title: 管理工作流程權限
description: 了解如何管理工作流程權限
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 管理工作流程權限{#managing-rights}

![](../../assets/common.svg)

如果Adobe Campaign運算子不是管理員，則需要存取權限才能建立、執行或修改工作流程。

一般而言，依工作流程運作的運算子必須存取包含各種活動（收件者、收件者清單、訂閱、傳送等）期間所使用資料的檔案，以及可能包含其子檔案。

它們也必須對應至命名的權限，這些權限應與工作流程所執行的動作（收件者匯入、檔案存取、融合、SQL指令碼執行等）一致。

有關管理運算子和權限的詳細資訊，請參閱此[節](../../platform/using/access-management.md)。

## 運算元組 {#operator-groups-wf}

下列運算子群組會與工作流程相關聯：

* **[!UICONTROL Workflow execution]**&#x200B;群組可讓您控制目標工作流程的執行和核准：名為「權限」的工作流將映射到此組的運算子。 除了存取資料檔案的權限外，工作流程上的所有動作都需要此功能。 預設情況下，**[!UICONTROL Workflow execution]**&#x200B;組對標準目標工作流檔案和工作流模板具有只讀訪問權限。 此組中的操作員也具有對待批准檔案的讀寫權限。
* **[!UICONTROL Workflow supervisors]**&#x200B;群組可讓運算子管理工作流程核准。
* 存取促銷活動工作流程的&#x200B;**[!UICONTROL Operation Managers]**&#x200B;群組。

## 已命名的權限 {#named-rights}

只有名為右側的工作流程專屬於工作流程：它可讓您建立、啟動和停止工作流程。 需要有工作流檔案的讀取權限才能適用已命名的權限。 對於目標工作流程，**[!UICONTROL Profiles and Targets]**&#x200B;檔案上需要右鍵的讀取。

## 工作流執行帳戶 {#workflow-execution-account}

您可以設定要在工作流程範本層級使用的執行帳戶。 執行帳戶可讓您直接將授權對應至工作流程，而不考慮開始執行的Adobe Campaign運算子。 依預設，每個工作流程都會以啟動該工作流程的運算子的權限執行。

要將執行帳戶映射到工作流，請轉至工作流模板清單，然後按一下右鍵連結到工作流的模板。 選擇&#x200B;**[!UICONTROL Action > Change execution account...]**，然後選擇要使用的帳戶。
