---
product: campaign
title: 實施步驟
description: 市場活動交互模組的實施步驟
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# 實施步驟{#implementation-steps}

![](../../assets/v7-only.svg)

## 配置交互 {#configuring-interaction}

>[!NOTE]
>
>以下步驟應由 **管理員** 只在設計環境中。

1. 正在建立用戶配置檔案。 有關此內容的詳細資訊，請參閱 [運算子配置檔案](../../interaction/using/operator-profiles.md)。
1. 通過目標維建立服務環境。 有關此內容的詳細資訊，請參閱 [建立服務環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 為每個環境建立類型規則。 有關此內容的詳細資訊，請參閱 [建立和引用聘用演示規則](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 為每個環境建立提供空間並配置呈現功能。 有關此內容的詳細資訊，請參閱 [建立聘用空間](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空間由標識模式下的酉通道定義，則必須為此空間指定高級參數。

1. 為入站交互配置提供引擎，以呈現和更新一個或多個提供。

   各種整合模式在 [關於入站通道](../../interaction/using/about-inbound-channels.md)。

   >[!NOTE]
   >
   >在入站Web通道上建立空間時，還需要在顯示優惠的站點上進行配置。

## 管理服務目錄 {#managing-the-offer-catalog-}

>[!NOTE]
>
>以下步驟應由 **服務經理**。

1. 在設計環境中建立產品類別。 有關此內容的詳細資訊，請參閱 [建立聘用類別](../../interaction/using/creating-offer-categories.md)。
1. 在設計環境中建立產品。 有關此內容的詳細資訊，請參閱 [建立優惠](../../interaction/using/creating-an-offer.md)。
1. 在一個或多個空間上批准和發佈服務，以便在交付經理的即時環境中提供服務。 有關此內容的詳細資訊，請參閱 [批准和激活聘用](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用優惠目錄 {#using-the-offer-catalog-}

>[!NOTE]
>
>以下步驟應由 **交付經理** 檔案。 他們只能編輯即時環境中的服務。

1. 建立行銷活動.
1. 引用市場活動或市場活動交付中的優惠。 有關此內容的詳細資訊，請參閱 [關於出站通道](../../interaction/using/about-outbound-channels.md)。
