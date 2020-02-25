---
title: 時區管理
seo-title: 時區管理
description: 時區管理
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# 時區管理{#time-zone-management}

## 操作原則 {#operating-principle}

Adobe Campaign可讓您根據其時區來表示日期：這可讓國際使用者在不同的時區工作。 使用相同例項的每個國家／地區都可以管理促銷活動的執行、追蹤、封存等。 視當地時間而定。

為了讓Adobe Campaign平台在國際範圍內使用，系統使用的所有日期都必須可連結至時區。 因此，已知時區的日期可以匯入至任何其他時區，或不論時區為何。

Adobe Campaign可讓您以UTC（協調的通用時間）格式儲存日期／時間。 資料公開時，會轉換為運算子的本機日期／時間。 當資料庫以UTC配置時，轉換會自動執行(請參 [閱Configuration](#configuration))。 如果資料庫未在UTC中配置，則平台中日期的時區資訊儲存在一個選項中。

與時區管理相關的主要平台功能包括：匯入／匯出資料和運算子，以及工作流程管理。 繼承 **概念適用於** 「匯入／匯出」或「工作流程」。 預設情況下，它們是為資料庫伺服器時區配置的，但您可以為工作流甚至單個活動重新定義新時區。

**運算子** 可在傳送設定 **期間修改時區** ，並可指定執行傳送的特定時區。

>[!CAUTION]
>
>如果資料庫不管理多個時區，則對於所有資料過濾操作，必須在資料庫伺服器的時區中執行SQL查詢。

每個Adobe Campaign運算子都會連結至時區：此資訊是在其設定檔中設定的。 For more on this, refer to [this document](../../platform/using/access-management.md).

當Adobe Campaign平台不需要時區管理時，您可以使用特定連結時區的本機格式來維持儲存模式。

## 建議 {#recommendations}

時區結合了幾個現實：該表達式可以用UTC日期描述恆定的時差，或者用每年可能改變兩次的區域的時間（日光節約時間）來描述。

**例如，在postgreSQL中，** SET TIME ZONE &#39;Europe/Paris&#39;;command將考慮夏季和冬季時間：日期將以UTC+1或UTC+2表示，具體取決於年份的時間。

**但是，如果使用** SET TIME ZONE 0200;命令時，時差將始終為UTC+2。

## 配置 {#configuration}

在建立資料庫期間，會選擇日期和時間的儲存模式(請參 [閱建立新實例](#creating-a-new-instance))。 在進行移轉時，連結至日期的小時數會轉換為本機日期和小時數(請參 [閱移轉](#migration))。

從技術角度看，在資料庫中儲存 **Date+time** type資訊有兩種方式：

1. 時間戳記，時區格式：資料庫引擎以UTC儲存日期。 每個開啟的作業都會有時區，並會根據時區轉換日期。
1. 本地格式+本地時區：所有日期都以本機格式儲存（無時差管理），並指派單一時區給它們。 時區會儲存在Adobe Campaign例項的 **WdbcTimeZone** ，並可透過樹狀結構 **[!UICONTROL Administration > Platform > Options]** 的選單加以變更。

>[!CAUTION]
>
>請注意，此項修改可能會導致資料一致性和同步問題。

### 建立新實例 {#creating-a-new-instance}

若要讓數位國際使用者在同一個例項上工作，您在建立該例項時，必須設定時區，以管理各國之間的時差。 在建立實例期間，在資料庫配置階段的部分中選 **[!UICONTROL Time zone]** 擇日期和時間管理模式。

選中 **[!UICONTROL UTC database (date fields with time zone)]** 以UTC格式（SQL欄位和XML欄位）儲存所有日期和時間的資料選項。

![](assets/install_wz_select_utc_option.png)

>[!CAUTION]
>
>如果使用 **Oracle**，則Oracle客戶端層的時區檔案(.dat)必須與伺服器上安裝的時區檔案相容。

如果資料庫不是UTC，則可以選擇下拉清單中提供的時區之一。 您也可以使用伺服器的時區，或選擇「UTC（協調通用時間）」選項。

![](assets/install_wz_unselect_utc_option.png)

選擇該 **[!UICONTROL UTC Database (date fields with time zone)]** 選項後，SQL欄位將以TIMESTAMP WITH TIMEZONE格式儲存。

否則，它們將以本地格式儲存，您需要選擇要應用於資料庫的時區。

### 移轉 {#migration}

遷移至舊版（不需要時區管理）時，您需要在資料庫中定義日期儲存模式。

為確保與存取Adobe Campaign資料庫的外部工具相容， **Date+time** type SQL欄位預設會以本機格式儲存。

包含日期的XML欄位現在會儲存在UTC中。 在載入期間，非UTC格式的欄位會使用伺服器的時區自動轉換。 這表示所有XML欄位將逐步轉換為UTC格式。

要使用現有實例，請添加 **WdbcTimeZone** 選項並輸入實例的時區。

>[!CAUTION]
>
>請確保為WdbcTimeZone選項配置了正確的值：稍後所做的改變可能會導致不一致。

可能值的範例：

* 歐洲／巴黎，
* 歐洲／倫敦
* America/New_York等

   這些值取自tz(Olson)資料庫。 如需詳細資訊，請參閱 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。

