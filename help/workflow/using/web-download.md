---
product: campaign
title: 網頁下載
description: 進一步瞭解網頁下載工作流程活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 2%

---

# 網頁下載{#web-download}



**網頁下載**&#x200B;活動會啟動在明確URL、外部帳戶或Adobe Campaign執行個體上的檔案下載。 會使用HTTP通訊協定。 這可以是GET或POST下載。

## 屬性 {#properties}

1. **選取網頁檔案**

   若要指定要下載的檔案，您可以輸入檔案URL、使用儲存檔案的外部HTTP帳戶，或透過Adobe Campaign執行個體載入檔案。 可用的引數詳述如下：

   * 若要直接輸入要下載的檔案URL，請選取&#x200B;**[!UICONTROL Explicit URL]**&#x200B;選項，並在適當的欄位中指定URL。 此URL可使用變數資料建構。

     ![](assets/download_web_edit.png)

   * 若要使用&#x200B;**[!UICONTROL External account]**，請從下拉式清單中選取帳戶，並指定要下載的檔案。

     從Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點設定外部帳戶。 帳戶引數可以透過&#x200B;**[!UICONTROL Edit link]**&#x200B;圖示編輯。

     ![](assets/download_web_edit_external.png)

   * 若要從Adobe Campaign執行個體下載檔案，請選取&#x200B;**[!UICONTROL Adobe Campaign Instance]**&#x200B;選項。

     ![](assets/download_web_edit_instance.png)

1. **檔案歷史化**

   **[!UICONTROL File historization settings...]**&#x200B;連結可讓您指定檔案儲存目錄和此目錄的清除頻率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下選項：

   * **[!UICONTROL Use a default storage directory]**：檔案一律會在處理前移動。 如果核取此選項，檔案會移至預設儲存目錄(Adobe Campaign安裝資料夾的&#x200B;**vars**&#x200B;目錄)。 若要指定儲存目錄，請取消核取方塊並在&#x200B;**[!UICONTROL Storage directory]**&#x200B;欄位中輸入其路徑
   * **[!UICONTROL Number of files]**：輸入要保留在儲存目錄中的檔案數目上限。
   * **[!UICONTROL Maximum size (in Mb)]**：輸入儲存目錄的最大容量(MB)。

   每個檔案會保留24小時，之後才會受到定義的清除規則的限制。 清除作業會在活動開始之前進行，因此不會考慮進行中的工作流程檔案。

   會根據檔案的年齡（從最舊到最新）來刪除檔案。 最舊的檔案會被清除，直到兩個清除規則都得到驗證為止。 因此，如果定義了100個檔案的限制，這表示儲存目錄在工作流程開始之前將一律包含100個最新檔案，以及在進行中的工作流程中正在處理的檔案。

   如果您不想再設定&#x200B;**[!UICONTROL Number of files]**&#x200B;和&#x200B;**[!UICONTROL Maximum size (in Mb)]**&#x200B;選項的限制，請輸入0作為值。

1. **高級參數**

   **[!UICONTROL Advanced parameters...]**&#x200B;連結可讓您指定下列其他選項：

   * **[!UICONTROL Follow redirections]**：檔案重新導向可讓您使用覆寫，將資料輸入或輸出導向到其他型別的裝置。
   * **[!UICONTROL Add the HTTP headers to the file]**：在某些情況下，您可能會想要將額外的HTTP標頭新增至檔案。 最常見的情況是，這些標頭將用於提供其他資訊以進行疑難排解、用於[跨原始資源共用(CORS)](https://developer.mozilla.org/docs/Web/HTTP/CORS)，或用於設定特定的快取指示。
   * **[!UICONTROL Ignore the HTTP return code]**： HTTP傳回碼（也稱為HTTP狀態碼）表示HTTP要求的結果。

   ![](assets/download_web_edit_advanced.png)

   **[!UICONTROL Process errors]**&#x200B;選項在[處理錯誤](monitoring-workflow-execution.md#processing-errors)中有詳細說明。

## 輸出引數 {#output-parameters}

* 檔案名稱：下載檔案的完整名稱。
