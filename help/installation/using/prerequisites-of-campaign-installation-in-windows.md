---
product: campaign
title: 在Windows安裝Campaign的必要條件
description: 在Windows安裝Campaign的必要條件
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 11%
---
# 開始在Windows上安裝Campaign {#prerequisites-of-campaign-installation-in-windows}



安裝Adobe Campaign所需的技術設定和軟體會顯示在[相容性矩陣](../../rn/using/compatibility-matrix.md)中。

多執行個體使用的Adobe Campaign伺服器安裝程式在[安裝伺服器](../../installation/using/installing-the-server.md)中說明。

主要步驟如下：

1. 安裝應用程式伺服器，請參閱[正在執行安裝程式](../../installation/using/installing-the-server.md#executing-the-installation-program)。
1. 與Web伺服器整合（選擇性，視部署的元件而定），請參閱[設定IIS Web伺服器](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)。

安裝步驟完成後，您需要設定執行個體、資料庫和伺服器。 有關詳細資訊，請參閱[關於初始設定](../../installation/using/about-initial-configuration.md)。

>[!NOTE]
>
>將Adobe Campaign部署到Windows環境時，擁有必要存取許可權的使用者可以在網路上的檔案操作期間，針對存取路徑使用UNC語法(Universal.Uniform Naming Convention)。
