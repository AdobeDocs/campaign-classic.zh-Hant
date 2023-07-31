---
product: campaign
title: 移轉至Campaign Classic
description: 瞭解如何從舊版Campaign移轉至Campaign Classic
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 3%

---

# 開始使用移轉{#about-migration}



本檔案詳細說明移轉的必要條件，以及移轉至Adobe Campaign Classic v7的步驟。 步驟和可選設定取決於您的設定。

移轉程式必須謹慎執行，其影響必須事前充分考慮，且程式必須嚴格執行。 該操作必須僅由專家使用者執行。 我們強烈建議您聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 開始任何移轉程式之前。

必須先在測試/預備環境中測試移轉，以確保其順利執行且沒有任何錯誤。 只有在移轉的測試環境經完整驗證後，才能執行生產環境移轉。

>[!NOTE]
>
>Adobe Campaign v7的新功能和改進專案詳情，請參見 [發行說明](../../rn/using/latest-release.md).


## 必要條件

* 移轉程式必須由專家使用者執行。 您必須至少有來自Adobe Campaign的資料庫專家、系統管理員和應用程式開發人員協助。
* 開始移轉之前，請檢查您使用的系統和系統元件是否與v7相容。 [了解更多](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign雲端通訊（中間來源部署），請在開始前聯絡Adobe客戶服務。
* 開始移轉程式之前，請先請 **必須** 備份您的資料。
* 移轉程式可能需要數天的時間才能完成。
* Adobe Campaign v7是比舊版更安全的版本：這會影響設定指南，以避免資料損毀之類的問題，並維護資料庫中的資料完整性。 身為客戶，您有責任測試所有設定，包括工作流程。

如需更多必備條件，請參閱 [此頁面](../../migration/using/before-starting-migration.md).


## 現代化環境 {#modernizing-your-environment}

執行移轉可能是更新環境（資料庫引擎、作業系統）的機會。 Adobe Campaign強烈建議您將生產環境升級至最新版本。

>[!CAUTION]
>
>如需Adobe Campaign v7所支援版本的進一步資訊，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md).

## 重要移轉步驟 {#key-migration-steps}

移轉至Adobe Campaign v7的一般程式詳見 [此頁面](../../migration/using/before-starting-migration.md).


## 特定設定 {#specific-configurations}

Adobe Campaign v7帶來的變更可能也代表您必須調整在舊版中開發的特定設定。 因此，您可能需要在移轉前對所有設定執行稽核：如需任何協助，請聯絡Adobe Campaign 。

例如，應特別注意Web應用程式、具有SQL資料的結構描述擴充功能或現成可用的結構描述複製的特定設定。 如需詳細資訊，請參閱[本頁面](../../migration/using/configuring-your-platform.md)。

同樣地，為了回應Adobe Campaign中增強的安全性，部分內部機制已修改：您必須據此調整這些設定。

