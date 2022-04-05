---
product: campaign
title: 建立Experience Manager新聞稿
description: 建立Experience Manager新聞稿
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 建立Experience Manager新聞稿{#creating-an-experience-manager-newsletter}

![](../../assets/common.svg)

例如，可以利用這種整合在Adobe Experience Manager建立一份新聞簡報，然後在Adobe Campaign作為電子郵件活動的一部分使用。

**來自Adobe Experience Manager:**

1. 在作者AEM實例中，按一下 **Adobe體驗** 頁面左上側的徽標並選擇 **[!UICONTROL Sites]**。

   ![](assets/aem_uc_1.png)

1. 選取 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 按一下 **[!UICONTROL Create]** 按鈕，然後選擇 **[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 選擇 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 模板並命名您的新聞稿。
1. 建立頁面後，訪問 **[!UICONTROL Page information]** 的 **[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在 **[!UICONTROL Cloud Services]** 頁籤 **[!UICONTROL Adobe Campaign]** 如 **[!UICONTROL Cloud service configuration]** 還有你的Adobe Campaign案。

   ![](assets/aem_uc_4.png)

1. 通過添加元件(如Adobe Campaign的個性化欄位)編輯電子郵件內容。
1. 當您的電子郵件準備好時，訪問 **[!UICONTROL Page information]** 的 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 從第一個下拉清單中，選擇 **[!UICONTROL Publish to Adobe Campaign]** 作為工作流模型，按一下 **[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然後，如上一步，啟動 **[!UICONTROL Approve for Campaign]** 工作流。
1. 免責聲明將出現在頁面頂部。 按一下 **[!UICONTROL Complete]** 確認審閱，然後按一下 **[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再次按一下 **[!UICONTROL Complete]** 選擇 **[!UICONTROL Newsletter approval]** 的 **[!UICONTROL Next Step]** 下拉。

   ![](assets/aem_uc_8.png)

您的新聞稿現已準備好並在Adobe Campaign同步。

**來自Adobe Campaign:**

1. 從 **[!UICONTROL Campaigns]** 按鈕 **[!UICONTROL Deliveries]** 然後 **[!UICONTROL Create]**。

   ![](assets/aem_uc_9.png)

1. 在 **[!UICONTROL Delivery template]** 下拉，選擇 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 的下界。

   ![](assets/aem_uc_10.png)

1. 添加 **[!UICONTROL Label]** 到您的交貨，按一下 **[!UICONTROL Continue]**。
1. 按一下 **[!UICONTROL Synchronize]** 按鈕。

   如果此按鈕未出現在介面中，請按一下 **[!UICONTROL Properties]** 按鈕 **[!UICONTROL Advanced]** 頁籤。 的 **[!UICONTROL Content editing mode]** 欄位應設定為 **[!UICONTROL AEM]** 你AEM的案例 **[!UICONTROL AEM account]** 的子菜單。

   ![](assets/aem_uc_11.png)

1. 選擇以前在Adobe Experience Manager建立的交貨，然後按一下 **[!UICONTROL Ok]**。
1. 按一下 **[!UICONTROL Refresh content]** 按鈕，將選定控制項在Tab鍵次序中AEM移動。

   ![](assets/aem_uc_12.png)

您的電子郵件現在已準備好發送給您的受眾。
