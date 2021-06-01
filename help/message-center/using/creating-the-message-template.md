---
solution: Campaign Classic
product: campaign
title: 設計交易式訊息範本
description: 了解如何在Adobe Campaign Classic中建立和設計交易式訊息範本。
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: a9054fb8e10bef37675922b2f81c7615cd04c1bb
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 設計交易式訊息範本{#creating-the-message-template}

若要確保每個事件都可變更為個人化訊息，您需要建立訊息範本，以符合每個事件類型。

>[!IMPORTANT]
>
>事件類型需要預先建立。 有關詳細資訊，請參閱[建立事件類型](../../message-center/using/creating-event-types.md)。

交易式訊息範本包含個人化交易式訊息的必要資訊。 您也可以使用範本來測試訊息預覽，並在傳送至最終目標之前使用種子地址傳送校樣。 有關詳細資訊，請參閱[測試交易式訊息範本](../../message-center/using/testing-message-templates.md)。

## 建立訊息範本 {#creating-message-template}

1. 前往Adobe Campaign樹狀結構中的&#x200B;**[!UICONTROL Message Center >Transactional message templates]**&#x200B;資料夾。

1. 在交易式訊息範本清單中，按一下滑鼠右鍵並選取下拉式選單中的&#x200B;**[!UICONTROL New]**，或按一下交易式訊息範本清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

   ![](assets/messagecenter_create_model_001.png)

1. 在傳送視窗中，選取適合您要使用之通道的傳送範本。

   ![](assets/messagecenter_create_model_002.png)

1. 視需要變更其標籤。

1. 選取符合您要傳送之訊息的事件類型。

   ![](assets/messagecenter_create_model_003.png)

   事件類型必須預先在主控台中建立。 有關詳細資訊，請參閱[建立事件類型](../../message-center/using/creating-event-types.md)。

   >[!IMPORTANT]
   >
   >無法將事件類型連結到多個模板。

1. 輸入性質和說明，然後按一下&#x200B;**[!UICONTROL Continue]**&#x200B;以建立訊息內文（請參閱[建立訊息內容](#creating-message-content)）。

   ![](assets/messagecenter_create_model_004.png)

## 建立訊息內容{#creating-message-content}

交易式訊息內容的定義與Adobe Campaign中定期傳送的定義相同。 例如，對於電子郵件傳送，您可以建立HTML或文字格式的內容、新增附件或個人化傳送物件。 如需詳細資訊，請參閱[電子郵件傳送](../../delivery/using/about-email-channel.md)的章節。

>[!IMPORTANT]
>
>訊息中包含的影像必須可公開存取。 Adobe Campaign不提供任何交易式訊息的影像上傳機制。\
>與JSSP或webApp不同，`<%=`沒有任何預設逸出。
>
>在此情況下，您必須正確逸出來自事件的每個資料。 此逸出取決於此欄位的使用方式。 例如，在URL中，請使用encodeURIComponent。 要在HTML中顯示，可以使用escapeXMLString。

定義訊息內容後，您可以將事件資訊整合至訊息內文，並加以個人化。 由於個人化標籤，事件資訊會插入文字內文。

![](assets/messagecenter_create_content_001.png)

* 所有個人化欄位皆來自有效負載。
* 可以在交易式訊息中參考一或多個個人化區塊。 在發佈至執行例項期間，區塊內容會新增至傳送內容。

若要將個人化標籤插入電子郵件訊息的內文，請套用下列步驟：

1. 在訊息範本中，按一下符合電子郵件格式（HTML或文字）的索引標籤。

1. 輸入訊息的內文。

1. 在文字本文中，使用&#x200B;**[!UICONTROL Real time events > Event XML]**&#x200B;功能表插入標籤。

   ![](assets/messagecenter_create_custo_002.png)

1. 使用下列語法填入標籤：**元素名稱**。@**屬性名稱**，如下所示。

   ![](assets/messagecenter_create_custo_003.png)

1. 儲存您的內容。

您的訊息現在已準備好成為[tested](../../message-center/using/testing-message-templates.md)。
