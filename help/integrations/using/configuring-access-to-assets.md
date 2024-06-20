---
product: campaign
title: 設定資產存取權
description: 設定資產存取權
feature: Asset Sharing
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 設定資產存取權 {#configuring-access-to-assets}

本節詳細說明在Adobe Campaign中使用與Assets或Adobe Experience Manager Assets (AEM Assets)資料庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是並行的。 在進行任何設定前，請仔細閱讀下列資訊。

* 與整合 **Experience Cloud資產**：此整合可讓您從Adobe Experience Cloud資料庫插入影像。 若要設定此整合，您必須安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign中的內建套件。
* 與整合 **AEM Assets**：此整合可讓您從Adobe Experience Manager Assets資料庫插入影像。 若要設定此整合，您必須安裝 **[!UICONTROL AEM Integration]** Adobe Campaign中的內建套件。 請注意，從Adobe Experience Manager 6.4開始，將不再提供這項整合。

>[!NOTE]
>
>如果兩個套件(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，則只能使用Adobe Experience Cloud資料庫中的可用資產。

## 與Experience Cloud資產整合 {#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign與Experience Cloud資產之間的整合，您必須擁有：

* Adobe Experience Cloud組織
* Adobe IMS驗證模式已啟用

若要啟用Adobe Campaign與Adobe Experience Cloud之間的連線，請透過IMS (Adobe ID連線服務)設定連線。 此設定的詳細資料請參見 [透過Adobe ID連線](../../integrations/using/about-adobe-id.md) 檔案。 其中涉及：

* 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 封裝。
* 設定Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>與此整合連結的功能僅適用於透過IMS連線至其Adobe ID的使用者。

## 與AEM Assets整合 {#integrating-with-aem-assets}


>[!CAUTION]
>
>自Adobe Experience Manager 6.4起，此功能已停止服務。 [瞭解更多](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

若要將AEM Assets與Adobe Campaign整合，您必須先設定Adobe Experience Manager與Adobe Campaign之間的整合。 此設定主要需要：

* 安裝 **[!UICONTROL AEM Integration]** 內建套件
* 設定Adobe Experience Manager專用的外部帳戶

瞭解如何在中整合Adobe Campaign和Adobe Experience Manager [詳細檔案](../../integrations/using/about-adobe-experience-manager.md).

設定這項整合後，您可以在Adobe Campaign中設定新的傳遞範本，以使用AEM Assets資料庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳遞範本，或複製現有範本。 有關傳送範本的詳細資訊，請參閱 [此頁面](../../delivery/using/about-templates.md).
1. 編輯 **屬性** 範本的URL。
1. 在 **[!UICONTROL Advanced]** 標籤，設定 **[!UICONTROL Content editing mode]** 至 **DCE**.
1. 選取外部 **[!UICONTROL AEM account]** 需要使用來存取AEM Assets資料庫。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳送的內容時， **[!UICONTROL Select a shared asset]** 選項之後，您就可以在AEM Assets資料庫中瀏覽影像。 若要了解詳細資訊，請參閱[本章節](../../integrations/using/inserting-a-shared-asset.md)。

>[!NOTE]
>
>如果 **[!UICONTROL Integration with the Adobe Experience Cloud]** 套件也會安裝在Adobe Campaign執行個體上，您只能使用Adobe Experience Cloud資料庫中的可用資產。 若要存取AEM Assets資料庫中的資產，您必須同步AEM Assets和Adobe Experience Cloud。 AEM Assets中的資產也將可在Adobe Experience Cloud資料庫中使用。 在此情況下，您不需要建立特定的傳遞範本。
