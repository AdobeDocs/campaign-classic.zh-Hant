---
product: campaign
title: 假設範本
description: 了解如何在Campaign回應管理員中建立假設範本
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 428c7677-454b-4618-bae7-0be7df6dfcaa
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 2%

---

# 假設範本{#hypothesis-templates}

![](../../assets/common.svg)

## 建立假設模型 {#creating-a-hypothesis-model}

設定假設範本可讓您定義用於測量反應的內容，無論是針對傳送或選件。 這是引用各種測量表的地方，包括用於定義個人、假設和交易表之間關係的表。

若要建立假設範本，請套用下列步驟：

1. 在Adobe Campaign檔案總管中，按一下 **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. 按一下 **[!UICONTROL New]** 或在範本清單中按一下滑鼠右鍵，然後選擇 **[!UICONTROL New]** 中。
1. 輸入假設標籤。
1. 指定範本是否會經由 **[!UICONTROL Hypothesis type]**.
1. 針對 **[!UICONTROL Delivery]** 類型模板，指定測量應使用還是不使用控制組執行。 [了解更多](#properties-of-a-hypothesis-template)
1. 針對 **[!UICONTROL Delivery]** 類型範本，您可以選擇特定管道，或決定使用 **[!UICONTROL Channel]** 下拉式清單。 [了解更多](#properties-of-a-hypothesis-template)
1. 選取 **[!UICONTROL Execution folder]** 您要建立並自動執行將從此模板建立的假設。
1. 選擇執行設定。 [了解更多](#hypothesis-template-execution-settings)
1. 指定假設計算期間。 [了解更多](#hypothesis-template-execution-settings)

   >[!CAUTION]
   >
   >此期間由聯絡日期決定。

1. 在 **[!UICONTROL Transactions]** 索引標籤，指定假設計算所需的表格和欄位。 [了解更多](#transactions)
1. 如果您的範本已設定為 **[!UICONTROL Offer]** 類型假設，您可以啟用 **[!UICONTROL Update offer proposition status]** 選項：在此情況下，請選取您要變更的優惠方案主張的狀態。
1. 指定假設應用程式的範圍。 [了解更多](#hypothesis-perimeter)
1. 如有必要，請使用指令碼完成篩選。 [了解更多](#hypothesis-perimeter)

### 假設範本的屬性 {#properties-of-a-hypothesis-template}

範本的 **[!UICONTROL General]** 標籤中，您可以指定一般範本選項。 可用欄位包括：

* **[!UICONTROL Hypothesis type]**:可讓您判斷範本是否應以傳送或選件的假設為目標。

   您也可以選擇建立將同時套用至傳送和選件的假設。

   >[!NOTE]
   >
   >如果範本套用至選件，則 **[!UICONTROL Update offer proposition status]** 選項 **[!UICONTROL Transactions]** 標籤。

* **[!UICONTROL Measurement with control group]**:可讓您指出是否已為傳送或促銷活動定義控制組，並將其納入測量指標中。 未接收傳送的控制組可讓您透過將促銷活動與已接收傳送的目標母體比較，來評估傳送後促銷活動的影響。

   >[!NOTE]
   >
   >如果將範本設定為考慮控制組，但在假設所關注的傳送中未定義任何組，則結果將僅基於目標收件者。

   有關定義和配置控制組的詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Channel]**:您可以選取特定通道，或將假設範本提供給Adobe Campaign主控台中的所有通道使用 **[!UICONTROL All channels]** 中。 如果您設定特定管道的範本，則可讓您在建立假設時，根據管道自動篩選傳送。 [了解更多](creating-hypotheses.md)

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**:可讓您指定假設的執行資料夾。
* **[!UICONTROL Taken into account in campaign ROI calculation]**:在計算相關促銷活動的ROI時，會考量假設結果。

### 假設範本執行設定 {#hypothesis-template-execution-settings}

範本的 **[!UICONTROL General]** 索引標籤也可讓您指定假設執行參數。 可用選項如下：

* **[!UICONTROL Schedule execution for a time of low activity]**:可讓您排程假設啟動，以最佳化Adobe Campaign效能。 核取此選項後，促銷活動的處理工作流程會在停機期間執行假設計算。

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**:套用至假設的層級，以在有同時執行時省下假設計算順序。

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**:如有必要，可讓您排程假設重新計算（例如，如果您想要定期更新指標，直到傳送結束）。

   ![](assets/response_exec_settings_001.png)

   要指定計畫，請應用以下流程：

   1. 按一下 **[!UICONTROL Frequency of execution...]** 連結，然後 **[!UICONTROL Change...]** 按鈕。

      ![](assets/response_frequency_execution_001.png)

   1. 設定頻率、相關事件和有效期。

      ![](assets/response_frequency_execution_002.png)

   1. 按一下 **[!UICONTROL Finish]** 以儲存排程。

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**:此函式保留給專家用戶。 它可讓您將索引標籤新增至測量假設稽核，以顯示SQL查詢。 這樣，當模擬完成錯誤時，就能夠檢測可能的故障。
* **[!UICONTROL Keep execution workflow]**:可讓您保留在假設計算開始時自動產生的工作流程。 在從已勾選此選項的範本建立的假設中，產生的工作流程可用於遵循此程式。

   >[!CAUTION]
   >
   >如果執行假設時發生錯誤，則只能啟動此選項以進行除錯。\
   >此外，自動產生的工作流程不得修改。 在以後的計算中，不會考慮任何最終修改。\
   >如果您已核取此選項，請在執行工作流程後將其刪除。

### 交易 {#transactions}

此索引標籤包含各種欄位和表格，可讓您以交易方式儲存收件者反應的歷史記錄。 請參閱 [節](../../configuration/using/about-schema-reference.md) 有關專用於響應管理的表的詳細資訊。

* **[!UICONTROL Schema (reaction log storage)]**:選擇收件人反應表。 Adobe Campaign的現成可用表格為 **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**:選擇假設將涉及的表，即交易或購買表。
* **[!UICONTROL Querying schema]**:選擇篩選假設的准則。
* **[!UICONTROL Link to individuals]**:選擇個人和用作事務架構的表之間的連結。
* **[!UICONTROL Link to the household]**:如果要將家庭的所有成員納入假設，請在交易結構中選擇指向家庭的連結。 此欄位為選填欄位。
* **[!UICONTROL Transaction date]**:此欄位為選用欄位，但建議使用，因為它可讓您定義假設計算的範圍。
* **[!UICONTROL Measurement period]**:可讓您設定執行假設和復原購買行的開始和結束日期。

   當假設連結至傳送時，測量會在直接郵件傳送的聯絡日期後數天，或在電子郵件或簡訊傳送的傳送日期後自動觸發。

   ![](assets/response_measurement_001.png)

   如果假設是即時啟動的，如果想要立即觸發，就可以強制進行。 否則，會根據已設定的計算結束（即根據假設建立日期）自動觸發。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**:這些欄位是可選欄位，可讓您自動計算週轉指標。 [了解更多](hypothesis-tracking.md#indicators)
* **[!UICONTROL Unit amount]**:可讓您設定用於計算收入的金額。 [了解更多](hypothesis-tracking.md#indicators)

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**:可讓您指定其他報表測量或不同表格中欄位的軸。
* **[!UICONTROL Update offer proposition status]**:可讓您在以假設識別優惠方案收件者時，變更優惠方案主張的狀態。

   ![](assets/response_offer_status_001.png)

### 假設周長 {#hypothesis-perimeter}

一旦定義了交易表以及假設將涉及的欄位後，您就可以使用篩選器指定目標交易和傳送，以縮小假設的範圍。 您也可以使用JavaScript指令碼，明確指向交易表中引用的產品。

* **篩選交易**:在 **[!UICONTROL Scope]** 標籤中，您可以設定假設的篩選。 操作步驟：

   1. 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結。

      ![](assets/response_scope_filtering_001.png)

   1. 指定您的篩選條件。

      ![](assets/response_scope_filtering_002.png)

   1. 選擇假設要涉及的交易。

      ![](assets/response_scope_filtering_003.png)

* **篩選收件者**:在 **[!UICONTROL Scope]** 索引標籤中，您可以將假設限制在連結至訊息（傳遞、收件者、電子郵件地址、服務等）的任何資訊：

   1. 按一下 **[!UICONTROL Add a filter]** 連結，然後 **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. 指定您的篩選條件。

      ![](assets/response_scope_filtering_005.png)

   1. 按一下 **[!UICONTROL Finish]** 以保存查詢。

      ![](assets/response_scope_filtering_006.png)

* **指令碼**:您可以使用JavaScript指令碼，在假設設定執行期間以動態方式過載。

   若要這麼做，請按一下 **[!UICONTROL Advanced settings]** 連結，然後輸入所需的指令碼。

   >[!NOTE]
   >
   >此選項適用於專家使用者。

   ![](assets/response_hypothesis_model_creation_011.png)

## 範例：在傳遞中建立假設範本 {#example--creating-a-hypothesis-template-on-a-delivery}

在此範例中，我們將建立直接郵件類型傳送的假設範本。 事務表(**購買** 在此範例中)，假設將以包含連結至文章或產品的購買行為為基礎。 我們想要設定模型，以在購買表格中建立有關文章或產品的假設。

1. 在Adobe Campaign探索器中，前往 **[!UICONTROL Resources > Templates > Hypothesis templates]** 節點。
1. 按一下 **[!UICONTROL New]** 來建立範本。

   ![](assets/response_hypothesis_model_example_001.png)

1. 變更範本標籤。

   ![](assets/response_hypothesis_model_example_002.png)

1. 選擇 **[!UICONTROL Deliveries]** 假設類型。
1. 核取相關方塊，以指定傳送可包含控制組。
1. 選擇 **[!UICONTROL Direct mail]** 頻道。

   >[!NOTE]
   >
   >由於範本是直接郵件傳送的專屬範本，使用此模型建立的假設可能不會連結至任何其他傳送類型。

1. 在 **[!UICONTROL Transactions]** 頁簽，選擇「收件人反應」(recipient reactions)表。

   ![](assets/response_hypothesis_model_example_006.png)

1. 在 **[!UICONTROL Transactions schema]** 欄位，選擇購買表格。

   ![](assets/response_hypothesis_model_example_007.png)

1. 在 **[!UICONTROL Querying schema]** 欄位。

   ![](assets/response_hypothesis_model_example_008.png)

1. 選擇連結至購買表格的收件者。

   ![](assets/response_hypothesis_model_example_009.png)

1. 選取連結至購買日期的欄位。

   這可讓您定義假設的時間範圍。 此階段不是強制性的，但建議使用。

   ![](assets/response_hypothesis_model_example_010.png)

1. 設定5至25天的計算期間。

   ![](assets/response_hypothesis_model_example_005.png)

1. 在 **[!UICONTROL Scope]** 按一下 **[!UICONTROL Edit query]** 來篩選假設。

   ![](assets/response_hypothesis_model_example_011.png)

   因此建立的模板使您能夠對購買表中的產品或文章運行假設。

1. 按一下 **[!UICONTROL Save]** 來記錄範本。
