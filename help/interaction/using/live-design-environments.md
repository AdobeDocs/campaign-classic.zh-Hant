---
solution: Campaign Classic
product: campaign
title: 即時/設計環境
description: 即時/設計環境
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


# 即時/設計環境{#live-design-environments}

## 操作原則 {#operating-principle}

互動可與兩種選件環境運作：

* **[!UICONTROL Design]** 包含正在編輯且可加以變更之選件的選件環境。這些優惠尚未經過核准週期，也未傳送給聯絡人。
* **[!UICONTROL Live]** 選件環境，當已核准的選件顯示給聯絡人時，這些選件環境便會包含在內。此環境中的選件為唯讀。

![](assets/offer_environments_overview_001.png)

每個&#x200B;**[!UICONTROL Design]**&#x200B;環境都與&#x200B;**[!UICONTROL Live]**&#x200B;環境連結。 當選件完成時，其內容和資格規則會受到核准週期的約束。 完成此循環後，相關選件會自動部署至&#x200B;**[!UICONTROL Live]**&#x200B;環境。 從現在開始，它將可供交付。

預設情況下，交互附帶有&#x200B;**[!UICONTROL Design]**&#x200B;環境和&#x200B;**[!UICONTROL Live]**&#x200B;環境。 這兩個環境都已預先設定為定位現成可用的收件者表格。

>[!NOTE]
>
>若要定位其他表格（匿名選件的訪客表格或特定收件者表格），您必須使用定位對應精靈來建立環境。 有關詳細資訊，請參閱[建立選件環境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

選件管理員和傳送管理員可存取不同的環境檢視。 傳送管理員只能檢視&#x200B;**[!UICONTROL Live]**&#x200B;選件環境，並使用選件來傳送。 選件管理員可以檢視和變更&#x200B;**[!UICONTROL Design]**&#x200B;環境，並檢視&#x200B;**[!UICONTROL Live]**&#x200B;環境。 有關詳細資訊，請參閱[Operator profiles](../../interaction/using/operator-profiles.md)。

## 建立選件環境{#creating-an-offer-environment}

依預設，互動隨附預先設定的環境，以定位收件者表格（已識別的選件）。 如果您想要定位另一個表格（匿名選件的訪客表格或特定收件者表格），則需要套用下列組態：

1. 將游標置於&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**&#x200B;節點上。 以滑鼠右鍵按一下您要使用的傳送對應（如果您要使用匿名選件，請按&#x200B;**[!UICONTROL Visitors]**），然後選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;繼續嚮導中的下一個螢幕，選中&#x200B;**[!UICONTROL Generate a storage schema for propositions]**&#x200B;框並按一下&#x200B;**[!UICONTROL Save]**。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果該框已勾選，請取消選中該框，然後重新勾選。

1. Adobe Campaign會建立兩個環境（**[!UICONTROL Design]**&#x200B;和&#x200B;**[!UICONTROL Live]**），其中包含先前啟用之目標對應的定位資訊。 環境已預先配置了定位資訊。

   如果已激活&#x200B;**[!UICONTROL Visitor]**&#x200B;映射，則&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;框將自動選中環境的&#x200B;**[!UICONTROL General]**&#x200B;頁籤。

   此選項可讓您啟用匿名互動的特定功能，尤其是在設定環境提供空格時。 您也可以設定選項，讓您從「已識別」環境切換至「匿名」環境。

   例如，您可以將收件者環境選件空間（已識別的連絡人）與符合訪客環境（未識別的連絡人）的選件空間連結。 這樣，根據是否已識別聯繫人，將向聯繫人提供不同的選件。 有關詳細資訊，請參閱[建立選件空間](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>有關傳入渠道上的匿名交互的詳細資訊，請參閱[匿名交互](../../interaction/using/anonymous-interactions.md)。

