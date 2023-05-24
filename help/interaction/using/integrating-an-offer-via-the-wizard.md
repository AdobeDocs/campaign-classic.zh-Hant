---
product: campaign
title: 透過精靈整合優惠方案
description: 透過精靈整合優惠方案
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 64aea8b9-7f06-4db0-a3e6-6a0e17c3ddcb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---

# 透過精靈整合優惠方案{#integrating-an-offer-via-the-wizard}



建立傳送時，有兩種整合優惠方案的方法：

* 在傳遞內文中呼叫優惠方案引擎。
* 透過行銷活動的傳遞大網參考優惠方案。 此方法通常用於紙張行銷活動。

## 透過呼叫優惠方案引擎進行傳遞 {#delivering-with-a-call-to-the-offer-engine}

若要在行銷活動期間呈現優惠方案，只需根據所選管道建立傳統傳遞動作即可。 定義傳遞內容時，按一下「 」，系統會呼叫優惠方案引擎 **[!UICONTROL Offers]** 圖示加以存取。

![](assets/offer_delivery_009.png)

進一步瞭解直接郵件傳送 [在本節中](../../delivery/using/about-direct-mail-channel.md). 進一步瞭解行銷活動 [在本節中](../../campaign/using/setting-up-marketing-campaigns.md).

### 將優惠方案插入傳遞的主要步驟 {#main-steps-for-inserting-an-offer-into-a-delivery}

若要將優惠方案主張插入傳遞中，請套用下列步驟：

1. 在傳送視窗中，按一下優惠方案圖示。

   ![](assets/offer_delivery_001.png)

1. 選取符合優惠方案環境的空間。

   ![](assets/offer_delivery_002.png)

1. 若要調整引擎對優惠方案的選擇，請選取要呈現的優惠方案所屬類別，或選取一/數個主題。 我們建議一次只使用其中一個欄位，以避免多載限制。

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. 指定您要插入傳遞內文的選件數目。

   ![](assets/offer_delivery_005.png)

1. 選取 **[!UICONTROL Exclude non-eligible recipients]** 選項（如有需要）。 有關詳細資訊，請參閱 [用於呼叫優惠方案引擎的引數](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. 如有必要，請選取 **[!UICONTROL Do not display anything if no offers are selected]** 選項。 有關詳細資訊，請參閱 [用於呼叫優惠方案引擎的引數](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. 使用合併欄位將屬性插入傳遞內容。 可用主張的數量取決於引擎呼叫的設定方式，而其順序則取決於優惠方案的優先順序。

   ![](assets/offer_delivery_008.png)

1. 照常完成內容並傳送您的傳遞。

   ![](assets/offer_delivery_010.png)

### 用於呼叫優惠方案引擎的引數 {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** ：必須選取優惠方案環境的空間，才能啟用優惠方案引擎。
* **[!UICONTROL Category]** ：優惠排序所在的特定資料夾。 如果未指定類別，則優惠方案引擎將會考慮環境中包含的所有優惠方案，除非選取了主題。
* **[!UICONTROL Themes]** ：類別中上游定義的關鍵字。 這些可作為篩選條件，讓您藉由在一組類別中選取優惠方案，調整要呈現的優惠方案數量。
* **[!UICONTROL Number of propositions]** ：引擎傳回的可插入傳遞內文的優惠方案數。 如果未插入訊息中，仍會產生優惠，但不會顯示。
* **[!UICONTROL Exclude non-eligible recipients]** ：此選項可讓您針對沒有足夠的合格優惠方案來啟用或停用收件者排除功能。 合格主張的數量可能低於要求的主張數量。 如果核取此方塊，則沒有足夠主張的收件者將會從傳遞中排除。 如果您未選取此選項，這些收件者將不會被排除，但他們不會有要求的建議數量。
* **[!UICONTROL Do not display anything if no offer is selected]** ：此選項可讓您選擇當其中一個主張不存在時，如何處理訊息。 核取此方塊時，不會顯示缺少主張的表現，且此主張的訊息中不會出現任何內容。 如果未核取此方塊，訊息本身會在傳送期間取消，收件者將不再接收任何訊息。

### 在傳遞中插入優惠方案主張 {#inserting-an-offer-proposition-into-a-delivery}

要呈現的優惠方案會透過合併欄位插入傳遞的正文中。 主張的數量會在優惠方案引擎呼叫的引數中定義。

您可以使用優惠的欄位或轉譯函式（若是電子郵件）將傳送個人化。

![](assets/offer_delivery_011.png)

## 透過傳遞大網傳遞 {#delivering-with-delivery-outlines}

您也可以使用傳遞大綱，在傳遞中顯示優惠方案。

如需傳遞大網的詳細資訊，請參閱 [行銷活動 — MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) 指南。

1. 建立新行銷活動或存取現有行銷活動。
1. 透過行銷活動的存取傳遞大網 **[!UICONTROL Edit]** > **[!UICONTROL Documents]** 標籤。
1. 新增大綱，然後以滑鼠右鍵按一下大綱並選取「 」，將任意數目的選件插入大綱 **[!UICONTROL New]** > **[!UICONTROL Offer]**，然後儲存行銷活動。

   ![](assets/int_compo_offre1.png)

1. 建立您有權存取其傳遞大綱的傳遞（例如，直接郵件傳遞）。
1. 編輯傳送時，按一下 **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >根據傳送型別，此選項可在以下連結中找到： **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** 功能表（例如用於電子郵件傳送）。

   ![](assets/int_compo_offre2.png)

1. 使用 **[!UICONTROL Offers]** 按鈕後，您就可以設定優惠方案空間，以及要在傳送中呈現的優惠方案數量。

   ![](assets/int_compo_offre3.png)

1. 使用個人化欄位將主張新增至傳遞內文(如需詳細資訊，請參閱 [在傳遞中插入優惠方案主張](#inserting-an-offer-proposition-into-a-delivery) 區段)，或在直接郵件傳遞的情況下，透過編輯擷取檔案格式來進行。

   將從傳遞大網中參照的優惠方案中選取主張。

   >[!NOTE]
   >
   >如果優惠直接在傳送中產生，則優惠排名和權重的相關資訊只會儲存在主張表格中。
