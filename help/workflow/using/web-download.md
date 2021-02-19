---
solution: Campaign Classic
product: campaign
title: 網頁下載
description: 進一步瞭解網頁下載工作流程活動
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---


# 網頁下載{#web-download}

**Web download**&#x200B;活動會啟動在明確URL、外部帳戶或Adobe Campaign例項上下載檔案。 使用HTTP通訊協定。 這可以是GET或POST下載。

## 屬性 {#properties}

1. **選擇Web檔案**

   若要指定要下載的檔案，您可以輸入檔案URL、使用儲存檔案的外部HTTP帳戶，或透過Adobe Campaign例項載入檔案。 可用參數的詳細說明如下：

   * 若要直接輸入要下載的檔案的URL，請選取&#x200B;**[!UICONTROL Explicit URL]**&#x200B;選項，然後在適當欄位中指定URL。 此URL可以使用變數資料來建構。

      ![](assets/download_web_edit.png)

   * 若要使用&#x200B;**[!UICONTROL External account]**，請從下拉式清單中選取帳戶，並指定要下載的檔案。

      外部帳戶是從Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點設定。 帳戶參數可透過&#x200B;**[!UICONTROL Edit link]**&#x200B;圖示編輯。

      ![](assets/download_web_edit_external.png)

   * 若要從Adobe Campaign例項下載檔案，請選取&#x200B;**[!UICONTROL Adobe Campaign Instance]**&#x200B;選項。

      ![](assets/download_web_edit_instance.png)

1. **檔案歷史化**

   **[!UICONTROL File historization settings...]**&#x200B;連結可讓您指定檔案儲存目錄和此目錄的清除頻率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下選項：

   * **[!UICONTROL Use a default storage directory]**:檔案在處理前一律會先移動。如果勾選此選項，檔案會移入預設儲存目錄（Adobe Campaign安裝資料夾的&#x200B;**vars**&#x200B;目錄）。 要指定儲存目錄，請取消選中該框，並在&#x200B;**[!UICONTROL Storage directory]**&#x200B;欄位中輸入其路徑
   * **[!UICONTROL Number of files]**:輸入儲存目錄中要保存的最大檔案數。
   * **[!UICONTROL Maximum size (in Mb)]**:輸入儲存目錄的最大容量（以兆位元組為單位）。

   在遵守定義的清除規則之前，每個檔案將保留24小時。 清除會在活動開始前進行，因此不會考慮進行中的工作流檔案。

   檔案會視其年齡（最舊到最新）而刪除。 在驗證兩個清除規則之前，將清除最舊的檔案。 因此，如果定義了100個檔案限制，這意味著儲存目錄將始終包含工作流開始前的100個最新檔案，以及正在進行中的工作流中正在處理的檔案。

   如果您不想再為&#x200B;**[!UICONTROL Number of files]**&#x200B;和&#x200B;**[!UICONTROL Maximum size (in Mb)]**&#x200B;選項設定限制，請輸入0作為值。

1. **高級參數**

   **[!UICONTROL Advanced parameters...]**&#x200B;連結可讓您指定下方顯示的其他選項：

   ![](assets/download_web_edit_advanced.png)

   **[!UICONTROL Process errors]**&#x200B;選項在[處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)中有詳細說明。

## 輸出參數{#output-parameters}

* 檔案名：已下載檔案的完整名稱。
