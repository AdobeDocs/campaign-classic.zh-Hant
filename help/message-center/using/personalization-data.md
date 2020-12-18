---
solution: Campaign Classic
product: campaign
title: 個人化資料
description: 個人化資料
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# 個人化資料{#personalization-data}

可以使用消息模板中的資料來測試事務性消息個性化。 此功能可用來產生預覽或傳送校樣。 如果安裝&#x200B;**Deliverability**&#x200B;模組，則此資料允許您顯示各種網際網路訪問提供商的消息渲染（**收件箱渲染**）:如需詳細資訊，請參閱[本節](../../delivery/using/inbox-rendering.md))。

此資料的目的是在訊息最終傳遞之前先進行測試。 這些消息與要由消息中心處理的實際資料不一致。 但是，XML結構必須與儲存在執行實例中的事件結構相同，如下所示。

![](assets/messagecenter_create_custo_006.png)

此資訊可讓您使用個人化標籤來個人化訊息內容（如需詳細資訊，請參閱[建立訊息內容](../../message-center/using/creating-message-content.md)）。

1. 在消息模板中，按一下&#x200B;**[!UICONTROL Seed addresses]**&#x200B;頁籤。
1. 在事件內容中，以XML格式輸入測試資訊。

   ![](assets/messagecenter_create_custo_001.png)
