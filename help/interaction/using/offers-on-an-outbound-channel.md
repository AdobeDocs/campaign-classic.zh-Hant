---
product: campaign
title: 傳出頻道上的優惠
description: 傳出頻道上的優惠
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 3%

---

# 傳出頻道上的優惠{#offers-on-an-outbound-channel}



## 電子郵件選件傳遞 {#email-offer-delivery}

在我們的資料庫中，有一個前往非洲的旅行優惠方案類別。 已設定每個優惠方案的適用性、內容與表示方式。 我們現在想要建立行銷活動，透過電子郵件呈現我們的優惠方案。

1. 建立行銷活動和目標定位工作流程。

   ![](assets/offer_delivery_example_001.png)

1. 編輯電子郵件傳遞，然後按一下 **[!UICONTROL Offers]** 圖示。

   ![](assets/offer_delivery_example_002.png)

1. 為您的優惠方案環境選擇符合假日的電子郵件空間。

   ![](assets/offer_delivery_example_003.png)

1. 選擇包含非洲旅行優惠方案的類別。

   ![](assets/offer_delivery_example_004.png)

1. 將傳送中的選件數量設定為兩個。

   ![](assets/offer_delivery_example_005.png)

1. 關閉Offer Management視窗，並建立您的傳遞內容。

   ![](assets/offer_delivery_example_006.png)

1. 使用功能表插入第一個優惠方案主張，並選擇HTML轉譯函式。

   ![](assets/offer_delivery_example_007.png)

1. 插入第二個優惠方案主張。

   ![](assets/offer_delivery_example_008.png)

1. 按一下 **[!UICONTROL Preview]** 若要在傳送中預覽您的優惠，請選取收件者，以便在他們收到優惠時預覽優惠。

   ![](assets/offer_delivery_example_009.png)

1. 儲存您的傳送並啟動目標定位工作流程。
1. 開啟您的傳遞，然後按一下 **[!UICONTROL Audit]** 傳遞的索引標籤：您可以看到優惠方案引擎已選取要從目錄中的各種優惠方案進行的主張。

   ![](assets/offer_delivery_example_010.png)

## 執行優惠方案模擬 {#perform-an-offer-simulation}

1. 在 **[!UICONTROL Profiles and Targets]** 索引標籤，按一下 **[!UICONTROL Simulations]** 連結，然後按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/offer_simulation_001.png)

1. 選擇標籤，並視需要指定執行設定。

   ![](assets/offer_simulation_example_002.png)

1. 儲存模擬。 然後會在新標籤中開啟。

   ![](assets/offer_simulation_example_003.png)

1. 按一下 **[!UICONTROL Edit]** 標籤，然後 **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. 選擇要模擬優惠方案的類別。

   ![](assets/offer_simulation_example_005.png)

1. 選擇要用於模擬的優惠方案空間。

   ![](assets/offer_simulation_example_006.png)

1. 輸入有效日期。 您至少必須輸入開始日期。 這可讓優惠方案引擎篩選優惠方案，並選擇在指定日期有效的優惠方案。
1. 如有必要，請指定一或多個主題，將選件數量限製為設定中包含此關鍵字的選件數量。

   在我們的範例中， **旅遊** 類別包含兩個子類別，子類別有兩個獨立的主題。 我們想使用對優惠方案執行模擬 **客戶>1年** 主題。

   ![](assets/offer_simulation_example_007.png)

1. 選擇您要鎖定的收件者。

   ![](assets/offer_simulation_example_008.png)

1. 設定要傳送給每個收件者的優惠方案數量。

   在我們的範例中，優惠方案引擎會為每個收件者選擇權重最高的3個優惠方案。

   ![](assets/offer_simulation_example_009.png)

1. 儲存您的設定，然後按一下 **[!UICONTROL Start]** 在 **[!UICONTROL Dashboard]** 標籤以執行模擬。

   ![](assets/offer_simulation_example_010.png)

1. 模擬完成後，請查閱 **[!UICONTROL Results]** 以取得每個優惠方案主張的詳細劃分。

   在我們的範例中，優惠方案引擎是根據3個主張進行優惠方案劃分。

   ![](assets/offer_simulation_example_011.png)

1. 顯示 **[!UICONTROL Breakdown of offers by rank]** 以檢視優惠方案引擎選取的優惠方案清單。

   ![](assets/offer_simulation_example_012.png)

1. 如有必要，您可以變更範圍設定，然後按一下以再次執行模擬 **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. 若要儲存模擬資料，請使用報表中可用的歷史記錄或匯出函式。

   ![](assets/offer_simulation_example_013.png)
