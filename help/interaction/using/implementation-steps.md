---
product: campaign
title: 實施步驟
description: Campaign互動模組的實作步驟
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---

# 實施步驟{#implementation-steps}



## 設定互動 {#configuring-interaction}

>[!NOTE]
>
>下列步驟應由&#x200B;**管理員**&#x200B;設定檔執行，並且只應在設計環境中執行。

1. 建立使用者設定檔。 如需詳細資訊，請參閱[運運算元設定檔](../../interaction/using/operator-profiles.md)。
1. 透過目標維度建立優惠方案環境。 如需詳細資訊，請參閱[建立優惠方案環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 為每個環境建立型別規則。 如需詳細資訊，請參閱[建立和參考優惠方案簡報規則](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 為每個環境建立選件空間，並設定演算功能。 如需詳細資訊，請參閱[建立優惠方案空間](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空間是由識別模式上的單一通道所定義，則必須指定此空間的進階引數。

1. 為傳入互動設定優惠方案引擎，以顯示和更新一或多個優惠方案。

   各種整合模式在[關於傳入頻道](../../interaction/using/about-inbound-channels.md)中有詳細說明。

   >[!NOTE]
   >
   >在傳入的Web Channel上建立空間時，顯示優惠方案的網站上也需要設定。

## 管理優惠方案目錄 {#managing-the-offer-catalog-}

>[!NOTE]
>
>**優惠方案管理員**&#x200B;應該執行下列步驟。

1. 在設計環境中建立優惠方案類別。 如需詳細資訊，請參閱[建立優惠方案類別](../../interaction/using/creating-offer-categories.md)。
1. 在設計環境中建立優惠方案。 如需詳細資訊，請參閱[建立選件](../../interaction/using/creating-an-offer.md)。
1. 在一或多個空間上核准和發佈優惠方案，以便在傳遞管理員的即時環境中提供這些優惠方案。 如需詳細資訊，請參閱[核准及啟用優惠方案](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用優惠方案目錄 {#using-the-offer-catalog-}

>[!NOTE]
>
>**傳遞管理員**&#x200B;設定檔應執行下列步驟。 他們只能在即時環境中編輯選件。

1. 建立行銷活動。
1. 在行銷活動或行銷活動傳遞中參考優惠方案。 如需詳細資訊，請參閱[關於傳出頻道](../../interaction/using/about-outbound-channels.md)。
