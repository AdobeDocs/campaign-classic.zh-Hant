---
product: campaign
title: 設定與Adobe Target的整合
description: 瞭解如何設定與Adobe Target的整合
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 設定與Adobe Target的整合{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> 作為託管或混合型客戶，請聯絡您的Adobe代表以設定此整合。 以下步驟僅適用於內部部署客戶。

這項整合需要：

* Adobe Experience Cloud和Adobe Target組織
* 指定用來與Adobe Campaign建立連線的Adobe Target rawbox

若要在Adobe Campaign中設定這項整合，請遵循下列步驟：

1. 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 內建套件。 [了解更多](../../platform/using/working-with-data-packages.md#importing-packages)

   此套件可讓您透過Digital Asset Manager存取共用資產。

1. 啟用透過IMS (Adobe ID連線服務)的連線，以在您的電子郵件中使用透過Adobe Experience Cloud共用的影像。 [了解更多](../../integrations/using/about-adobe-id.md)
1. 瀏覽至 **[!UICONTROL Administration > Platform > Options]** 若要設定Adobe Target的伺服器和組織（租使用者）選項：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** ：用於整合的Adobe Target伺服器。 此選項預設為已選取。 此值對應至Adobe Target **[!UICONTROL Domain Server]**，後跟值 **/m2**. 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** ：Adobe Target組織名稱。 此值對應至Adobe Target的名稱 **[!UICONTROL Client]**.


>[!CAUTION]
>
>對於混合式架構和託管式架構，必須在所有伺服器上設定這些選項，包括 [中間來源伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行例項](../../message-center/using/configuring-instances.md#execution-instance).