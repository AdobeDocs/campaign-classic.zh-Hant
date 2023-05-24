---
product: campaign
title: 設定對資產的存取權
description: 設定對資產的存取權
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# 設定對資產的存取權{#configuring-access-to-assets}



本節詳細說明在Adobe Campaign中使用與Assets核心服務或Adobe Experience Manager Assets (AEM Assets)資料庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是並行的。 在進行任何設定之前，請仔細閱讀下列資訊。

* 與整合 **Experience Cloud資產**：此整合可讓您從Adobe Experience Cloud資料庫插入影像。 此整合必須透過安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign中的內建套件。
* 與整合 **AEM Assets**：此整合可讓您從Adobe Experience Manager資產資料庫插入影像。 此整合必須透過安裝 **[!UICONTROL AEM Integration]** Adobe Campaign中的內建套件。 請注意，自Adobe Experience Manager 6.4起，將不再提供這項整合。

>[!NOTE]
>
>如果兩個套件(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，則只能使用Adobe Experience Cloud資料庫中可用的資產。

## 與Experience Cloud資產整合 {#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign與Experience Cloud資產之間的整合，您必須具備：

* Adobe Experience Cloud組織
* Adobe IMS驗證模式已啟用

若要啟用Adobe Campaign與Adobe Experience Cloud之間的連線，請透過IMS (Adobe ID連線服務)設定連線。 此設定的詳細資訊請參閱 [透過Adobe ID連線](../../integrations/using/about-adobe-id.md) 檔案。 其中涉及：

* 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 封裝。
* 設定Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>連結至此整合的功能僅適用於透過IMS連線至其Adobe ID的使用者。

## 與AEM Assets整合 {#integrating-with-aem-assets}


>[!CAUTION]
>
>此功能已從Adobe Experience Manager 6.4開始停止服務。 [瞭解更多](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

若要將AEM Assets與Adobe Campaign整合，您必須先設定Adobe Experience Manager與Adobe Campaign之間的整合。 此設定主要需要：

* 安裝 **[!UICONTROL AEM Integration]** 內建套件
* 設定Adobe Experience Manager專用的外部帳戶

瞭解如何在中整合Adobe Campaign和Adobe Experience Manager [詳細檔案](../../integrations/using/about-adobe-experience-manager.md).

設定這項整合後，您可以在Adobe Campaign中設定新的傳遞範本，以使用AEM Assets資料庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳遞範本 — 或複製現有的傳遞範本。 如需傳送範本的詳細資訊，請參閱 [此頁面](../../delivery/using/about-templates.md).
1. 編輯 **屬性** 此範本的。
1. 在 **[!UICONTROL Advanced]** 標籤，設定 **[!UICONTROL Content editing mode]** 至 **DCE**.
1. 選取外部 **[!UICONTROL AEM account]** 需要使用來存取AEM Assets資料庫。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳送的內容時， **[!UICONTROL Select a shared asset]** 選項之後，您就可以瀏覽AEM Assets資料庫中的影像。 在[本章節](../../integrations/using/inserting-a-shared-asset.md)了解更多資訊。

>[!NOTE]
>
>如果 **[!UICONTROL Integration with the Adobe Experience Cloud]** 套件也安裝在您的Adobe Campaign執行個體上，您只能使用Adobe Experience Cloud資料庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience Cloud資料庫中使用。 在這種情況下，您不需要建立特定的傳遞範本。
