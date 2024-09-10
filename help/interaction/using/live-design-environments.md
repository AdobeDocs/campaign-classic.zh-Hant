---
product: campaign
title: 即時/設計環境
description: 即時/設計環境
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 即時/設計環境{#live-design-environments}



## 操作原則 {#operating-principle}

互動適用於兩種型別的優惠方案環境：

* **[!UICONTROL Design]**&#x200B;優惠方案環境，其中包含正在編輯且可以變更的優惠方案。 這些優惠方案尚未經過核准週期，因此不會傳送給連絡人。
* **[!UICONTROL Live]**&#x200B;優惠方案環境包含向連絡人展示的已核准優惠方案。 此環境中的選件是唯讀的。

![](assets/offer_environments_overview_001.png)

每個&#x200B;**[!UICONTROL Design]**&#x200B;環境都連結到&#x200B;**[!UICONTROL Live]**&#x200B;環境。 當優惠方案完成時，其內容和適用性規則會受限於核准週期。 此週期完成後，相關選件會自動部署至&#x200B;**[!UICONTROL Live]**&#x200B;環境。 從現在開始，該檔案將可供傳送。

依預設，互動會隨附一個&#x200B;**[!UICONTROL Design]**&#x200B;環境以及與其連結的&#x200B;**[!UICONTROL Live]**&#x200B;環境。 這兩個環境都已預先設定為鎖定內建的收件者表格。

>[!NOTE]
>
>若要鎖定其他表格（匿名選件的訪客表格或特定的收件者表格），您需要使用目標對應助理來建立環境。 如需詳細資訊，請參閱[建立優惠方案環境](#creating-an-offer-environment)。

![](assets/offer_environments_overview_002.png)

優惠方案管理員和傳遞管理員都可存取環境的不同檢視。 傳遞管理員只能檢視&#x200B;**[!UICONTROL Live]**&#x200B;優惠方案環境，並使用優惠方案進行傳遞。 優惠方案管理員可以檢視和變更&#x200B;**[!UICONTROL Design]**&#x200B;環境以及檢視&#x200B;**[!UICONTROL Live]**&#x200B;環境。 如需詳細資訊，請參閱[運運算元設定檔](../../interaction/using/operator-profiles.md)。

## 建立優惠方案環境 {#creating-an-offer-environment}

依預設，互動會隨附預先設定的環境，以鎖定收件者表格（已識別的優惠方案）。 如果您想要鎖定其他表格（匿名優惠方案的訪客表格或特定的收件者表格），則需要套用下列設定：

1. 將游標置於&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**&#x200B;節點上。 用滑鼠右鍵按一下您要使用的傳遞對應（**[!UICONTROL Visitors]**&#x200B;如果您想要使用匿名優惠），然後選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**。

   ![](assets/offer_env_anonymous_001.png)

1. 按一下「**[!UICONTROL Next]**」以繼續進入助理的下一個畫面，核取「**[!UICONTROL Generate a storage schema for propositions]**」方塊並按一下「**[!UICONTROL Save]**」。

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果已核取該方塊，請取消核取該方塊，然後重新核取它。

1. Adobe Campaign會使用先前啟用目標對應的目標定位資訊，建立兩個環境（**[!UICONTROL Design]**&#x200B;和&#x200B;**[!UICONTROL Live]**）。 環境已預先設定目標定位資訊。

   如果您已啟用&#x200B;**[!UICONTROL Visitor]**&#x200B;對應，系統會自動在環境的&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中勾選&#x200B;**[!UICONTROL Environment dedicated to incoming anonymous interactions]**&#x200B;方塊。

   此選項可讓您啟用匿名互動的特定功能，尤其是在設定環境優惠方案空間時。 您也可以設定選項來讓您從「已識別」環境切換至「匿名」環境。

   例如，您可以將收件者環境優惠方案空間（已識別的連絡人）與符合訪客環境（未識別的連絡人）的優惠方案空間連結。 如此一來，聯絡人便可獲得不同的優惠方案，具體取決於是否識別此聯絡人。 如需詳細資訊，請參閱[建立優惠方案空間](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>如需傳入頻道上匿名互動的詳細資訊，請參閱[匿名互動](../../interaction/using/anonymous-interactions.md)。
