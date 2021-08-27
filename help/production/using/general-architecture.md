---
product: campaign
title: 一般架構
description: 一般架構
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# 一般架構{#general-architecture}

![](../../assets/v7-only.svg)

## 最小架構 {#minimum-architecture}

在最低設定中，Adobe Campaign的運作方式為：

* Adobe Campaign應用程式伺服器，
* 資料庫。

   ![](assets/formation_exploitation.png)

此圖表顯示最小體系結構上下文中涉及的唯一流量是：

1. 透過網際網路傳送HTTP通訊協定至Adobe Campaign伺服器，
1. 透過網際網路從Adobe Campaign伺服器傳送和傳送至SMTP通訊協定的流量。

## 分佈式架構 {#distributed-architecture}

Adobe Campaign由多個模組組成，可在數部電腦上劃分。 此操作模式有以下幾項優點：

* 負載平衡，
* 設定模組冗餘，
* 建立依數個服務提供者劃分的架構（對所提供服務的細分）。

![](assets/architecturerepartie.png)

模組在多台機器上的分佈提供了使用的極大靈活性和改進的適應性。

>[!NOTE]
>
>有關各種體系結構的詳細資訊，請參閱[此部分](../../installation/using/general-architecture.md)。

## 開啟埠的清單 {#list-of-open-ports}

| 埠號 | 相關Adobe Campaign模組或應用程式 | 可設定 |
|---|---|---|
| 443/tcp或80/tcp | Web伺服器(Apache/IIS) | 是 |
| 6666/udp（本地） | Adobe Campaign:敘斯洛格德 | 是 |
| 8005/tcp（本地） | Adobe Campaign:網頁模組 | 是 |
| 8080/tcp | Adobe Campaign:web模組(tomcat) | 是 |
| 7777 | 統計伺服器（統計伺服器） | 是 |
