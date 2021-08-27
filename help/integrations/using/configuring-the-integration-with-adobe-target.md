---
product: campaign
title: 設定與Adobe Target的整合
description: 設定與Adobe Target的整合
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# 設定與Adobe Target的整合{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)

## 先決條件 {#prerequisites}

若要使用Adobe Campaign與Adobe Target之間的整合，您必須具備：

* Adobe Experience Cloud和Adobe Target組織
* 指定用來建立與Adobe Campaign連線的Adobe Target rawbox

## 設定Adobe Campaign {#configuring-adobe-campaign}

若要設定Adobe Campaign:

1. 安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;標準軟體包。 安裝整合套件與安裝標準套件相同，有關詳情請參閱[套件匯入](../../platform/using/working-with-data-packages.md#importing-packages)區段。 這可讓您透過數位資產管理器存取共用資產。
1. 啟用透過IMS的連線(Adobe ID連線服務)，以在電子郵件中使用透過Adobe Experience Cloud共用的影像。 請參閱[IMS](../../integrations/using/about-adobe-id.md)相關區段。
1. 在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;中，配置Adobe Target的伺服器和組織（租用戶）選項：

   * **[!UICONTROL TNT_EdgeServer]** :用於整合的Adobe Target伺服器。預設已選取此選項。 此值對應於Adobe Target **[!UICONTROL Domain Server]**，後跟值&#x200B;**/m2**。 例如：**tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target組織名稱。此值與Adobe Target **[!UICONTROL Client]**&#x200B;的名稱對應。

   ![](assets/tar_options.png)

>[!CAUTION]
>
>對於混合架構和托管架構，必須在所有伺服器上設定這些選項，包括[中間來源伺服器](../../installation/using/mid-sourcing-server.md)和[執行實例](../../message-center/using/configuring-instances.md#execution-instance)。