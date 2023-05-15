---
product: campaign
title: 建立優惠方案類別
description: 建立優惠方案類別
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 建立優惠方案類別{#creating-offer-categories}



優惠方案類別的建立只能在 **[!UICONTROL Design]** 環境。 它們會自動部署在 **[!UICONTROL Live]** 環境（即當已建立/修改的選件獲得核準時）。 依預設， **[!UICONTROL Design]** 環境包含接收所有選件的類別。 可以建立子類別，將階層新增至目錄選件。

對於每個類別，您可以定義資格日期，即類別中包含的優惠方案可能不再呈現給其目標的期間。 如果您希望優惠方案引擎將特定類別的優惠方案選為優先順序，以便更妥善地公開產品，您可以將乘冪加到類別，以增加指定期間的加權。

要建立其他類別，請應用以下步驟：

1. 前往 **[!UICONTROL Offer catalog]** 檔案夾。

   ![](assets/offer_cat_create_001.png)

1. 按一下右鍵並選擇 **[!UICONTROL Create a new "Offer category" folder]** 從下拉式清單中。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用 **[!UICONTROL General]** 標籤。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，視需要建立任意數量的類別。

   之後，您可視需要：

   * 從 **[!UICONTROL Eligibility]** 標籤。

      ![](assets/offer_cat_create_004.png)

   * 使用 **[!UICONTROL Themes]** 欄位。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >呼叫優惠方案引擎時，僅會選取主題或類別符合參數的目錄部分。

   * 透過 **[!UICONTROL Multiplier weight]** 欄位。

      ![](assets/offer_cat_create_006.png)

資格規則的重述會顯示在類別中所包含優惠方案的控制面板上。 若要檢視，請按一下 **[!UICONTROL Schedule and eligibility rules of the offer]** 連結。

![](assets/offer_create_006.png)
