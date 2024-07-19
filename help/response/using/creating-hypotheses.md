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

* 透過&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;資料夾，根據現有範本建立新的假設，並將其連結至現有傳遞。
* 透過行銷活動中的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;索引標籤。
* 透過從行銷活動建立的傳遞的&#x200B;**[!UICONTROL Measurement]**&#x200B;選項。

只有在啟動行銷活動且收件者已收到傳遞後，才能計算假設。 如果假設是根據優惠方案主張，則後者至少需要呈現，並且仍然有效。 優惠和傳遞假設是透過&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;資料夾建立，並以假設範本為基礎。 不過，您可以在行銷活動開始之前，直接在傳送或行銷活動中參考假設。 在這種情況下，一旦行銷活動啟動，系統會根據執行設定自動計算假設。 [了解更多](hypothesis-templates.md#hypothesis-template-execution-settings)

## 在傳遞中即時建立假設 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

若要在現有傳遞上建立假設，請套用下列程式：

>[!NOTE]
>
>此作業僅適用於待處理的傳遞。

1. 在Adobe Campaign樹狀結構中，移至&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 按一下「**[!UICONTROL New]**」按鈕，或在假設清單上按一下滑鼠右鍵，然後在下拉式清單中選取&#x200B;**[!UICONTROL New]**。

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

1. 您可以編輯&#x200B;**[!UICONTROL General]**、**[!UICONTROL Transactions]**&#x200B;和&#x200B;**[!UICONTROL Scope]**&#x200B;標籤，以個人化您的假設。 [了解更多](hypothesis-templates.md#creating-a-hypothesis-model)
1. 按一下&#x200B;**[!UICONTROL Start]**&#x200B;開始假設。

   系統會自動建立工作流程以執行測量。 系統會根據假設組態自動定義名稱。

   >[!CAUTION]
   >
   >如果您已勾選&#x200B;**[!UICONTROL Keep execution workflow]**&#x200B;方塊，則可存取此專案。\
   >此選項僅能用於偵錯，以防執行假設時發生錯誤。 自動產生的工作流程會儲存在Adobe Campaign檔案總管的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]**&#x200B;資料夾中。
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

1. 根據您的需求，您可以建立一或多個&#x200B;**[!UICONTROL Delivery]**&#x200B;型別範本，如[本節](hypothesis-templates.md#creating-a-hypothesis-model)所述
1. 建立行銷活動和目標定位工作流程。
1. 在傳遞視窗中，按一下&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;圖示。
1. 選取假設範本（在模型中設定的查詢會顯示在假設視窗中）。

   行銷活動完成後，系統會根據模型中設定的日期，自動計算假設。 [了解更多](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## 將預設假設新增至行銷活動的傳遞 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以在行銷活動層級直接參考假設。 在此情況下，假設會自動連結至行銷活動中建立的所有傳送。 操作步驟：

1. 前往行銷活動的&#x200B;**[!UICONTROL Edit]**&#x200B;標籤。
1. 在測量區段中，按一下&#x200B;**[!UICONTROL Default hypotheses]**&#x200B;標籤。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取假設範本。

   ![](assets/response_hypothesis_instance_creation_011.png)

   根據此範本的假設，現在預設會在行銷活動的每個新傳遞中參照。

   ![](assets/response_hypothesis_instance_creation_012.png)

可以在假設的&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;標籤中檢視假設結果。 [了解更多](hypothesis-tracking.md)

如需詳細資訊，您也可以參考[此範例](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 在優惠方案上建立假設 {#creating-a-hypothesis-on-an-offer}

在優惠方案主張上建立假設，類似於建立即時傳遞假設。 只要優惠方案有效，就可以執行假設。 計算期間以優惠方案主張日期為基礎。 當假設可讓您將收件者連結至購買時，可能會被接受的優惠方案主張的狀態可以自動變更。 [了解更多](hypothesis-templates.md#transactions)

1. 依照[本節](hypothesis-templates.md#creating-a-hypothesis-model)的說明，建立一或多個&#x200B;**[!UICONTROL Offer]**&#x200B;型別模型。
1. 前往&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;節點。
1. 選取先前建立的模型，以建立&#x200B;**[!UICONTROL Offers]**&#x200B;型別假設。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中建立的查詢會出現在視窗中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 選擇要建立假設的優惠方案。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 視需要調整查詢。
1. 按一下&#x200B;**[!UICONTROL Start]**&#x200B;以執行假設。
1. 可以在其&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;索引標籤中檢視假設結果。 [了解更多](hypothesis-tracking.md)

   對優惠方案所做的假設已在&#x200B;**[!UICONTROL Measurement]**&#x200B;索引標籤中參照。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果在假設範本中啟用了&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;選項，則優惠方案主張的狀態會自動變更，從而對行銷活動的影響提供回饋（如需詳細資訊，請參閱[交易](hypothesis-templates.md#transactions)）。

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

1. 開啟&#x200B;**[!UICONTROL Direct mail delivery]**&#x200B;並按一下&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 從下拉式清單中選擇先前建立的假設範本。

   ![](assets/response_hypothesis_delivery_example_004.png)

   將顯示在模型中建立的查詢。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 按一下&#x200B;**[!UICONTROL Edit query...]**，並輸入假設所關心的產品，以調整查詢。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以在行銷活動的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;索引標籤中檢查該假設是否連結至傳遞。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 啟動您的目標定位工作流程，並執行必要的檢查，直到行銷活動完成為止。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign樹狀結構中，前往&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;節點以檢查由假設所計算的指標。

   ![](assets/response_hypothesis_delivery_example_010.png)
