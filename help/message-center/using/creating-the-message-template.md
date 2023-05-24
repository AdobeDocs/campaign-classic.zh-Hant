---
product: campaign
title: 設計異動訊息範本
description: 瞭解如何在Adobe Campaign Classic中建立及設計異動訊息範本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 設計異動訊息範本 {#creating-the-message-template}



為確保每個事件都能變更為個人化訊息，您需要建立訊息範本以符合每個事件型別。

>[!IMPORTANT]
>
>事件型別需要預先建立。 有關詳細資訊，請參閱 [建立事件型別](../../message-center/using/creating-event-types.md).

交易式訊息範本包含個人化交易式訊息的必要資訊。 您也可以使用範本來測試訊息預覽，並在傳送至最終目標之前使用種子地址傳送校樣。 如需詳細資訊，請參閱 [測試異動訊息範本](../../message-center/using/testing-message-templates.md).

## 建立訊息範本 {#creating-message-template}

1. 前往 **[!UICONTROL Message Center >Transactional message templates]** Adobe Campaign樹狀結構中的資料夾。

1. 在交易式訊息範本清單中，按一下滑鼠右鍵並選取 **[!UICONTROL New]** 在下拉式功能表中，或按一下 **[!UICONTROL New]** 按鈕（異動訊息範本清單上方）。

   ![](assets/messagecenter_create_model_001.png)

1. 在傳遞視窗中，選取適用於您要使用之管道的傳遞範本。

   ![](assets/messagecenter_create_model_002.png)

1. 視需要變更其標籤。

1. 選取符合您要傳送之訊息的事件型別。

   ![](assets/messagecenter_create_model_003.png)

   事件型別需要預先在主控台中建立。 有關詳細資訊，請參閱 [建立事件型別](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >事件型別無法連結至多個範本。

1. 輸入性質和說明，然後按一下 **[!UICONTROL Continue]** 若要建立訊息內文(請參閱 [建立訊息內容](#creating-message-content))。

   ![](assets/messagecenter_create_model_004.png)

## 建立訊息內容 {#creating-message-content}

交易式訊息內容的定義與Adobe Campaign中定期傳送的定義相同。 例如，對於電子郵件傳遞，您可以建立HTML或文字格式的內容、新增附件或個人化傳遞物件。 如需詳細資訊，請參閱 [電子郵件傳遞](../../delivery/using/about-email-channel.md) 章節。

>[!IMPORTANT]
>
>訊息中包含的影像必須可公開存取。 Adobe Campaign不提供任何異動訊息的影像上傳機制。\
>不同於JSSP或webApp， `<%=` 沒有任何預設逸出。
>
>在此情況下，您必須正確逸出來自事件的每個資料。 此逸出取決於此欄位的使用方式。 例如，在URL中，請使用encodeURIComponent。 若要顯示在HTML中，您可以使用escapeXMLString。

定義訊息內容後，您可以將事件資訊整合至訊息內文並加以個人化。 由於個人化標籤，事件資訊會插入文字內文中。

![](assets/messagecenter_create_content_001.png)

* 所有個人化欄位都來自裝載。
* 可以在交易式訊息中參考一或多個個人化區塊。 區塊內容將在發佈至執行例項期間新增至傳遞內容。

若要將個人化標籤插入電子郵件內文中，請套用下列步驟：

1. 在訊息範本中，按一下符合電子郵件格式(HTML或文字)的索引標籤。

1. 輸入訊息內文。

1. 在文字內文中，使用 **[!UICONTROL Real time events > Event XML]** 功能表。

   ![](assets/messagecenter_create_custo_002.png)

1. 使用下列語法填入標籤： **元素名稱**.@**屬性名稱** 如下所示。

   ![](assets/messagecenter_create_custo_003.png)

1. 儲存您的內容。

您的訊息現在已準備就緒 [已測試](../../message-center/using/testing-message-templates.md).
