---
title: 網路下載
seo-title: 網路下載
description: 網路下載
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 網路下載{#web-download}

「網 **頁下載** 」活動會在明確的URL、外部帳戶或Adobe Campaign例項上啟動檔案下載。 使用HTTP通訊協定。 這可以是GET或POST下載。

## 屬性 {#properties}

1. **選擇Web檔案**

   若要指定要下載的檔案，您可以輸入檔案URL、使用儲存檔案的外部HTTP帳戶，或透過Adobe Campaign例項載入檔案。 可用參數的詳細說明如下：

   * 若要直接輸入要下載的檔案的URL，請選取選 **[!UICONTROL Explicit URL]** 項並在適當欄位中指定URL。 此URL可以使用變數資料來建構。

      ![](assets/download_web_edit.png)

   * 若要使 **[!UICONTROL External account]**&#x200B;用，請從下拉式清單中選取帳戶，並指定要下載的檔案。

      外部帳戶是從Adobe Campaign樹 **[!UICONTROL Administration > Platform > External accounts]** 狀結構的節點設定。 帳戶參數可透過圖示 **[!UICONTROL Edit link]** 編輯。

      ![](assets/download_web_edit_external.png)

   * 若要從Adobe Campaign例項下載檔案，請選取選 **[!UICONTROL Adobe Campaign Instance]** 項。

      ![](assets/download_web_edit_instance.png)

1. **檔案歷史化**

   該鏈 **[!UICONTROL File historization settings...]** 接允許您指定檔案儲存目錄和此目錄的清除頻率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下選項：

   * **[!UICONTROL Use a default storage directory]**:檔案在處理前一律會先移動。 如果勾選此選項，檔案會移入預設儲存目錄(Adobe Campaign安 **裝檔案夾的** vars目錄)。 要指定儲存目錄，請取消選中該框，並在欄位中輸入其路 **[!UICONTROL Storage directory]** 徑
   * **[!UICONTROL Number of files]**:輸入儲存目錄中要保存的最大檔案數。
   * **[!UICONTROL Maximum size (in Mb)]**:輸入儲存目錄的最大容量（以兆位元組為單位）。
   在遵守定義的清除規則之前，每個檔案將保留24小時。 清除會在活動開始前進行，因此不會考慮進行中的工作流檔案。

   檔案會視其年齡（最舊到最新）而刪除。 在驗證兩個清除規則之前，將清除最舊的檔案。 因此，如果定義了100個檔案限制，這意味著儲存目錄將始終包含工作流開始之前的100個最新檔案，以及正在進行中的工作流中正在處理的檔案。

   如果您不想再設定和選項的限 **[!UICONTROL Number of files]** 制 **[!UICONTROL Maximum size (in Mb)]** ，請輸入0作為值。

1. **高級參數**

   連結 **[!UICONTROL Advanced parameters...]** 可讓您指定下列顯示的其他選項：

   ![](assets/download_web_edit_advanced.png)

   「處 **[!UICONTROL Process errors]** 理錯誤」中詳細 [介紹了該選項](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 輸出參數 {#output-parameters}

* 檔案名

   已下載檔案的完整名稱。

