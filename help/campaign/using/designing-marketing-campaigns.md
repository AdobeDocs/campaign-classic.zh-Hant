---
title: 設計行銷宣傳
seo-title: 設計行銷宣傳
description: 設計行銷宣傳
seo-description: null
page-status-flag: never-activated
uuid: e0fd5df6-7516-4ca6-bbdf-243a264d0283
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: a9eb6627-2e51-42d0-9b29-5b798bdf5b33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 設計行銷宣傳{#designing-marketing-campaigns}

Adobe Campaign可讓您定義、最佳化、執行及分析通訊和行銷宣傳。 Adobe Campaign的運作方式類似於行銷策略的統一訂單與執行中心。 如需詳細資訊，請參閱存 [取促銷活動](../../campaign/using/accessing-campaigns.md)[和設定行銷活動](../../campaign/using/setting-up-marketing-campaigns.md)。

此外，行銷資 **源管理(MRM)** (Marketing Resource Management,MRM)模組可讓您以協作模式控制行銷動作，提供對相關任務、預算和行銷資源的完整管理和即時追蹤。 「行銷資源管理」可讓您最佳化並規範內部和外部程式、資源與行銷宣傳以及第三方關係（代理商、印表機等）的管理。 如需詳細資訊，請參閱[本小節](../../campaign/using/about-marketing-resource-management.md)。

>[!NOTE]
>
>如需Adobe Campaign核心功能的詳細資訊，請參閱「快速 [入門](../../platform/using/about-adobe-campaign-classic.md) 」一節。\
>本節將詳細說明在不同通道上進行人口定位、訊息個人化和訊息傳遞的相關 [功能](../../delivery/using/communication-channels.md)。

## 核心概念 {#core-concepts}

下列概念需在促銷活動中知道：

* **行銷活動**

   促銷活動會集中與行銷促銷活動相關的所有元素：傳送、定位規則、成本、匯出檔案、相關檔案等。 每個促銷活動都會附加至一個方案。

   如需此方面的詳細資訊，請參 [閱新增促銷活動](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign)。

* **方案**

   方案可讓您定義日曆期間的行銷動作：啟動、遊說、忠誠等。 每個方案都包含連結至日曆的促銷活動，提供整體檢視。

* **計畫**

   行銷計畫可包含多個方案。 它連結至日曆期間、已分配預算，也可連結至檔案和目標。

   For more on this, refer to [Campaign calendar](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **工作流程**

   促銷活動工作流程包含的活動與所有工作流程相同，但是特定於促銷活動。 它可讓您建立並設定所有可用渠道的傳送。

   如需詳細資訊，請參閱[本小節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。

* **目標**

   在促銷活動、方案或計畫中，您可以列出目標清單。 這些是要達到的量化值。 在促銷活動、方案或計畫結束時，MRM模組可讓您比較專用報表中的目標和結果。

* **傳送大綱**

   傳送大綱是傳送的結構化描述。 每個傳送都可參照傳送大綱，其中包含例如相關選件、要附加的檔案或商店連結。 選件可根據所選的傳送大綱在傳送中參考。

   有關詳情，請參閱關聯 [和建構透過傳送大綱連結的資源](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。
