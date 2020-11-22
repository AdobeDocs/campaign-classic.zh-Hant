---
solution: Campaign Classic
product: campaign
title: 設定與Adobe Target的整合
description: 設定與Adobe Target的整合
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Configuring the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

## 必要條件 {#prerequisites}

若要使用Adobe Campaign與Adobe Target之間的整合，您必須：

* Adobe Experience Cloud和Adobe Target組織
* 指定Adobe Target rawbox以建立與Adobe Campaign的連線

## 設定Adobe Campaign {#configuring-adobe-campaign}

若要設定Adobe Campaign:

1. 安裝標 **[!UICONTROL Integration with the Adobe Experience Cloud]** 準套件。 安裝整合套件與安裝標準套件相同，如「套件匯入」一節 [中所述](../../platform/using/working-with-data-packages.md#importing-packages) 。 這可讓您透過Digital Asset Manager存取共用資產。
1. 透過IMS（Adobe ID連線服務）啟用連線，以在電子郵件中使用透過Adobe Experience Cloud共用的影像。 請參閱 [IMS相關章節](../../integrations/using/about-adobe-id.md)。
1. 在中 **[!UICONTROL Administration > Platform > Options]**，設定Adobe Target的伺服器和組織（租用戶）選項：

   * **[!UICONTROL TNT_EdgeServer]** :用於整合的Adobe Target伺服器。 預設已選取此選項。 此值與Adobe Target相 **[!UICONTROL Domain Server]**&#x200B;對應，後跟 **值/m2**。 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :Adobe Target組織名稱。 此值與Adobe Target的名稱相對應 **[!UICONTROL Client]**。

   ![](assets/tar_options.png)

