---
title: 個人化資料
seo-title: 個人化資料
description: 個人化資料
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 個人化資料{#personalization-data}

可以使用消息模板中的資料來測試事務性消息個性化。 此功能可用來產生預覽或傳送校樣。 如果您安裝了 **Deliverability** module，則此資料允許您顯示各種Internet訪問提供商的消息渲染(收件箱&#x200B;**渲染**:有關此內容的詳細資訊，請參 [閱本節](../../delivery/using/about-deliverability.md))。

此資料的目的是在訊息最終傳遞之前先進行測試。 這些消息與要由消息中心處理的實際資料不一致。 但是，XML結構必須與儲存在執行實例中的事件結構相同，如下所示。

![](assets/messagecenter_create_custo_006.png)

此資訊可讓您使用個人化標籤來個人化訊息內容(如需詳細資訊，請參 [閱建立訊息內容](../../message-center/using/creating-message-content.md))。

1. 在訊息範本中，按一下標 **[!UICONTROL Seed addresses]** 簽。
1. 在事件內容中，以XML格式輸入測試資訊。

   ![](assets/messagecenter_create_custo_001.png)

