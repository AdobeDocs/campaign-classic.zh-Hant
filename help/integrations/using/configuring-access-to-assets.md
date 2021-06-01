---
product: campaign
title: 設定資產存取權
description: 設定資產存取權
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---

# 設定資產存取權{#configuring-access-to-assets}

本節詳細說明Adobe Campaign中使用與Assets核心服務或Adobe Experience Manager Assets資料庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是同時進行的。 進行任何配置前，請仔細閱讀以下資訊。

* 與&#x200B;**Experience Cloud資產**&#x200B;整合：此整合可讓您從Adobe Experience Cloud資料庫插入影像。 此程式庫可以是資產核心服務或隨選資產，視您的設定和授權模式而定。 必須在Adobe Campaign中安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;內建套件，才能設定此整合。
* 與&#x200B;**AEM Assets**&#x200B;整合：此整合可讓您從Adobe Experience Manager資產資料庫插入影像。 必須在Adobe Campaign中安裝&#x200B;**[!UICONTROL AEM Integration]**&#x200B;內建套件，才能設定此整合。

>[!NOTE]
>
>如果安裝了兩個套件（**[!UICONTROL AEM Integration]**&#x200B;和&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**），則只能使用Adobe Experience Cloud資料庫中可用的資產。

## 與Experience Cloud資產整合{#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign與Experience Cloud資產之間的整合，您必須：

* Adobe Experience Cloud組織
* 已啟用AdobeIMS驗證模式

若要啟用Adobe Campaign與Adobe Experience Cloud之間的連線，請透過IMS(Adobe ID連線服務)設定連線。 在[透過Adobe ID](../../integrations/using/about-adobe-id.md)連線檔案中會詳細說明此設定。 它涉及：

* 安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;套件。
* 設定Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>連結至此整合的功能僅適用於透過IMS連結至其Adobe ID的使用者。

## 與AEM Assets整合{#integrating-with-aem-assets}

若要整合AEM Assets與Adobe Campaign，您必須先設定Adobe Experience Manager與Adobe Campaign之間的整合。 此設定主要需要：

* 安裝&#x200B;**[!UICONTROL AEM Integration]**&#x200B;內建套件
* 設定專屬於Adobe Experience Manager的外部帳戶

在[詳細檔案](../../integrations/using/about-adobe-experience-manager.md)中了解如何整合Adobe Campaign和Adobe Experience Manager。

設定此整合後，您就可以在Adobe Campaign中設定新的傳送範本，以使用AEM Assets資料庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳遞範本 — 或複製現有的傳遞範本。 如需傳送範本的詳細資訊，請參閱[本頁面](../../delivery/using/about-templates.md)。
1. 編輯此模板的&#x200B;**屬性**。
1. 在&#x200B;**[!UICONTROL Advanced]**&#x200B;頁簽中，將&#x200B;**[!UICONTROL Content editing mode]**&#x200B;設定為&#x200B;**DCE**。
1. 選取您需要用來存取AEM Assets程式庫的外部&#x200B;**[!UICONTROL AEM account]**。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳送的內容中時，**[!UICONTROL Select a shared asset]**&#x200B;選項將可讓您瀏覽AEM Assets資料庫中的影像。 進一步了解[本節](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果您的Adobe Campaign執行個體上也安裝了&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;套件，則您將只能使用Adobe Experience Cloud資料庫中的可用資產。 若要同時存取AEM Assets資料庫中的資產，您必須同步AEM Assets和Adobe Experience Cloud。 接著，AEM Assets中的資產也可在Adobe Experience Cloud資料庫中使用。 在此情況下，您不需要建立特定的傳送範本。 有關在AEM Assets和Adobe Experience Cloud之間同步的詳細資訊，請參閱[詳細檔案](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration)。
