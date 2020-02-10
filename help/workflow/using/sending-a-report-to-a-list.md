---
title: 傳送報表至清單
seo-title: 傳送報表至清單
description: 傳送報表至清單
seo-description: null
page-status-flag: never-activated
uuid: 29759fd8-47f3-47cc-9f7e-263e305fd6fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 41b8a8a8-efac-4e8e-8aea-d4fd06c46e74
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 傳送報表至清單{#sending-a-report-to-a-list}

此使用案例詳細說明如何以PDF格式產生每月現成可用的 **[!UICONTROL Tracking indicators]** 報表，以及如何將它傳送至收件者清單。

![](assets/use_case_report_intro.png)

此使用案例的主要實施步驟為：

* 建立接收遞送的收件者清單(請參閱：步 [驟1:建立收件者清單](#step-1--creating-the-recipient-list))。
* 建立傳送範本，讓您在每次執行工作流程時產生新的傳送(請參閱：步 [驟2:建立傳送範本](#step-2--creating-the-delivery-template))。
* 建立工作流程，讓您以PDF格式產生報表並傳送至收件者清單(請參閱：步 [驟3:建立工作流程](#step-3--creating-the-workflow))。

## 步驟1:建立收件者清單 {#step-1--creating-the-recipient-list}

前往宇宙 **[!UICONTROL Profiles and targets]** ，按一下連結 **[!UICONTROL Lists]** ，然後按一下 **[!UICONTROL Create]** 按鈕。 為 **[!UICONTROL New list]** 要傳送的報表選擇並建立新的收件者清單。

![](assets/use_case_report_1.png)

有關建立清單的詳細資訊，請參 [閱](../../platform/using/creating-and-managing-lists.md)。

## 步驟2:建立傳送範本 {#step-2--creating-the-delivery-template}

1. 前往Adobe **[!UICONTROL Resources > Templates > Delivery templates]** Campaign檔案總管的節點，並復 **[!UICONTROL Email delivery]** 制現成可用的範本。

   ![](assets/use_case_report_2.png)

   如需建立傳送範本的詳細資訊，請參閱本 [節](../../delivery/using/about-templates.md)。

1. 輸入各種模板參數：標籤、目標（先前建立的收件者清單）、主旨和內容。

   ![](assets/use_case_report_3.png)

1. 每次執行工作流程時，報 **[!UICONTROL Tracking indicators]** 表都會更新(請參 [閱步驟3:建立工作流程](#step-3--creating-the-workflow))。 若要在傳送中包含報表的最新版本，您必須新增 **[!UICONTROL Calculated attachment]**:

   有關建立計算附件的詳細資訊，請參 [閱](../../delivery/using/attaching-files.md#creating-a-calculated-attachment)。

   * 按一下連 **[!UICONTROL Attachments]** 結並按一 **[!UICONTROL Add]**&#x200B;下，然後選取 **[!UICONTROL Calculated attachment]**。

      ![](assets/use_case_report_4.png)

   * 前往欄位 **[!UICONTROL Type]** 並選取第四個選項： **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**。

      ![](assets/use_case_report_5.png)

      在欄位中輸入的 **[!UICONTROL Label]** 值不會出現在最終傳送中。

   * 轉到編輯區域並輸入檔案的訪問路徑和名稱。

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >該檔案必須存在於伺服器上。 其路徑和名稱必須與在工作流的類型活動 **[!UICONTROL JavaScript code]** 中輸入的路徑和名稱相同(請參閱：步 [驟3:建立工作流程](#step-3--creating-the-workflow))。

   * 選擇該選 **[!UICONTROL Advanced]** 項卡並選中 **[!UICONTROL Script the name of the file name displayed in the mails sent]**。 前往編輯區域，然後輸入您要在最終傳送中提供附件的名稱。

      ![](assets/use_case_report_6bis.png)

## 步驟3:建立工作流程 {#step-3--creating-the-workflow}

為此使用案例建立了下列工作流程。 它有三項活動：

* 一種 **[!UICONTROL Scheduler]** 類型活動，可讓您每月執行一次工作流程，
* 一種 **[!UICONTROL JavaScript code]** 類型活動，可讓您產生PDF格式的報表，
* 一個 **[!UICONTROL Delivery]** 使用先前建立的傳送範本的類型活動。

![](assets/use_case_report_8.png)

1. 現在，請移至節 **[!UICONTROL Administration > Production > Technical workflows]** 點並建立新的工作流程。

   ![](assets/use_case_report_7.png)

1. 首先，新增 **[!UICONTROL Scheduler]** 類型活動並加以設定，讓工作流程在當月的第一個星期一執行。

   ![](assets/use_case_report_9.png)

   有關配置調度程式的詳細資訊，請參 [閱Scheduler](../../workflow/using/scheduler.md)。

1. 然後新增 **[!UICONTROL JavaScript code]** 類型活動。

   ![](assets/use_case_report_10.png)

   在編輯區域中輸入以下代碼：

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   使用下列變數：

   * **var reportName**:以雙引號輸入報表的內部名稱。 在此情況下，追蹤指標報表的內 **部名稱** 為「deliveryFeedback」。
   * **var路徑**:輸入檔案的儲存路徑(&quot;tmp/files/&quot;)、您要指定檔案的名稱(&quot;deliveryFeedback&quot;)和副檔名(&quot;。pdf&quot;)。 在本例中，我們使用內部名稱作為檔案名。 值必須在雙引號之間，並以&quot;+&quot;字元分隔。

      >[!CAUTION]
      >
      >檔案必須儲存在伺服器上。 必須在編輯窗口的頁籤中為計算附件輸入 **[!UICONTROL General]** 相同的路徑和相同的名稱(請參閱：步 [驟2:建立傳送範本](#step-2--creating-the-delivery-template))。

   * **var exportFormat**:輸入檔案的匯出格式(「PDF」)。
   * **var _ctx** (context):在此案例中，我們會在其全域內 **[!UICONTROL Tracking indicators]** 容中使用報表。

1. 完成時，請新增 **[!UICONTROL Delivery]** 具有下列選項的類型活動：

   * **[!UICONTROL Delivery]**:選擇 **[!UICONTROL New, created from a template]**，然後選擇先前建立的傳送模板。
   * 對於和 **[!UICONTROL Recipients]** 字 **[!UICONTROL Content]** 段，選擇 **[!UICONTROL Specified in the delivery]**。
   * **[!UICONTROL Action to execute]**:選擇「 **[!UICONTROL Prepare and start]** Select（選擇）」。
   * 取消檢查 **[!UICONTROL Generate an outbound transition]** 和 **[!UICONTROL Process errors]**。
   ![](assets/use_case_report_11.png)

