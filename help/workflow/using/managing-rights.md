---
title: 管理權限
seo-title: 管理權限
description: 管理權限
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 管理權限{#managing-rights}

如果Adobe Campaign營運商不是管理員，則需要建立、執行或修改工作流程的存取權限。

一般而言，負責工作流程的營運商必須存取包含各種活動（收件者、收件者清單、訂閱、傳送等）期間所使用資料的檔案，以及可能的子檔案。

它們還必須映射到與工作流執行的操作（收件人導入、檔案訪問、融合、SQL指令碼執行等）一致的命名權限。

如需有關管理運算子和權限的詳細資訊，請參閱本 [節](../../platform/using/access-management.md)。

## 運算元群組 {#operator-groups}

下列運算元群組與工作流程相關聯：

* 此群 **[!UICONTROL Workflow execution]** 組可讓您控制定位工作流程的執行和核准：名為right的工作流程會映射至此群組的運算子。 除了資料檔案的存取權限外，工作流程上的所有動作都需要此選項。 依預設，群組 **[!UICONTROL Workflow execution]** 可以唯讀存取標準定位工作流程檔案和工作流程範本。 此群組中的運算子也擁有待核准檔案的讀取和寫入存取權。
* 群組可 **[!UICONTROL Workflow supervisors]** 讓營運商管理工作流程核准。
* 存取促 **[!UICONTROL Operation Managers]** 銷活動工作流程的群組。

## 命名權限 {#named-rights}

只有指名為right的WORKFLOW才是工作流的特定內容：它可讓您建立、啟動和停止工作流程。 必須具備工作流檔案的讀取權限，才能適用已命名的權限。 若要定位工作流程，必須在檔案上 **[!UICONTROL Profiles and Targets]** 直接閱讀。

## 工作流程執行帳戶 {#workflow-execution-account}

您可以設定要在工作流程範本層級使用的執行帳戶。 執行帳戶可讓您直接將授權對應至工作流程，而不考慮啟動執行的Adobe Campaign運算子。 依預設，每個工作流程都會以啟動該工作流程的運算子的權限執行。

若要將執行帳戶映射至工作流程，請移至工作流程範本清單，然後在連結至工作流程的範本上按一下滑鼠右鍵。 選 **[!UICONTROL Action > Change execution account...]** 擇，然後選擇要使用的帳戶。
