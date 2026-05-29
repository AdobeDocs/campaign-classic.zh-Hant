---
product: campaign
title: 插入共用資產
description: 插入共用資產
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
TQID: https://experienceleague.adobe.com/5SrvIw1sYSNd4Hw1we554AfxDj3VgeTeqIOOzTTrWuY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 233
ht-degree: 1%

---

# 插入共用資產{#inserting-a-shared-asset}

從Adobe Experience Cloud共用的Assets可用於您的電子郵件和登入頁面，如下所示：

1. 建立新電子郵件或新登陸頁面。

   如果您使用Adobe Experience Manager資產庫的資產，請使用在[設定整合](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)時建立的傳遞範本。

   如果您沒有此特定範本，請確定在傳遞&#x200B;**Properties**&#x200B;中，**[!UICONTROL Content editing mode]** （**[!UICONTROL Advanced]**&#x200B;索引標籤）已設定為&#x200B;**DCE**，並且已提供您要用來存取AEM Assets資源程式庫的AEM外部帳戶。

1. 在編輯視窗中，選取選項以新增影像：

   * 如果您使用[標準編輯模式](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=zh-Hant#adding-images){target="_blank"}，請選取&#x200B;**[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**。

     ![](assets/dam_insert_image_standard.png)

   * 如果您使用[進階編輯模式](../../web/using/about-campaign-html-editor.md) (DCE)，請移至影像區塊，然後透過內容功能表選取&#x200B;**[!UICONTROL Select a shared asset]**。

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >使用DCE時，您無法從[網頁存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)的Adobe Campaign插入共用影像。

1. 在開啟的選取範圍視窗中，選取影像，然後確認。

   可用的影像來自Adobe Experience Cloud資料庫或AEM Assets資料庫，視您的Adobe Campaign執行個體的設定方式而定。 請參閱[設定Assets存取權](../../integrations/using/configuring-access-to-assets.md)區段。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您透過Adobe Target整合，則可以使用共用影像作為預設影像。 請參見[此頁面](../../integrations/using/integrating-with-adobe-target.md)。
