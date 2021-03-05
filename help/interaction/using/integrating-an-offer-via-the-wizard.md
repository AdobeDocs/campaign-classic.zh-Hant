---
solution: Campaign Classic
product: campaign
title: 透過精靈整合優惠方案
description: 透過精靈整合優惠方案
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---


# 透過精靈整合優惠方案{#integrating-an-offer-via-the-wizard}

建立傳送時，有兩種可能的整合選件方法：

* 在傳送內文呼叫選件引擎。
* 透過促銷活動的傳送大綱來參照選件。 此方法通常用於紙本促銷活動。

## 呼叫選件引擎進行傳送{#delivering-with-a-call-to-the-offer-engine}

若要在行銷促銷活動期間呈現選件，只需根據所選的渠道建立傳統的傳送動作。 定義傳送內容時，會按一下工具列中的&#x200B;**[!UICONTROL Offers]**&#x200B;圖示，呼叫選件引擎。

![](assets/offer_delivery_009.png)

在本節](../../delivery/using/about-direct-mail-channel.md)中，進一步瞭解直接郵件傳送[。 在本節](../../campaign/using/setting-up-marketing-campaigns.md)中進一步瞭解行銷促銷活動[。

### 將選件插入傳送{#main-steps-for-inserting-an-offer-into-a-delivery}的主要步驟

若要將選件建議插入傳送，請套用下列步驟：

1. 在傳送視窗中，按一下「選件」圖示。

   ![](assets/offer_delivery_001.png)

1. 選取符合您選件環境的空間。

   ![](assets/offer_delivery_002.png)

1. 若要調整引擎選擇的選件，請選取要呈現的選件所屬類別，或選取一／多個主題。 我們建議一次只使用其中一個欄位，以避免超出限制。

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. 指定您要插入傳送內文的選件數目。

   ![](assets/offer_delivery_005.png)

1. 如有必要，請選擇&#x200B;**[!UICONTROL Exclude non-eligible recipients]**&#x200B;選項。 如需詳細資訊，請參閱[呼叫選件引擎](#parameters-for-calling-offer-engine)的參數。

   ![](assets/offer_delivery_006.png)

1. 如有必要，請選擇&#x200B;**[!UICONTROL Do not display anything if no offers are selected]**&#x200B;選項。 如需詳細資訊，請參閱[呼叫選件引擎](#parameters-for-calling-offer-engine)的參數。

   ![](assets/offer_delivery_007.png)

1. 使用合併欄位將屬性插入傳送內容。 可用的主張數取決於引擎調用的配置方式，其順序取決於選件的優先順序。

   ![](assets/offer_delivery_008.png)

1. 完成內容並照常傳送。

   ![](assets/offer_delivery_010.png)

### 呼叫選件引擎{#parameters-for-calling-offer-engine}的參數

* **[!UICONTROL Space]** :必須選取以啟用選件引擎的選件環境空間。
* **[!UICONTROL Category]** :選件排序的特定資料夾。如果未指定類別，除非選取主題，否則選件引擎會考量環境中包含的所有選件。
* **[!UICONTROL Themes]** :關鍵字。這些選件可當成篩選，讓您透過在一組類別中選取選件來調整要呈現的選件數量。
* **[!UICONTROL Number of propositions]** :引擎傳回的可插入傳送主體的選件數。如果未將選件插入訊息中，選件仍會產生，但不會顯示。
* **[!UICONTROL Exclude non-eligible recipients]** :此選項可讓您啟用或停用排除不符合資格選件的收件者。合格命題的數目可能低於所請求的命題數目。 如果勾選此方塊，則沒有足夠建議的收件者將會從傳送中排除。 如果您未選取此選項，這些收件者將不會被排除，但是他們將沒有要求數目的建議。
* **[!UICONTROL Do not display anything if no offer is selected]** :此選項可讓您選擇在其中一個陳述式不存在時如何處理訊息。選中此框後，不顯示缺少命題的表示，並且不會在此命題的消息中顯示任何內容。 如果未勾選此方塊，則訊息本身會在傳送期間取消，而收件者將不再收到任何訊息。

### 將選件提案插入傳送{#inserting-an-offer-proposition-into-a-delivery}

要呈現的選件的表示方式會透過合併欄位插入傳送的主體中。 在選件引擎呼叫的參數中定義命題數。

您可使用選件欄位將傳送內容個人化，或在電子郵件中，使用轉換功能。

![](assets/offer_delivery_011.png)

## 使用傳送大綱傳送{#delivering-with-delivery-outlines}

您也可以使用傳送外框在傳送中呈現選件。

有關傳送大綱的詳細資訊，請參閱[促銷活動- MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)指南。

1. 建立新促銷活動或存取現有促銷活動。
1. 透過促銷活動的&#x200B;**[!UICONTROL Edit]** > **[!UICONTROL Documents]**&#x200B;標籤存取傳送大綱。
1. 新增大綱，然後在大綱上按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL New]** > **[!UICONTROL Offer]**，再儲存促銷活動，以插入您想要的選件數。

   ![](assets/int_compo_offre1.png)

1. 建立您可存取其傳送大綱的傳送（例如，直接郵件傳送）。
1. 編輯傳送時，按一下&#x200B;**[!UICONTROL Select a delivery outline]**。

   >[!NOTE]
   >
   >視傳送類型而定，此選項可在&#x200B;**[!UICONTROL Properties]** > **[!UICONTROL Advanced]**&#x200B;功能表中找到（例如，電子郵件傳送）。

   ![](assets/int_compo_offre2.png)

1. 然後，您可以使用&#x200B;**[!UICONTROL Offers]**&#x200B;按鈕，設定選件空間以及要在傳送中顯示的選件數。

   ![](assets/int_compo_offre3.png)

1. 使用個人化欄位將主張新增至傳送內文（如需詳細資訊，請參閱[將選件提案插入傳送](#inserting-an-offer-proposition-into-a-delivery)區段），或在直接郵件傳送的情況下，編輯擷取檔案格式。

   將從交付大綱中引用的選件中選擇建議。

   >[!NOTE]
   >
   >只有當選件直接在傳送中產生時，才會將選件排名和權重的相關資訊儲存在提案表格中。

