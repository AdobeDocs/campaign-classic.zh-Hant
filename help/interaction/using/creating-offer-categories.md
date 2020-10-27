---
title: 建立優惠方案類別
seo-title: 建立優惠方案類別
description: 建立優惠方案類別
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 4%

---


# 建立優惠方案類別{#creating-offer-categories}

選件類別的建立只能在環境中 **[!UICONTROL Design]** 進行。 當所建立／修改的選 **[!UICONTROL Live]** 件獲得核準時，這些選件會自動部署在環境中（亦即已提供）。 依預設，環境 **[!UICONTROL Design]** 包含接收所有選件的類別。 可建立子類別，以新增階層至目錄選件。

您可以針對每個類別定義資格日期，亦即類別中包含的選件可能不再呈現給其目標的期間。 如果您希望選件引擎將特定類別的選件選為優先順序，例如，為了更好地公開產品，您可以新增乘冪至類別，以增加特定期間的加權。

若要建立其他類別，請套用下列步驟：

1. Go to the **[!UICONTROL Offer catalog]** folder.

   ![](assets/offer_cat_create_001.png)

1. 在下拉式清單中 **[!UICONTROL Create a new "Offer category" folder]** 按一下滑鼠右鍵並加以選取。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用標籤來編輯標 **[!UICONTROL General]** 簽。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，以視需要建立多個類別。

   之後，您可以視需要：

   * 從標籤指派資格 **[!UICONTROL Eligibility]** 日期。

      ![](assets/offer_cat_create_004.png)

   * 使用欄位，輸入可用於在此類別中選擇選件的關鍵字 **[!UICONTROL Themes]** 詞。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >呼叫選件引擎時，只會選取主題或類別符合參數的目錄部分。

   * 透過欄位暫時「提升」特定時段內類別的選件 **[!UICONTROL Multiplier weight]** 權重。

      ![](assets/offer_cat_create_006.png)

在類別所包含的選件儀表板中，可以重新檢視資格規則。 若要檢視，請按一下連 **[!UICONTROL Schedule and eligibility rules of the offer]** 結。

![](assets/offer_create_006.png)

