---
title: 實作
seo-title: 實作
description: 實作
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 實作{#implementation}

下面是一個圖表，其中包含了此場景中涉及的不同步驟。

![](assets/message-center-uc1.png)

首先，從設計附件開始。 請參閱這 [篇文章](../../delivery/using/attaching-files.md#attach-a-personalized-file)。 這可讓您將檔案附加至電子郵件，即使這些檔案並非由執行例項代管。

您可以透過SOAP訊息觸發器傳送電子郵件。 有關SOAP請求的詳細資訊，請參閱事 [件說明](../../message-center/using/event-description.md)。 在SOAP呼叫中，有URL參數(attachmentURL)。

設計電子郵件時，請按一下 **[!UICONTROL Attachment]** 。 在螢幕 **[!UICONTROL Attachment definition]** 中，輸入SOAP附件參數：

```
<%= rtEvent.ctx.attachementUrl %>
```

當消息處理／部署時，系統將從遠程位置（第三方伺服器）獲取檔案，並將其附加到單個消息。

由於此參數可以是變數，因此它應接受您檔案的完整格式遠端URL變數，並透過SOAP呼叫傳送。

![](assets/message-center-uc2.png)

