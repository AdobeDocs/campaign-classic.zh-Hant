---
product: campaign
title: 網頁下載
description: 深入了解網頁下載工作流程活動
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# 網頁下載{#web-download}

![](../../assets/common.svg)

此 **網頁下載** 活動會在明確URL、外部帳戶或Adobe Campaign例項上啟動檔案下載。 已使用HTTP通訊協定。 這可以是GET或POST下載。

## 屬性 {#properties}

1. **選擇Web檔案**

   若要指定要下載的檔案，您可以輸入檔案URL、使用儲存檔案的外部HTTP帳戶，或透過Adobe Campaign例項載入檔案。 可用參數詳細說明如下：

   * 若要直接輸入要下載的檔案URL，請選取 **[!UICONTROL Explicit URL]** 選項並在適當欄位中指定URL。 此URL可使用變數資料來建構。

      ![](assets/download_web_edit.png)

   * 若要使用 **[!UICONTROL External account]**，請從下拉式清單中選取帳戶，並指定要下載的檔案。

      外部帳戶是從 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign樹的節點。 帳戶參數可透過 **[!UICONTROL Edit link]** 表徵圖。

      ![](assets/download_web_edit_external.png)

   * 若要從Adobe Campaign例項下載檔案，請選取 **[!UICONTROL Adobe Campaign Instance]** 選項。

      ![](assets/download_web_edit_instance.png)

1. **檔案歷史化**

   此 **[!UICONTROL File historization settings...]** 連結允許您指定檔案儲存目錄和此目錄的清除頻率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下選項：

   * **[!UICONTROL Use a default storage directory]**:檔案一律會在處理前移動。 如果選中此選項，則檔案將移入預設儲存目錄( **vars** Adobe Campaign安裝資料夾的目錄)。 要指定儲存目錄，請取消選中該框，並在 **[!UICONTROL Storage directory]** 欄位
   * **[!UICONTROL Number of files]**:輸入儲存目錄中要保留的檔案數上限。
   * **[!UICONTROL Maximum size (in Mb)]**:輸入儲存目錄的最大容量（以兆位元組為單位）。

   每個檔案在遵守定義的清除規則之前保留24小時。 清除作業會在活動開始前進行，因此不會考慮進行中的工作流程檔案。

   檔案會根據其年齡（從最舊到最新）來刪除。 清除最舊的檔案，直到驗證兩個清除規則為止。 因此，如果定義了100個檔案限制，這意味著儲存目錄將始終包含工作流開始之前的100個最新檔案，以及正在進行的工作流中正在處理的檔案。

   如果您不想再為 **[!UICONTROL Number of files]** 和 **[!UICONTROL Maximum size (in Mb)]** 選項，輸入0作為值。

1. **高級參數**

   此 **[!UICONTROL Advanced parameters...]** 連結可讓您指定下列其他選項：

   ![](assets/download_web_edit_advanced.png)

   此 **[!UICONTROL Process errors]** 選項，詳見 [處理錯誤](monitoring-workflow-execution.md#processing-errors).

## 輸出參數 {#output-parameters}

* 檔案名：下載檔案的完整名稱。
