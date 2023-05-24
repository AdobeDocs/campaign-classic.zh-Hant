---
product: campaign
title: 建立Experience Manager電子報
description: 建立Experience Manager電子報
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 建立Experience Manager電子報{#creating-an-experience-manager-newsletter}



例如，這項整合可用來在Adobe Experience Manager中建立電子報，然後在Adobe Campaign中作為電子郵件促銷活動的一部分使用。

**從Adobe Experience Manager：**

1. 在您的AEM編寫執行個體中，按一下 **Adobe Experience** 標誌，並選取 **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. 選取 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 按一下 **[!UICONTROL Create]** 按鈕並選取「 」 **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. 選取 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 範本並命名您的Newsletter。
1. 建立頁面後，請存取 **[!UICONTROL Page information]** 功能表並按一下 **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. 在 **[!UICONTROL Cloud Services]** 索引標籤，選取 **[!UICONTROL Adobe Campaign]** 作為 **[!UICONTROL Cloud service configuration]** 和您的Adobe Campaign例項。

   ![](assets/aem_uc_4.png)

1. 新增元件以編輯電子郵件內容，例如Adobe Campaign的個人化欄位。
1. 當您的電子郵件準備就緒時，請存取 **[!UICONTROL Page information]** 功能表並按一下 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. 從第一個下拉式清單中選取 **[!UICONTROL Publish to Adobe Campaign]** 作為工作流程模型並按一下 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. 接著，在上一步中，啟動 **[!UICONTROL Approve for Campaign]** 工作流程。
1. 免責宣告會出現在您的頁面頂端。 按一下 **[!UICONTROL Complete]** 若要確認檢閱並按一下 **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. 再按一下 **[!UICONTROL Complete]** 並選取 **[!UICONTROL Newsletter approval]** 在 **[!UICONTROL Next Step]** 下拉式清單。

   ![](assets/aem_uc_8.png)

您的Newsletter現已準備就緒，並在Adobe Campaign中同步。

**從Adobe Campaign：**

1. 從 **[!UICONTROL Campaigns]** 標籤，按一下 **[!UICONTROL Deliveries]** 則 **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 在 **[!UICONTROL Delivery template]** 從下拉式清單中選取 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 範本。

   ![](assets/aem_uc_10.png)

1. 新增 **[!UICONTROL Label]** 至您的傳遞，然後按一下 **[!UICONTROL Continue]**.
1. 按一下 **[!UICONTROL Synchronize]** 按鈕。

   如果此按鈕沒有出現在您的介面中，請按一下 **[!UICONTROL Properties]** 按鈕並選取 **[!UICONTROL Advanced]** 標籤。 此 **[!UICONTROL Content editing mode]** 欄位應設為 **[!UICONTROL AEM]** 將您的AEM執行個體放在 **[!UICONTROL AEM account]** 欄位。

   ![](assets/aem_uc_11.png)

1. 選取先前在Adobe Experience Manager中建立的傳遞，然後按一下 **[!UICONTROL Ok]**.
1. 按一下 **[!UICONTROL Refresh content]** 對AEM傳遞進行變更後立即按一下按鈕。

   ![](assets/aem_uc_12.png)

您的電子郵件現在已準備好傳送給您的對象。
