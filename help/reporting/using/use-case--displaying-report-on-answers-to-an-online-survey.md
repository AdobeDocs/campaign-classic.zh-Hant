---
product: campaign
title: '"使用案例：顯示線上意見調查之答案的報表"'
description: '"使用案例：顯示線上意見調查之答案的報表"'
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 6%

---

# 使用案例：顯示線上意見調查的答案報告{#use-case-displaying-report-on-answers-to-an-online-survey}

您可使用專屬報告來收集和分析Adobe Campaign調查的答案。

在下列範例中，我們想要收集線上調查的答案，並將其顯示在樞紐表格中

應用以下步驟：

1. 建立工作流程，以復原調查的答案並將其儲存在清單中。
1. 使用清單中的資料建立多維資料集。
1. 使用樞紐表格建立報表並檢視答案劃分。

開始使用此使用案例之前，您必須擁有調查的存取權，以及您可以分析的一組答案。

>[!NOTE]
>
>只有在您取得&#x200B;**調查管理員**&#x200B;選項時，才可實作此使用案例。 請檢查您的授權合約。

## 步驟1 — 建立資料收集和儲存工作流程 {#step-1---creating-the-data-collection-and-storage-workflow}

若要收集調查的答案，請套用下列步驟：

1. 建立工作流程並放置&#x200B;**[!UICONTROL Answers to a survey]**&#x200B;活動。 有關使用此活動的詳細資訊，請參閱[此部分](../../surveys/using/publish--track-and-use-collected-data.md#using-the-collected-data)。
1. 編輯活動，並選取您要分析其答案的調查。
1. 啟用&#x200B;**[!UICONTROL Select all the answer data]**&#x200B;選項以收集所有資訊。

   ![](assets/reporting_usecase_1_01.png)

1. 選取要擷取的欄(在此例中為：選擇：所有已封存欄位。 這些欄位包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 設定答案收集方塊後，請放置&#x200B;**[!UICONTROL List update]**&#x200B;類型活動以儲存資料。

   ![](assets/reporting_usecase_1_04.png)

   在此活動中，指定要更新的清單並取消勾選&#x200B;**[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]**&#x200B;選項：答案會新增至現有表格。 此選項可讓您參考多維資料集中的清單。 連結到清單的架構將不會為每次更新重新生成，這保證了使用此清單的多維資料集的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 啟動工作流程以確認其設定。

   ![](assets/reporting_usecase_1_05.png)

   系統會建立指定清單，並包含調查之答案的結構。

1. 新增排程器，以自動每日收集答案和清單更新。

   **[!UICONTROL List update]**&#x200B;和&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動在中詳細說明。

## 第2步 — 建立多維資料集、其度量及其指標 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然後，可以建立多維資料集並配置其測量：這些指標將用於建立將顯示在報告中的指標。 有關建立和配置多維資料集的詳細資訊，請參閱[關於多維資料集](../../reporting/using/about-cubes.md)。

在此範例中，多維資料集以先前建立之工作流程饋送清單中的資料為基礎。

![](assets/reporting_usecase_2_01.png)

定義要在報表中顯示的維和測量。 在此，我們要顯示合約日期和回應者的國家。

![](assets/reporting_usecase_2_02.png)

**[!UICONTROL Preview]**&#x200B;標籤可讓您控制報表的呈現。

## 步驟3 — 建立報表並在表格中設定資料配置 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然後，您可以根據此多維資料集建立報告並處理資料和資訊。

![](assets/reporting_usecase_3_01.png)

根據您的需求調整資訊以顯示。

![](assets/reporting_usecase_3_02.png)
