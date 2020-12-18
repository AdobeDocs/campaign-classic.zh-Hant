---
solution: Campaign Classic
product: campaign
title: 設定資產存取權
description: 設定資產存取權
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---


# 設定資產存取權{#configuring-access-to-assets}

本節詳細說明Adobe Campaign中使用與Assets核心服務或Adobe Experience Manager資產庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是並行的。 進行任何配置前，請仔細閱讀以下資訊。

* 與&#x200B;**Experience Cloud資產**&#x200B;整合：此整合可讓您插入Adobe Experience Cloud資料庫中的影像。 視您的設定和授權模式而定，此程式庫可以是「資產」核心服務或「隨選資產」。 此整合必須透過在Adobe Campaign中安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;內建套件來設定。
* 與&#x200B;**AEM Assets**&#x200B;整合：此整合可讓您插入Adobe Experience Manager資產庫中的影像。 此整合必須透過在Adobe Campaign中安裝&#x200B;**[!UICONTROL AEM Integration]**&#x200B;內建套件來設定。

>[!NOTE]
>
>如果已安裝兩個套件（**[!UICONTROL AEM Integration]**&#x200B;和&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**），則只能使用Adobe Experience Cloud程式庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步化AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience Cloud資料庫中取用。 如需同步化AEM資產和Adobe Experience Cloud的詳細資訊，請參閱[詳細檔案](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

## 與Experience Cloud資產整合{#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign和Experience Cloud資產之間的整合，您必須：

* Adobe Experience Cloud組織
* 啟用Adobe IMS驗證模式

若要啟用Adobe Campaign與Adobe Experience Cloud之間的連線，請透過IMS（Adobe ID連線服務）設定連線。 此設定在[透過Adobe ID](../../integrations/using/about-adobe-id.md)檔案進行連線中詳述。 它包括：

* 安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;軟體包。
* 設定Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>連結至此整合的功能僅適用於透過IMS連結其Adobe ID的使用者。

## 與AEM Assets {#integrating-with-aem-assets}整合

若要將AEM Assets與Adobe Campaign整合，您必須先設定Adobe Experience Manager與Adobe Campaign之間的整合。 此配置主要要求：

* 安裝&#x200B;**[!UICONTROL AEM Integration]**&#x200B;內置軟體包
* 設定Adobe Experience Manager專用的外部帳戶

瞭解如何在[詳細檔案](../../integrations/using/about-adobe-experience-manager.md)中整合Adobe Campaign和Adobe Experience Manager。

在設定此整合後，您就可以在Adobe Campaign中設定新的傳送範本，以使用AEM Assets程式庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳送範本——或複製現有的傳送範本。 有關「傳送」範本的詳細資訊，請參閱[本頁](../../delivery/using/about-templates.md)。
1. 編輯此模板的&#x200B;**屬性**。
1. 在&#x200B;**[!UICONTROL Advanced]**&#x200B;頁籤中，將&#x200B;**[!UICONTROL Content editing mode]**&#x200B;設定為&#x200B;**DCE**。
1. 選取您需要用來存取AEM Assets程式庫的外部&#x200B;**[!UICONTROL AEM account]**。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳送的內容時，**[!UICONTROL Select a shared asset]**&#x200B;選項會允許您瀏覽AEM Assets程式庫中的影像。 進一步瞭解[本節](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;套件也安裝在您的Adobe Campaign實例上，則您只能使用Adobe Experience Cloud程式庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步化AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience Cloud資料庫中取用。 在這種情況下，您不需要建立特定的傳送範本。 如需AEM Assets與Adobe Experience Cloud同步化的詳細資訊，請參閱[詳細檔案](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

