---
product: campaign
title: 管理工作流權限
description: 瞭解如何管理工作流權限
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 管理工作流權限{#managing-rights}

![](../../assets/v7-only.svg)

如果它們不是管理員，則Adobe Campaign操作員需要建立、執行或修改工作流的訪問權限。

通常，對工作流執行操作的操作員需要訪問包含在各種活動（收件人、收件人清單、訂閱、遞送等）期間使用的資料的檔案，以及可能的子檔案。

它們還必須映射到與工作流執行的操作（收件人導入、檔案訪問、融合、SQL指令碼執行等）相一致的命名權限。

有關管理操作員和權限的詳細資訊，請參閱 [節](../../platform/using/access-management.md)。

## 運算子組 {#operator-groups-wf}

以下運算子組與工作流關聯：

* 的 **[!UICONTROL Workflow execution]** 組用於控制目標工作流的執行和批准：名為right的工作流已映射到此組的運算子。 除了對資料檔案的訪問權限之外，工作流上的所有操作都需要此選項。 預設情況下， **[!UICONTROL Workflow execution]** 組具有對標準目標工作流檔案和工作流模板的只讀訪問權限。 此組中的操作員也具有對待處理批准檔案的讀寫權限。
* 的 **[!UICONTROL Workflow supervisors]** 組允許操作員管理工作流批准。
* 的 **[!UICONTROL Operation Managers]** 組以訪問市場活動工作流。

## 命名權限 {#named-rights}

只有名為right的WORKFLOW特定於工作流：它允許您建立、啟動和停止工作流。 要適用命名權限，需要對工作流檔案進行讀取權限。 對於目標工作流， **[!UICONTROL Profiles and Targets]** 檔案。

## 工作流執行帳戶 {#workflow-execution-account}

您可以配置要在工作流模板級別使用的執行帳戶。 執行帳戶允許您直接將授權映射到工作流，而不管開始執行的Adobe Campaign操作員如何。 預設情況下，每個工作流都使用啟動該工作流的操作員的權限執行。

要將執行帳戶映射到工作流，請轉到工作流模板清單並按一下右鍵連結到工作流的模板。 選擇 **[!UICONTROL Action > Change execution account...]** 然後選擇要使用的帳戶。
