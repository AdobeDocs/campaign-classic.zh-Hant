---
product: campaign
title: 建立優惠方案類別
description: 建立優惠方案類別
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 建立優惠方案類別{#creating-offer-categories}



優惠方案類別的建立只能在&#x200B;**[!UICONTROL Design]**&#x200B;環境中進行。 當它們包含的建立/修改選件獲得核準時，會自動部署在&#x200B;**[!UICONTROL Live]**&#x200B;環境中（亦即可供使用）。 依預設，**[!UICONTROL Design]**&#x200B;環境包含接收所有優惠方案的類別。 可以建立子類別以將階層新增至目錄優惠方案。

對於每個類別，您可以定義適用日期，也就是類別中包含的優惠方案不再顯示給其目標的期間。 如果您希望優惠方案引擎將特定類別的優惠方案選為優先順序，以更好地公開產品，例如，您可以對類別新增乘法加權，以增加其在指定期間的權重。

若要建立其他類別，請套用下列步驟：

1. 前往&#x200B;**[!UICONTROL Offer catalog]**&#x200B;資料夾。

   ![](assets/offer_cat_create_001.png)

1. 按一下滑鼠右鍵並從下拉式清單中選取&#x200B;**[!UICONTROL Create a new "Offer category" folder]**。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用&#x200B;**[!UICONTROL General]**&#x200B;索引標籤來編輯標籤。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，視需要建立儘可能多的類別。

   此後，您可以視需要：

   * 從&#x200B;**[!UICONTROL Eligibility]**&#x200B;索引標籤指派適用日期。

     ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;欄位，輸入可用於選取此類別中優惠方案的關鍵字。

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >呼叫優惠方案引擎時，只會選取主題或類別符合引數的目錄部分。

   * 透過&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;欄位在指定期間內暫時「提升」類別的優惠方案權重。

     ![](assets/offer_cat_create_006.png)

類別中包含的優惠方案控制面板上提供適用性規則的回顧。 若要檢視，請按一下&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;連結。

![](assets/offer_create_006.png)
