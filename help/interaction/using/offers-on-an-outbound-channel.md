---
solution: Campaign Classic
product: campaign
title: 對出頻道上的優惠方案
description: 對出頻道上的優惠方案
audience: interaction
content-type: reference
topic-tags: case-study
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 3%

---


# 對出頻道上的優惠方案{#offers-on-an-outbound-channel}

## 電子郵件選件傳送{#email-offer-delivery}

在我們的資料庫中，有一類旅行優惠是去非洲。 已設定每個選件的資格、上下文和表示法。 我們現在想要建立促銷活動，透過電子郵件呈現我們的選件。

1. 建立行銷促銷活動和定位工作流程。

   ![](assets/offer_delivery_example_001.png)

1. 編輯電子郵件傳送，然後按一下&#x200B;**[!UICONTROL Offers]**&#x200B;圖示。

   ![](assets/offer_delivery_example_002.png)

1. 選擇符合節假日的選件環境電子郵件空間。

   ![](assets/offer_delivery_example_003.png)

1. 選擇包含非洲旅遊優惠的類別。

   ![](assets/offer_delivery_example_004.png)

1. 將傳送中的選件數設為2。

   ![](assets/offer_delivery_example_005.png)

1. 關閉選件管理視窗，並建立傳送的內容。

   ![](assets/offer_delivery_example_006.png)

1. 使用功能表插入第一個選件提案並選擇HTML轉換功能。

   ![](assets/offer_delivery_example_007.png)

1. 插入第二個選件提案。

   ![](assets/offer_delivery_example_008.png)

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;以在傳送中預覽選件，然後選取收件者以在收到選件時預覽選件。

   ![](assets/offer_delivery_example_009.png)

1. 儲存您的傳送並啟動定位工作流程。
1. 開啟您的傳送，然後按一下傳送的&#x200B;**[!UICONTROL Audit]**&#x200B;標籤：您可以看到選件引擎已從目錄中的各種選件中選取要提出的建議。

   ![](assets/offer_delivery_example_010.png)

## 執行選件模擬{#perform-an-offer-simulation}

1. 在&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Simulations]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

   ![](assets/offer_simulation_001.png)

1. 選擇標籤並指定執行設定（如有需要）。

   ![](assets/offer_simulation_example_002.png)

1. 儲存模擬。 然後，在新標籤中開啟。

   ![](assets/offer_simulation_example_003.png)

1. 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;頁籤，然後按一下&#x200B;**[!UICONTROL Scope]**。

   ![](assets/offer_simulation_example_004.png)

1. 選擇您要模擬選件的類別。

   ![](assets/offer_simulation_example_005.png)

1. 選擇要用於模擬的選件空間。

   ![](assets/offer_simulation_example_006.png)

1. 輸入有效日期。 您必須至少輸入開始日期。 這可讓選件引擎篩選選件，並選擇在指定日期有效的選件。
1. 如有必要，請指定一或多個主題，將選件數限制為設定中包含此關鍵字的選件數。

   在我們的範例中，**Travel**&#x200B;類別包含兩個具有兩個不同主題的子類別。 我們想要運用&#x200B;**Customers>1年**&#x200B;主題對選件進行模擬。

   ![](assets/offer_simulation_example_007.png)

1. 選擇要定位的收件者。

   ![](assets/offer_simulation_example_008.png)

1. 設定要傳送給每個收件者的選件數。

   在我們的範例中，選件引擎會為每個收件者選擇3個具有最大權重的選件。

   ![](assets/offer_simulation_example_009.png)

1. 儲存您的設定，然後按一下&#x200B;**[!UICONTROL Dashboard]**&#x200B;標籤中的&#x200B;**[!UICONTROL Start]**&#x200B;以執行模擬。

   ![](assets/offer_simulation_example_010.png)

1. 模擬完成後，請參閱&#x200B;**[!UICONTROL Results]**&#x200B;以取得每個選件的主張詳細劃分資訊。

   在我們的範例中，選件引擎以3個選件劃分為基礎。

   ![](assets/offer_simulation_example_011.png)

1. 顯示&#x200B;**[!UICONTROL Breakdown of offers by rank]**&#x200B;以檢視選件引擎所選的選件清單。

   ![](assets/offer_simulation_example_012.png)

1. 如有必要，可以通過按一下&#x200B;**[!UICONTROL Start simulation]**&#x200B;來更改範圍設定並再次運行模擬。

   ![](assets/offer_simulation_example_010.png)

1. 若要儲存模擬資料，請使用報表中可用的步驟記錄或匯出功能。

   ![](assets/offer_simulation_example_013.png)

