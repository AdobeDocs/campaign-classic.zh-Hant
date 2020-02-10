---
title: 關於Adobe Campaign Classic中的傳遞能力
description: 進一步瞭解如何在Adobe Campaign Classic中管理傳遞性。
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 控制您的訊息內容{#control-message-content}

為了提高電子郵件的傳遞率，並確保您的電子郵件送達您的收件人，電子郵件必須遵守下面詳述的若干規則。

## 發件人地址 {#sender-address}

某些ISP在接受消息之前檢查發件人地址(From)的有效性。 錯誤形成的地址可能導致接收伺服器拒絕。 您必須確保在例項層級（功能表）或最常使用的情 **[!UICONTROL Tools > Advanced > Deployment wizard...]**&#x200B;形中提供正確的位址。

## 退出連結和表單 {#opt-out}

依預設，在分析訊息時，排版規則會檢查是否已包含選擇退出連結，並在遺失時產生警告。 您可以變更此規則，以產生錯誤而非簡單警告，並停止傳送離開此連結。

您必須在每次傳送前檢查退出連結是否正常運作。 例如，傳送校樣時，請確定連結有效、表單是線上，且驗證此表格會將欄位的值變 **[!UICONTROL No longer contact this recipient]** 更為 **[!UICONTROL Yes]**。 您應該系統性地進行此檢查，因為在進入連結或更改表單時，總是可能出現人為錯誤。

如果在傳送開始後偵測到有關取消訂閱的問題，則仍可以手動（例如使用大量更新功能）對點按選擇退出連結的收件者執行取消訂閱，即使他們無法確認其選擇。

一般而言，請勿嘗試透過要求收件者填寫電子郵件地址或姓名等欄位，來妨礙想要退出的收件者。 表單應僅包含一個驗證按鈕，且僅應對加密的識別碼執行協調。 要求額外確認是不可靠的：使用者可能有兩個電子郵件地址被重新導向至相同方塊(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件者只能記住第一個位址，並希望透過傳送給另一個位址的訊息取消訂閱，表單將會拒絕訂閱，因為加密的識別碼與輸入的電子郵件地址不符。

## SpamAssassin {#spamassassin}

Adobe Campaign可設定為與SpamAssassin搭配運作。 這樣，可以對電子郵件進行分數，以確定郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

在開始傳送之前，「預覽」標籤可讓您評估風險。 警告訊息會顯示測試結果。

在本節中進一步 [瞭解](../../delivery/using/spamassassin.md)。