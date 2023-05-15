---
product: campaign
title: 在 Windows 安裝 Campaign 的必要條件
description: 在 Windows 安裝 Campaign 的必要條件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# 開始在Windows上安裝Campaign {#prerequisites-of-campaign-installation-in-windows}



安裝Adobe Campaign所需的技術設定和軟體會顯示在 [相容性矩陣](../../rn/using/compatibility-matrix.md).

以下說明多執行個體使用的Adobe Campaign伺服器安裝程式： [安裝伺服器](../../installation/using/installing-the-server.md).

主要步驟如下：

1. 安裝應用程式伺服器，請參閱 [執行安裝程式](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. 與Web伺服器整合（可選，視部署的元件而定），請參閱 [配置IIS Web伺服器](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

安裝步驟完成後，您需要配置實例、資料庫和伺服器。 有關詳細資訊，請參閱 [關於初始配置](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>將Adobe Campaign部署到Windows環境時，具有必要訪問權限的用戶可以在網路上的檔案操作期間使用UNC語法(Universal.Uniform Naming Convention)來獲取訪問路徑。
