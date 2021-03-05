---
solution: Campaign Classic
product: campaign
title: 建立假設
description: 瞭解如何在促銷活動回應管理員中建立假設
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---


# 建立假設{#creating-hypotheses}

建立／連結促銷活動選件或傳送的假設有多種可能：

* 透過&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;資料夾，根據現有範本建立新假設並將其連結至現有傳送。
* 透過促銷活動中的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;標籤。
* 透過從促銷活動建立之傳送的&#x200B;**[!UICONTROL Measurement]**&#x200B;選項。

只有在行銷促銷活動啟動且收件者收到傳送後，才能計算假設。 如果假設是基於選件命題，則後者至少需要提出，而且仍然有效。 選件和傳送假設是透過&#x200B;**[!UICONTROL Measurement hypotheses]**&#x200B;資料夾建立，並以假設範本為基礎。 不過，在促銷活動開始之前，可以直接在傳送或促銷活動中參考假設。 在此例中，一旦啟動行銷促銷活動，就會根據執行設定自動計算假設（如需詳細資訊，請參閱[假設範本執行設定](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)）。

## 在傳送{#creating-a-hypothesis-on-the-fly-on-a-delivery}時即時建立假設

要在現有交貨上建立假設，請應用以下流程：

>[!NOTE]
>
>此操作僅適用於待定交貨。

1. 在Adobe Campaign樹中，轉至&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;按鈕或在假設清單上按滑鼠右鍵，然後在下拉式清單中選取&#x200B;**[!UICONTROL New]**。

   ![](assets/response_hypothesis_instance_creation_002.png)

1. 在假設窗口中，選擇以前建立的模板（請參閱[假設模板](../../campaign/using/hypothesis-templates.md)）。

   ![](assets/response_hypothesis_instance_creation_003.png)

   在所選模型中定義的假設上下文將顯示在窗口中。

   >[!NOTE]
   >
   >在模板中定義且在此步驟中不可見的設定也保留在記憶體中，並重新指派到正在進行的假設。

   ![](assets/response_hypothesis_instance_creation_004.png)

1. 選擇要為其建立假設的交貨。

   ![](assets/response_hypothesis_instance_creation_005.png)

1. 您可以編輯&#x200B;**[!UICONTROL General]**、**[!UICONTROL Transactions]**&#x200B;和&#x200B;**[!UICONTROL Scope]**&#x200B;標籤，以個人化您的假設。 有關詳細資訊，請參閱[建立假設模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 按一下&#x200B;**[!UICONTROL Start]**&#x200B;開始假設。

   系統會自動建立工作流程以執行測量。 名稱會根據假設設定自動定義。

   >[!CAUTION]
   >
   >如果選中了&#x200B;**[!UICONTROL Keep execution workflow]**&#x200B;框，則可以訪問此選項。\
   >此選項必須僅用於除錯，以在執行假設時發生錯誤時啟用。 自動生成的工作流將保存在Adobe Campaign資源管理器的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]**&#x200B;資料夾中。
   > 
   >此外，自動產生的工作流程不得修改。 在以後的計算中，不會考慮其他地方的最終修改。
   >
   >如果您已勾選此選項，請在工作流執行後刪除它。

   ![](assets/response_hypothesis_instance_creation_006.png)

   計算完成後，測量指標會自動更新。

   ![](assets/response_hypothesis_instance_creation_007.png)

1. 如有必要，請變更設定並重新啟動假設。

## 參考促銷活動傳送中的假設{#referencing-a-hypothesis-in-a-campaign-delivery}

您可以在行銷促銷活動開始之前參考假設。 在此情況下，假設會根據假設範本中定義的執行設定，在傳送傳送後自動啟動。 若要在傳送中建立假設，請套用下列程式：

1. 視您的需求而定，您可以建立一或多個&#x200B;**[!UICONTROL Delivery]**&#x200B;類型範本，如[本節](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)所述
1. 建立行銷促銷活動和定位工作流程。
1. 在傳送視窗中，按一下&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;圖示。
1. 選取假設範本（模型中設定的查詢會顯示在假設視窗中）。

   促銷活動完成後，會根據模型中設定的日期自動計算假設（請參閱[假設範本執行設定](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)）。

   ![](assets/response_hypothesis_instance_creation_008.png)

## 新增促銷活動{#adding-a-default-hypothesis-to-deliveries-for-a-campaign}的傳送預設假設

您可以直接在促銷活動層級參考假設。 在這種情況下，假設會自動連結至促銷活動中建立的所有傳送。 操作步驟：

