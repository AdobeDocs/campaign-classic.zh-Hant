---
product: campaign
title: 定義正確對象
description: 瞭解選取對象時的最佳實務
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Audiences
role: User
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 4%

---

# 定義正確對象 {#define-the-right-audience}

目標人口是關鍵：仔細建立您的清單，在熱門電子郵件使用者端和行動裝置上測試您的電子郵件，並確保您的電子郵件清單是最新的（沒有未知或過時的地址）。 您也可以傳送校樣來幫助設定完整的驗證週期。

進一步瞭解目標母體 [在本節中](steps-defining-the-target-population.md)

## 鎖定正確的對象 {#target-the-right-audience}

內容準備就緒後，您需要仔細定義將接收訊息的人員。

若要成功傳遞，您想要將最相關的個人化內容傳送給正確的收件者。 Adobe Campaign可讓您建立最精確的目標：您可以根據收件者的年齡、本地化、購買內容、是否在上一次傳送中按一下連結等來選取收件者。 透過Adobe Campaign，您還可以定義測試設定檔、控制組和種子地址，以確保您的目標正確無誤。

## 目標對應 {#target-mappings}

在Campaign Classic中，預設為傳遞範本目標 **收件者**. Adobe Campaign為您的傳送提供其他目標對應，您可以視需求加以變更。

例如，您可以傳送給已透過社交網路收集設定檔的訪客，或訂閱資訊服務的訪客。

下列對應會出現 [在本節中](selecting-a-target-mapping.md).

您也可以建立並使用自訂的目標對應。 如需詳細資訊，請參閱[本章節](../../configuration/using/target-mapping.md)。

## 外部收件者 {#external-recipients}

您可以傳遞至儲存在外部檔案中而非儲存在資料庫中的收件者。 瞭解更多 [在本節中](steps-defining-the-target-population.md#selecting-external-recipients).

## 傳送給您的訂閱者 {#send-to-subscribers}

若要傳送訊息給電子報的訂閱者，您可以直接將訂閱者定位到對應的資訊服務。 瞭解更多 [在本節中](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## 測試收件者和種子地址 {#test-recipients-seed-addresses}

若要測試您的傳遞，請在傳送至主要目標之前使用證明。

請務必選取適當的校樣收件者，因為他們會驗證訊息的表單和內容。 以下說明定義校樣收件者的步驟 [在本節中](steps-defining-the-target-population.md#selecting-the-proof-target).

種子地址用於鎖定不符合所定義目標條件的收件者，以便在傳送至主要目標之前測試傳遞。 它們會出現 [在本節中](about-seed-addresses.md).

## 重複位址 {#deduplicate-addresses}

請務必避免電子郵件地址重複，因為這可能會對您的目標造成影響：

* 分割目標時，相同的訊息可以傳送多次。

* 如果收件者在收到訊息後取消訂閱，其重複的設定檔仍會收到未來的訊息。

對地址進行重複資料刪除可保護您的傳送信譽，並確保良好的隔離管理。

**相關主題：**

* [重複資料刪除活動](../../workflow/using/deduplication.md).
* [使用案例：使用重複資料刪除活動的合併功能](../../workflow/using/deduplication-merge.md)

## 為電子郵件地址建立索引 {#index-addresses}

為了最佳化應用程式中使用的SQL查詢效能，可以從資料結構描述的主要元素宣告索引。

說明將索引新增至電子郵件地址的步驟 [在本節中](../../configuration/using/database-mapping.md#indexed-fields).
