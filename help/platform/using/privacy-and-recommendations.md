---
title: 隱私權和建議
seo-title: 隱私權和建議
description: 隱私權和建議
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 33bf5c5a08613cf88eaace91b85a76157cac7ba1

---


# 隱私權和建議{#privacy-and-recommendations}

## 有關隱私權及許可 {#about-privacy-and-consent}

Adobe Campaign 是一款強大的工具，用於收集和處理包括個人資訊在內的超大資料。我們鼓勵Adobe Campaign的所有使用者在法規（DPA、CAN-SPAM、歐洲隱私與電子通訊指令、歐洲GDPR、CCPA等）範圍內工作，以負責任和道德的方式使用個人資訊，避免傳送未經請求的電子郵件、推播通知和SMS訊息（「垃圾訊息」）。 在打造顧客終生價值及忠誠度的過程中，我們篤信許可式行銷原則，因此我們嚴格禁止使用 Adobe Campaign 傳送未經請求的訊息。

如需詳細資訊，請參閱 [Adobe Experience Cloud 隱私權](https://www.adobe.com/privacy/marketing-cloud.html)。

請前往[安全性和隱私權檢查清單](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)，以了解有關安全性和隱私權需要檢查的核心元素。

## 隱私權管理 {#privacy-management}

GDPR（通用資料保護規則）是歐盟(EU)的隱私法，協調資料保護要求並以現代化方式規範資料保護要求。 GDPR 適用於所持有資料的主體居住於歐盟的 Adobe Campaign 客戶。

CCPA（加州消費者隱私法）為加州居民提供個人資訊的新權利，並對在加州經營業務的特定實體負有資料保護責任。

除了同意管理、資料保留設定和權限管理外，我們還以資料處理者的角色提供額外的功能，以協助您做好準備，做為資料掌控者，處理特定隱私權要求。

在本文 [章中](https://helpx.adobe.com/campaign/kb/acc-privacy.html)，您將瞭解Adobe Campaign如何協助您管理不同的隱私權關鍵功能：存取權、被遺忘權、同意權、資料保留權和使用者角色。 您也會找到最佳實務，以協助您在使用我們的服務時符合隱私權規範。

## Cookie 和追蹤功能 {#cookies-and-tracking-capabilities}

有了 Adobe Campaign 的追蹤功能，您可以追蹤內容接收者在網站上的瀏覽痕跡。Adobe Campaign 透過工作階段 Cookie 和永久性 Cookie 實現上述功能。

有關「隱私及電子通訊」的歐洲法令 2009/136/CE 和歐洲一般資料保護規範 (GDPR) 規定，公司在安裝任何 Cookie 之前都需要取得網站使用者之同意。您必須透過授權請求 (有時出現在網站頁面中) 告知使用者，網站已載入追蹤工具並要求使用者點擊核取方塊授權安裝 Cookie，或在使用者登陸的首頁頂端新增橫幅等。請不要使用彈出式視窗，因為彈出式視窗經常被瀏覽器封鎖。

帶有選擇退出橫幅的網路應用程式與登陸頁面都可以設定使用者追蹤管理。請參見[此頁面](../../web/using/web-application-tracking-opt-out.md)。

Adobe Campaign 使用兩種類型的 Cookie：

1. 工作階段 Cookie (nlid)：它包含傳送到連絡人之電子郵件的識別碼 (broadlogId)，以及訊息範本的識別碼 (deliveryId)。連絡人按一下由 Adobe Campaign 傳送的電子郵件中包含的 URL 後即可添加識別碼，並且允許您追蹤他們在網路上的行為。瀏覽器關閉時，將自動清除工作階段 Cookie。連絡人可以將其瀏覽器設定為拒絕 Cookie。
1. 永久性 Cookie (uuid230)：它可讓您在使用者造訪網站時，識別出與 Adobe Campaign 互動的使用者。Adobe Campaign 可使用該 Cookie 計算行銷活動中的點擊數，估算傳輸速率。當聯絡人在電子郵件中點按時，在 Adobe Campaign 填入表單時或傳入互動引擎呼叫期間，將放置此 Cookie。使用者可以將其瀏覽器設定為刪除或拒絕 Cookie。

## 資料庫完整性 {#database-integrity}

Adobe Campaign 具有大量豐富的功能。因此，使用了複雜的資料庫結構。資料庫包含許多資料表、欄位、連結以及索引。某些中繼資料表未顯示在介面中。該軟體會自動建立、刪除或修改特定連結、欄位以及索引。只有 Adobe Campaign 介面 (圖形介面、匯入方案、伺服器模組、網路模組、傳遞伺服器、新增欄位、資料庫延伸模組等等) 可以修改資料庫內容，同時保留資料庫的完整性。

**請勿使用此軟體以外的任何工具修改資料庫內容或結構。**&#x200B;此類修改可能會損毀資料庫，導致意外修改或連結遺失、建立準刪除記錄或連結、嚴重錯誤訊息等，或導致 Adobe Campaign 提供的擔保與技術支援合約無效或廢止等。

在 Adobe Campaign 系統中，所有資料都儲存在資料庫中。此資料是否可用於網路模組的訂閱、管理和取消訂閱，以及管理螢幕、傳遞佇列、傳送最佳化機制等將決定了整個 Adobe Campaign 系統是否可正常運作。

## Apache Tomcat {#apache-tomcat}

Adobe Campaign 中納入了由 Apache Software Foundation ([https://www.apache.org/](https://www.apache.org/)) 開發的 Apache Tomcat。