1. 前往促銷活動的&#x200B;**[!UICONTROL Edit]**&#x200B;標籤。
1. 在測量區段中，按一下&#x200B;**[!UICONTROL Default hypotheses]**&#x200B;標籤。

   ![](assets/response_hypothesis_instance_creation_010.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取假設範本。

   ![](assets/response_hypothesis_instance_creation_011.png)

   根據此範本的假設，現在會依預設在促銷活動的每個新傳送中參考。

   ![](assets/response_hypothesis_instance_creation_012.png)

假設結果可在假設的&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;標籤中檢視（請參閱[假設追蹤](../../campaign/using/hypothesis-tracking.md)）

如需詳細資訊，您也可以參閱[此範例](#example--creating-a-hypothesis-linked-to-a-delivery)。

## 建立選件{#creating-a-hypothesis-on-an-offer}的假設

建立選件提案的假設與建立即時傳送假設類似。 只要選件有效，就可以執行假設。 計算期間以優惠提案日期為基礎。 當假設可讓您將收件者連結至購買時，可能會被接受的選件提案狀態可自動變更（如需詳細資訊，請參閱[Transactions](../../campaign/using/hypothesis-templates.md#transactions)）。

1. 按照[本節](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)所述，建立一個或多個&#x200B;**[!UICONTROL Offer]**&#x200B;類型模型。
1. 轉至&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;節點。
1. 選取先前建立的模型，建立&#x200B;**[!UICONTROL Offers]**&#x200B;類型假設。

   ![](assets/response_hypothesis_instance_offer_001.png)

   在模型中建立的查詢將出現在窗口中。

   ![](assets/response_hypothesis_instance_offer_003.png)

1. 選擇您要建立假設的選件。

   ![](assets/response_hypothesis_instance_offer_004.png)

1. 視需要調整查詢。
1. 按一下&#x200B;**[!UICONTROL Start]**&#x200B;以執行假設。
1. 假設結果可在其&#x200B;**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Reactions]**&#x200B;標籤中檢視（請參閱[假設追蹤](../../campaign/using/hypothesis-tracking.md)）。

   選件上的假設在&#x200B;**[!UICONTROL Measurement]**&#x200B;標籤中參考。

   ![](assets/response_hypothesis_instance_offer_007.png)

   如果假設範本中啟用了&#x200B;**[!UICONTROL Update offer proposition status]**&#x200B;選項，選件的狀態會自動變更，從而提供促銷活動影響的意見回應（如需詳細資訊，請參閱[Transactions](../../campaign/using/hypothesis-templates.md#transactions)）。

## 範例：建立連結至{#example--creating-a-hypothesis-linked-to-a-delivery}遞送的假設

在此範例中，我們想建立連結至遞送的假設。 此假設將以先前建立的模型為基礎（請參閱[此範例](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)）。 然後，我們將細化從模型繼承的查詢，對購買表的特定文章進行假設。

1. 建立促銷活動和傳送（如需詳細資訊，請參閱[建立行銷活動](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   在我們的範例中，我們將使用直接郵件類型傳送。

1. 配置種子地址：先前建立的假設範本設定為在反應結果中考慮控制群組。

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >有關詳細資訊，請參閱[定義控制組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

1. 開啟&#x200B;**[!UICONTROL Direct mail delivery]**&#x200B;並按一下&#x200B;**[!UICONTROL Delivery measurement]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/response_hypothesis_delivery_example_002.png)

1. 從下拉式清單中選擇先前建立的假設範本。

   ![](assets/response_hypothesis_delivery_example_004.png)

   將顯示在模型中建立的查詢。

   ![](assets/response_hypothesis_delivery_example_005.png)

1. 按一下&#x200B;**[!UICONTROL Edit query...]**，然後輸入假設所關注的產品以調整查詢。

   ![](assets/response_hypothesis_delivery_example_006.png)

   您可以在促銷活動的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Measurement]**&#x200B;標籤中檢查假設是否已連結至傳送。

   ![](assets/response_hypothesis_delivery_example_008.png)

1. 啟動您的定位工作流程並執行必要的檢查，直到促銷活動完成為止（如需詳細資訊，請參閱[本節](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)）。

   ![](assets/response_hypothesis_delivery_example_009.png)

1. 在Adobe Campaign樹中，轉至&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;節點檢查由假設計算的指示符。

   ![](assets/response_hypothesis_delivery_example_010.png)

