---
solution: Campaign Classic
product: campaign
title: '"使用案例：顯示線上意見調查之答案的報表"'
description: '"使用案例：顯示線上意見調查之答案的報表"'
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 6%

---


# 使用案例：顯示線上調查的回覆報告{#use-case-displaying-report-on-answers-to-an-online-survey}

可使用專屬報告收集和分析Adobe Campaign調查的答案。

在下列範例中，我們想要收集線上調查的答案，並在樞紐表格中顯示答案

應用以下步驟：

1. 建立工作流程，以復原調查的答案並將之儲存在清單中。
1. 使用清單中的資料建立立方。
1. 使用樞紐表建立報表並檢視答案劃分。

在開始使用此使用案例之前，您必須擁有調查的存取權以及可分析的答案集。

>[!NOTE]
>
>只有在您取得&#x200B;**調查管理員**&#x200B;選項時，才能實作此使用案例。 請檢查您的授權合約。

## 步驟1 —— 建立資料收集和儲存工作流{#step-1---creating-the-data-collection-and-storage-workflow}

若要收集調查的答案，請套用下列步驟：

1. 建立工作流程並放置&#x200B;**[!UICONTROL Answers to a survey]**&#x200B;活動。 有關使用本練習的詳細資訊，請參閱[本節](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data)。
1. 編輯活動並選取您要分析其答案的調查。
1. 啟用&#x200B;**[!UICONTROL Select all the answer data]**&#x200B;選項以收集所有資訊。

   ![](assets/reporting_usecase_1_01.png)

1. 選擇要提取的列(在本例中：選擇：所有已封存的欄位。 這些欄位包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 在設定答案收集方塊後，請放置&#x200B;**[!UICONTROL List update]**&#x200B;類型活動以儲存資料。

   ![](assets/reporting_usecase_1_04.png)

   在本練習中，指定要更新的清單並取消選中&#x200B;**[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]**&#x200B;選項：答案會新增至現有表格。 此選項將允許您引用立方中的清單。 連結到清單的方案不會為每次更新重新生成，這保證了使用此清單的立方的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 啟動工作流以確認其配置。

   ![](assets/reporting_usecase_1_05.png)

   會建立指定的清單，並包含調查答案的結構。

1. 新增排程器，以自動化每日的答案收集和清單更新。

   **[!UICONTROL List update]**&#x200B;和&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動在中詳細介紹。

## 步驟2 —— 建立立方、其度量及其指示器{#step-2---creating-the-cube--its-measures-and-its-indicators}

然後可以建立立方並配置其度量：它們將用來建立將顯示在報表中的指標。 有關建立和配置立方的詳細資訊，請參閱[關於立方](../../reporting/using/about-cubes.md)。

在此示例中，立方基於以前建立的工作流所提供的清單中的資料。

![](assets/reporting_usecase_2_01.png)

定義要顯示在報表中的維和度量。 在此，我們要顯示被申請人的合約日期和國家。

![](assets/reporting_usecase_2_02.png)

**[!UICONTROL Preview]**&#x200B;標籤可讓您控制報表的轉譯。

## 步驟3 —— 建立報告並在表{#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}中配置資料佈局

然後，您可以根據此立方建立報告並處理資料和資訊。

![](assets/reporting_usecase_3_01.png)

根據您的需求調整資訊以顯示。

![](assets/reporting_usecase_3_02.png)

