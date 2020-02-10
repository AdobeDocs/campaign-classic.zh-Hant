---
title: 設定資產存取權
seo-title: 設定資產存取權
description: 設定資產存取權
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 設定資產存取權{#configuring-access-to-assets}

本節詳細說明Adobe Campaign中使用與Assets核心服務或Adobe Experience Manager資產庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是並行的。 進行任何配置前，請仔細閱讀以下資訊。

* 與 **Experience cloud資產整合**:此整合可讓您插入Adobe Experience cloud資料庫中的影像。 視您的設定和授權模式而定，此程式庫可以是「資產」核心服務或「隨選資產」。 此整合必須透過在Adobe Campaign中安 **[!UICONTROL Integration with the Adobe Experience Cloud]** 裝內建套件來設定。
* 與 **AEM Assets整合**:此整合可讓您插入Adobe Experience Manager資產庫中的影像。 此整合必須透過在Adobe Campaign中安 **[!UICONTROL AEM Integration]** 裝內建套件來設定。

>[!NOTE]
>
>如果安裝了兩個&#x200B;**[!UICONTROL AEM Integration]** 套件( **[!UICONTROL Integration with the Adobe Experience Cloud]** 和)，則只能使用Adobe Experience cloud資料庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步化AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience cloud資料庫中取用。 如需同步化AEM Assets和Adobe Experience cloud的詳細資訊，請參閱詳細 [檔案](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

## 與Experience cloud資產整合 {#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign和Experience cloud資產之間的整合，您必須：

* Adobe Experience cloud組織
* 啟用Adobe IMS驗證模式

若要啟用Adobe Campaign與Adobe Experience cloud之間的連線，請透過IMS（Adobe ID連線服務）設定連線。 此設定在「透過Adobe ID連 [線」檔案中詳述](../../integrations/using/about-adobe-id.md) 。 它包括：

* 安裝包 **[!UICONTROL Integration with the Adobe Experience Cloud]** 。
* 設定Adobe Experience cloud外部帳戶。

>[!NOTE]
>
>連結至此整合的功能僅適用於透過IMS連結其Adobe ID的使用者。

## 與AEM Assets整合 {#integrating-with-aem-assets}

若要將AEM Assets與Adobe Campaign整合，您必須先設定Adobe Experience manager與Adobe Campaign之間的整合。 此配置主要要求：

* 安裝 **[!UICONTROL AEM Integration]** 內置軟體包
* 設定Adobe Experience manager專用的外部帳戶

在詳細檔案中瞭解如何整合Adobe Campaign和Adobe Experience Manager [](../../integrations/using/about-adobe-experience-manager.md)。

在設定此整合後，您就可以在Adobe Campaign中設定新的傳送範本，以使用AEM Assets程式庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳送範本——或複製現有的傳送範本。 For more on Delivery templates, refer to [this page](../../delivery/using/about-templates.md).
1. 編輯此 **範本的** 「屬性」。
1. 在頁籤 **[!UICONTROL Advanced]** 中，將設定 **[!UICONTROL Content editing mode]** 為 **DCE**。
1. 選取您需 **[!UICONTROL AEM account]** 要用來存取AEM Assets程式庫的外部。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳送的內容時，選 **[!UICONTROL Select a shared asset]** 項會允許您瀏覽AEM Assets資料庫中的影像。 在本節中進 [一步瞭解](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果套 **[!UICONTROL Integration with the Adobe Experience Cloud]** 件也安裝在您的Adobe Campaign實例上，則您只能使用Adobe Experience cloud資料庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步化AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience cloud資料庫中取用。 在這種情況下，您不需要建立特定的傳送範本。 如需AEM Assets與Adobe Experience cloud之間同步化的詳細資訊，請參閱詳細 [檔案](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)。

