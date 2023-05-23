---
product: campaign
title: 同步對象
description: 瞭解如何使受眾與ACS連接器同步
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 1%

---

# 同步對象{#synchronizing-audiences}



您可以使用Campaign v7高級功能構建一個複雜的清單，並以受眾身份直接、即時地與Campaign Standard（包括其他資料）無縫地共用此清單。 然後，您的Campaign Standard用戶可以在Adobe Campaign Standard消耗受眾。

只能使用Campign v7實現複雜目標，其中涉及未在Campaign Standard中複製的其他資料。

您也只需共用收件人清單或通過連接器(如帶Campaign Standard的MicrosoftDynamics)發送的資料。

此使用案例說明如何準備在市場活動v7中交付的目標，以及如何在與Adobe Campaign Standard一起建立和發送的交付中重複使用此目標及其附加資料。

>[!NOTE]
>
>如果您需要的所有資料都已複製，您還可以使用Adobe Campaign Standard的聚合和集合來豐富資料。

## 必要條件 {#prerequisites}

要實現這一點，您需要：

* 儲存在市場活動v7資料庫中並與Campaign Standard同步的收件人。 請參閱 [同步配置檔案](../../integrations/using/synchronizing-profiles.md) 的子菜單。
* 其他資料，如儲存在與市場活動v7資料庫中nms:recipients相關的表中的預訂或事務。 這些資料可以來自市場活動v7 OOB架構或自定義表。 預設情況下，Campaign Standard中不可用它們，因為它們未同步。
* 有權在市場活動v7和Campaign Standard中執行工作流。
* 在Campaign Standard中建立和執行交貨的權限。

## 在市場活動v7中建立具有其他資料的目標工作流 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

只能使用Campign v7實現複雜目標，其中涉及未在Campaign Standard中複製的其他資料。

一旦定義了目標及其附加資料，就可以將其另存為可與Campaign Standard共用的清單。

>[!NOTE]
>
>這是一個例子。 根據您的要求，您只需查詢收件人清單，並與ACS共用，而無需進一步處理。 您還可以使用其他資料管理活動來準備最終目標。

要獲取最終受眾及其附加資料：

1. 建立新工作流 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。
1. 添加 **[!UICONTROL Query]** 活動，然後選擇要向其發送最終電子郵件的收件人。 例如，所有18至30歲的受助者都生活在法國。

   ![](assets/acs_connect_query1.png)

1. 從查詢中添加其他資料。 有關詳細資訊，請參閱 [添加資料](../../workflow/using/query.md#adding-data) 的子菜單。

   此示例說明如何添加聚合以計算接收人在一年中收到的交貨數量。

   在 **[!UICONTROL Query]**&#x200B;選中 **[!UICONTROL Add data...]**。

   ![](assets/acs_connect_query2.png)

1. 選取 **[!UICONTROL Data linked to the filtering dimension]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query3.png)

1. 選擇 **[!UICONTROL Data linked to the filtering dimension]** ，然後選擇 **[!UICONTROL Recipient delivery logs]** 按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query4.png)

1. 選擇 **[!UICONTROL Aggregates]** 的 **[!UICONTROL Data collected]** 按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query5.png)

1. 添加篩選條件以僅考慮過去365天內建立的日誌，然後按一下 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query6.png)

1. 定義輸出列。 這裡，唯一需要的列是計算交貨數的列。 為此：

   * 選擇 **[!UICONTROL Add]** 窗戶右邊。
   * 從 **[!UICONTROL Select field]** 窗口，按一下 **[!UICONTROL Advanced selection]**。
   * 選擇 **[!UICONTROL Aggregate]**，則 **[!UICONTROL Count]**。 檢查 **[!UICONTROL Distinct]** ，然後按一下 **[!UICONTROL Next]**。
   * 在欄位清單中，選擇用於 **計數** 的子菜單。 選擇始終填充的欄位，例如 **[!UICONTROL Primary key]** ，然後按一下 **[!UICONTROL Finish]**。
   * 更改中的表達式 **[!UICONTROL Alias]** 的雙曲餘切值。 此別名將允許您輕鬆檢索最終交貨中添加的列。 例如 **NB交付**。
   * 按一下 **[!UICONTROL Finish]** 並保存 **[!UICONTROL Query]** 活動配置。

   ![](assets/acs_connect_query7.png)

