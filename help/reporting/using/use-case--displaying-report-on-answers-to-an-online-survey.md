---
title: 「使用案例：顯示線上調查回答的報表」
seo-title: 「使用案例：顯示線上調查回答的報表」
description: 「使用案例：顯示線上調查回答的報表」
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 使用案例：顯示線上調查答案的報告{#use-case-displaying-report-on-answers-to-an-online-survey}

您可使用專屬報表來收集和分析Adobe Campaign調查的答案。

在下列範例中，我們想要收集線上調查的答案，並將它們顯示在樞紐表格中

應用以下步驟：

1. 建立工作流程，以復原調查的答案並將之儲存在清單中。
1. 使用清單中的資料建立立方。
1. 使用樞紐表建立報表並檢視答案劃分。

在開始使用此使用案例之前，您必須擁有調查的存取權以及可分析的答案集。

>[!NOTE]
>
>只有在您取得「調查管理員」選項時，才能實 **施此使用案例** 。 請檢查您的授權合約。

## 步驟1 —— 建立資料收集和儲存工作流程 {#step-1---creating-the-data-collection-and-storage-workflow}

若要收集調查的答案，請套用下列步驟：

1. 建立工作流程並放置活 **[!UICONTROL Answers to a survey]** 動。 For more on using this activity, refer to [this section](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. 編輯活動並選取您要分析其答案的調查。
1. 啟用選 **[!UICONTROL Select all the answer data]** 項以收集所有資訊。

   ![](assets/reporting_usecase_1_01.png)

1. 選擇要提取的列(在本例中：選擇：所有已封存的欄位。 這些欄位包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 在設定答案收集方塊後，請定位 **[!UICONTROL List update]** 類型活動以儲存資料。

   ![](assets/reporting_usecase_1_04.png)

   在本練習中，指定要更新的清單並取消選中 **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** 選項：答案會新增至現有表格。 此選項將允許您引用立方中的清單。 連結到清單的方案不會為每次更新重新生成，這保證了使用此清單的立方的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 啟動工作流以確認其配置。

   ![](assets/reporting_usecase_1_05.png)

   會建立指定的清單，並包含調查答案的結構。

1. 新增排程器，以自動化每日的答案收集和清單更新。

   有關 **[!UICONTROL List update]** 和 **[!UICONTROL Scheduler]** 活動的詳細資訊，請參閱。

## 步驟2 —— 建立立方、其度量及其指示符 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然後可以建立立方並配置其度量：它們將用來建立將顯示在報表中的指標。 有關建立和配置立方的詳細資訊，請參閱關於 [立方](../../reporting/using/about-cubes.md)。

在此示例中，立方基於以前建立的工作流所提供的清單中的資料。

![](assets/reporting_usecase_2_01.png)

定義要顯示在報表中的維和度量。 在此，我們要顯示被申請人的合約日期和國家。

![](assets/reporting_usecase_2_02.png)

此標 **[!UICONTROL Preview]** 簽可讓您控制報表的轉譯。

## 步驟3 —— 建立報表並設定表格中的資料配置 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然後，您可以根據此立方建立報告並處理資料和資訊。

![](assets/reporting_usecase_3_01.png)

根據您的需求調整資訊以顯示。

![](assets/reporting_usecase_3_02.png)

