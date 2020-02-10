---
title: 即時／設計環境
seo-title: 即時／設計環境
description: 即時／設計環境
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 即時／設計環境{#live-design-environments}

## 操作原則 {#operating-principle}

互動可與兩種選件環境運作：

* **[!UICONTROL Design]** 包含正在編輯且可加以變更之選件的選件環境。 這些優惠尚未經過核准週期，也未傳送給聯絡人。
* **[!UICONTROL Live]** 選件環境，當已核准的選件顯示給聯絡人時，這些選件環境便會包含在內。 此環境中的選件為唯讀。

![](assets/offer_environments_overview_001.png)

每個 **[!UICONTROL Design]** 環境都與一個環境 **[!UICONTROL Live]** 連結。 當選件完成時，其內容和資格規則會受到核准週期的約束。 完成此週期後，相關選件會自動部署至環 **[!UICONTROL Live]** 境。 從現在開始，它將可供交付。

依預設，「互動」會隨附一 **[!UICONTROL Design]** 個與其連結 **[!UICONTROL Live]** 的環境和環境。 這兩個環境都已預先設定為定位現成可用的收件者表格。

>[!NOTE]
>
>若要定位其他表格（匿名選件的訪客表格或特定收件者表格），您必須使用定位對應精靈來建立環境。 如需詳細資訊，請參閱「 [建立選件環境」](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

選件管理員和傳送管理員可存取不同的環境檢視。 交付經理只能檢視選件環 **[!UICONTROL Live]** 境，並使用選件來傳送選件。 選件管理員可以檢視和變更環 **[!UICONTROL Design]** 境並檢視環 **[!UICONTROL Live]** 境。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## 建立選件環境 {#creating-an-offer-environment}

依預設，互動隨附預先設定的環境，以定位收件者表格（已識別的選件）。 如果您想要定位另一個表格（匿名選件的訪客表格或特定收件者表格），則需套用下列組態：

1. 將游標置於 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** >節 **[!UICONTROL Delivery mappings]** 點。 以滑鼠右鍵按一下您要使用的傳送對應(**[!UICONTROL Visitors]** 如果您想使用匿名選件)，然後選取 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 單 **[!UICONTROL Next]** 擊繼續嚮導中的下一個螢幕，選中該框並 **[!UICONTROL Generate a storage schema for propositions]** 按一下 **[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果該框已勾選，請取消選中該框，然後重新勾選。

1. Adobe Campaign會建立兩個環境(**[!UICONTROL Design]** 和 **[!UICONTROL Live]** )，其中包含先前啟用之定位對應的定位資訊。 環境已預先配置了定位資訊。

   如果已激活 **[!UICONTROL Visitor]** 映射，則 **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 該框將自動在環境的頁籤中被選 **[!UICONTROL General]** 中。

   此選項可讓您啟用匿名互動的特定功能，尤其是在設定環境提供空格時。 您也可以設定選項，讓您從「已識別」環境切換至「匿名」環境。

   例如，您可以將收件者環境選件空間（已識別的連絡人）與符合訪客環境（未識別的連絡人）的選件空間連結。 這樣，根據是否已識別聯繫人，將向聯繫人提供不同的選件。 如需詳細資訊，請參閱「建立選 [件空間」](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有關傳入渠道上匿名互動的詳細資訊，請參閱匿名 [互動](../../interaction/using/anonymous-interactions.md)。

