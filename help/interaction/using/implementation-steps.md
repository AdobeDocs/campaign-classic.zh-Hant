---
solution: Campaign Classic
product: campaign
title: 實施步驟
description: 實施步驟
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---


# 實施步驟{#implementation-steps}

## 配置交互{#configuring-interaction}

>[!NOTE]
>
>以下步驟應由&#x200B;**管理員**&#x200B;配置式執行，且僅在設計環境中執行。

1. 建立使用者設定檔。 有關詳細資訊，請參閱[Operator profiles](../../interaction/using/operator-profiles.md)。
1. 透過定位維度建立選件環境。 有關詳細資訊，請參閱[建立選件環境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 為每個環境建立類型學規則。 如需詳細資訊，請參閱[建立並參考選件簡報規則](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 為每個環境建立選件空間並配置渲染功能。 有關詳細資訊，請參閱[建立選件空間](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空間由標識模式上的酉通道定義，則必須為此空間指定高級參數。

1. 設定傳入互動的選件引擎，以呈現和更新一或多個選件。

   [關於入站通道](../../interaction/using/about-inbound-channels.md)中詳細介紹了各種整合模式。

   >[!NOTE]
   >
   >在傳入Web頻道上建立空間時，您也必須在要顯示選件的網站上進行設定。

## 管理選件目錄{#managing-the-offer-catalog-}

>[!NOTE]
>
>**選件管理員**&#x200B;應執行下列步驟。

1. 在設計環境中建立選件類別。 如需詳細資訊，請參閱[建立選件類別](../../interaction/using/creating-offer-categories.md)。
1. 在設計環境中建立選件。 如需詳細資訊，請參閱[建立選件](../../interaction/using/creating-an-offer.md)。
1. 在一或多個空間上核准和發佈選件，以便在即時環境中提供給傳送管理員。 如需詳細資訊，請參閱[核准和啟用選件](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用選件目錄{#using-the-offer-catalog-}

>[!NOTE]
>
>**傳送管理員**&#x200B;描述檔應執行下列步驟。 他們只能在即時環境中編輯選件。

1. 建立行銷活動.
1. 參考促銷活動或促銷活動傳送中的選件。 有關詳細資訊，請參閱[關於出站通道](../../interaction/using/about-outbound-channels.md)。

