---
product: campaign
title: 傳送報吿至清單
description: 瞭解如何使用工作流程將報告傳送至清單
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# 傳送報吿至清單{#sending-a-report-to-a-list}



此使用案例詳細說明如何產生每月現成可用的 **[!UICONTROL Tracking indicators]** 以PDF格式報告，以及如何將其傳送給收件者清單。

![](assets/use_case_report_intro.png)

此使用案例的主要實施步驟為：

* 建立將接收傳遞的收件者清單(請參閱： [步驟1：建立收件者清單](#step-1--creating-the-recipient-list))。
* 建立傳遞範本，可讓您每次執行工作流程時都產生新傳遞(請參閱： [步驟2：建立傳遞範本](#step-2--creating-the-delivery-template))。
* 建立工作流程，讓您以PDF格式產生報表，並傳送給收件者清單(請參閱： [步驟3：建立工作流程](#step-3--creating-the-workflow))。

## 步驟1：建立收件者清單 {#step-1--creating-the-recipient-list}

前往 **[!UICONTROL Profiles and targets]** 索引標籤，按一下 **[!UICONTROL Lists]** 連結，然後 **[!UICONTROL Create]** 按鈕。 選取 **[!UICONTROL New list]** 和建立新收件者清單，以供報表傳送至。

![](assets/use_case_report_1.png)

有關建立清單的詳細資訊，請參閱此 [區段](../../platform/using/creating-and-managing-lists.md).

## 步驟2：建立傳遞範本 {#step-2--creating-the-delivery-template}

1. 前往 **[!UICONTROL Resources > Templates > Delivery templates]** Adobe Campaign檔案總管的節點並複製 **[!UICONTROL Email delivery]** 現成可用的範本。

   ![](assets/use_case_report_2.png)

   如需建立傳遞範本的詳細資訊，請參閱此 [區段](../../delivery/using/about-templates.md).

1. 輸入各種範本引數：標籤、目標（先前建立的收件者清單）、主旨和內容。

   ![](assets/use_case_report_3.png)

1. 每次執行工作流程時， **[!UICONTROL Tracking indicators]** 報告已更新(請參閱 [步驟3：建立工作流程](#step-3--creating-the-workflow))。 若要在傳送中包含最新版本的報告，您需要新增 **[!UICONTROL Calculated attachment]**：

   有關建立計算附件的詳細資訊，請參閱此 [區段](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * 按一下 **[!UICONTROL Attachments]** 連結並按一下 **[!UICONTROL Add]**，然後選取 **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * 前往 **[!UICONTROL Type]** 欄位並選取第四個選項： **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      在中輸入的值 **[!UICONTROL Label]** 欄位不會出現在最終傳遞中。

   * 前往編輯區域並輸入檔案的存取路徑和名稱。

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >檔案必須存在於伺服器上。 其路徑和名稱必須與 **[!UICONTROL JavaScript code]** 工作流程的型別活動(請參閱： [步驟3：建立工作流程](#step-3--creating-the-workflow))。

   * 選取 **[!UICONTROL Advanced]** 標籤並核取 **[!UICONTROL Script the name of the file name displayed in the mails sent]**. 前往編輯區域，並輸入要在最終傳遞中指定附件的名稱。

      ![](assets/use_case_report_6bis.png)

## 步驟3：建立工作流程 {#step-3--creating-the-workflow}

已針對此使用案例建立下列工作流程。 它有三個活動：

* 一 **[!UICONTROL Scheduler]** 輸入活動可讓您每月執行工作流程一次，
* 一 **[!UICONTROL JavaScript code]** 輸入活動，讓您以PDF格式產生報表；
* 一 **[!UICONTROL Delivery]** 輸入使用先前建立之傳遞範本的活動。

![](assets/use_case_report_8.png)

1. 現在移至 **[!UICONTROL Administration > Production > Technical workflows]** 節點，並建立新的工作流程。

   ![](assets/use_case_report_7.png)

1. 從新增開始 **[!UICONTROL Scheduler]** 輸入活動並進行設定，讓工作流程在當月第一個星期一執行。

   ![](assets/use_case_report_9.png)

   有關設定排程器的詳細資訊，請參閱 [排程器](scheduler.md).

1. 然後新增 **[!UICONTROL JavaScript code]** 型別活動。

   ![](assets/use_case_report_10.png)

   在編輯區域中輸入下列程式碼：

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   會使用下列變數：

   * **var reportName**：以雙引號輸入報表的內部名稱。 在此案例中， **追蹤指標** 報表為「deliveryFeedback」。
   * **var路徑**：輸入檔案的儲存路徑(&quot;tmp/files/&quot;)、您要提供檔案的名稱(&quot;deliveryFeedback&quot;)和副檔名(&quot;。pdf&quot;)。 在此案例中，我們使用內部名稱作為檔案名稱。 值必須位於雙引號之間，並以「+」字元分隔。

      >[!CAUTION]
      >
      >檔案必須儲存在伺服器上。 您必須在「 」中輸入相同的路徑和名稱 **[!UICONTROL General]** 已計算附件之編輯視窗的標籤(請參閱： [步驟2：建立傳遞範本](#step-2--creating-the-delivery-template))。

   * **var exportFormat**：輸入檔案的匯出格式(「PDF」)。
   * **var _ctx** （內容）：在此案例中，我們使用 **[!UICONTROL Tracking indicators]** 在其全域內容中報告。

1. 完成方式是新增 **[!UICONTROL Delivery]** 使用下列選項輸入activity ：

   * **[!UICONTROL Delivery]**：選取 **[!UICONTROL New, created from a template]**，並選取先前建立的傳遞範本。
   * 對於 **[!UICONTROL Recipients]** 和 **[!UICONTROL Content]** 欄位，選取 **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**：選取 **[!UICONTROL Prepare and start]**.
   * 取消核取 **[!UICONTROL Generate an outbound transition]** 和 **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)
