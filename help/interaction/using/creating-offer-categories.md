---
solution: Campaign Classic
product: campaign
title: 建立優惠方案類別
description: 建立優惠方案類別
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# 建立優惠方案類別{#creating-offer-categories}

選件類別的建立只能在&#x200B;**[!UICONTROL Design]**&#x200B;環境中進行。 當其包含的已建立／修改選件獲得批准時，這些選件會自動部署在&#x200B;**[!UICONTROL Live]**&#x200B;環境中（亦即已提供）。 依預設，**[!UICONTROL Design]**&#x200B;環境包含接收所有選件的類別。 可建立子類別，以新增階層至目錄選件。

您可以針對每個類別定義資格日期，亦即類別中包含的選件可能不再呈現給其目標的期間。 如果您希望選件引擎將特定類別的選件選為優先順序，例如，為了更好地公開產品，您可以新增乘冪至類別，以增加特定期間的加權。

若要建立其他類別，請套用下列步驟：

1. 前往&#x200B;**[!UICONTROL Offer catalog]**&#x200B;資料夾。

   ![](assets/offer_cat_create_001.png)

1. 按一下右鍵並從下拉清單中選擇&#x200B;**[!UICONTROL Create a new "Offer category" folder]**。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用&#x200B;**[!UICONTROL General]**&#x200B;標籤編輯標籤。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，以視需要建立多個類別。

   之後，您可以視需要：

   * 從&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤指派資格日期。

      ![](assets/offer_cat_create_004.png)

   * 使用&#x200B;**[!UICONTROL Themes]**&#x200B;欄位，輸入可用於從此類別中選擇選件的關鍵字。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >呼叫選件引擎時，只會選取主題或類別符合參數的目錄部分。

   * 透過&#x200B;**[!UICONTROL Multiplier weight]**&#x200B;欄位，暫時「提升」特定期間類別的選件權重。

      ![](assets/offer_cat_create_006.png)

在類別所包含的選件儀表板中，可以重新檢視資格規則。 若要檢視，請按一下&#x200B;**[!UICONTROL Schedule and eligibility rules of the offer]**&#x200B;連結。

![](assets/offer_create_006.png)

