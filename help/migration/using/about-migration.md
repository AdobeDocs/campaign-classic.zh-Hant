---
product: campaign
title: 移轉至Campaign Classic
description: 了解如何從舊版Campaign移轉至Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# 開始移轉{#about-migration}



本檔案詳細說明移轉的先決條件，以及移轉至Adobe Campaign Classic v7的步驟。 步驟和選用設定視您的配置而定。

移民進程必須謹慎進行，其影響必須事先充分考慮，而且必須嚴格執行。 只能由專家使用者執行。 強烈建議您與 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 開始任何移轉程式之前。

必須預先在測試/測試環境中測試移轉，以確保其順暢運作，且不會出現任何錯誤。 只有在已移轉的測試環境經過完整驗證後，才必須執行生產環境移轉。

>[!NOTE]
>
>Adobe Campaign v7的新功能和改善項目將於 [發行說明](../../rn/using/latest-release.md).


## 必要條件

* 移轉程式必須由專家使用者執行。 您至少必須得到Adobe Campaign的資料庫專家、系統管理員和應用程式開發人員的協助。
* 開始移轉之前，請先檢查您使用的系統和系統元件是否與v7相容。 [了解更多](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign雲端訊息（中間來源部署），請先聯絡Adobe客戶服務再開始。
* 開始移轉程式前，請 **必須** 備份資料。
* 移轉程式可能需要數天才能完成。
* Adobe Campaign v7是比舊版更安全的版本：這會影響配置指南，以避免資料損壞等問題，並保留資料庫中的資料完整性。 身為客戶，您負責測試所有設定，包括工作流程。

如需更多必要條件，請參閱 [本頁](../../migration/using/before-starting-migration.md).


## 現代化環境 {#modernizing-your-environment}

執行遷移是更新環境（資料庫引擎、作業系統）的機會。 Adobe Campaign強烈建議將生產環境升級至最新版本。

>[!CAUTION]
>
>如需Adobe Campaign v7支援版本的詳細資訊，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md).

## 重要移轉步驟 {#key-migration-steps}

移轉至Adobe Campaign v7的一般程式於 [本頁](../../migration/using/before-starting-migration.md).


## 特定配置 {#specific-configurations}

Adobe Campaign v7帶來的變更也可能意味著您必須調整在舊版中開發的特定設定。 因此，在移轉前，可能需要對所有設定執行稽核：請聯絡Adobe Campaign以取得任何協助。

例如，應特別注意Web應用程式的特定設定、具有SQLdata的架構擴展或現成的架構克隆。 如需詳細資訊，請參閱[本頁面](../../migration/using/configuring-your-platform.md)。

同樣，為了應對Adobe Campaign內加強的安全，一些內部機制也作了修改：您必須據以調整這些設定。

