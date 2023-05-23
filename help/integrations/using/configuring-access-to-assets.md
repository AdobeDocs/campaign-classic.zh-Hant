---
product: campaign
title: 配置對資產的訪問
description: 配置對資產的訪問
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

# 配置對資產的訪問{#configuring-access-to-assets}



本節詳細介紹在Adobe Campaign使用資產核心服務或Adobe Experience Manager資產(AEM Assets)庫的整合功能所需的配置步驟。

>[!CAUTION]
>
>這些整合是併發的。 在進行任何配置之前，請仔細閱讀以下資訊。

* 與 **Experience Cloud資產**:此整合允許您從Adobe Experience Cloud庫插入影像。 必須通過安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign的內置包。
* 與 **AEM Assets**:此整合允許您從Adobe Experience Manager資產庫插入影像。 必須通過安裝 **[!UICONTROL AEM Integration]** Adobe Campaign的內置包。 請注意，從Adobe Experience Manager6.4開始，此整合不再可用。

>[!NOTE]
>
>如果兩個包(**[!UICONTROL AEM Integration]** 和 **[!UICONTROL Integration with the Adobe Experience Cloud]** )，只能使用Adobe Experience Cloud庫中的可用資產。

## 與Experience Cloud資產整合 {#integrating-with-experience-cloud-assets}

要使用Adobe Campaign與Experience Cloud資產之間的整合，您必須：

* Adobe Experience Cloud組織
* 已啟用Adobe IMS驗證模式

要啟用Adobe Campaign和Adobe Experience Cloud之間的連接，請通過IMS(Adobe ID連接服務)配置連接。 此配置在 [通過Adobe ID連接](../../integrations/using/about-adobe-id.md) 的子菜單。 它涉及：

* 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 檔案。
* 配置Adobe Experience Cloud外部帳戶。

>[!NOTE]
>
>與這一整合相關的功能只適用於通過網際網路管理系統與其Adobe ID相連的用戶。

## 與AEM Assets整合 {#integrating-with-aem-assets}


>[!CAUTION]
>
>從Adobe Experience Manager6.4開始，已退出該功能。 [瞭解更多資訊](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

要整合AEM Assets和Adobe Campaign，首先必須配置Adobe Experience Manager和Adobe Campaign的整合。 此配置主要要求：

* 安裝 **[!UICONTROL AEM Integration]** 內置軟體包
* 配置特定於Adobe Experience Manager的外部帳戶

瞭解如何將Adobe Campaign和Adobe Experience Manager整合到 [詳細文檔](../../integrations/using/about-adobe-experience-manager.md)。

設定此整合後，您可以在Adobe Campaign配置新的交付模板以使用AEM Assets庫。 要執行此操作，請遵循下列步驟：

1. 建立新的交貨模板 — 或複製現有的交貨模板。 有關交付模板的詳細資訊，請參閱 [此頁](../../delivery/using/about-templates.md)。
1. 編輯 **屬性** 的下界。
1. 在 **[!UICONTROL Advanced]** 頁籤 **[!UICONTROL Content editing mode]** 至 **DCE**。
1. 選擇外部 **[!UICONTROL AEM account]** 你需要用來訪問你的AEM Assets圖書館。

   ![](assets/dam_aem_assets1.png)

當您根據此模板將影像插入到遞送的內容時， **[!UICONTROL Select a shared asset]** 選項，您可以瀏覽AEM Assets庫中的影像。 在[本章節](../../integrations/using/inserting-a-shared-asset.md)了解更多資訊。

>[!NOTE]
>
>如果 **[!UICONTROL Integration with the Adobe Experience Cloud]** 軟體包也安裝在您的Adobe Campaign實例上，您將只能使用Adobe Experience Cloud庫中的可用資產。 要訪問您的AEM Assets庫中的資產，您必須同步AEM Assets和Adobe Experience Cloud。 AEM Assets的資產也將在Adobe Experience Cloud圖書館提供。 在這種情況下，您不需要建立特定的交貨模板。
