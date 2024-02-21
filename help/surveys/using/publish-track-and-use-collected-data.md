---
product: campaign
title: 發佈、追蹤及使用收集的資料
description: 瞭解如何發佈、追蹤及使用調查中所收集的資料
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 2%

---

# 發佈、追蹤及使用收集的資料{#publish-track-and-use-collected-data}



建立、設定和發佈表單後，您就可以與對象共用連結，並追蹤回應。

>[!NOTE]
>
>Adobe Campaign中調查的生命週期及其發佈和傳送模式類似於Web表單的生命週期：詳見 [本節](../../web/using/about-web-forms.md).

## 調查儀表板 {#survey-dashboard}

每個調查都有自己的控制面板，可讓您檢視其狀態、說明、公用URL和可用性排程。 它也可讓您檢視可用的報表。 [了解更多](#reports-on-surveys)。

調查問卷的公用URL會顯示在控制面板上：

![](assets/survey_public_url.png)

## 回應追蹤 {#response-tracking}

您可以在記錄檔與報表中追蹤意見調查回應。

### 調查記錄 {#survey-logs}

對於已傳送的每個調查，您都可以在以下位置追蹤回應： **[!UICONTROL Logs]** 標籤。 此索引標籤顯示已完成調查的使用者清單及其來源：

![](assets/s_ncs_admin_survey_logs.png)

連按兩下某一行，以顯示回應填入的調查表單。 您可以瀏覽調查問卷的全文，並完整存取答案。 這些檔案可匯出到外部檔案中。 有關詳細資訊，請參閱 [匯出答案](#exporting-answers).

透過新增下列字元，在調查URL中指出來源：

```
?origin=xxx
```

在編輯調查時，其URL包含引數 **[!UICONTROL __uuid]**，表示其處於測試階段且尚未上線。 當您透過此URL存取意見調查時，建立的記錄不會納入追蹤（報表）的考量。 原點會強製為值 **[!UICONTROL Adobe Campaign]**.

如需URL引數的詳細資訊，請參閱 [此頁面](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### 調查報表 {#reports-on-surveys}

控制面板標籤可讓您存取調查報表。 按一下報表名稱即可檢視。

![](assets/s_ncs_admin_survey_report_doc.png)

問卷的結構可見於 **[!UICONTROL Documentation]** 報告。

關於網路調查的其他兩份報告可在以下網址取得： **[!UICONTROL Reports]** 調查的索引標籤： **[!UICONTROL General]** 和 **[!UICONTROL Breakdown of responses]**.

* 一般

  此報表包含調查的一般資訊：回應的數量如何隨著時間而改變，以及依來源和語言的分佈。

  一般報表的範例：

  ![](assets/s_ncs_admin_survey_report_0.png)

* 回覆的劃分

  此報表顯示每個問題的回覆細目。 此劃分僅適用於所儲存欄位的答案 **[!UICONTROL Question]** 輸入容器。 它僅適用於選取控制項（例如文字欄位沒有劃分）。

  ![](assets/s_ncs_admin_survey_report_2.png)

## 匯出答案 {#exporting-answers}

意見調查的結果可以匯出到外部檔案中，以便稍後處理。 有兩種方法可以達成此目的：

1. 匯出報表資料

   若要匯出報表資料，請按一下 **[!UICONTROL Export]** 按鈕並選擇匯出格式。

   如需匯出報表資料的詳細資訊，請參閱 [本節](../../reporting/using/about-reports-creation-in-campaign.md).

1. 匯出答案

   若要匯出答案，請按一下 **[!UICONTROL Responses]** 問卷的索引標籤，然後按一下滑鼠右鍵。 選取 **[!UICONTROL Export...]**。

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然後輸入要匯出的資訊和儲存檔案。

   您可以在匯出精靈中設定輸出檔案的內容和格式。

   這可讓您：

   * 將欄新增至輸出檔案，並復原收件者的資訊（儲存在資料庫中），
   * 格式化匯出的資料，
   * 選取檔案中資訊的編碼格式。

   如果您要匯出的問卷包含數個 **[!UICONTROL Multi-line text]** 或 **[!UICONTROL HTML text]** 欄位，它必須匯出到 **[!UICONTROL XML]** 格式。 若要這麼做，請在 **[!UICONTROL Output format]** 欄位，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   按一下 **[!UICONTROL Start]** 以執行匯出。

   >[!NOTE]
   >
   >資料匯出及其設定的階段詳見 [本節](../../platform/using/about-generic-imports-exports.md).

## 使用收集的資料 {#using-the-collected-data}

透過線上調查收集的資訊可在目標定位工作流程的框架內復原。 若要這麼做，請使用 **[!UICONTROL Survey responses]** 方塊。

在下列範例中，我們想要針對線上上調查中至少有兩個孩子且分數最高的五名收件者，特別提供網站優惠方案。 本問卷的答案為：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在目標定位工作流程中， **[!UICONTROL Survey responses]** 將設定如下：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

首先，請選取相關的調查，然後在視窗的中央區段中選取要擷取的資料。 在此情況下，我們至少需要擷取分數欄，因為此分數欄將用於分割方塊，以復原5個最高分數。

按一下「 」，指示答案的篩選條件 **[!UICONTROL Edit query...]** 連結。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

開始目標定位工作流程。 查詢找回8個收件者。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

在集合方塊的輸出轉變上按一下滑鼠右鍵以檢視。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然後，在工作流程中放置分割方塊，以復原分數最高的5個收件者。

編輯分割方塊以進行設定：

* 首先，選取 **[!UICONTROL General]** 標籤，然後設定子集：

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 前往 **[!UICONTROL Sub-sets]** 標籤並選取 **[!UICONTROL Limit the selected records]** 選項，然後按一下 **[!UICONTROL Edit...]** 連結。

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 選取 **[!UICONTROL Keep only the first records after sorting]** 選項並選取排序欄。 核取 **[!UICONTROL Descending sort]** 選項。

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 按一下 **[!UICONTROL Next]** 按鈕並將記錄數限製為5。

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 按一下 **[!UICONTROL Finish]** 然後重新啟動工作流程以核准鎖定目標。

## 標準化資料 {#standardizing-data}

您可以在Adobe Campaign中為使用別名收集的資料設定標準化流程。 這可讓您標準化資料庫中儲存的資料：若要這麼做，請在包含相關資訊的逐項清單中定義別名。 [了解更多](../../platform/using/managing-enumerations.md#about-enumerations)
