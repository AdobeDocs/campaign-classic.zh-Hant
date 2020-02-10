---
title: 建立假設
seo-title: 建立假設
description: 建立假設
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立假設{#creating-hypotheses}

建立／連結促銷活動選件或傳送的假設有多種可能：

* 透過資 **[!UICONTROL Measurement hypotheses]** 料夾，根據現有範本建立新假設，並將其連結至現有傳送。
* 透過促銷 **[!UICONTROL Edit]** 活動 **[!UICONTROL Measurement]** 中的>標籤。
* 透過從 **[!UICONTROL Measurement]** 促銷活動建立的傳送選項。

只有在行銷促銷活動啟動且收件者收到傳送後，才能計算假設。 如果假設是基於選件命題，則後者至少需要提出，而且仍然有效。 選件和傳送假設是經由資料夾 **[!UICONTROL Measurement hypotheses]** 建立，並以假設範本為基礎。 不過，在促銷活動開始之前，可以直接在傳送或促銷活動中參考假設。 在此情況下，一旦啟動行銷促銷活動，就會根據執行設定自動計算假設(如需詳細資訊，請參閱 [假設範本執行設定](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))。

## 在交貨時即時建立假設 {#creating-a-hypothesis-on-the-fly-on-a-delivery}

要在現有交貨上建立假設，請應用以下流程：

>[!NOTE]
>
>此操作僅適用於待定交貨。

1. 在Adobe Campaign樹狀結構中，前往 **[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 按一 **[!UICONTROL New]** 下按鈕或在假設清單上按一下滑鼠右鍵，然後 **[!UICONTROL New]** 在下拉式清單中選取。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假設窗口中，選擇以前建立的模板(請參閱 [假設模板](../../campaign/using/hypothesis-templates.md))。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所選模型中定義的假設上下文將顯示在窗口中。

   >[!NOTE]
   >
   >在模板中定義且在此步驟中不可見的設定也保留在記憶體中，並重新指派到正在進行的假設。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 選擇要為其建立假設的交貨。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以編輯和標籤，以個人化 **[!UICONTROL General]**&#x200B;您的 **[!UICONTROL Transactions]** 假設 **[!UICONTROL Scope]** 設定。 有關詳細資訊，請參閱 [建立假設模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 按一下即可開始假設 **[!UICONTROL Start]**。

   系統會自動建立工作流程以執行測量。 名稱會根據假設設定自動定義。

   >[!CAUTION]
   >
   >如果您已勾選方塊，則可以存取此 **[!UICONTROL Keep execution workflow]** 項。\
   >此選項必須僅用於除錯，以在執行假設時發生錯誤時啟用。 自動產生的工作流程會儲存在 **[!UICONTROL Administration]** Adobe Campaign檔案總管的> **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** 檔案夾中。
   > 
   >此外，自動產生的工作流程不得修改。 在以後的計算中，不會考慮其他地方的最終修改。
   >
   >如果您已勾選此選項，請在工作流執行後刪除它。

   ![](assets/response_hypothesis_instance_creation_006.png)

   計算完成後，測量指標會自動更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，請變更設定並重新啟動假設。

## 在促銷活動傳送中參照假設 {#referencing-a-hypothesis-in-a-campaign-delivery}

您可以在行銷促銷活動開始之前參考假設。 在此情況下，假設會根據假設範本中定義的執行設定，在傳送傳送後自動啟動。 若要在傳送中建立假設，請套用下列程式：

1. 視您的需求而定，您可以建立一或多個文字范 **[!UICONTROL Delivery]** 本，如建立假設模 [型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. 建立行銷促銷活動和定位工作流程。
1. 在傳送視窗中，按一下 **[!UICONTROL Delivery measurement]** 圖示。
1. 選取假設範本（模型中設定的查詢會顯示在假設視窗中）。

   促銷活動完成後，會根據模型中設定的日期自動計算假設(請參閱 [假設範本執行設定](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings))。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 新增促銷活動的傳送預設假設 {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

您可以直接在促銷活動層級參考假設。 在這種情況下，假設會自動連結至促銷活動中建立的所有傳送。 操作步驟：

1. 前往促銷 **[!UICONTROL Edit]** 活動的標籤。
1. 在測量區段中，按一下標 **[!UICONTROL Default hypotheses]** 簽。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 按一 **[!UICONTROL Add]** 下並選取假設範本。

   ![](assets/response_hypothesis_instance_creation_011.png)

   根據此範本的假設，現在會依預設在促銷活動的每個新傳送中參考。

   ![](assets/response_hypothesis_instance_creation_012.png)

假設結果可在假設的標 **[!UICONTROL General]** 簽和 **[!UICONTROL Reactions]** 標籤中檢視(請參閱 [假設追蹤](../../campaign/using/hypothesis-tracking.md))

如需詳細資訊，您也可以參閱 [範例：建立連結至遞送的假設](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 建立選件的假設 {#creating-a-hypothesis-on-an-offer}

建立選件提案的假設與建立即時傳送假設類似。 只要選件有效，就可以執行假設。 計算期間以優惠提案日期為基礎。 當假設可讓您將收件者連結至購買時，可能被接受的選件提案狀態會自動變更(如需詳細資訊，請參閱「交 [易](../../campaign/using/hypothesis-templates.md#transactions)」)。

1. 建立一個或多個 **[!UICONTROL Offer]** 類型模型，如建立假 [說模型中所述](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 轉至節 **[!UICONTROL Campaign management > Measurement hypotheses]** 點。
1. 選取先 **[!UICONTROL Offers]** 前建立的模型，建立類型假設。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中建立的查詢將出現在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 選擇您要建立假設的選件。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 視需要調整查詢。
1. 按一 **[!UICONTROL Start]** 下以執行假設。
1. 假設結果可在其標籤和標籤中 **[!UICONTROL General]** 檢視 **[!UICONTROL Reactions]** (請參閱 [假設追蹤](../../campaign/using/hypothesis-tracking.md))。

   選件上的假設在標籤中參 **[!UICONTROL Measurement]** 考。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果 **[!UICONTROL Update offer proposition status]** 在假設範本中啟用了選項，則選件提案的狀態會自動變更，從而提供對促銷活動影響的意見回應(如需詳細資訊，請參閱 [交易](../../campaign/using/hypothesis-templates.md#transactions))。

## 範例：建立與交付有關的假設 {#example--creating-a-hypothesis-linked-to-a-delivery}

在此範例中，我們想建立連結至遞送的假設。 此假設將基於先前建立的模型(請參 [閱：在傳送上建立假設範本](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery))。 然後，我們將細化從模型繼承的查詢，對購買表的特定文章進行假設。

1. 建立促銷活動和傳送(如需詳細資訊，請參閱建 [立促銷活動](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   在我們的範例中，我們將使用直接郵件類型傳送。

1. 配置種子地址：先前建立的假設範本設定為在反應結果中考慮控制群組。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有關詳細資訊，請參 [閱定義控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 開啟 **[!UICONTROL Direct mail delivery]** 並按一下圖 **[!UICONTROL Delivery measurement]** 示，然後按一下 **[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 從下拉式清單中選擇先前建立的假設範本。

   ![](assets/response_hypothesis_delivery_example_004.png)

   將顯示在模型中建立的查詢。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 按一 **[!UICONTROL Edit query...]** 下並調整查詢，方法是輸入假設所關注的產品。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以在促銷活動的「 >」標籤中檢查假設 **[!UICONTROL Edit]** 是否已 **[!UICONTROL Measurement]** 連結至傳送。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 啟動您的定位工作流程並執行必要的檢查，直到促銷活動完成(如需詳細資訊，請參 [閱啟動傳送](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign樹狀結構中，前往節 **[!UICONTROL Campaign management > Measurement hypotheses]** 點以檢查由假設計算的指標。

   ![](assets/response_hypothesis_delivery_example_010.png)

