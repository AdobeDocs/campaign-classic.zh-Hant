---
product: campaign
title: 建立假設
description: 瞭解如何在Campaign回應管理員中建立假設
feature: Campaigns
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 3%

---

# 建立假設{#creating-hypotheses}



建立/將假設連結至行銷活動選件或傳送有多種可能性：

* 透過 **[!UICONTROL Measurement hypotheses]** 資料夾，方法是根據現有範本建立新的假設，並將其連結至現有傳遞。
* 透過 **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 定位字元。
* 透過 **[!UICONTROL Measurement]** 從行銷活動建立的傳遞選項。

只有在啟動行銷活動且收件者已收到傳遞後，才能計算假設。 如果假設是根據優惠方案主張，則後者至少需要呈現，並且仍然有效。 優惠和傳遞假設是透過以下方式建立： **[!UICONTROL Measurement hypotheses]** 資料夾為基礎，並以假設範本為基礎。 不過，您可以在行銷活動開始之前，直接在傳送或行銷活動中參考假設。 在這種情況下，一旦行銷活動啟動，系統會根據執行設定自動計算假設。 [了解更多](hypothesis-templates.md#hypothesis-template-execution-settings)

## 在傳遞中即時建立假設 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

若要在現有傳遞上建立假設，請套用下列程式：

>[!NOTE]
>
>此作業僅適用於待處理的傳遞。

1. 在Adobe Campaign樹中，前往 **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. 按一下 **[!UICONTROL New]** 按鈕或以滑鼠右鍵按一下假設清單，然後選取 **[!UICONTROL New]** ，位於下拉式清單中。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假設視窗中，選取先前建立的範本。 [了解更多](hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所選模型中定義的假設前後關聯會顯示在視窗中。

   >[!NOTE]
   >
   >範本中定義且在此步驟中不可見的設定也會保留在記憶體中，並重新指派給進行中的假設。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 選取您要建立假設的傳遞。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以透過編輯 **[!UICONTROL General]**， **[!UICONTROL Transactions]** 和 **[!UICONTROL Scope]** 索引標籤。 [了解更多](hypothesis-templates.md#creating-a-hypothesis-model)
1. 按一下以開始假設 **[!UICONTROL Start]**.

   系統會自動建立工作流程以執行測量。 系統會根據假設組態自動定義名稱。

   >[!CAUTION]
   >
   >如果您已核取 **[!UICONTROL Keep execution workflow]** 方塊。\
   >此選項僅能用於偵錯，以防執行假設時發生錯誤。 自動產生的工作流程會儲存在 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 資料夾中的「Adobe Campaign總管」。
   > 
   >此外，不得修改自動產生的工作流程。 在之後的計算中，任何最終修改都不會在其他地方被考慮。
   >
   >如果您已核取此選項，請在工作流程執行後將其刪除。

   ![](assets/response_hypothesis_instance_creation_006.png)

   計算完成後，測量指標會自動更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，請變更設定並重新啟動假設。

## 在行銷活動傳遞中參考假設 {#referencing-a-hypothesis-in-a-campaign-delivery}

您可以在行銷活動開始之前，先在行銷活動中參考假設。 在這種情況下，一旦傳送傳遞，就會根據假設範本中定義的執行設定，自動啟動假設。 若要在傳遞中建立假設，請套用下列程式：

1. 您可以視需要建立一或多個 **[!UICONTROL Delivery]** 型別範本，如所述 [本節](hypothesis-templates.md#creating-a-hypothesis-model)
1. 建立行銷活動和目標定位工作流程。
1. 在傳送視窗中，按一下 **[!UICONTROL Delivery measurement]** 圖示。
1. 選取假設範本（在模型中設定的查詢會顯示在假設視窗中）。

   行銷活動完成後，系統會根據模型中設定的日期，自動計算假設。 [了解更多](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## 將預設假設新增至行銷活動的傳遞 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以在行銷活動層級直接參考假設。 在此情況下，假設會自動連結至行銷活動中建立的所有傳送。 操作步驟：

1. 前往 **[!UICONTROL Edit]** 行銷活動的索引標籤。
1. 在測量區段中，按一下 **[!UICONTROL Default hypotheses]** 標籤。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 按一下 **[!UICONTROL Add]** 並選取假設範本。

   ![](assets/response_hypothesis_instance_creation_011.png)

   根據此範本的假設，現在預設會在行銷活動的每個新傳遞中參照。

   ![](assets/response_hypothesis_instance_creation_012.png)

假設結果可在以下專案中檢視： **[!UICONTROL General]** 和 **[!UICONTROL Reactions]** 假設的索引標籤。 [了解更多](hypothesis-tracking.md)

如需詳細資訊，您也可以參閱 [此範例](#example--creating-a-hypothesis-linked-to-a-delivery).

## 在優惠方案上建立假設 {#creating-a-hypothesis-on-an-offer}

在優惠方案主張上建立假設，類似於建立即時傳遞假設。 只要優惠方案有效，就可以執行假設。 計算期間以優惠方案主張日期為基礎。 當假設可讓您將收件者連結至購買時，可能會被接受的優惠方案主張的狀態可以自動變更。 [了解更多](hypothesis-templates.md#transactions)

1. 建立一或多個 **[!UICONTROL Offer]** 鍵入模型，如中所述 [本節](hypothesis-templates.md#creating-a-hypothesis-model).
1. 前往 **[!UICONTROL Campaign management > Measurement hypotheses]** 節點。
1. 建立 **[!UICONTROL Offers]** 選取先前建立的模型，輸入假設。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中建立的查詢會出現在視窗中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 選擇要建立假設的優惠方案。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 視需要調整查詢。
1. 按一下 **[!UICONTROL Start]** 以執行假設。
1. 假設結果可以在以下專案中檢視： **[!UICONTROL General]** 和 **[!UICONTROL Reactions]** 索引標籤。 [了解更多](hypothesis-tracking.md)

   對優惠方案所做的假設會在以下連結中參照： **[!UICONTROL Measurement]** 標籤。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果 **[!UICONTROL Update offer proposition status]** 已在假設範本中啟用選項，優惠方案主張的狀態會自動變更，從而提供行銷活動影響的意見回饋(如需詳細資訊，請參閱 [交易](hypothesis-templates.md#transactions))。

## 範例：建立連結至傳遞的假設 {#example--creating-a-hypothesis-linked-to-a-delivery}

在此範例中，我們要建立連結至傳送的假設。 此假設將以先前建立的模型為基礎。 [了解更多](hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)

然後，我們將調整從模型繼承的查詢，以針對購買表格的特定文章提出假設。

1. 建立行銷活動和傳遞。 [了解更多](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)

   在我們的範例中，我們將使用直接郵件型別傳遞。

1. 設定種子地址：先前建立的假設範本已設定為在反應結果中考慮控制組。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >如需詳細資訊，請參閱[本區段](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 開啟 **[!UICONTROL Direct mail delivery]** 並按一下 **[!UICONTROL Delivery measurement]** 圖示，然後按一下 **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 從下拉式清單中選擇先前建立的假設範本。

   ![](assets/response_hypothesis_delivery_example_004.png)

   將顯示在模型中建立的查詢。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 按一下 **[!UICONTROL Edit query...]** 並輸入假設所關注的產品以縮小查詢。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以在以下位置中檢查該假設是否連結至傳遞： **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** 行銷活動的索引標籤。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 啟動您的目標定位工作流程，並執行必要的檢查，直到行銷活動完成為止。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign樹中，前往 **[!UICONTROL Campaign management > Measurement hypotheses]** 節點，以檢查由假設計算的指標。

   ![](assets/response_hypothesis_delivery_example_010.png)