1. 儲存工作流程。下一節介紹如何與ACS共用人口。

## 與Campaign Standard共用目標 {#share-the-target-with-campaign-standard}

定義目標群體後，您可以通過 **[!UICONTROL List update]** 的子菜單。

1. 在以前建立的工作流中，添加 **[!UICONTROL List update]** 並指定要更新或建立的清單。

   指定要在「市場活動v7」中保存清單的資料夾。 清單受實施期間定義的資料夾映射的約束，一旦在Campaign Standard中共用，這些映射會影響其可見性。 請參閱 [權利轉換](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) 的子菜單。

1. 確保 **[!UICONTROL Share with ACS]** 頁籤 預設情況下會選中它。

   ![](assets/acs_connect_listupdate1.png)

1. 保存並執行工作流。

   目標及其附加資料將保存在市場活動v7的清單中，並立即作為清單受眾以Campaign Standard形式共用。 只有已複製的配置檔案才與ACS共用。

如果在 **[!UICONTROL List update]** 活動，這意味著與Campaign Standard的同步可能已失敗。 若要查看有關出錯的詳細資訊，請轉到 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此資料夾包含由 **[!UICONTROL List update]** 活動執行。 請參閱 [診斷ACS連接器](../../integrations/using/troubleshooting-the-acs-connector.md) 的子菜單。

## 在Campaign Standard中檢索資料並在傳遞中使用 {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

在「市場活動7」中執行目標工作流後，您可以從 **[!UICONTROL Audiences]** 的子菜單。

![](assets/acs_connect_deliveryworkflow_audience.png)

通過在Campaign Standard中建立交付工作流，可以使用此受眾及其在交付中包含的附加資料。

1. 從 **[!UICONTROL Marketing activities]** 的子菜單。
1. 添加 **[!UICONTROL Read audience]** 活動，並選擇您以前從「市場活動7」中共用的受眾。

   此活動用於檢索所選受眾的資料。 您還可以應用 **[!UICONTROL Source Filtering]** 如果需要，請使用此活動的「相應」頁籤。

1. 添加 **[!UICONTROL Email delivery]** 將其配置為 [電子郵件傳遞活動](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)。
1. 開啟傳遞內容。
1. 新增個人化欄位。從彈出窗口中，找到 **[!UICONTROL Additional data (targetData)]** 的下界。 此節點包含在初始目標工作流中計算的受眾的其他資料。 您可以將它們用作任何其他個性化欄位。

   對於此示例，原始目標工作流提供的附加資料是過去365天內發送給每個收件人的交貨數。 在目標工作流中指定的NBdeliveries別名在此處可見。

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 保存交貨和工作流。

   工作流現在已準備好執行。 將分析交貨並準備發送。

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 發送並監控您的交貨 {#send-and-monitor-your-delivery}

一旦交付及其內容準備就緒，請發送：

1. 執行傳遞工作流。 此步驟準備發送電子郵件。
1. 在交貨控制面板中，人工確認可以發送交貨。
1. 監視傳送的報告和日誌：

   * **Campaign Standard**:訪問 [報告](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 和 [日誌](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) 與任何交貨相關。
   * **在活動v7和Campaign Standard**:交付ID、電子郵件廣泛日誌和電子郵件跟蹤日誌都同步到Campaign v7。 然後，您可以從「市場活動v7」獲得360°的營銷活動視圖。

      隔離將自動同步回「市場活動7」。 這允許將不可交付資訊納入「市場活動v7」中執行的下一個目標。

      您可以在中查找有關Campaign Standard中隔離管理的詳細資訊 [此部分](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。
