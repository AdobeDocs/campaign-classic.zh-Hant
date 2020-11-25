---
solution: Campaign Classic
product: campaign
title: 隱私權與同意
description: 進一步瞭解隱私權與同意
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# 隱私權常見問答集 {#privacy-faq}

以下是使用Adobe Campaign時有關隱私權與同意的常見問題。

## 主要條款 {#key-terms}

**隱私權的主要條款為何？**

下列項目會連結至Adobe Campaign中與隱私權和同意相關的主要條款與概念：

* [隱私權管理規定](../../platform/using/privacy-management.md#privacy-management-regulations)
* [個人資料與角色](../../platform/using/privacy-and-recommendations.md#personal-data)
* [存取權與被遺忘權](../../platform/using/privacy-management.md#right-access-forgotten)
* [同意、保留和角色](../../platform/using/privacy-management.md#consent-retention-roles)

## 隱私權法規準備 {#privacy-regulations-readiness}

**Adobe Campaign建議您遵守最新的隱私權法規嗎？**

Adobe不提供法律建議。 您應與自己的法律顧問合作，確保他們採取一切必要步驟，以便做好GDPR、CCPA、PDPA、LGPD或任何其他適用法規的準備。

**準備資料存取和刪除請求**

* 識別接收／回應資料主體要求的程式，包括指定隱私權聯絡點。

* 檢閱儲存在Adobe Campaign中的各種客戶資料，並判斷唯一識別碼（可能不止一個）。

* 確定驗證／驗證策略和資料主體身份確認流程。

* 請確定「資料主體」回應易於理解。

**考慮同意**

* 視需要列出並更新GDPR資料擷取的所有接觸點（例如，考慮語言、同意機制和同意記錄）。

* 請確定所有行銷電子郵件都包含取消訂閱連結。

* 評估電子郵件行銷的全球策略，以決定地理特定的實施。

**瞭解您的資料**

* 檢閱所有資料匯入並擷取資料流入Adobe Campaign的來源，並記錄用於行銷工作的欄位。

* 從您的Adobe Campaign資料庫移除任何未使用的資料屬性。

* 使用Adobe Campaign中可用的資料來擷取資料，並為收件者提供更佳的個人化體驗。

* 檢閱和更新資料存取權限，協助確保Adobe Campaign的使用者僅能充分運用執行其促銷活動所需的資料，但不能存取其他資料。

* 確保Adobe Campaign的每位使用者都擁有執行其所需工作的適當存取權，但沒有執行其他工作的任何其他權限。

## 保留使用者參與 {#preserve-user-engagement}

**資料掌控者如何取得同意，而對使用者參與的影響最小？**

在某些行銷活動需要同意的情況下，消費者同意需要有效（即，無須靜默即附件或預先勾選的方塊）、解除捆綁，且可能不需要提供服務。

有時甚至需要重新整理某些同意，才能繼續使用後續的資料。

行銷人員不會將這些增強的同意要求視為對有價市場的風險，而是可以將它們視為品牌參與度和忠誠度以及客戶滿意度和信任的真正指標。

## 管理同意 {#manage-consent}

**資料掌控者如何在Adobe Campaign中管理同意？**

Adobe Campaign已提供多種功能，讓行銷人員透過自訂資料欄位或一或多項服務，以比多數行銷人員更高的層級管理同意。

行銷人員應洽詢其法律顧問，以取得如何進行的指引，然後善用Adobe Campaign內建的功能。

例如，將Adobe Campaign中的資料模型擴充為不僅在人們選擇加入時追蹤，還可追蹤選擇加入的時間戳記，以及擷取精確同意範圍的某類指標。

## 資料刪除 {#data-deletion}

**Adobe Campaign中的資料掌控者可以根據資料主體的客戶要求刪除哪些資料？**

所有與資料主體相關的資料都會被刪除，包括現成可用的表格和自訂表格。

技術上而言，所有連結至「資料主體」的資 `integrity="own"` 料都將刪除。

身為資料掌控者，您可以選擇自訂此項，方法是變更資料結構中定義之連結的完整性（例如，若您有商業理由不刪除某些資料）。

**刪除傳送和追蹤記錄時，報表會受到哪些影響？**

Adobe Campaign中的報表是以根據來自傳送和追蹤記錄的匯總資料計算的指標為基礎。 因此，移除個別記錄檔時，不應影響報表上顯示的量度。

## 重新匯入資料 {#re-import-data}

**通常在Adobe Campaign中，記錄會從外部資料來源上傳。 我是否需要留意稍後可能重新匯入資料？**

身為資料掌控者，您需要確保在收到刪除請求時，從所有系統刪除資料主體的所有必要資料。

## 再次選擇加入 {#opt-in-again}

**資料主體（其資料已從Adobe Campaign中清除）可以稍後再次選擇加入嗎？**

資料主體可能會再次選擇加入，或在其資料從Adobe Campaign中刪除後以新收件者身分新增。

您可以使用稽核線索，詳細瞭解執行先前刪除的時間和建立新收件者的時間。