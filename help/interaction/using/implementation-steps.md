---
title: 實施步驟
seo-title: 實施步驟
description: 實施步驟
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 實施步驟{#implementation-steps}

## 設定互動 {#configuring-interaction}

>[!NOTE]
>
>以下步驟應由管理員配置式 **執行** ，且僅在設計環境中執行。

1. 建立使用者設定檔。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. 透過定位維度建立選件環境。 如需詳細資訊，請參閱「 [建立選件環境」](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 為每個環境建立類型學規則。 如需詳細資訊，請參閱建 [立和參考選件簡報規則](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 為每個環境建立選件空間並配置渲染功能。 如需詳細資訊，請參閱「建立選 [件空間」](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空間由標識模式上的酉通道定義，則必須為此空間指定高級參數。

1. 設定傳入互動的選件引擎，以呈現和更新一或多個選件。

   有關入站通道，將詳細介紹 [各種整合模式](../../interaction/using/about-inbound-channels.md)。

   >[!NOTE]
   >
   >在傳入Web頻道上建立空間時，您也必須在要顯示選件的網站上進行設定。

## 管理選件目錄 {#managing-the-offer-catalog-}

>[!NOTE]
>
>選件管理員應執行下列 **步驟**。

1. 在設計環境中建立選件類別。 如需詳細資訊，請參閱「建立選 [件類別」](../../interaction/using/creating-offer-categories.md)。
1. 在設計環境中建立選件。 如需詳細資訊，請參閱「 [建立選件」](../../interaction/using/creating-an-offer.md)。
1. 在一或多個空間上核准和發佈選件，以便在即時環境中提供給傳送管理員。 如需詳細資訊，請參閱核 [準和啟用選件](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用選件目錄 {#using-the-offer-catalog-}

>[!NOTE]
>
>下列步驟應由「傳送管理員」設 **定檔執行** 。 他們只能在即時環境中編輯選件。

1. 建立促銷活動。
1. 參考促銷活動或促銷活動傳送中的選件。 有關詳情，請參閱關於 [出站渠道](../../interaction/using/about-outbound-channels.md)。

