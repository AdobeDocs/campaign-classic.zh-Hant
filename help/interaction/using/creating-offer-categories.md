---
product: campaign
title: 建立優惠方案類別
description: 建立優惠方案類別
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 建立優惠方案類別{#creating-offer-categories}

![](../../assets/v7-only.svg)

選件類別的建立只能在&#x200B;**[!UICONTROL Design]**&#x200B;環境中進行。 核准所建立/修改的選件時，系統會自動部署在&#x200B;**[!UICONTROL Live]**&#x200B;環境中（即可供使用）。 依預設，**[!UICONTROL Design]**&#x200B;環境包含接收所有選件的類別。 可以建立子類別，將階層新增至目錄選件。

對於每個類別，您可以定義資格日期，即類別中包含的優惠方案可能不再呈現給其目標的期間。 如果您希望優惠方案引擎將特定類別的優惠方案選為優先順序，以便更妥善地公開產品，您可以將乘冪加到類別，以增加指定期間的加權。

要建立其他類別，請應用以下步驟：

1. 前往&#x200B;**[!UICONTROL Offer catalog]**&#x200B;資料夾。

   ![](assets/offer_cat_create_001.png)

1. 按一下右鍵，然後從下拉清單中選擇&#x200B;**[!UICONTROL Create a new "Offer category" folder]**。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用&#x200B;**[!UICONTROL General]**&#x200B;標籤來編輯標籤。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，視需要建立任意數量的類別。

   之後，您可視需要：

   * 從&#x200B;**[!UICONTROL Eligibility]**&#x200B;索引標籤指派資格日期。

      ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;欄位，輸入可用於從此類別中選取優惠方案的關鍵字。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >呼叫優惠方案引擎時，僅會選取主題或類別符合參數的目錄部分。

   * 透過&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;欄位暫時「提升」指定期間類別的選件權重。

      ![](assets/offer_cat_create_006.png)

資格規則的重述會顯示在類別中所包含優惠方案的控制面板上。 若要檢視，請按一下&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;連結。

![](assets/offer_create_006.png)
