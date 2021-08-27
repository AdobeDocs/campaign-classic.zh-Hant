---
product: campaign
title: 時區管理
description: 時區管理
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# 時區管理{#time-zone-management}

![](../../assets/v7-only.svg)

## 操作原則 {#operating-principle}

Adobe Campaign可讓您根據其時區來表示日期：這可讓國際使用者在不同時區上工作。 使用相同例項的每個國家/地區都可以管理行銷活動、追蹤、封存等的執行。 取決於當地時間。

為使Adobe Campaign平台能夠在國際範圍內使用，系統使用的所有日期都必須可連結到一個時區。 因此，可將其時區已知的日期匯入至任何其他時區，或無論時區為何。

Adobe Campaign可讓您以UTC（協調通用時間）格式儲存日期/時間。 資料公開時，會轉換為運算子的本機日期/時間。 當以UTC配置資料庫時，將自動執行轉換（請參閱[Configuration](#configuration)）。 如果未以UTC配置資料庫，有關平台日期時區的資訊將儲存在選項中。

有關時區管理的主要平台功能包括：匯入/匯出資料和運算子與工作流程管理。 **繼承概念**&#x200B;可用於匯入/匯出或工作流程。 預設情況下，它們是為資料庫伺服器時區配置的，但您可以為工作流乃至單個活動重新定義新時區。

**** 運算子在傳送設定 **期** 間掃描修改時區，並可指定將執行傳送的特定時區。

>[!IMPORTANT]
>
>如果資料庫不管理多個時區，則對於所有資料過濾操作，必須在資料庫伺服器的時區中執行SQL查詢。

每個Adobe Campaign運算子都連結至時區：此資訊會在其設定檔中設定。 有關詳細資訊，請參閱[本文檔](../../platform/using/access-management.md)。

當Adobe Campaign平台不需要時區管理時，您可以透過特定連結的時區，以本機格式保留儲存模式。

## 建議 {#recommendations}

時區結合了幾個現實：該表達式可以用UTC日期描述恆定的時間延遲，或者可能每年更改兩次的區域時間（日光節約時間）。

例如，在postgreSQL中，**SET TIME ZONE &#39;Europe/Paris&#39;;**&#x200B;命令將考慮夏季和冬季時間：日期會根據年份時間，以UTC+1或UTC+2表示。

但是，如果使用&#x200B;**SET TIME ZONE 0200;**&#x200B;命令，則時差將始終為UTC+2。

## 設定 {#configuration}

在資料庫建立期間，會選擇日期和時間的儲存模式（請參閱[建立新實例](#creating-a-new-instance)）。 若是移轉，則連結至日期的小時數會轉換為本機日期和小時數（請參閱[Migration](#migration)）。

從技術角度看，有兩種方式可將&#x200B;**Date+time**&#x200B;類型資訊儲存在資料庫中：

1. 時區格式的時間戳記：資料庫引擎以UTC儲存日期。 每個開啟的工作階段都會有時區，並會根據時區轉換日期。
1. 本地格式+本地時區：所有日期都會以本機格式儲存（無時差管理），且會為其指派單一時區。 時區儲存在Adobe Campaign實例的&#x200B;**WdbcTimeZone**&#x200B;選項中，並可通過樹的&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;菜單進行更改。

>[!IMPORTANT]
>
>請注意，此修改可能會導致資料一致性和同步問題。

### 建立新執行個體 {#creating-a-new-instance}

若要讓數個國際使用者處理同一個執行個體，您必須在建立執行個體時設定時區，以管理國家/地區之間的時差。 在建立實例期間，在資料庫配置階段的&#x200B;**[!UICONTROL Time zone]**&#x200B;部分中選擇日期和時間管理模式。

核取&#x200B;**[!UICONTROL UTC database (date fields with time zone)]**&#x200B;選項，以UTC格式（SQL欄位和XML欄位）儲存具有日期和時間的所有資料。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用&#x200B;**Oracle**,Oracle客戶端層的時區檔案(.dat)必須與伺服器上安裝的時區檔案相容。

如果資料庫不是UTC，則可以選擇下拉清單中提供的時區之一。 您也可以使用伺服器的時區，或選取UTC（協調通用時間）選項。

![](assets/install_wz_unselect_utc_option.png)

選擇&#x200B;**[!UICONTROL UTC Database (date fields with time zone)]**&#x200B;選項後，SQL欄位將以TIMESTAMP WITH TIMEZONE格式儲存。

否則，它們會以本地格式儲存，您需要選取要套用至資料庫的時區。

### 移轉 {#migration}

移轉至較舊版本時（不需要時區管理），您需要在資料庫中定義日期儲存模式。

為了確保與存取Adobe Campaign資料庫的外部工具相容，預設情況下，**Date+time**&#x200B;類型SQL欄位仍以本機格式儲存。

包含日期的XML欄位現在會以UTC儲存。 載入期間，系統會使用伺服器的時區自動轉換UTC格式以外的欄位。 這表示所有XML欄位將逐步轉換為UTC格式。

若要使用現有實例，請添加&#x200B;**WdbcTimeZone**&#x200B;選項並輸入實例的時區。

>[!IMPORTANT]
>
>請確保為WdbcTimeZone選項配置了正確的值：稍後進行的變更可能會導致不一致。

可能的值範例：

* 歐洲/巴黎，
* 歐洲/倫敦，
* America/New_York等

   這些值取自tz(Olson)資料庫。 如需詳細資訊，請參閱[https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。
