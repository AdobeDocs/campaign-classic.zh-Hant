---
product: campaign
title: 設計和執行行銷活動
description: 定義、最佳化、執行和分析行銷活動
role: User
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Campaigns
exl-id: 4e0df18f-3623-4dfb-a2f8-ad293dbc4dd5
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 21%

---

# 設計和執行行銷活動{#designing-marketing-campaigns}


Adobe Campaign可讓您定義、最佳化、執行和分析通訊與行銷活動。 Adobe Campaign就像行銷策略的統一訂單和執行中心。 有關詳細資訊，請參閱 [存取行銷活動](../../distributed/using/accessing-campaigns.md) 和 [建立行銷活動](../../campaign/using/setting-up-marketing-campaigns.md).

此外， **行銷資源管理(RM)** 模組可讓您透過提供相關任務、預算和行銷資源的完整管理和即時追蹤，以合作模式控制行銷動作。 「行銷資源管理」可讓您最佳化並規範內部與外部流程、資源與行銷宣傳，以及第三方關係（代理商、印表機等）的管理。 如需詳細資訊，請參閱[本章節](../../mrm/using/about-marketing-resource-management.md)。

>[!NOTE]
>
>如需Adobe Campaign核心功能的詳細資訊，請參閱 [本節](../../platform/using/about-adobe-campaign-classic.md) 區段。\
>有關各種通道上母體鎖定目標、訊息個人化和訊息傳送的功能，詳情請參閱 [本節](../../delivery/using/steps-about-delivery-creation-steps.md).

![](assets/do-not-localize/how-to-video.png) [在影片中探索行銷活動重要概念](#video)

## 核心概念 {#core-concepts}

在Campaign中需要知道以下概念：

* **Campaign**

  行銷活動會集中與行銷活動相關的所有元素：傳送、目標定位規則、成本、匯出檔案、相關檔案等。 每個行銷活動都會附加至一個方案。

  有關詳細資訊，請參閱 [新增行銷活動](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **方案**

  方案可讓您定義日曆期間的行銷動作：啟動、游說、忠誠度等。 每個方案都包含連結至日曆的行銷活動，提供整體檢視。

* **計畫**

  行銷計畫可包含多個方案。 它連結至日曆期間、已分配預算，也可連結至文件和目標。

  有關詳細資訊，請參閱 [行銷活動行事曆](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **工作流程**

  行銷活動工作流程包含與所有工作流程相同的活動，但專屬於行銷活動。 它可讓您為所有可用通道建立和設定傳送。

  如需詳細資訊，請參閱[本章節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。

* **目標**

  在行銷活動、方案或計畫中，您可以陳述目標清單。 這些是可達到的量化值。 在行銷活動、方案或計畫結束時，MRM模組可讓您在專用報告中比較目標和結果。

* **傳遞大綱**

  傳遞大網是傳遞的結構化說明。 每個傳送都可以參照傳送大網，其中包含相關優惠方案、要附加的檔案或商店連結等。 根據所選的傳遞大網，可在傳遞中參考優惠方案。

  如需詳細資訊，請參閱[本章節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

## 教學課程 {#video}

此影片說明行銷活動的主要概念。

>[!VIDEO](https://video.tv.adobe.com/v/35131?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
