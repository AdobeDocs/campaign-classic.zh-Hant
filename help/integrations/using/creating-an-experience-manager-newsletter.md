---
title: 建立Experience Manager電子報
seo-title: 建立Experience Manager電子報
description: 建立Experience Manager電子報
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 建立Experience Manager電子報{#creating-an-experience-manager-newsletter}

此整合可用來建立Adobe Experience manager中的電子報，然後在Adobe Campaign中用作電子郵件促銷活動的一部分。

如需如何使用此整合的更詳細範例，請參閱 [此逐步指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html)。

**來自Adobe Experience Manager:**

1. 在您的AEM作者實例中，按一下頁面左上方 **的Adobe Experience** logo並選取 **[!UICONTROL Sites]**。

   ![](assets/aem_uc_1.png)

1. Select **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. 按一下 **[!UICONTROL Create]** 頁面右上方的按鈕，然後選取 **[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 選取范 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 本並命名電子報。
1. 建立頁面後，請存取功能表 **[!UICONTROL Page information]** 並按一下 **[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在標籤 **[!UICONTROL Cloud Services]** 中，選 **[!UICONTROL Adobe Campaign]** 擇 **[!UICONTROL Cloud service configuration]** 為，並在第二個下拉式清單中選取您的Adobe Campaign例項。

   ![](assets/aem_uc_4.png)

1. 透過新增元件（例如Adobe Campaign的個人化欄位）來編輯您的電子郵件內容。
1. 當您的電子郵件準備就緒時，請存取功能 **[!UICONTROL Page information]** 表並按一下 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 從第一個下拉式清單中，選取為工 **[!UICONTROL Publish to Adobe Campaign]** 作流程模型，然後按一下 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然後，如同上一步，啟動工作 **[!UICONTROL Approve for Campaign]** 流程。
1. 免責聲明會顯示在您頁面的頂端。 按一 **[!UICONTROL Complete]** 下以確認檢閱，然後按一下 **[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再按一 **[!UICONTROL Complete]** 下，然 **[!UICONTROL Newsletter approval]** 後在下 **[!UICONTROL Next Step]** 拉式清單中選取。

   ![](assets/aem_uc_8.png)

您的電子報現在已可在Adobe Campaign中準備好並同步化。

**從Adobe Campaign:**

1. 在標籤 **[!UICONTROL Campaigns]** 中，按一 **[!UICONTROL Deliveries]** 下 **[!UICONTROL Create]**。

   ![](assets/aem_uc_9.png)

1. 在下拉 **[!UICONTROL Delivery template]** 式清單中，選取范 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 本。

   ![](assets/aem_uc_10.png)

1. 將新增 **[!UICONTROL Label]** 至傳送，然後按一下 **[!UICONTROL Continue]**。
1. Click the **[!UICONTROL Synchronize]** button.

   如果此按鈕未顯示在您的介面中，請按一下按 **[!UICONTROL Properties]** 鈕並選取標 **[!UICONTROL Advanced]** 簽。 欄 **[!UICONTROL Content editing mode]** 位中的欄位應設 **[!UICONTROL AEM]** 為您的AEM例項 **[!UICONTROL AEM account]** 。

   ![](assets/aem_uc_11.png)

1. 選取先前在Adobe Experience Manager中建立的傳送，然後按一下 **[!UICONTROL Ok]**。
1. 對AEM **[!UICONTROL Refresh content]** 傳送進行某些變更後，請按一下按鈕。

   ![](assets/aem_uc_12.png)

您的電子郵件現在已準備好傳送給您的觀眾。
