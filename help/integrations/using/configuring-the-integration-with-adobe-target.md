---
product: campaign
title: 設定與Adobe Target的整合
description: 設定與Adobe Target的整合
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---

# 設定與Adobe Target的整合{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> 身為托管或混合客戶，請聯絡您的Adobe代表以設定此整合。 下列步驟僅適用於內部部署客戶。

## 先決條件 {#prerequisites}

若要使用Adobe Campaign與Adobe Target之間的整合，您必須具備：

* Adobe Experience Cloud和Adobe Target組織
* 指定用來建立與Adobe Campaign連線的Adobe Target rawbox

## 設定Adobe Campaign {#configuring-adobe-campaign}

若要設定Adobe Campaign:

1. 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 內建套件。 [了解更多](../../platform/using/working-with-data-packages.md#importing-packages)

   此套件可讓您透過Digital Asset Manager存取共用資產。

1. 啟用透過IMS的連線(Adobe ID連線服務)，以在電子郵件中使用透過Adobe Experience Cloud共用的影像。 [了解更多](../../integrations/using/about-adobe-id.md)
1. 瀏覽至 **[!UICONTROL Administration > Platform > Options]** 若要設定Adobe Target的伺服器與組織（租用戶）選項：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** :用於整合的Adobe Target伺服器。 預設已選取此選項。 此值對應至Adobe Target **[!UICONTROL Domain Server]**，後面接著值 **/m2**. 例如： **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :Adobe Target組織名稱。 此值對應至Adobe Target的名稱 **[!UICONTROL Client]**.


>[!CAUTION]
>
>對於混合式和托管架構，這些選項必須在所有伺服器上設定，包括 [中間來源伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行實例](../../message-center/using/configuring-instances.md#execution-instance).