---
solution: Campaign Classic
product: campaign
title: 同步受眾
description: 同步受眾
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---


# 同步受眾{#synchronizing-audiences}

您可以使用Campaign v7進階功能建立複雜的清單，並與Campaign Standard（包括其他資料）以順暢的方式直接即時地以觀眾身分分享此清單。 然後，您的Campaign Standard使用者就可以在Adobe Campaign Standard中使用對象。

複雜的定位涉及未在Campaign Standard中複製的其他資料，只能使用Campaign v7來達成。

您也只需共用收件者清單或透過連接器（例如Microsoft Dynamics with Campaign Standard）傳送的資料。

此使用案例說明如何在Campaign v7中準備您的傳送目標，以及如何在使用Adobe Campaign Standard建立和傳送的傳送中重複使用此目標及其他資料。

>[!NOTE]
>
>如果您需要的所有資料都已複製，您也可以在Adobe Campaign Standard中使用匯總和集合來豐富資料。

## 必要條件 {#prerequisites}

為達到此目的，您需要：

* 儲存在Campaign v7資料庫並與Campaign Standard同步的收件者。 請參閱[同步配置檔案](../../integrations/using/synchronizing-profiles.md)部分。
* 其他資料，例如儲存在Campaign v7資料庫中與nms:recipients相關的表格中的訂閱或交易。 這些資料可來自Campaign v7 OOB結構描述或自訂表格。 由於未同步化，因此在Campaign Standard中預設無法使用這些項目。
* 在Campaign v7和Campaign Standard中執行工作流程的權限。
* 在Campaign Standard中建立和執行傳送的權限。

## 在Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}中建立包含其他資料的定位工作流程

複雜的定位涉及未在Campaign Standard中複製的其他資料，只能使用Campaign v7來達成。

定義目標及其其他資料後，就可將其儲存為可與「促銷活動標準」共用的清單。

>[!NOTE]
>
>這就是一個例子。 根據您的需求，您只需查詢收件者清單，並與ACS共用，毋需進一步處理。 您也可以使用其他資料管理活動來準備最終目標。

若要取得最終受眾及其他資料：

1. 從&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;建立新的工作流程。
1. 新增&#x200B;**[!UICONTROL Query]**&#x200B;活動，並選取您要傳送最終電子郵件給的收件者。 例如，所有18到30歲的收受者都住在法國。

   ![](assets/acs_connect_query1.png)

1. 從查詢中新增其他資料。 有關詳細資訊，請參閱[添加data](../../workflow/using/query.md#adding-data)部分。

   此範例說明如何新增匯總，以計算收件者在一年中收到多少傳送。

   在&#x200B;**[!UICONTROL Query]**&#x200B;中，選擇&#x200B;**[!UICONTROL Add data...]**。

   ![](assets/acs_connect_query2.png)

1. 選取 **[!UICONTROL Data linked to the filtering dimension]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query3.png)

1. 選擇&#x200B;**[!UICONTROL Data linked to the filtering dimension]**，然後選擇&#x200B;**[!UICONTROL Recipient delivery logs]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_query4.png)

1. 在&#x200B;**[!UICONTROL Data collected]**&#x200B;欄位中選擇&#x200B;**[!UICONTROL Aggregates]** ，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_query5.png)

1. 新增篩選條件，只考慮過去365天內建立的帳戶記錄，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/acs_connect_query6.png)

1. 定義輸出列。 在這裡，唯一需要的欄是計算傳送次數的欄。 若要這麼做：

   * 選擇窗口右側的&#x200B;**[!UICONTROL Add]**。
   * 在&#x200B;**[!UICONTROL Select field]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Advanced selection]**。
   * 選擇&#x200B;**[!UICONTROL Aggregate]**，然後選擇&#x200B;**[!UICONTROL Count]**。 選中&#x200B;**[!UICONTROL Distinct]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]**。
   * 在欄位清單中，選擇用於&#x200B;**Count**&#x200B;函式的欄位。 選擇永遠填入的欄位，例如&#x200B;**[!UICONTROL Primary key]**&#x200B;欄位，然後按一下&#x200B;**[!UICONTROL Finish]**。
   * 更改&#x200B;**[!UICONTROL Alias]**&#x200B;列中的表達式。 此別名可讓您輕鬆擷取最終傳送中新增的欄。 例如&#x200B;**NBdeliveries**。
   * 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;並保存&#x200B;**[!UICONTROL Query]**&#x200B;活動配置。

   ![](assets/acs_connect_query7.png)

