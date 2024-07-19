---
product: campaign
title: 建立Experience Manager電子報
description: 建立Experience Manager電子報
feature: Experience Manager Integration
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 1%

---

# 建立Experience Manager電子報{#creating-an-experience-manager-newsletter}



例如，這項整合可用於在Adobe Experience Manager中建立電子報，接著在Adobe Campaign中作為電子郵件促銷活動的一部分使用。

來自Adobe Experience Manager的&#x200B;**：**

1. 從您的AEM作者執行個體中，按一下頁面左上方的&#x200B;**Adobe體驗**&#x200B;標誌，然後選取&#x200B;**[!UICONTROL Sites]**。

   ![](assets/aem_uc_1.png)

1. 選取 **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**。
1. 按一下頁面右上角的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，然後選取&#x200B;**[!UICONTROL Page]**。

   ![](assets/aem_uc_2.png)

1. 選取&#x200B;**[!UICONTROL Adobe Campaign Email (AC 6.1)]**&#x200B;範本並命名您的Newsletter。
1. 建立您的頁面後，存取&#x200B;**[!UICONTROL Page information]**&#x200B;功能表並按一下&#x200B;**[!UICONTROL Open Properties]**。

   ![](assets/aem_uc_3.png)

1. 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;索引標籤中，選取&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;作為&#x200B;**[!UICONTROL Cloud service configuration]**，並在第二個下拉式清單中選取您的Adobe Campaign執行個體。

   ![](assets/aem_uc_4.png)

1. 新增元件以編輯電子郵件內容，例如Adobe Campaign的個人化欄位。
1. 當您的電子郵件準備就緒時，存取&#x200B;**[!UICONTROL Page information]**&#x200B;功能表並按一下&#x200B;**[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_5.png)

1. 從第一個下拉式清單中，選取&#x200B;**[!UICONTROL Publish to Adobe Campaign]**&#x200B;作為工作流程模型，然後按一下&#x200B;**[!UICONTROL Start workflow]**。

   ![](assets/aem_uc_6.png)

1. 然後，在上一步中，啟動&#x200B;**[!UICONTROL Approve for Campaign]**&#x200B;工作流程。
1. 免責宣告會出現在您的頁面頂端。 按一下&#x200B;**[!UICONTROL Complete]**&#x200B;以確認檢閱，然後按一下&#x200B;**[!UICONTROL Ok]**。

   ![](assets/aem_uc_7.png)

1. 再按一下&#x200B;**[!UICONTROL Complete]**&#x200B;並在&#x200B;**[!UICONTROL Next Step]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Newsletter approval]**。

   ![](assets/aem_uc_8.png)

您的Newsletter現已準備就緒，並已在Adobe Campaign中同步。

來自Adobe Campaign的&#x200B;**：**

1. 從&#x200B;**[!UICONTROL Campaigns]**&#x200B;索引標籤，按一下&#x200B;**[!UICONTROL Deliveries]**&#x200B;然後&#x200B;**[!UICONTROL Create]**。

   ![](assets/aem_uc_9.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL Email delivery with AEM content (mailAEMContent)]**&#x200B;範本。

   ![](assets/aem_uc_10.png)

1. 新增&#x200B;**[!UICONTROL Label]**&#x200B;至您的傳遞，然後按一下&#x200B;**[!UICONTROL Continue]**。
1. 按一下 **[!UICONTROL Synchronize]** 按鈕。

   若此按鈕未出現在您的介面中，請按一下&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤。 在&#x200B;**[!UICONTROL AEM account]**&#x200B;欄位中，您的AEM執行個體應將&#x200B;**[!UICONTROL Content editing mode]**&#x200B;欄位設為&#x200B;**[!UICONTROL AEM]**。

   ![](assets/aem_uc_11.png)

1. 選取先前在Adobe Experience Manager中建立的傳遞，然後按一下&#x200B;**[!UICONTROL Ok]**。
1. 對您的AEM傳遞進行一些變更後，請按一下&#x200B;**[!UICONTROL Refresh content]**&#x200B;按鈕。

   ![](assets/aem_uc_12.png)

您的電子郵件現在已準備好傳送給您的對象。
