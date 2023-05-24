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



優惠方案類別的建立只能在 **[!UICONTROL Design]** 環境。 它們會自動部署在 **[!UICONTROL Live]** 環境（亦即可供使用）中所建立/修改的選件獲核準時。 根據預設， **[!UICONTROL Design]** 環境包含可接收所有優惠方案的類別。 可以建立子類別以將階層新增至目錄選件。

對於每個類別，您可以定義適用日期，也就是類別中包含的優惠方案不再顯示給其目標的期間。 如果您希望優惠方案引擎選取特定類別的優惠方案作為優先順序，以更好地公開產品，例如，您可以藉由將乘數權重新增至類別，增加其在指定期間的權重。

若要建立其他類別，請套用下列步驟：

1. 前往 **[!UICONTROL Offer catalog]** 資料夾。

   ![](assets/offer_cat_create_001.png)

1. 按一下右鍵並選取 **[!UICONTROL Create a new "Offer category" folder]** 下拉式清單中的。

   ![](assets/offer_cat_create_002.png)

1. 重新命名類別。 您稍後可以使用編輯標籤 **[!UICONTROL General]** 標籤。

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >重複這些步驟，視需要建立儘可能多的類別。

   此後，您可以視需要：

   * 從以下日期指派適用日期： **[!UICONTROL Eligibility]** 標籤。

      ![](assets/offer_cat_create_004.png)

   * 輸入關鍵字以用來選取此類別中的優惠方案，使用 **[!UICONTROL Themes]** 欄位。

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >呼叫優惠方案引擎時，只會選取主題或類別符合引數的目錄部分。

   * 透過以下方式暫時性「提升」指定時段內類別的優惠方案權重： **[!UICONTROL Multiplier weight]** 欄位。

      ![](assets/offer_cat_create_006.png)

類別中包含的優惠方案控制面板上提供適用性規則的回顧。 若要檢視，請按一下 **[!UICONTROL Schedule and eligibility rules of the offer]** 連結。

![](assets/offer_create_006.png)
