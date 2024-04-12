---
product: campaign
title: 設定與Adobe Target的整合
description: 瞭解如何設定與Adobe Target的整合
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 設定與Adobe Target的整合{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> 身為託管或混合型客戶，請聯絡您的Adobe代表以設定這項整合。 以下步驟僅適用於內部部署客戶。

這項整合需要：

* Adobe Experience Cloud和Adobe Target組織
* 已指定Adobe Target rawbox來與Adobe Campaign建立連線

若要在Adobe Campaign中設定這項整合，請遵循下列步驟：

1. 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 內建套件。 [了解更多](../../platform/using/working-with-data-packages.md#importing-packages)

   此套件可讓您透過Digital Asset Manager存取共用資產。

1. 啟用透過IMS的連線(Adobe ID連線服務)，以在您的電子郵件中使用透過Adobe Experience Cloud共用的影像。 [了解更多](../../integrations/using/about-adobe-id.md)
1. 瀏覽至 **[!UICONTROL Administration > Platform > Options]** 若要設定Adobe Target的伺服器和組織（租使用者）選項：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** ：用於整合的Adobe Target伺服器。 依預設，已選取此選項。 此值對應至Adobe Target **[!UICONTROL Domain Server]**，接著值 **/m2**. 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** ：Adobe Target組織名稱。 此值對應至Adobe Target的名稱 **[!UICONTROL Client]**.


>[!CAUTION]
>
>對於混合式與託管式架構，必須在所有伺服器上設定這些選項，包括 [中間來源伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行例項](../../message-center/using/configuring-instances.md#execution-instance).