1. 儲存工作流程。下節說明如何與ACS共用人口。

## 與Campaign Standard {#share-the-target-with-campaign-standard}共用目標

定義目標人口後，您可以通過&#x200B;**[!UICONTROL List update]**&#x200B;活動與ACS共用目標人口。

1. 在先前建立的工作流程中，新增&#x200B;**[!UICONTROL List update]**&#x200B;活動並指定您要更新或建立的清單。

   指定您要在Campaign v7中儲存清單的檔案夾。 清單受實作期間所定義的資料夾對應所約束，一旦在Campaign Standard中共用後，這些對其可見性會有影響。 請參閱[Rights conversion](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion)一節。

1. 請確定已勾選&#x200B;**[!UICONTROL Share with ACS]**&#x200B;選項。 預設情況下會選中它。

   ![](assets/acs_connect_listupdate1.png)

1. 儲存並執行工作流程。

   定位及其其他資料會儲存在Campaign v7的清單中，並立即在Campaign Standard中以清單對象的身分共用。 只有已複製的配置檔案與ACS共用。

如果&#x200B;**[!UICONTROL List update]**&#x200B;活動發生錯誤，表示與Campaign Standard的同步可能失敗。 若要查看更多錯誤的詳細資訊，請前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此資料夾包含由&#x200B;**[!UICONTROL List update]**&#x200B;活動執行觸發的同步工作流。 請參閱[「Troubleshooting the ACS Connector](../../integrations/using/troubleshooting-the-acs-connector.md)（ACS連接器疑難排解）」部分。

## 擷取Campaign Standard中的資料，並用於傳送{#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

在Campaign v7中執行定位工作流程後，您就可以從Campaign Standard的&#x200B;**[!UICONTROL Audiences]**&#x200B;選單中，以唯讀模式找到清單對象。

![](assets/acs_connect_deliveryworkflow_audience.png)

在Campaign Standard中建立傳送工作流程後，就可使用此對象及其在傳送中包含的其他資料。

1. 從&#x200B;**[!UICONTROL Marketing activities]**&#x200B;功能表建立新的工作流程。
1. 新增&#x200B;**[!UICONTROL Read audience]**&#x200B;活動，並選取您先前從Campaign v7共用的對象。

   此活動用於擷取所選對象的資料。 您也可以使用本練習的「相應」頁籤，視需要套用額外的&#x200B;**[!UICONTROL Source Filtering]**。

1. 新增&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動，並將其設定為其他[電子郵件傳送活動](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)。
1. 開啟傳送內容。
1. 新增個人化欄位。從彈出式菜單中，找到&#x200B;**[!UICONTROL Additional data (targetData)]**&#x200B;節點。 此節點包含初始定位工作流程中計算的觀眾其他資料。 您可將其當做任何其他個人化欄位使用。

   在此範例中，原始定位工作流程所產生的其他資料是過去365天內傳送給每個收件者的傳送數。 在定位工作流程中指定的NBdeliveries別名在此處可見。

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 儲存傳送和工作流程。

   工作流程現在已可供執行。 傳送內容將進行分析並準備傳送。

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 傳送並監控您的傳送{#send-and-monitor-your-delivery}

傳送及其內容準備就緒後，請傳送傳送，如[本節](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)中的詳細資訊所述：

1. 執行傳送工作流程。 此步驟會準備傳送電子郵件。
1. 從傳送控制面板，手動確認可傳送。
1. 監控傳送的報表和記錄：

   * **在Campaign Standard中**:存取與 [](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 傳送 [](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) 相關的報表和記錄，作為任何傳送。
   * **在Campaign v7和Campaign Standard中**:傳送ID、電子郵件廣泛記錄檔和電子郵件追蹤記錄檔會同步至Campaign v7。然後，您就可以從Campaign v7獲得行銷宣傳的360度檢視。

      隔離會自動同步回Campaign v7。 這可讓您將無法傳遞的資訊納入Campaign v7中執行的下一個定位。

      您可在[本節](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)的「促銷活動標準」中，找到有關隔離管理的更多資訊。

