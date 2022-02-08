---
product: campaign
title: 定義正確對象
description: 在選擇受眾時瞭解最佳做法
feature: Audiences
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 3%

---

# 定義正確對象 {#define-the-right-audience}

![](../../assets/common.svg)

目標人口是關鍵：精心構建您的清單，在常用電子郵件客戶端和移動設備上test電子郵件，並確保您的電子郵件清單是最新的（沒有未知或過時的地址）。 您還可以發送校樣，以幫助設定完整的驗證週期。

瞭解有關目標群體的詳細資訊 [此部分](steps-defining-the-target-population.md)

## 瞄準正確的受眾 {#target-the-right-audience}

當您的內容準備好後，您需要仔細定義接收您的消息的人。

要使交付成功，您希望將最相關的個性化內容發送到正確的收件人。 Adobe Campaign使您能夠構建最準確的目標：您可以根據收件人的年齡、本地化、他們購買的內容，如果他們按一下了先前遞送中的連結，等等來選擇收件人。 使用Adobe Campaign，您還可以定義test配置檔案、控制組和種子地址，以確保目標正確。

## 目標映射 {#target-mappings}

在Campaign Classic中，預設情況下，交貨模板目標 **收件人**。 Adobe Campaign為您的交貨提供了其他目標映射，您可以根據需要進行更改。

例如，您可以向通過社交網路收集個人資料的訪問者或訂閱資訊服務的訪問者發送資料。

這些映射被顯示 [此部分](selecting-a-target-mapping.md)。

您還可以建立和使用自定義的目標映射。 如需詳細資訊，請參閱[本章節](../../configuration/using/target-mapping.md)。

## 外部收件人 {#external-recipients}

您可以傳遞給儲存在外部檔案中而不是保存在資料庫中的收件人。 瞭解更多資訊 [此部分](steps-defining-the-target-population.md#selecting-external-recipients)。

## 發送給您的訂閱者 {#send-to-subscribers}

要向新聞簡報的訂閱者發送消息，您可以直接將訂閱者定位到相應的資訊服務。 瞭解更多資訊 [此部分](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)。


## Test收件人和種子地址 {#test-recipients-seed-addresses}

要test交貨，請在發送到主目標之前使用校樣。

確保您選擇適當的證明收件人，因為他們會驗證表單和郵件內容。 給出了定義證明接收方的步驟 [此部分](steps-defining-the-target-population.md#selecting-the-proof-target)。

種子地址用於目標與定義的目標條件不匹配的收件人，以便在發送到主目標之前test傳遞。 它們是 [此部分](about-seed-addresses.md)。

## 消除重複地址 {#deduplicate-addresses}

避免使用重複的電子郵件地址非常重要，因為這樣會對您的目標產生影響：

* 當目標被拆分時，可以多次發送同一消息。

* 如果收件人在收到消息後取消訂閱，則其重複的配置檔案仍將接收將來的消息。

消除重複地址可保護您的發送信譽並確保良好的隔離管理。

**相關主題：**

* [重複資料消除活動](../../workflow/using/deduplication.md)。
* [用例：使用重複資料消除活動的合併功能](../../workflow/using/deduplication-merge.md)

## 索引電子郵件地址 {#index-addresses}

要優化應用程式中使用的SQL查詢的效能，可以從資料架構的主要元素聲明索引。

將介紹向電子郵件地址添加索引的步驟 [此部分](../../configuration/using/database-mapping.md#indexed-fields)。
