---
title: 通用架構
seo-title: 通用架構
description: 通用架構
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 通用架構{#general-architecture}

## 最低架構 {#minimum-architecture}

在最低設定中，Adobe Campaign可與下列項目搭配運作：

* Adobe Campaign應用程式伺服器、
* 資料庫。

   ![](assets/formation_exploitation.png)

此圖表顯示，在最小體系結構的上下文中，唯一涉及的流量是：

1. 透過網際網路傳送HTTP通訊協定至Adobe Campaign伺服器，
1. 透過網際網路從Adobe Campaign伺服器傳入和傳入Adobe Campaign伺服器的SMTP通訊協定流量。

## 分佈式體系結構 {#distributed-architecture}

Adobe Campaign由多個模組組成，可劃分成多部電腦。 這種操作模式具有以下幾個優點：

* 負載平衡，
* 設定模組冗餘，
* 建立由數家服務供應商劃分的架構（所提供服務的區段）。

![](assets/architecturerepartie.png)

在多台機器上分配模組提供了極大的使用靈活性和增強的適應性。

>[!NOTE]
>
>有關各種體系結構的詳細資訊，請參 [閱本節](../../installation/using/general-architecture.md)。

## 開啟埠清單 {#list-of-open-ports}

| 埠號 | 關注的Adobe Campaign模組或應用程式 | 可配置 |
|---|---|---|
| 443/tcp或80/tcp | Web伺服器(Apache/IIS) | 是 |
| 6666/udp（本地） | Adobe Campaign:Syslogd | 是 |
| 8005/tcp（本地） | Adobe Campaign:Web模組 | 是 |
| 8080/tcp | Adobe Campaign:Web模組(tomcat) | 是 |
| 7777 | 統計伺服器（stat伺服器） | 是 |

