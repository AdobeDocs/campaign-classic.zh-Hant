---
product: campaign
title: 即時/設計環境
description: 即時/設計環境
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# 即時/設計環境{#live-design-environments}



## 操作原則 {#operating-principle}

互動會與兩種選件環境搭配運作：

* **[!UICONTROL Design]** 包含正在編輯且可以變更之選件的選件環境。 這些優惠尚未通過審批週期，也未傳遞給聯繫人。
* **[!UICONTROL Live]** 將已核准的優惠方案呈現給聯絡人的優惠方案環境。 此環境中的選件為唯讀。

![](assets/offer_environments_overview_001.png)

每個 **[!UICONTROL Design]** 環境連結至 **[!UICONTROL Live]** 環境。 優惠方案完成後，其內容和資格規則會受到核准週期的約束。 完成此週期後，相關選件會自動部署至 **[!UICONTROL Live]** 環境。 從現在開始，它將可供交付。

依預設，互動會隨 **[!UICONTROL Design]** 環境與 **[!UICONTROL Live]** 環境。 兩個環境都已預先設定為鎖定內建的收件者表格。

>[!NOTE]
>
>若要鎖定另一個表格（匿名選件或特定收件者表格的訪客表格），您需要使用目標對應精靈來建立環境。 有關詳細資訊，請參閱 [建立優惠方案環境](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

選件管理員和傳送管理員可存取不同的環境檢視。 傳送管理員只能檢視 **[!UICONTROL Live]** 選件環境，並使用選件來傳送。 優惠方案管理員可以檢視和變更 **[!UICONTROL Design]** 環境和檢視 **[!UICONTROL Live]** 環境。 有關詳細資訊，請參閱 [運算元描述檔](../../interaction/using/operator-profiles.md).

## 建立優惠方案環境 {#creating-an-offer-environment}

依預設，互動會隨預先設定的環境提供，以鎖定收件者表格（已識別的選件）。 如果您想要鎖定另一個表格（匿名選件的訪客表格或特定收件者表格），則需套用下列設定：

1. 將游標置於 **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** 節點。 以滑鼠右鍵按一下您要使用的傳送對應(**[!UICONTROL Visitors]** 如果您想使用匿名選件)，並選取 **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. 按一下 **[!UICONTROL Next]** 若要繼續執行精靈中的下一個畫面，請核取 **[!UICONTROL Generate a storage schema for propositions]** 框，按一下 **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >如果已核取方塊，請取消勾選，然後重新勾選。

1. Adobe Campaign建立兩個環境(**[!UICONTROL Design]** 和 **[!UICONTROL Live]** )，以及先前啟用之目標對應的目標資訊。 環境已預先設定目標資訊。

   如果已激活 **[!UICONTROL Visitor]** 映射， **[!UICONTROL Environment dedicated to incoming anonymous interactions]** 框中的 **[!UICONTROL General]** 標籤。

   此選項可讓您啟用匿名互動的特定功能，尤其是在設定環境提供空間時。 您也可以配置選項，讓您從「已識別」環境切換至「匿名」環境。

   例如，您可以將收件者環境選件空間（已識別的連絡人）與符合訪客環境（未識別的連絡人）的選件空間連結。 如此一來，根據是否識別此連絡人，聯絡人將可使用不同的優惠方案。 有關詳細資訊，請參閱 [建立優惠方案空間](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>如需傳入頻道上匿名互動的詳細資訊，請參閱 [匿名互動](../../interaction/using/anonymous-interactions.md).
