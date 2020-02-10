---
title: 建立消息內容
seo-title: 建立消息內容
description: 建立消息內容
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# 建立消息內容{#creating-message-content}

交易訊息內容的定義與Adobe Campaign中定期傳送的定義相同。 例如，對於電子郵件傳送，您可以建立HTML或文字格式的內容、新增附件或個人化傳送物件。 如需詳細資訊，請參閱「電子郵件傳 [送」一章](../../delivery/using/about-email-channel.md)。

>[!CAUTION]
>
>訊息中包含的影像必須可公開存取。 Adobe Campaign不提供任何交易訊息的影像上傳機制。\
>與JSSP或webApp不同， `<%=` 沒有任何預設逸出。
>
>在這種情況下，您必須正確地逸出事件中的每個資料。 此逸出取決於此欄位的使用方式。 例如，在URL中，請使用encodeURIComponent。 若要顯示在HTML中，您可以使用escapeXMLString。

在定義了消息內容後，您可以將事件資訊整合到消息正文中並對其進行個性化。 由於個人化標籤，事件資訊會插入文字正文中。

![](assets/messagecenter_create_content_001.png)

* 所有個人化欄位都來自負載。
* 在事務性消息中可以引用一個或多個個性化塊。 在發佈到執行實例期間，塊內容將添加到傳送內容。

若要將個人化標籤插入電子郵件內文，請套用下列步驟：

1. 在訊息範本中，按一下符合電子郵件格式（HTML或文字）的標籤。
1. 輸入消息的正文。
1. 在文字的正文中，使用選單插入標 **[!UICONTROL Real time events>Event XML]** 記。

   ![](assets/messagecenter_create_custo_002.png)

1. 使用下列語法填入標籤：元 **素名稱**。@**屬性名稱** ，如下所示。

   ![](assets/messagecenter_create_custo_003.png)

