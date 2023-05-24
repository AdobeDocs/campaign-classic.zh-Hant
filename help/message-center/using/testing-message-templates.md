---
product: campaign
title: 測試異動訊息範本
description: 瞭解如何管理交易式訊息中的種子地址，以便在Adobe Campaign Classic中預覽和測試它們
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 2%

---

# 測試異動訊息範本 {#testing-message-templates}



一旦您的 [訊息範本](../../message-center/using/creating-the-message-template.md) 準備就緒，請按照以下步驟預覽和測試。

## 管理異動訊息中的種子地址 {#managing-seed-addresses-in-transactional-messages}

種子地址可讓您在電子郵件或簡訊傳送前顯示訊息預覽、傳送校樣並測試訊息個人化。 種子地址會連結至傳遞，且無法用於其他傳遞。

若要在交易式訊息中建立種子地址，請遵循下列步驟：

1. 在交易式訊息範本中，按一下 **[!UICONTROL Seed addresses]** 標籤。

   ![](assets/messagecenter_create_seedaddr_001.png)

1. 指派標籤給它，以便稍後輕鬆選取。

   ![](assets/messagecenter_create_seedaddr_002.png)

1. 輸入種子地址（電子郵件或行動電話，視通訊通道而定）。

   ![](assets/messagecenter_create_seedaddr_003.png)

1. 輸入外部識別碼：此選擇性欄位可讓您輸入商業金鑰（唯一ID、名稱+電子郵件等） 這是網站上所有應用程式通用的功能，用來識別您的設定檔。 如果此欄位也出現在Adobe Campaign行銷資料庫中，您可以協調事件與資料庫中的設定檔。

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. 插入測試資料(請參閱 [個人化資料](#personalization-data))。

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. 按一下 **[!UICONTROL Add other seed addresses]** 連結，然後按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. 重複此程式，視需要建立多個位址。

   ![](assets/messagecenter_create_seedaddr_008.png)

建立地址後，您可以顯示其預覽和個人化。 請參閱 [交易式訊息預覽](#transactional-message-preview).

## 個人化資料 {#personalization-data}

您可以使用訊息範本中的資料來測試交易式訊息個人化。 此功能用於產生預覽或傳送校樣。 您也可以顯示不同網際網路存取提供者所顯示的訊息。 如需詳細資訊，請參閱 [收件匣轉譯](../../delivery/using/inbox-rendering.md).

此資料的用途是在訊息最終傳送前測試訊息。 這些訊息與要處理的實際資料不一致。 不過，XML結構必須與儲存在執行例項中的事件結構相同，如下所示：

![](assets/messagecenter_create_custo_006.png)

此資訊可讓您使用個人化標籤來個人化訊息內容(如需詳細資訊，請參閱 [建立訊息內容](../../message-center/using/creating-the-message-template.md#creating-message-content))。

1. 選取異動訊息範本。

1. 在範本中，按一下 **[!UICONTROL Seed addresses]** 標籤。

1. 在事件內容中，以XML格式輸入測試資訊。

   ![](assets/messagecenter_create_custo_001.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

## 異動訊息預覽 {#transactional-message-preview}

建立一或多個種子地址和訊息內文後，您可以預覽訊息並檢查其個人化。

1. 在訊息範本中，按一下 **[!UICONTROL Preview]** 標籤。

   ![](assets/messagecenter_preview_001.png)

1. 選取 **[!UICONTROL A seed address]** 下拉式清單中的。

   ![](assets/messagecenter_preview_002.png)

1. 選取先前建立的種子地址，以顯示個人化訊息。

   ![](assets/messagecenter_create_seedaddr_009.png)

使用種子地址，您還可以為各種網際網路存取提供者顯示訊息的呈現。 如需詳細資訊，請參閱 [收件匣轉譯](../../delivery/using/inbox-rendering.md).

## 傳送證明 {#sending-a-proof}

您可以傳送證明至先前建立的種子地址，以測試訊息傳送。

傳送校樣涉及與相同的程式 [定期傳遞](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). 不過，使用交易式訊息傳送時，您需要預先執行下列操作：

* 建立一或多個 [種子地址](#managing-seed-addresses-in-transactional-messages) 替換為 [個人化資料](#personalization-data).
* [建立訊息內容](../../message-center/using/creating-the-message-template.md#creating-message-content).

若要傳送證明：

1. 按一下 **[!UICONTROL Send a proof]** 按鈕。
1. 分析傳遞。
1. 更正任何錯誤並確認傳遞。

   ![](assets/messagecenter_send_proof_001.png)

1. 檢查訊息是否已送達種子地址，其內容是否符合您的設定。

   ![](assets/messagecenter_send_proof_002.png)

校樣可在每個範本中透過 **[!UICONTROL Audit]** 標籤。 如需詳細資訊，請參閱 [傳送證明](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

![](assets/messagecenter_send_proof_003.png)

您的訊息範本現已準備就緒 [已發佈](../../message-center/using/publishing-message-templates.md).