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


# 設定與Adobe Target的整合{#configuring-the-integration-with-adobe-target}

## 必要條件 {#prerequisites}

若要使用Adobe Campaign與Adobe Target之間的整合，您必須：

* Adobe Experience Cloud和Adobe Target組織
* 指定Adobe Target rawbox以建立與Adobe Campaign的連線

## 設定Adobe Campaign {#configuring-adobe-campaign}

若要設定Adobe Campaign:

1. 安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;標準套件。 安裝整合軟體包與安裝標準軟體包相同，如[軟體包導入](../../platform/using/working-with-data-packages.md#importing-packages)部分中所述。 這可讓您透過Digital Asset Manager存取共用資產。
1. 透過IMS（Adobe ID連線服務）啟用連線，以在電子郵件中使用透過Adobe Experience Cloud共用的影像。 請參閱關於[IMS](../../integrations/using/about-adobe-id.md)的章節。
1. 在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;中，設定Adobe Target的伺服器與組織（租用戶）選項：

   * **[!UICONTROL TNT_EdgeServer]** :用於整合的Adobe Target伺服器。預設已選取此選項。 此值對應於Adobe Target **[!UICONTROL Domain Server]**，後面接著值&#x200B;**/m2**。 例如：**tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target組織名稱。此值與Adobe Target **[!UICONTROL Client]**&#x200B;的名稱相對應。

   ![](assets/tar_options.png)

