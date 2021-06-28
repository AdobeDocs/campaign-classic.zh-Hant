---
product: campaign
title: 發佈、追蹤及使用收集的資料
description: 了解如何發佈、追蹤及使用調查中收集的資料
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---

# 發佈、追蹤及使用收集的資料{#publish-track-and-use-collected-data}

建立、設定和發佈表單後，您就可以與對象共用連結並追蹤回應。

>[!NOTE]
>
>Adobe Campaign中調查的生命週期及其發佈和傳送模式與網路表單的類似：在[本節](../../web/using/about-web-forms.md)中詳細介紹了這些內容。

## 調查控制面板 {#survey-dashboard}

每個調查都有其專屬的控制面板，可讓您檢視其狀態、說明、公用URL和可用性排程。 它也可讓您檢視可用的報表。 [深入瞭解](#reports-on-surveys)。

調查的公用URL會顯示在控制面板上：

![](assets/survey_public_url.png)

## 回應追蹤 {#response-tracking}

您可以在記錄檔和報表中追蹤對調查的回應。

### 調查記錄 {#survey-logs}

對於傳送的每個調查，您可以在&#x200B;**[!UICONTROL Logs]**&#x200B;標籤中追蹤回應。 此索引標籤會顯示已完成調查的使用者清單及其來源：

![](assets/s_ncs_admin_survey_logs.png)

連按兩下某行，以顯示回應者填入的調查表單。 您可以完整瀏覽調查，並完整存取答案。 這些檔案可匯出為外部檔案。 有關詳細資訊，請參閱[導出答案](#exporting-answers)。

來源會在調查URL中新增下列字元以指出：

```
?origin=xxx
```

在編輯調查時，其URL包含參數&#x200B;**[!UICONTROL __uuid]**，指出調查處於測試階段且尚未上線。 當您透過此URL存取調查時，在追蹤（報表）中不會考慮已建立的記錄。 原點被強制為&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;值。

如需URL參數的詳細資訊，請參閱[此頁面](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

### 調查報表 {#reports-on-surveys}

控制面板標籤可讓您存取調查報表。 按一下報表名稱即可檢視。

![](assets/s_ncs_admin_survey_report_doc.png)

調查的結構會顯示在&#x200B;**[!UICONTROL Documentation]**&#x200B;報表中。

在調查的&#x200B;**[!UICONTROL Reports]**&#x200B;索引標籤中提供關於Web調查的其他兩份報告：**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Breakdown of responses]**。

* 一般

   此報告包含調查的一般資訊：回應數量隨時間的變化，以及依來源和語言的分佈。

   一般報表範例：

   ![](assets/s_ncs_admin_survey_report_0.png)

* 回應的劃分

   此報表顯示每個問題的回應劃分。 此劃分僅適用於為&#x200B;**[!UICONTROL Question]**&#x200B;類型容器中儲存的欄位提供的答案。 它僅對選取控制項有效（例如，文字欄位上沒有劃分）。

   ![](assets/s_ncs_admin_survey_report_2.png)

## 匯出答案 {#exporting-answers}

調查的答案可匯出為外部檔案，以供稍後處理。 執行此作業有兩種方式：

1. 匯出報表資料

   要導出報告資料，請按一下&#x200B;**[!UICONTROL Export]**&#x200B;按鈕並選擇導出格式。

   如需匯出報表資料的詳細資訊，請參閱[此區段](../../reporting/using/about-reports-creation-in-campaign.md)。

1. 匯出答案

   若要匯出答案，請按一下調查的&#x200B;**[!UICONTROL Responses]**&#x200B;標籤，然後按一下滑鼠右鍵。 選取 **[!UICONTROL Export...]**。

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然後輸入要導出的資訊和儲存檔案。

   您可以在匯出精靈中設定輸出檔案的內容和格式。

   這可讓您：

   * 向輸出檔案添加列並恢復收件者的資訊（儲存在資料庫中）,
   * 格式化導出的資料，
   * 為檔案中的資訊選擇編碼格式。

   如果要匯出的調查包含數個&#x200B;**[!UICONTROL Multi-line text]**&#x200B;或&#x200B;**[!UICONTROL HTML text]**&#x200B;欄位，則必須以&#x200B;**[!UICONTROL XML]**&#x200B;格式匯出。 要執行此操作，請在&#x200B;**[!UICONTROL Output format]**&#x200B;欄位的下拉式清單中選取此格式，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   按一下&#x200B;**[!UICONTROL Start]**&#x200B;以執行匯出。

   >[!NOTE]
   >
   >在[本節](../../platform/using/about-generic-imports-exports.md)中詳細說明資料導出及其配置的階段。

## 使用收集的資料 {#using-the-collected-data}

透過線上調查收集的資訊可在目標工作流程的框架內復原。 要執行此操作，請使用&#x200B;**[!UICONTROL Survey responses]**&#x200B;框。

在以下範例中，我們想特別為線上上調查中分數最高、至少有兩個子女的五位收件者，提供網路優惠。 本調查的答案為：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在目標工作流程中，**[!UICONTROL Survey responses]**&#x200B;的設定如下：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

首先選取相關調查，然後在視窗的中央區段中擷取資料。 在此情況下，我們需要至少擷取分數欄，因為此欄將用於分割方塊，以復原五個最高分數。

按一下&#x200B;**[!UICONTROL Edit query...]**&#x200B;連結，指出答案的篩選條件。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

啟動目標工作流程。 查詢會復原8個收件者。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

以滑鼠右鍵按一下集合方塊的輸出轉變以檢視。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然後在工作流程中放置分割方塊，以復原分數最高的5個收件者。

編輯分割方塊以進行設定：

* 首先，在&#x200B;**[!UICONTROL General]**&#x200B;標籤中選取適當的架構，然後設定子集：

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 前往&#x200B;**[!UICONTROL Sub-sets]**&#x200B;標籤，選取&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;連結。

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 選擇&#x200B;**[!UICONTROL Keep only the first records after sorting]**&#x200B;選項並選擇排序列。 核取 **[!UICONTROL Descending sort]** 選項。

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕，並將記錄數限制為5。

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 按一下&#x200B;**[!UICONTROL Finish]**，然後重新啟動工作流程以核准目標定位。

## 標準化資料 {#standardizing-data}

可以在Adobe Campaign中為使用別名收集的資料設定標準化程式。 這可讓您標準化儲存在資料庫中的資料：要執行此操作，請在包含相關資訊的分項清單中定義別名。 [深入瞭解](../../platform/using/managing-enumerations.md#about-enumerations)
