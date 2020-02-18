---
title: 設定您的平台
seo-title: 設定您的平台
description: 設定您的平台
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 40391fbea53757decb48fd937f5e74e8ba6fb207

---


# 設定您的平台{#configuring-your-platform}

Adobe Campaign v7中的某些重大變更需要設定，以確保其有效運作。 遷移前後可能需要這些參數。 本節將介紹相關更改及其配置模式。

在遷移期間， **NmsRecipient** 表將從模式定義重建。 在Adobe Campaign之外對此表的SQL結構所做的任何更改都將丟失。

要檢查的元素範例：

* 如果已將列（或索引）添加到 **NmsRecipient** 表中，但尚未在架構中詳細說明，則不會保存該列。
* 預設情 **況下** ，表空間屬性會回收其值，即部署嚮導中定義的值。
* 如果已將參考視圖添加到NmsRecipient表，則必須在遷移前將其刪除。

此警告還涉及Oracle用戶：如果您在設定檔期 **間新增了usetimestamptz:1** 選項(請參閱時區 [)，則會重建包含至少一個](../../migration/using/general-configurations.md#time-zones)**** date+time欄位的所有表格。

## 移轉前 {#before-the-migration}

移轉至Adobe Campaign v7時，必須設定下列元素。 必須先處理這些元素，才能啟 **動postupgrade**。

* 時區

   在從v5.11平台移轉期間，您必須指定在設定升級期間使用的時區。

   如果要使用「多時區」模式，請參閱「時 [區](../../migration/using/general-configurations.md#time-zones) 」。

   如果將Oracle用作資料庫，請檢查Oracle時區檔案是否已在應用程式伺服器和資料庫伺服器之間正確同步。 For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* 安全區

   基於安全性原因，Adobe Campaign平台不再預設為可存取：您必須配置安全區，這要求在遷移前收集用戶IP地址。

   如需詳細資訊，請參閱「安 [全性](../../migration/using/general-configurations.md#security) 」一節。

* 語法

   JavaScript中的某些語法可能在5.11和6.02版中接受，而v7版中則不再接受，因為使用了新的解釋器。 如需詳細資訊，請參閱 [JavaScript](../../migration/using/general-configurations.md#javascript) 區段。

   同樣地，Adobe Campaign v7中也引入了新語法，以取代以SQLData為基礎的語法。 如果您使用此語法的程式碼元素，則必須加以調整。 有關詳細資訊，請參閱 [SQLData部分](../../migration/using/general-configurations.md#sqldata) 。

* 密碼

   您必須設定「管 **理** 」和「 **內部** 」密碼。 如需詳細資訊，請參閱「使用 [者密碼](../../migration/using/before-starting-migration.md#user-passwords) 」一節。

* 樹狀結構

   如果從v5.11平台移轉，您必鬚根據Adobe Campaign v6規範重新組織樹狀結構資料夾。 如需詳細資訊，請參閱 [Adobe Campaign v7樹狀結構區段](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) 。

* 互動

   如果您使 **用Interaction**，則必須刪除v7中不再存在的所有6.02架構參考。 如需詳細資訊，請參閱「互動 [」一節](../../migration/using/general-configurations.md#interaction) 。

## 移轉後 {#after-the-migration}

運行 **Postupgrade**&#x200B;後，必須考慮以下元素並執行相應的配置。

* 鏡像頁

   鏡像頁面個人化區塊已隨v6.x變更。此新版本可改善存取這些頁面時的安全性。

   如果您在訊息中使用v5個人化區塊，鏡像頁面顯示將會失敗。 Adobe強烈建議在訊息中插入鏡像頁面時使用新的個人化區塊。

   但是，作為臨時解決方案（且鏡像頁面仍然生效），您可以返回舊的個人化區塊，以透過變更選項並將其設 **[!UICONTROL XtkAcceptOldPasswords]** 為來避免此問 **[!UICONTROL 1]**&#x200B;題。 這不會影響新v6.x個人化區塊的使用。

* 語法

   如果您在配置過程中遇到任何與語法相關的錯誤，則必須臨時激活 **serverConf.xml檔案中的** allowSQLInjeption **** 選項，因為這樣您有時間重寫代碼。 在程式碼調整後，請務必重新啟用安全性。 For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 衝突

   移轉是透過程式檔執行，而衝突可能會出現在報表、表單或Web應用程式中。 這些衝突可以從控制台中解決。

   請參閱 [衝突](../../migration/using/general-configurations.md#conflicts) 。

* Tomcat

   如果您自訂安裝資料夾，請務必檢查在移轉後是否正確更新。 有關詳細資訊，請參閱 [Tomcat](../../migration/using/general-configurations.md#tomcat) 部分。

* 報表

   現成可用的報表目前使用v6.x轉換引擎。 如果您已將JavaScript程式碼新增至報表中，某些元素可能會變更。

   請參閱「 [報表](../../migration/using/general-configurations.md#reports) 」區段。

* Web應用程式

   在配置升級後，如果您在連接到已識別的Web應用程式時有任何問題，則必須在serverConf.xml **檔案中啟用** allowUserPassword **** 和sessionTokenOnly **** 選項。 請記得先停用這兩個選項。 如需詳細資訊，請參閱「已識 [別的Web應用程式](../../migration/using/general-configurations.md#identified-web-applications) 」一節。

   視Web應用程式類型及其組態而定，您必須執行其他操作，以確保它們正常運作。

   請參閱「 [Web應用程式](../../migration/using/general-configurations.md#web-applications) 」區段。

   如果從v5.11平台移轉，則必須執行其他配置：如需詳細資訊，請參閱「網頁應 [用程式](../../migration/using/specific-configurations-in-v5-11.md#web-applications) 」一節。

* 安全區。

   在啟動伺服器之前，必須配置安全區。 如需詳細資訊，請參 [閱本節](../../installation/using/configuring-campaign-server.md#defining-security-zones) ，以 [及安全性](../../migration/using/general-configurations.md#security) 。

* 結構描述

   在Red hat中，編輯某些結構時可能會遇到錯誤。 For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* 工作流程

   如果從v5.11平台移轉，您必須控制工作流程執行階段目錄。 For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* 追蹤

   如果從v5.11平台移轉，您必須設定追蹤模式。 For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* 首頁

   如果從v6.02平台移轉，您可以定義其他參數，將舊首頁保留在v6.02。有關詳情，請參閱： [用戶友好：首頁和導覽區](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) 。

* 互動

   如果您使用 **Interaction**，則必須在移轉後調整任何參數。 For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

