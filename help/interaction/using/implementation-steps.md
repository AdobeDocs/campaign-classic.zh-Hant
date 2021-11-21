---
product: campaign
title: 實施步驟
description: 實施步驟
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---

# 實施步驟{#implementation-steps}

![](../../assets/v7-only.svg)

## 設定互動 {#configuring-interaction}

>[!NOTE]
>
>下列步驟應由 **管理員** 設定檔，且僅限在設計環境中。

1. 建立使用者設定檔。 有關詳細資訊，請參閱 [運算元描述檔](../../interaction/using/operator-profiles.md).
1. 依目標維度建立優惠方案環境。 有關詳細資訊，請參閱 [建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. 為每個環境建立類型規則。 有關詳細資訊，請參閱 [建立和參考優惠方案簡報規則](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. 為每個環境建立優惠方案空間並設定轉譯功能。 有關詳細資訊，請參閱 [建立優惠方案空間](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >如果空間由標識模式上的統一通道定義，則必須為此空間指定高級參數。

1. 為入站互動設定選件引擎，以呈現和更新一或多個選件。

   若要了解各種整合模式，請參閱 [關於傳入頻道](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >在入站Web頻道上建立空間時，也需要在將顯示選件的網站上進行設定。

## 管理優惠方案目錄 {#managing-the-offer-catalog-}

>[!NOTE]
>
>下列步驟應由 **優惠方案管理員**.

1. 在設計環境中建立優惠方案類別。 有關詳細資訊，請參閱 [建立優惠方案類別](../../interaction/using/creating-offer-categories.md).
1. 在設計環境中建立優惠方案。 有關詳細資訊，請參閱 [建立優惠方案](../../interaction/using/creating-an-offer.md).
1. 在一或多個空間核准和發佈優惠方案，以便供傳遞管理員在即時環境中使用。 有關詳細資訊，請參閱 [核准和啟用優惠方案](../../interaction/using/approving-and-activating-an-offer.md).

## 使用優惠方案目錄 {#using-the-offer-catalog-}

>[!NOTE]
>
>下列步驟應由 **傳送管理員** 設定檔。 他們只能編輯即時環境中的選件。

1. 建立行銷活動.
1. 參考促銷活動或促銷活動傳送中的選件。 有關詳細資訊，請參閱 [關於傳出頻道](../../interaction/using/about-outbound-channels.md).
