---
title: 設定與Adobe target的整合
seo-title: 設定與Adobe target的整合
description: 設定與Adobe target的整合
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 設定與Adobe target的整合{#configuring-the-integration-with-adobe-target}

## 必要條件 {#prerequisites}

若要使用Adobe Campaign與Adobe Target之間的整合，您必須：

* Adobe Experience cloud和Adobe target組織
* 指定Adobe Target rawbox以建立與Adobe Campaign的連線

## 設定Adobe Campaign {#configuring-adobe-campaign}

若要設定Adobe Campaign:

1. 安裝標 **[!UICONTROL Integration with the Adobe Experience Cloud]** 準套件。 安裝整合套件與安裝標準套件相同，如「套件匯入」一節 [中所述](../../platform/using/working-with-data-packages.md#importing-packages) 。 這可讓您透過Digital Asset manager存取共用資產。
1. 透過IMS（Adobe ID連線服務）啟用連線，以在電子郵件中使用透過Adobe Experience cloud共用的影像。 請參閱 [IMS相關章節](../../integrations/using/about-adobe-id.md)。
1. 在中 **[!UICONTROL Administration > Platform > Options]**，設定Adobe target的伺服器和組織（租用戶）選項：

   * **[!UICONTROL TNT_EdgeServer]** :用於整合的Adobe Target伺服器。 預設已選取此選項。 此值與Adobe Target相 **[!UICONTROL Domain Server]**&#x200B;對應，後跟 **值/m2**。 例如： **tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe target組織名稱。 此值與Adobe Target的名稱相對應 **[!UICONTROL Client]**。
   ![](assets/tar_options.png)

