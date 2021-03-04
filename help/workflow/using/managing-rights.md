---
solution: Campaign Classic
product: campaign
title: 管理工作流程權限
description: 瞭解如何管理工作流程權限
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# 管理工作流權限{#managing-rights}

如果非管理員，Adobe Campaign營運商需要建立、執行或修改工作流程的存取權。

一般而言，負責工作流程的營運商必須存取包含各種活動（收件者、收件者清單、訂閱、傳送等）期間所使用資料的檔案，以及可能的子檔案。

它們還必須映射到與工作流執行的操作（收件人導入、檔案訪問、融合、SQL指令碼執行等）一致的命名權限。

有關管理運算子和權限的詳細資訊，請參閱此[部分](../../platform/using/access-management.md)。

## 運算子群組{#operator-groups}

下列運算元群組與工作流程相關聯：

* **[!UICONTROL Workflow execution]**&#x200B;群組可讓您控制定位工作流程的執行和核准：名為right的工作流程會映射至此群組的運算子。 除了資料檔案的存取權限外，工作流程上的所有動作都需要此選項。 依預設，**[!UICONTROL Workflow execution]**&#x200B;群組具有標準定位工作流程檔案和工作流程範本的唯讀存取權。 此群組中的運算子也擁有待核准檔案的讀取和寫入存取權。
* **[!UICONTROL Workflow supervisors]**&#x200B;群組可讓營運商管理工作流程核准。
* **[!UICONTROL Operation Managers]**&#x200B;群組，可存取促銷活動工作流程。

## 命名權限{#named-rights}

只有指名為right的WORKFLOW才是工作流的特定內容：它可讓您建立、啟動和停止工作流程。 必須具備工作流檔案的讀取權限，才能適用已命名的權限。 對於定位工作流程，**[!UICONTROL Profiles and Targets]**&#x200B;檔案上必須右側閱讀。

## 工作流執行帳戶{#workflow-execution-account}

您可以設定要在工作流程範本層級使用的執行帳戶。 執行帳戶可讓您直接將授權對應至工作流程，而不考慮啟動執行的Adobe Campaign運算子。 依預設，每個工作流程都會以啟動該工作流程的運算子的權限執行。

若要將執行帳戶映射至工作流程，請移至工作流程範本清單，然後在連結至工作流程的範本上按一下滑鼠右鍵。 選擇&#x200B;**[!UICONTROL Action > Change execution account...]**，然後選擇要使用的帳戶。
