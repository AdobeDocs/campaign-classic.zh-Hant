---
title: 管理事務性消息中的種子地址
seo-title: 管理事務性消息中的種子地址
description: 管理事務性消息中的種子地址
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 管理事務性消息中的種子地址{#managing-seed-addresses-in-transactional-messages}

種子位址可讓您在傳送電子郵件或簡訊之前，先顯示訊息的預覽、傳送證明，並測試訊息個人化。 種子地址與傳送相連結，不能用於其他傳送。

## 建立種子地址 {#creating-a-seed-address}

1. 在事務性消息模板中，按一下該選 **[!UICONTROL Seed addresses]** 項卡。

   ![](assets/messagecenter_create_seedaddr_001.png)

1. 指派標籤給標籤，以方便日後選取。

   ![](assets/messagecenter_create_seedaddr_002.png)

1. 輸入種子地址（電子郵件或行動電話，視通訊頻道而定）。

   ![](assets/messagecenter_create_seedaddr_003.png)

1. 輸入外部標識符：此可選欄位可讓您輸入商業金鑰（唯一ID、名稱+電子郵件等）網站上所有應用程式的通用識別碼，用來識別您的個人檔案。 如果此欄位也存在於Adobe Campaign行銷資料庫中，則您可以調節事件與資料庫中的描述檔。

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. 插入測試資料(請參 [閱個人化資料](../../message-center/using/personalization-data.md))。

   ![](assets/messagecenter_create_custo_001.png)

## 建立多個種子地址 {#creating-several-seed-addresses}

1. 按一下 **[!UICONTROL Add other seed addresses]** 連結，然後按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/messagecenter_create_seedaddr_004.png)

1. 請遵循「建立種子地址」部分中詳細說明的 [種子地址配置步驟](#creating-a-seed-address) 。
1. 重複此過程，建立所需的地址數。

   ![](assets/messagecenter_create_seedaddr_008.png)

建立地址後，您就可以顯示其預覽和個人化。 請參閱「事 [務性訊息預覽](../../message-center/using/transactional-message-preview.md)」。
