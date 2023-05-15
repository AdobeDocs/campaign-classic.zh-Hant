---
product: campaign
title: 設定資產存取權
description: 設定資產存取權
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---

# 設定資產存取權{#configuring-access-to-assets}



本節詳細說明Adobe Campaign中使用與Assets核心服務或Adobe Experience Manager Assets(AEM Assets)程式庫整合功能的必要設定步驟。

>[!CAUTION]
>
>這些整合是同時進行的。 進行任何配置前，請仔細閱讀以下資訊。

* 與整合 **Experience Cloud資產**:此整合可讓您從Adobe Experience Cloud資料庫插入影像。 必須安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign中的內建套件。
* 與整合 **AEM Assets**:此整合可讓您從Adobe Experience Manager Assets資料庫插入影像。 必須安裝 **[!UICONTROL AEM Integration]** Adobe Campaign中的內建套件。 請注意，自Adobe Experience Manager 6.4起，將不再提供此整合。

>[!NOTE]
>
>如果這兩個包(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，則只能使用Adobe Experience Cloud程式庫中可用的資產。

## 與Experience Cloud資產整合 {#integrating-with-experience-cloud-assets}

若要使用Adobe Campaign與Experience Cloud資產之間的整合，您必須：

* Adobe Experience Cloud組織
* 已啟用Adobe IMS驗證模式

若要啟用Adobe Campaign與Adobe Experience Cloud之間的連線，請透過IMS(Adobe ID連線服務)設定連線。 此設定在 [透過Adobe ID連線](../../integrations/using/about-adobe-id.md) 檔案。 它涉及：

* 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 包。
* 設定Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>連結至此整合的功能僅適用於透過IMS連結至其Adobe ID的使用者。

## 與AEM Assets整合 {#integrating-with-aem-assets}


>[!CAUTION]
>
>自Adobe Experience Manager 6.4起，已停止支援此功能。 [深入了解](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

若要整合AEM Assets與Adobe Campaign，您必須先設定Adobe Experience Manager與Adobe Campaign之間的整合。 此設定主要需要：

* 安裝 **[!UICONTROL AEM Integration]** 內建套件
* 設定專屬於Adobe Experience Manager的外部帳戶

了解如何將Adobe Campaign和Adobe Experience Manager整合至 [詳細檔案](../../integrations/using/about-adobe-experience-manager.md).

設定此整合後，您就可以在Adobe Campaign中設定新的傳送範本，以使用AEM Assets資料庫。 要執行此操作，請遵循下列步驟：

1. 建立新的傳遞範本 — 或複製現有的傳遞範本。 如需傳送範本的詳細資訊，請參閱 [本頁](../../delivery/using/about-templates.md).
1. 編輯 **屬性** 範本。
1. 在 **[!UICONTROL Advanced]** 頁簽，設定 **[!UICONTROL Content editing mode]** to **DCE**.
1. 選取外部 **[!UICONTROL AEM account]** 需要用來存取AEM Assets程式庫。

   ![](assets/dam_aem_assets1.png)

當您根據此範本將影像插入傳遞的內容時， **[!UICONTROL Select a shared asset]** 選項，即可瀏覽AEM Assets資料庫中的影像。 在[本章節](../../integrations/using/inserting-a-shared-asset.md)了解更多資訊。

>[!NOTE]
>
>若 **[!UICONTROL Integration with the Adobe Experience Cloud]** 套件也會安裝在您的Adobe Campaign執行個體上，您將只能使用Adobe Experience Cloud資料庫中可用的資產。 若要同時存取AEM Assets資料庫中的資產，您必須同步AEM Assets和Adobe Experience Cloud。 接著，AEM Assets中的資產也可在Adobe Experience Cloud資料庫中使用。 在此情況下，您不需要建立特定的傳送範本。
