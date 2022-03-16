---
product: campaign
title: 配置與Adobe Target的整合
description: 瞭解如何配置與Adobe Target的整合
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 配置與Adobe Target的整合{#configuring-the-integration-with-adobe-target}

![](../../assets/v7-only.svg)


>[!CAUTION]
>
> 作為托管或混合型客戶，請聯繫您的Adobe代表以配置此整合。 以下步驟僅適用於現場客戶。

此整合需要：

* Adobe Experience Cloud和Adobe Target組織
* 指定與Adobe Campaign建立聯繫的Adobe Target羅布克

要在Adobe Campaign配置此整合，請執行以下步驟：

1. 安裝 **[!UICONTROL Integration with the Adobe Experience Cloud]** 內置包。 [了解更多](../../platform/using/working-with-data-packages.md#importing-packages)

   此包允許您通過Digital Asset Manager訪問共用資產。

1. 啟用通過IMS(Adobe ID連接服務)的連接，以在電子郵件中使用通過Adobe Experience Cloud共用的影像。 [了解更多](../../integrations/using/about-adobe-id.md)
1. 瀏覽到 **[!UICONTROL Administration > Platform > Options]** 要為Adobe Target配置伺服器和組織（租戶）選項：

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** :Adobe Target伺服器用於整合。 預設情況下，此選項已被選中。 此值與Adobe Target **[!UICONTROL Domain Server]**，後跟值 **/m2**。 例如： **tt.omtrdc.net/m2**。
   * **[!UICONTROL TNT_TenantName]** :Adobe Target組織名稱。 此值與Adobe Target **[!UICONTROL Client]**。


>[!CAUTION]
>
>對於混合和托管體系結構，必須在所有伺服器上設定這些選項，包括 [中間採購伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行實例](../../message-center/using/configuring-instances.md#execution-instance)。