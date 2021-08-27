---
product: campaign
title: 設定您的平台
description: 設定您的平台
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# 設定您的平台{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7中的某些重大變更需要設定，以確保其有效運作。 在移轉前或之後，可能需要這些參數。 本節將介紹相關更改及其配置模式。

在遷移期間，會根據方案定義重建&#x200B;**NmsRecipient**&#x200B;表。 在Adobe Campaign之外對此表的SQL結構所做的任何更改都將丟失。

要檢查的元素範例：

* 如果您已將欄（或索引）新增至&#x200B;**NmsRecipient**&#x200B;表格，但您尚未在架構中詳細說明，則系統不會儲存此欄。
* 預設情況下， **表空間**&#x200B;屬性將回取其值，即部署嚮導中定義的值。
* 如果已將參考視圖添加到NmsRecipient表，則必須在遷移前將其刪除。

此警告也與Oracle使用者有關：如果您在後期升級期間新增了&#x200B;**usetimestamptz:1**&#x200B;選項（請參閱[時區](../../migration/using/general-configurations.md#time-zones)），則會重建至少包含一個&#x200B;**date+time**&#x200B;欄位的所有表。

## 移轉前 {#before-the-migration}

移轉至Adobe Campaign v7時，必須設定下列元素。 在啟動&#x200B;**postupgrade**&#x200B;之前，必須處理這些元素。

* 時區

   從v5.11平台移轉期間，您必須指定在升級後期間要使用的時區。

   如果您想使用「多時區」模式，請參閱[時區](../../migration/using/general-configurations.md#time-zones)區段。

   如果將Oracle用作資料庫，請檢查應用程式伺服器和資料庫伺服器之間的Oracle時區檔案是否已正確同步。 如需詳細資訊，請參閱[Oracle](../../migration/using/general-configurations.md#oracle)區段。

* 安全區域

   基於安全考量，預設不再存取Adobe Campaign平台：您必須設定安全區域，這需要在移轉前收集使用者IP位址。

   如需詳細資訊，請參閱[Security](../../migration/using/general-configurations.md#security)區段。

* 語法

   JavaScript中的某些語法可能在5.11和6.02版中接受，而v7版中則不再接受，因為使用了新的解釋器。 如需詳細資訊，請參閱[JavaScript](../../migration/using/general-configurations.md#javascript)區段。

   同樣地，Adobe Campaign v7也導入了新語法，以取代SQLData型語法。 如果您使用此語法使用程式碼元素，則必須加以調整。 有關詳細資訊，請參閱[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 密碼

   您必須配置&#x200B;**Admin**&#x200B;和&#x200B;**內部**&#x200B;密碼。 有關詳細資訊，請參閱[用戶密碼](../../migration/using/before-starting-migration.md#user-passwords)部分。

* 樹結構

   如果從v5.11平台遷移，則必鬚根據Adobe Campaign v6規範重新組織樹結構資料夾。 如需詳細資訊，請參閱[Adobe Campaign v7樹結構](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure)區段。

* 互動

   如果您使用&#x200B;**Interaction**，則必須刪除v7中已不存在的所有6.02架構參考。 如需詳細資訊，請參閱[Interaction](../../migration/using/general-configurations.md#interaction)區段。

## 移轉後 {#after-the-migration}

執行&#x200B;**postupgrade**&#x200B;後，必須考慮下列元素並執行相應的配置。

* 鏡像頁面

   鏡像頁面個人化區塊已隨v6.x變更。這個新版本可改善存取這些頁面時的安全性。

   如果您在訊息中使用v5個人化區塊，鏡像頁面顯示將會失敗。 Adobe強烈建議在訊息中插入鏡像頁面時，使用新的個人化區塊。

   不過，作為暫時解決方案（且鏡像頁面仍為即時頁面），您可以變更選項&#x200B;**[!UICONTROL XtkAcceptOldPasswords]**&#x200B;並將其設為&#x200B;**[!UICONTROL 1]**，以返回舊的個人化區塊以避免此問題。 這不會影響新v6.x個人化區塊的使用。

* 語法

   如果您遇到與語法相關的錯誤，在升級後期間，必須臨時激活&#x200B;**serverConf.xml**&#x200B;檔案中的&#x200B;**allowSQLInjept**&#x200B;選項，因為這樣您有時間重寫代碼。 調整程式碼後，請務必重新啟用安全性。 有關詳細資訊，請參閱[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 衝突

   移轉是透過升級後執行，而報表、表單或網頁應用程式中可能會出現衝突。 這些衝突可從主控台解決。

   請參閱[衝突](../../migration/using/general-configurations.md#conflicts)部分。

* Tomcat

   如果您自訂了安裝資料夾，請務必確認移轉後資料夾已正確更新。 有關詳細資訊，請參閱[Tomcat](../../migration/using/general-configurations.md#tomcat)部分。

* 報告

   現成可用的所有報表目前都使用v6.x轉譯引擎。 若您已將JavaScript程式碼新增至報表中，某些元素可能會有所變更。

   請參閱[Reports](../../migration/using/general-configurations.md#reports)區段。

* Web應用程式

   升級後，如果連接到已識別的Web應用程式時遇到任何問題，則必須激活&#x200B;**serverConf.xml**&#x200B;檔案中的&#x200B;**allowUserPassword**&#x200B;和&#x200B;**sessionTokenOnly**&#x200B;選項。 請記得停用這兩個選項。 有關詳細資訊，請參閱[已識別的Web應用程式](../../migration/using/general-configurations.md#identified-web-applications)部分。

   您必鬚根據Web應用程式的類型及其配置執行其他操作，以確保它們正常工作。

   請參閱[Web應用程式](../../migration/using/general-configurations.md#web-applications)部分。

   如果從v5.11平台移轉，則必須執行其他設定：有關詳細資訊，請參閱[Web應用程式](../../migration/using/specific-configurations-in-v5-11.md#web-applications)部分。

* 安全區。

   啟動伺服器之前，必須配置安全區域。 有關詳細資訊，請參閱[此部分](../../installation/using/security-zones.md)和[Security](../../migration/using/general-configurations.md#security)部分。

* 結構

   在Red Hat中，編輯特定結構時可能會遇到錯誤。 有關詳細資訊，請參閱[Red-Hat](../../migration/using/general-configurations.md#red-hat)區段。

* 工作流程

   如果從v5.11平台移轉，您必須控制工作流程執行階段目錄。 如需詳細資訊，請參閱[Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows)區段。

* 追蹤

   如果從v5.11平台移轉，您必須設定追蹤模式。 如需詳細資訊，請參閱[追蹤](../../migration/using/specific-configurations-in-v5-11.md#tracking)區段。

* 首頁

   如果從v6.02平台遷移，則可以定義其他參數以將舊首頁保留在v6.02。有關詳細資訊，請參閱[用戶友好性：首頁和導航](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation)部分。

* 互動

   如果您使用&#x200B;**Interaction**，則必須在遷移後調整任何參數。 有關詳細資訊，請參閱[Interaction](../../migration/using/general-configurations.md#interaction)區段。
