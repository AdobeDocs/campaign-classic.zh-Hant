---
product: campaign
title: 定義正確對象
description: 了解選取對象時的最佳實務
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 4%

---

# 定義正確對象 {#define-the-right-audience}



目標人口是關鍵：請謹慎建立清單，在熱門的電子郵件用戶端和行動裝置上測試您的電子郵件，並確保您的電子郵件清單為最新狀態（沒有未知或過時的地址）。 您也可以傳送校樣，協助您設定完整的驗證週期。

深入了解目標母體 [在本節](steps-defining-the-target-population.md)

## 鎖定正確的對象 {#target-the-right-audience}

當您的內容準備就緒時，您必須謹慎定義將接收訊息的對象。

為了讓傳遞成功，您想要將最相關的個人化內容傳送給正確的收件者。 Adobe Campaign可讓您建立最精確的目標：您可以根據收件者的年齡、當地語系化、他們購買的內容，以及他們按一下先前傳遞的連結等來選取收件者。 使用Adobe Campaign，您也可以定義測試設定檔、控制群組和種子地址，以確保目標正確無誤。

## 目標對應 {#target-mappings}

依預設，在Campaign Classic中，傳遞範本目標為 **收件者**. Adobe Campaign提供您傳送的其他目標對應，您可以根據需求進行變更。

例如，您可以傳送給已透過社交網路收集其設定檔的訪客，或傳送給已訂閱資訊服務的訪客。

這些映射會呈現 [在本節](selecting-a-target-mapping.md).

您也可以建立和使用自訂的目標對應。 如需詳細資訊，請參閱[本章節](../../configuration/using/target-mapping.md)。

## 外部收件者 {#external-recipients}

您可以傳送給儲存在外部檔案中而非儲存在資料庫中的收件者。 深入了解 [在本節](steps-defining-the-target-population.md#selecting-external-recipients).

## 傳送給您的訂閱者 {#send-to-subscribers}

若要傳送訊息給電子報的訂閱者，您可以直接將訂閱者鎖定在對應的資訊服務。 深入了解 [在本節](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## 測試收件者和種子地址 {#test-recipients-seed-addresses}

若要測試您的傳送，請在傳送至主要目標之前使用校樣。

請確定您選取適當的校樣收件者，因為他們會驗證訊息的表單和內容。 會顯示定義校樣收件者的步驟 [在本節](steps-defining-the-target-population.md#selecting-the-proof-target).

種子地址用於定位不符合定義的目標標準的收件者，以便在發送到主目標之前測試傳遞。 會呈現 [在本節](about-seed-addresses.md).

## 去重複地址 {#deduplicate-addresses}

請務必避免有重複的電子郵件地址，因為這可能會影響您的目標：

* 分割目標時，可以多次傳送相同的訊息。

* 如果收件者在收到訊息後取消訂閱，其重複的設定檔仍會收到未來的訊息。

重複刪除地址可保護您的發送信譽並確保良好的隔離管理。

**相關主題：**

* [重複資料刪除活動](../../workflow/using/deduplication.md).
* [使用案例：使用重複資料刪除活動的合併功能](../../workflow/using/deduplication-merge.md)

## 索引電子郵件地址 {#index-addresses}

要優化應用程式中使用的SQL查詢的效能，可以從資料架構的主要元素聲明索引。

將顯示將索引新增至電子郵件地址的步驟 [在本節](../../configuration/using/database-mapping.md#indexed-fields).
