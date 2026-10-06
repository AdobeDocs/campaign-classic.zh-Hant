---
product: campaign
title: 使用案例：針對線上調查的回答顯示報吿
description: 使用案例：針對線上調查的回答顯示報吿
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting, Monitoring, Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 71b1c383-45b9-57e0-b8cd-ea2e98a01a26
    internal-label: Surveys
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 6%
---
# 使用案例：針對線上調查的回答顯示報告{#use-case-displaying-report-on-answers-to-an-online-survey}



Adobe Campaign調查的回答可使用專用報告進行收集和分析。

在以下範例中，我們想要收集線上意見調查的結果，並將這些結果顯示在樞紐分析表中

應用以下步驟：

1. 建立工作流程以復原意見調查的結果，並將結果儲存在清單中。
1. 使用清單中的資料建立立方結構。
1. 使用樞紐分析表建立報表，並檢視答案的劃分。

開始使用此使用案例之前，您需要具有調查存取權以及可分析的一組答案。

>[!NOTE]
>
>只有您已取得&#x200B;**問卷管理員**&#x200B;選項，才能實作此使用案例。 請檢查您的授權合約。

## 步驟1 — 建立資料收集和儲存工作流程 {#step-1---creating-the-data-collection-and-storage-workflow}

若要收集調查的答案，請套用下列步驟：

1. 建立工作流程並放置&#x200B;**[!UICONTROL Answers to a survey]**&#x200B;活動。 有關使用此活動的詳細資訊，請參閱[本區段](../../surveys/using/publish-track-and-use-collected-data.md#using-the-collected-data)。
1. 編輯活動並選取您要分析其答案的調查。
1. 啟用&#x200B;**[!UICONTROL Select all the answer data]**&#x200B;選項以收集所有資訊。

   ![](../../surveys/using/assets/reporting_usecase_1_01.png)

1. 選取要擷取的欄（在此案例中為： select：所有已封存欄位）。 這些欄位包含答案。

   ![](../../surveys/using/assets/reporting_usecase_1_02.png)

1. 設定回應收集方塊後，定位&#x200B;**[!UICONTROL List update]**&#x200B;型別活動以儲存資料。

   ![](../../surveys/using/assets/reporting_usecase_1_04.png)

   在此活動中，指定要更新的清單，並取消勾選&#x200B;**[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]**&#x200B;選項：將答案新增到現有表格。 此選項可讓您參照立方體中的清單。 每次更新都不會重新產生連結至清單的結構描述，以確保使用此清單的Cube完整性。

   ![](../../surveys/using/assets/reporting_usecase_1_03.png)

1. 啟動工作流程以確認其設定。

   ![](../../surveys/using/assets/reporting_usecase_1_05.png)

   指定的清單會建立，並包含調查答案的結構描述。

1. 新增排程器，以自動進行每日答案收集和清單更新。

   **[!UICONTROL List update]**&#x200B;和&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動在中詳細說明。

## 步驟2 — 建立立方結構、其測量值及其指示器 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然後您可以建立立方結構並設定其計量：它們將用於建立將顯示在報告中的指標。 有關建立和設定多維資料集的詳細資訊，請參閱[關於多維資料集](../../reporting/using/ac-cubes.md)。

在此範例中，Cube是以先前建立的工作流程饋送之清單中的資料為基礎。

![](../../surveys/using/assets/reporting_usecase_2_01.png)

定義要在報表中顯示的尺寸與測量。 在此處，我們要顯示合約日期與回應者的國家/地區。

![](../../surveys/using/assets/reporting_usecase_2_02.png)

**[!UICONTROL Preview]**&#x200B;索引標籤可讓您控制報表的呈現。

## 步驟3 — 建立報表並設定表格內的資料配置 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然後，您可以根據此立方結構建立報表，並處理資料與資訊。

![](../../surveys/using/assets/reporting_usecase_3_01.png)

根據您的需求調整資訊以顯示。

![](../../surveys/using/assets/reporting_usecase_3_02.png)
