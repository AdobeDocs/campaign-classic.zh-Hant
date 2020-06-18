---
title: SpamAssassin
seo-title: SpamAssassin
description: SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 3%

---


# SpamAssassin{#spamassassin}

## 關於SpamAssassin {#about-spamassassin}

Adobe Campaign可設定為可搭配 [SpamAssassin](https://spamassassin.apache.org)（用於電子郵件垃圾訊息篩選的協力廠商服務）運作。 這可讓您對電子郵件進行分數，以判斷收到時使用的反垃圾郵件工具是否會將郵件視為垃圾郵件。

SpamAssassin運用多種垃圾郵件偵測技術，包括：

* 基於DNS和基於模糊校驗和的垃圾郵件檢測
* 貝葉斯濾波
* 外部程式
* 塊清單
* 線上資料庫

>[!NOTE]
>
>SpamAssassin必須安裝並設定在Adobe Campaign應用程式伺服器上。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-spamassassin.md)。
>
>控管元素是否為垃圾訊息的規則會透過SpamAssassin管理，且可由具有權限的管理員編輯。

## 使用SpamAssassin {#using-spamassassin}

在您建立電子郵件傳送並定義其內容後，請依照下列步驟評估風險。

如需建立和設計傳送的詳細資訊，請參閱 [本節](../../delivery/using/about-email-channel.md)。

1. 轉至標 **[!UICONTROL Preview]** 簽。
1. 選取收件者以預覽您的傳送。

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >如果您未選取收件者，將無法執行反垃圾訊息檢查。

1. 警告訊息會顯示測試結果。 如果檢測到高風險，將顯示以下警告消息：

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 按一下 **[!UICONTROL More...]** 警告旁的連結。
1. 選擇選 **[!UICONTROL Anti-spam checking]** 項卡。
1. 請至本節 **[!UICONTROL Points / Rule / Description]** 以檢視此風險的原因。

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>每次按一下時， **[!UICONTROL Anti-spam checking]**&#x200B;都會調用SpamAssassin服務，並再次分析消息以檢測垃圾郵件。 請務必變更內容，然後再執行反垃圾訊息分析。
