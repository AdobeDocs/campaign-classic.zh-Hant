---
product: campaign
title: '"使用案例：顯示線上意見調查之答案的報表"'
description: '"使用案例：顯示線上意見調查之答案的報表"'
feature: Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 6%

---

# 用例：顯示有關線上調查答案的報告{#use-case-displaying-report-on-answers-to-an-online-survey}

![](../../assets/v7-only.svg)

Adobe Campaign調查的答案可以用專門報告收集和分析。

在下例中，我們要收集聯機調查的答案並在透視表中顯示

應用以下步驟：

1. 建立工作流以恢復對調查的回答並將其儲存在清單中。
1. 使用清單中的資料建立多維資料集。
1. 使用透視表建立報告並查看答案的細分。

在開始使用此使用案例之前，您需要訪問調查和一組可以分析的答案。

>[!NOTE]
>
>只有在您已獲得 **調查經理** 的雙曲餘切值。 請檢查您的授權合約。

## 步驟1 — 建立資料收集和儲存工作流 {#step-1---creating-the-data-collection-and-storage-workflow}

要收集調查的答案，請應用以下步驟：

1. 建立工作流並放置 **[!UICONTROL Answers to a survey]** 的子菜單。 有關使用本練習的詳細資訊，請參閱 [此部分](../../surveys/using/publish--track-and-use-collected-data.md#using-the-collected-data)。
1. 編輯活動，並選擇要分析其答案的調查。
1. 啟用 **[!UICONTROL Select all the answer data]** 頁籤

   ![](assets/reporting_usecase_1_01.png)

1. 選擇要提取的列(在本例中：選擇：所有存檔的欄位。 這些欄位包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 配置應答收集框後，將 **[!UICONTROL List update]** 鍵入activity以保存資料。

   ![](assets/reporting_usecase_1_04.png)

   在本練習中，指定要更新的清單並取消檢查 **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** 選項：答案將添加到現有表中。 此選項將允許您引用多維資料集中的清單。 將不會為每個更新重新生成連結到清單的架構，這保證了使用此清單的多維資料集的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 啟動工作流以確認其配置。

   ![](assets/reporting_usecase_1_05.png)

   將建立指定清單，並包括調查答案的架構。

1. 添加計畫程式以自動收集每日答案和清單更新。

   的 **[!UICONTROL List update]** 和 **[!UICONTROL Scheduler]** 活動詳見。

## 第2步 — 建立立方、其度量及其指示符 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然後，可以建立立方並配置其度量：這些指標將用於建立將在報告中顯示的指標。 有關建立和配置多維資料集的詳細資訊，請參閱 [關於立方](../../reporting/using/about-cubes.md)。

在此示例中，多維資料集基於先前建立的工作流所饋送的清單中的資料。

![](assets/reporting_usecase_2_01.png)

定義要在報告中顯示的維和度量。 在此，我們要顯示合同日期和被申請人的國家/地區。

![](assets/reporting_usecase_2_02.png)

的 **[!UICONTROL Preview]** 頁籤，用於控制報表的呈現。

## 步驟3 — 建立報表並配置表中的資料佈局 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然後，您可以基於此多維資料集建立報告並處理資料和資訊。

![](assets/reporting_usecase_3_01.png)

根據您的需求調整資訊以顯示。

![](assets/reporting_usecase_3_02.png)
