---
product: campaign
title: 插入共用資產
description: 插入共用資產
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 1%

---

# 插入共用資產{#inserting-a-shared-asset}

從Adobe Experience Cloud共用的資產可用於您的電子郵件和登入頁面，如下所示：

1. 建立新電子郵件或新登陸頁面。

   如果您使用Adobe Experience Manager資產庫中的資產，請使用在下列情況下建立的傳送範本： [設定整合](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   如果您沒有此特定範本，請務必在傳送中確認 **屬性**，則 **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** 標籤)設為 **DCE** 並會提供您用來存取AEM Assets資源庫的AEM外部帳戶。

1. 在編輯視窗中，選取選項以新增影像：

   * 如果您使用 [標準編輯模式](../../delivery/using/defining-the-email-content.md#adding-images)，選取 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * 如果您使用 [進階編輯模式](../../web/using/about-campaign-html-editor.md) (DCE)，前往影像區塊，然後透過內容功能表選取 **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >您無法從Adobe Campaign插入共用影像於 [網頁存取](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 使用DCE時。

1. 在開啟的選取範圍視窗中，選取影像，然後確認。

   可用的影像來自Adobe Experience Cloud資料庫或AEM Assets資料庫，視您的Adobe Campaign執行個體的設定方式而定。 請參閱 [設定資產存取權](../../integrations/using/configuring-access-to-assets.md) 區段。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您透過Adobe Target整合，則可以使用共用影像作為預設影像。 請參見[此頁面](../../integrations/using/integrating-with-adobe-target.md)。
