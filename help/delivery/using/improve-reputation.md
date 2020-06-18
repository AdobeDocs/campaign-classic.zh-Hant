---
title: 使用Adobe Campaign Classic提升您的聲譽
description: 進一步瞭解如何在使用Adobe Campaign Classic時提升您的聲譽。
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
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---


# 提升您的名譽{#improve-reputation}

為避免讓收件者筋疲力盡，請從目標位置刪除重複的電子郵件地址。 此步驟可保護您的發送信譽並確保良好的隔離管理。 Adobe Campaign提供必要的工具來建置這些建議，並避免ISP將其新增至區塊清單的風險。

為盡量避免重複，必須執行下列動作：

* 必須仔細配置導入
* 修改電子郵件地址時請注意
* 自動匯入時請注意
* 應將配置檔案分類到不同的資料夾

隔離管理介紹在 [本節中](../../delivery/using/understanding-quarantine-management.md)。

在下面，您將找到有關複製和隔離管理的詳細資訊。

您可以按IP位址監控已傳送的電子郵件卷。 此程式需要模式擴展。 您需要擴充Broadlogs表格以新增「公用識別碼」，並建立工作流程以擷取和顯示資料。 如果您需要，請聯絡Adobe。

## 複製 {#duplicates}

擁有重複的電子郵件地址可能會產生多種後果：

* 相同的訊息會多次傳送。 即使Campaign在傳送之前預設會執行去重複化程式，在分割目標時，也無法停止由具有相同內容的不同動作所傳送的相同訊息。
* 未接受取消訂閱請求。 如果收件者在收到訊息後取消訂閱，則其重複的描述檔仍符合日後訊息的資格。

除了選擇加入程式的這種側步外，這種情況還可能導致用戶將郵件視為垃圾郵件，並在ISP觸發塊清單過程。

在資料庫上執行操作時必須特別謹慎：

* 必須仔細配置導入，特別是在選擇協調密鑰時。
* 變更的電子郵件地址也可以是重複的來源。 特別是，兩個具有不同域的地址可以被路由到同一郵箱，例如，在某公司更改了名稱並在特定時間內維護了前一個域的情況下： joe.doe@amce-co.com和joe.doe@acme-rebranded.com。
* 自動匯入（無論是清單匯入還是其他資料庫匯入）是管理描述檔時要考慮的元素。 刪除或移動另一個分區中的配置檔案時會發生什麼情況？ 例如，在下訂單時，可通過自動導入在初始分區中重新建立。
* 可以使用視圖而不是分區來實現將配置檔案儲存在不同資料夾中。 這樣，您可以確定配置式位於同一物理分區中，同時仍能顯示和管理適當的權限。

同樣地，有時不同分區之間的複製是正常的。 例如，當傳送給第三方或不同的公司實體時，出於不同原因，同一個人是收件者是合乎邏輯的。 但是，在同一分區中查找重複項很少是正常的。

## 隔離 {#quarantines}

Adobe Campaign 管理隔離地址的清單。在傳送分析期間，預設會排除隔離地址的收件者： 它們不是目標。 例如，當收件箱已滿或地址不存在時，可以隔離電子郵件地址。 在所有情況下，隔離都符合下列具體規則。

隔離管理介紹在 [本節中](../../delivery/using/understanding-quarantine-management.md)。