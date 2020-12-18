---
solution: Campaign Classic
product: campaign
title: 假設範本
description: 假設範本
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%

---


# 假設範本{#hypothesis-templates}

## 建立假設模型{#creating-a-hypothesis-model}

設定假設範本可讓您定義用於測量反應的上下文，不論是傳送或選件。 這裡參考了各種測量表，包括用於定義個人、假設和事務表之間關係的表。

若要建立假設範本，請套用下列步驟：

1. 在Adobe Campaign檔案總管中，按一下&#x200B;**[!UICONTROL Resources>Templates>Hypothesis templates]**。

   ![](assets/response_hypothesis_model_creation_001.png)

1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;或按一下右鍵模板清單，然後在下拉清單中選擇&#x200B;**[!UICONTROL New]**。
1. 輸入假設標籤。
1. 指定範本是針對選件或透過&#x200B;**[!UICONTROL Hypothesis type]**&#x200B;傳送的假設。
1. 對於&#x200B;**[!UICONTROL Delivery]**&#x200B;類型範本，指定測量是否應使用或不使用控制群組進行（有關詳細資訊，請參閱[假設範本的屬性](#properties-of-a-hypothesis-template)）。
1. 對於&#x200B;**[!UICONTROL Delivery]**&#x200B;類型範本，您可以使用&#x200B;**[!UICONTROL Channel]**&#x200B;下拉式清單選擇特定渠道或決定將範本套用至Adobe Campaign中的所有可用渠道（如需詳細資訊，請參閱[假設範本的屬性](#properties-of-a-hypothesis-template)）。
1. 選擇要在其中建立的&#x200B;**[!UICONTROL Execution folder]**&#x200B;並自動執行將從此模板建立的假設。
1. 選擇執行設定（如需詳細資訊，請參閱[假設範本執行設定](#hypothesis-template-execution-settings)）。
1. 指定假設計算期間（有關詳情，請參閱[假設範本執行設定](#hypothesis-template-execution-settings)）。

   >[!CAUTION]
   >
   >此期間由聯絡日期確定。

1. 在&#x200B;**[!UICONTROL Transactions]**&#x200B;標籤中，指定假設計算所需的表和欄位（有關詳細資訊，請參閱[Transactions](#transactions)）。
1. 如果您的範本已針對&#x200B;**[!UICONTROL Offer]**&#x200B;類型假設設定，您可以啟用&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;選項：在此情況下，選取您要變更的選件提案狀態。
1. 指定假設應用的範圍（有關詳情，請參閱[假設周長](#hypothesis-perimeter)）。
1. 如有必要，請使用指令碼完成篩選（如需詳細資訊，請參閱[假設周長](#hypothesis-perimeter)）。

### 假設模板{#properties-of-a-hypothesis-template}的性質

範本的&#x200B;**[!UICONTROL General]**&#x200B;標籤可讓您指定一般範本選項。 可用欄位包括：

* **[!UICONTROL Hypothesis type]**:可讓您判斷範本是否應以傳送或選件的假設為目標。

   您也可以選擇建立同時套用至傳送和選件的假設。

   >[!NOTE]
   >
   >如果範本套用至選件，**[!UICONTROL Transactions]**&#x200B;標籤中會提供&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;選項。

* **[!UICONTROL Measurement with control group]**:可讓您指出是否已為傳送或促銷活動定義控制群組，並將其納入測量指標。控制群組（未接收傳送）可讓您比較傳送後促銷活動與已接收傳送的目標人口，以評估促銷活動的影響。

   >[!NOTE]
   >
   >如果模板被配置為考慮控制組，但在遞送中沒有定義任何組（這些假設涉及），則結果將僅基於目標接收者。

   有關定義和配置控制組的詳細資訊，請參閱[定義控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

* **[!UICONTROL Channel]**:您可以選擇特定渠道，或從下拉式清單中選取，讓假設範本可用於Adobe Campaign **[!UICONTROL All channels]** 控制台中的所有渠道。如果您設定特定渠道的範本，這可讓您在建立假設時自動篩選每個渠道的傳送（請參閱[建立假設](../../campaign/using/creating-hypotheses.md)）。

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**:可讓您指定假設的執行資料夾。
* **[!UICONTROL Taken into account in campaign ROI calculation]**:在相關促銷活動的ROI計算中會考慮假設結果。

### 假設模板執行設定{#hypothesis-template-execution-settings}

範本的&#x200B;**[!UICONTROL General]**&#x200B;標籤也可讓您指定假設執行參數。 可用的選項如下：

* **[!UICONTROL Schedule execution for a time of low activity]**:可讓您排程假設啟動，以最佳化Adobe Campaign績效。勾選此選項時，促銷活動的處理工作流程會在停機期間執行假設計算。

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**:級別，若有同時執行，則套用至假設以排除假設計算順序。

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**:如有必要，可讓您排程假設重新計算（例如，如果您想定期更新指標，直到傳送結束）。

   ![](assets/response_exec_settings_001.png)

   要指定計畫，請應用以下流程：

   1. 按一下&#x200B;**[!UICONTROL Frequency of execution...]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Change...]**&#x200B;按鈕。

      ![](assets/response_frequency_execution_001.png)

   1. 設定頻率、相關事件和有效期。

      ![](assets/response_frequency_execution_002.png)

   1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;保存計畫。

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**:此函式保留給專家用戶。它可讓您新增標籤至測量假設稽核，以顯示SQL查詢。 這樣，當模擬完成時，可以檢測可能的故障。
* **[!UICONTROL Keep execution workflow]**:可讓您保留在假設計算開始時自動產生的工作流程。在從已勾選此選項的範本建立的假設中，可使用產生的工作流程來遵循程式。

   >[!CAUTION]
   >
   >此選項必須僅用於除錯，以在執行假設時發生錯誤時啟用。\
   >此外，自動產生的工作流程不得修改。 在以後的計算中，不會考慮其他地方的最終修改。\
   >如果您已勾選此選項，請在工作流執行後刪除它。

### 事務{#transactions}

此標籤包含各種欄位和表格，可讓您儲存交易中收件者反應的歷史記錄。 有關響應管理專用表的詳細資訊，請參閱[Configuration](../../configuration/using/about-schema-reference.md)指南。

* **[!UICONTROL Schema (reaction log storage)]**:選擇收件人反應表。Adobe Campaign中的現成可用表是&#x200B;**NmsRematchRcp**。
* **[!UICONTROL Transaction schema]**:選擇假設將涉及的表，即交易或購買表。
* **[!UICONTROL Querying schema]**:選擇篩選假設的准則。
* **[!UICONTROL Link to individuals]**:選擇個人和用作事務方案的表之間的連結。
* **[!UICONTROL Link to the household]**:如果希望將家庭的所有成員包括在假設中，請在事務結構中選擇指向家庭的連結。此欄位為選擇性。
* **[!UICONTROL Transaction date]**:此欄位為選擇性，但建議使用，因為它可讓您定義假設計算範圍。
* **[!UICONTROL Measurement period]**:可讓您設定開始和結束日期，在此期間執行假設並復原購買行。

   當假設連結至傳送時，測量會在直接郵件傳送的聯絡日期後數天，或在電子郵件或簡訊傳送的傳送日期後自動觸發。

   ![](assets/response_measurement_001.png)

   如果假設是在飛行中啟動的，如果想立即觸發，就可以強制推動。 否則，根據基於假設建立日期的配置計算結束自動觸發該假設（請參閱[在交貨時即時建立假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)）。

* **[!UICONTROL Transaction/Margin amount]**:這些欄位是選用欄位，可讓您自動計算週轉指標(請參 [閱Indicators](../../campaign/using/hypothesis-tracking.md#indicators))。
* **[!UICONTROL Unit amount]**:可讓您設定計算收入的金額(請參 [閱Indicators](../../campaign/using/hypothesis-tracking.md#indicators))。

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**:可讓您指定其他報表度量或不同表格中欄位的軸。
* **[!UICONTROL Update offer proposition status]**:可讓您變更選件提案的狀態（如果選件收件者是由假設所識別）。

   ![](assets/response_offer_status_001.png)

### 假設周長{#hypothesis-perimeter}

一旦定義了事務表和假設將涉及的欄位，您就可以通過使用篩選器指定目標事務和傳送來細化假設的範圍。 您也可以使用JavaScript指令碼，明確指向交易表格中參考的產品。

* **篩選交易**:在標 **[!UICONTROL Scope]** 簽中，您可以設定假設的篩選。操作步驟：

   1. 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結。

      ![](assets/response_scope_filtering_001.png)

   1. 指定您的篩選條件。

      ![](assets/response_scope_filtering_002.png)

   1. 選擇假設將涉及的事務。

      ![](assets/response_scope_filtering_003.png)

* **篩選收件者**:在標 **[!UICONTROL Scope]** 簽中，您可以將假設限制為任何連結至訊息的資訊（傳送、收件者、電子郵件地址、服務等）:

   1. 按一下&#x200B;**[!UICONTROL Add a filter]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Edit query]**。

      ![](assets/response_scope_filtering_004.png)

   1. 指定您的篩選條件。

      ![](assets/response_scope_filtering_005.png)

   1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;保存查詢。

      ![](assets/response_scope_filtering_006.png)

* **指令碼**:您可以使用JavaScript指令碼，在假設設定執行期間動態超載假設設定。

   若要這麼做，請按一下&#x200B;**[!UICONTROL Advanced settings]**&#x200B;連結，然後輸入所要的指令碼。

   >[!NOTE]
   >
   >此選項適用於專家使用者。

   ![](assets/response_hypothesis_model_creation_011.png)

## 範例：在傳送{#example--creating-a-hypothesis-template-on-a-delivery}上建立假設範本

在此範例中，我們將建立直接郵件類型傳送的假設範本。 假設所依據的交易表（我們範例中的&#x200B;**Purchases**）包含連結至文章或產品的購買行。 我們想要設定我們的模型，以在購買表格中建立文章或產品的假設。

1. 在Adobe Campaign檔案總管中，前往&#x200B;**[!UICONTROL Resources > Templates > Hypothesis templates]**&#x200B;節點。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;以建立範本。

   ![](assets/response_hypothesis_model_example_001.png)

1. 變更範本標籤。

   ![](assets/response_hypothesis_model_example_002.png)

1. 選擇&#x200B;**[!UICONTROL Deliveries]**&#x200B;作為假設類型。
1. 勾選相關方塊，指定傳送可包含控制群組。
1. 選擇&#x200B;**[!UICONTROL Direct mail]**&#x200B;頻道。

   >[!NOTE]
   >
   >由於模板專用於直接郵件遞送，因此使用此模型建立的假設可能不連結到任何其他遞送類型。

1. 在&#x200B;**[!UICONTROL Transactions]**&#x200B;標籤中，選擇收件者反應表。

   ![](assets/response_hypothesis_model_example_006.png)

1. 在&#x200B;**[!UICONTROL Transactions schema]**&#x200B;欄位中，選擇您的購買表格。

   ![](assets/response_hypothesis_model_example_007.png)

1. 在&#x200B;**[!UICONTROL Querying schema]**&#x200B;欄位中選取購買行。

   ![](assets/response_hypothesis_model_example_008.png)

1. 選擇連結至購買表格的收件者。

   ![](assets/response_hypothesis_model_example_009.png)

1. 選擇連結至購買日期的欄位。

   這可讓您定義假設的時間範圍。 此階段並非強制性，但建議使用。

   ![](assets/response_hypothesis_model_example_010.png)

1. 設定5至25天的計算期間。

   ![](assets/response_hypothesis_model_example_005.png)

1. 在&#x200B;**[!UICONTROL Scope]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;以建立假設的篩選。

   ![](assets/response_hypothesis_model_example_011.png)

   如此建立的範本可讓您對購買表格中的產品或文章執行假設。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以記錄範本。

