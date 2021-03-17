---
solution: Campaign Classic
product: campaign
title: 設定您的平台
description: 設定您的平台
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# 設定您的平台{#configuring-your-platform}

Adobe Campaign第7版中的某些重大變更需要設定以確保其有效運作。 遷移前後可能需要這些參數。 本節將介紹相關更改及其配置模式。

在遷移期間，從模式定義重建&#x200B;**NmsRecipient**&#x200B;表。 在Adobe Campaign以外對此表的SQL結構所做的任何更改都將丟失。

要檢查的元素範例：

* 如果已將列（或索引）添加到&#x200B;**NmsRecipient**&#x200B;表中，但您尚未在架構中詳細說明該列（或索引），則不會保存該列。
* 預設情況下，**tablespace**&#x200B;屬性會回收其值，即部署嚮導中定義的值。
* 如果已將參考視圖添加到NmsRecipient表，則必須在遷移前將其刪除。

此警告也涉及Oracle用戶：如果您在播放期間新增了&#x200B;**usetimestamptz:1**&#x200B;選項（請參閱[時區](../../migration/using/general-configurations.md#time-zones)），則會重建包含至少一個&#x200B;**date+time**&#x200B;欄位的所有表格。

## 遷移前{#before-the-migration}

移轉至Adobe Campaignv7時，必須配置以下元素。 在啟動&#x200B;**postupgrade**&#x200B;之前，必須解決這些元素。

* 時區

   在從v5.11平台移轉期間，您必須指定在設定升級期間使用的時區。

   如果要使用「多時區」模式，請參閱[時區](../../migration/using/general-configurations.md#time-zones)部分。

   如果將Oracle用作資料庫，請檢查Oracle時區檔案是否已在應用程式伺服器和資料庫伺服器之間正確同步。 有關詳細資訊，請參閱[Oracle](../../migration/using/general-configurations.md#oracle)部分。

* 安全區

   出於安全原因，Adobe Campaign平台不再預設訪問：您必須配置安全區，這要求在遷移前收集用戶IP地址。

   有關詳細資訊，請參閱[Security](../../migration/using/general-configurations.md#security)部分。

* 語法

   JavaScript中的某些語法可能在5.11和6.02版中接受，而v7版中則不再接受，因為使用了新的解釋器。 如需詳細資訊，請參閱[JavaScript](../../migration/using/general-configurations.md#javascript)一節。

   同樣地，Adobe Campaignv7中引入了新語法來取代基於SQLData的語法。 如果您使用此語法的程式碼元素，則必須加以調整。 有關詳細資訊，請參閱[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 密碼

   您必須設定&#x200B;**Admin**&#x200B;和&#x200B;**Internal**&#x200B;密碼。 有關詳細資訊，請參閱[用戶密碼](../../migration/using/before-starting-migration.md#user-passwords)部分。

* 樹狀結構

   如果從v5.11平台移轉，您必鬚根據Adobe Campaignv6規範重新組織樹結構資料夾。 有關詳細資訊，請參閱[Adobe Campaignv7樹結構](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure)部分。

* 互動

   如果您使用&#x200B;**Interaction**，則必須刪除v7中不再存在的所有6.02架構參考。 如需詳細資訊，請參閱[Interaction](../../migration/using/general-configurations.md#interaction)一節。

## 遷移後{#after-the-migration}

運行&#x200B;**postupgrade**&#x200B;後，必須考慮以下元素並執行相應的配置。

* 鏡像頁

   鏡像頁面個人化區塊已隨v6.x變更。此新版本可改善存取這些頁面時的安全性。

   如果您在訊息中使用v5個人化區塊，鏡像頁面顯示將會失敗。 Adobe強烈建議在消息中插入鏡像頁時使用新的個性化塊。

   但是，作為臨時解決方案（且鏡像頁仍然有效），您可以返回舊的個人化區塊，以透過變更選項&#x200B;**[!UICONTROL XtkAcceptOldPasswords]**&#x200B;並將其設為&#x200B;**[!UICONTROL 1]**&#x200B;來避免此問題。 這不會影響新v6.x個人化區塊的使用。

* 語法

   如果您在配置過程中遇到與語法相關的錯誤，則必須臨時激活&#x200B;**serverConf.xml**&#x200B;檔案中的&#x200B;**allowSQLInjeption**&#x200B;選項，因為這樣您有時間重寫代碼。 在程式碼調整後，請務必重新啟用安全性。 有關詳細資訊，請參閱[SQLData](../../migration/using/general-configurations.md#sqldata)部分。

* 衝突

   移轉是透過程式檔執行，而衝突可能會出現在報表、表單或Web應用程式中。 這些衝突可以從控制台中解決。

   請參閱[衝突](../../migration/using/general-configurations.md#conflicts)一節。

* Tomcat

   如果您自訂安裝資料夾，請務必檢查在移轉後是否正確更新。 有關詳細資訊，請參閱[Tomcat](../../migration/using/general-configurations.md#tomcat)部分。

* 報告

   現成可用的報表目前使用v6.x轉換引擎。 如果您已將JavaScript程式碼新增至報表中，某些元素可能會變更。

   請參閱[Reports](../../migration/using/general-configurations.md#reports)一節。

* Web應用程式

   在配置升級後，如果您在連接到已識別的Web應用程式時有任何問題，您必須在&#x200B;**serverConf.xml**&#x200B;檔案中啟用&#x200B;**allowUserPassword**&#x200B;和&#x200B;**sessionTokenOnly**&#x200B;選項。 請記得先停用這兩個選項。 有關詳細資訊，請參閱[ Insified web applications](../../migration/using/general-configurations.md#identified-web-applications)一節。

   視Web應用程式類型及其組態而定，您必須執行其他操作，以確保它們正常運作。

   請參閱[Web應用程式](../../migration/using/general-configurations.md#web-applications)部分。

   如果從v5.11平台移轉，則必須執行其他配置：有關詳細資訊，請參閱[Web應用程式](../../migration/using/specific-configurations-in-v5-11.md#web-applications)部分。

* 安全區。

   在啟動伺服器之前，必須配置安全區。 如需詳細資訊，請參閱[本節](../../installation/using/security-zones.md)和[安全性](../../migration/using/general-configurations.md#security)一節。

* 結構描述

   在Red Hat中，編輯某些結構時可能會遇到錯誤。 有關詳細資訊，請參閱[Red-Hat](../../migration/using/general-configurations.md#red-hat)部分。

* 工作流程

   如果從v5.11平台移轉，您必須控制工作流程執行階段目錄。 有關詳細資訊，請參閱[Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows)部分。

* 追蹤

   如果從v5.11平台移轉，您必須設定追蹤模式。 有關詳細資訊，請參閱[Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking)部分。

* 首頁

   如果從v6.02平台移轉，您可以定義其他參數，將舊首頁保留在v6.02。有關詳細資訊，請參閱[用戶友好性：首頁和導覽](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation)區段。

* 互動

   如果您使用&#x200B;**Interaction**，則必須在遷移後調整任何參數。 有關詳細資訊，請參閱[Interaction](../../migration/using/general-configurations.md#interaction)部分。

