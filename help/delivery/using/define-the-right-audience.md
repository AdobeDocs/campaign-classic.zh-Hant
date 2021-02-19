---
solution: Campaign Classic
product: campaign
title: 定義正確受眾
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: fe7ff64d24113e026a47aa1c9f08daacce2b383e
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---


# 定義正確受眾 {#define-the-right-audience}

目標人口是關鍵：仔細建立您的清單、在熱門的電子郵件用戶端和行動裝置上測試您的電子郵件，並確保您的電子郵件清單是最新的（沒有未知或過時的位址）。 您也可以傳送校樣，協助設定完整的驗證週期。

在本節](../../delivery/using/steps-defining-the-target-population.md)中進一步瞭解目標人口族群[

## 鎖定適當的對象{#target-the-right-audience}

當您的內容準備好時，您需要仔細定義將收到訊息的對象。

為了讓傳遞成功，您想要將最相關的個人化內容傳送給適當的收件者。 Adobe Campaign可讓您建立最精確的目標：您可以根據收件者的年齡、當地語系、他們購買的商品，如果他們點選先前遞送的連結，等等。 有了Adobe Campaign，您也可以定義測試設定檔、控制群組和種子位址，以確定您的目標正確無誤。

## 目標映射{#target-mappings}

在Campaign Classic中，預設會將傳送範本定位在&#x200B;**收件者**。 Adobe Campaign會為您的傳送提供其他目標對應，您可以根據需要進行變更。

例如，您可以將描述檔透過社交網路收集到的訪客或訂閱資訊服務的訪客傳送至訪客。

這些映射在本節](../../delivery/using/selecting-a-target-mapping.md)中顯示。[

您也可以建立和使用自訂的目標對應。 如需詳細資訊，請參閱[本章節](../../configuration/using/target-mapping.md)。

## 外部收件者{#external-recipients}

您可以將內容傳送給儲存在外部檔案而非儲存在資料庫中的收件者。 瞭解本節](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)的更多資訊。[

## 傳送給您的訂閱者{#send-to-subscribers}

若要傳送訊息給電子報的訂閱者，您可以直接將訂閱者鎖定在對應的資訊服務。 瞭解本節](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)的更多資訊。[


## 測試收件人和種子地址{#test-recipients-seed-addresses}

若要測試傳送內容，請在傳送至主要目標之前先使用校樣。

請確定您選取了適當的校樣收件者，因為他們會驗證訊息的表單和內容。 定義校樣收件者的步驟在本節](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)中介紹。[

種子地址用於定位不符合定義的目標標準的接收者，以便在發送到主目標之前測試傳送。 本節](../../delivery/using/about-seed-addresses.md)中列出了它們。[

## 消除地址{#deduplicate-addresses}重複

請務必避免使用重複的電子郵件位址，因為這會對您的目標產生影響：

* 分割目標時，可多次傳送相同的訊息。

* 如果收件者在收到訊息後取消訂閱，其重複的描述檔仍會收到未來的訊息。

刪除重複地址可保護您的發送信譽並確保良好的隔離管理。

**相關主題：**

* [重複資料消除活動](../../workflow/using/deduplication.md)。
* [使用案例：使用重複資料消除活動的合併功能](../../workflow/using/deduplication-merge.md)

## 索引電子郵件地址{#index-addresses}

要優化應用程式中使用的SQL查詢的效能，可以從資料模式的主元素中聲明索引。

將索引添加到電子郵件地址的步驟在本節](../../configuration/using/database-mapping.md#indexed-fields)中顯示。[
