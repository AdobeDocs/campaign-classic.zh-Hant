---
product: campaign
title: 插入共用資產
description: 插入共用資產
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: d399c4800fe6c5b128a6ccb5fec15262cbef5ee8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 插入共用資產{#inserting-a-shared-asset}

從Adobe Experience Cloud共用的資產可在電子郵件和登錄頁面中使用，如下所示：

1. 建立新電子郵件或新登錄頁面。

   如果您使用Adobe Experience Manager資產資料庫中的資產，請使用在[設定整合時建立的傳送範本](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)。

   如果您沒有此特定範本，請確保在傳送&#x200B;**屬性**&#x200B;中，**[!UICONTROL Content editing mode]**（**[!UICONTROL Advanced]**&#x200B;標籤）設定為&#x200B;**DCE**，並提供您要用於存取AEM Assets資源庫的AEM外部帳戶。

1. 在編輯視窗中，選取要新增影像的選項：

   * 如果您使用[標準編輯模式](../../delivery/using/defining-the-email-content.md#adding-images)，請選擇&#x200B;**[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_standard.png)

   * 如果您使用[高級編輯模式](../../web/using/about-campaign-html-editor.md)(DCE)，請轉到影像塊，然後通過上下文菜單選擇&#x200B;**[!UICONTROL Select a shared asset]**。

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >使用DCE時，無法在[Web access](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)中插入來自Adobe Campaign的共用影像。

1. 在開啟的選取視窗中，選取影像，然後確認。

   可用的影像來自您的Adobe Experience Cloud資料庫或AEM Assets資料庫，端視您的Adobe Campaign執行個體的設定方式而定。 請參閱[設定資產存取權](../../integrations/using/configuring-access-to-assets.md)區段。

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>如果您使用與Adobe Target的整合，則可以使用共用影像作為預設影像。 請參見[此頁面](../../integrations/using/integrating-with-adobe-target.md)。
