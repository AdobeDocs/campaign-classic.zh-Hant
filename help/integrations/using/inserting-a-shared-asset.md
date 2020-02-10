---
title: 插入共用資產
seo-title: 插入共用資產
description: 插入共用資產
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 插入共用資產{#inserting-a-shared-asset}

從Adobe Experience cloud共用的資產可用於您的電子郵件和登陸頁面，如下所示：

1. 建立新電子郵件或新登陸頁面。

   如果您使用Adobe Experience Manager資產庫中的資產，請使用在設定整合時建立 [的傳送範本](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)。

   如果您沒有此特定範本，請確定在傳送屬性 ****, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** tab)已設為 **DCE** ，而且您要用來存取AEM Assets資源庫的AEM外部帳戶已提供。

1. 在編輯視窗中，選取要新增影像的選項：

   * 如果您使用標準編輯 [模式](../../delivery/using/defining-the-email-content.md#adding-images)，請選 **[!UICONTROL Image]** 取> **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_standard.png)

   * 如果您使用進階 [編輯模式](../../web/using/about-campaign-html-editor.md) (DCE)，請移至影像區塊，然後透過內容相關選單，選取 **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >使用DCE時，您無法在Web存取 [中插入](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) Adobe Campaign的共用影像。

1. 在開啟的選取視窗中，選取影像，然後確認。

   可用的影像會來自您的Adobe Experience cloud資料庫或AEM Assets資料庫，這取決於您的Adobe Campaign例項設定方式。 請參閱「設 [定資產存取權](../../integrations/using/configuring-access-to-assets.md) 」一節。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您使用與Adobe Target的整合，則可以使用共用影像做為預設影像。 請參見[此頁面](../../integrations/using/integrating-with-adobe-target.md)。

